# Tweety

Twitter desktop client for linux.

# Installation

Just clone this repository and copy the client anywhere you want.

```bash
git clone git@github.com:tjventurini/tweety.git /tmp/tweety
mv /tmp/tweety/tweety-linux-x64 ~/apps/tweety
```

Now you can add an app launcher as shown below and store it under `~/.local/share/applications/tweety.desktop`.

```
[Desktop Entry]
Type=Application
Version=1.0
Exec=/home/username/apps/tweety/tweety
Name=Tweety
Comment=Custom twitter client for linux.
Icon=/home/username/apps/tweety/icon.png
Terminal=false
Categories=Social
```

Don't forget to refresh the database of application entries afterwards 😉

```bash
update-desktop-database ~/.local/share/applications
```

# Building

If you want to build the client on your own you can read on.

You need to have the latest version of [docker](https://docs.docker.com/get-docker/) installed.

You will have to clone the repository.

```bash
git clone git@github.com:tjventurini/tweety.git
```

Next you will have pull the [nativefier](https://github.com/nativefier/nativefier) container in order to build the application.

```bash
docker pull nativefier/nativefier
```

Now you can build the electron application using the following command.

```bash
docker run --rm -v /path/to/tweety-repo:/src -v /tmp:/target nativefier/nativefier --icon /src/icon.png --name tweety -p linux -a x64 https://twitter.com/ /target/
```

Now you can copy the build wherever you want.

```bash
mv /tmp/tweety-linux-x64 ~/apps/tweety
```