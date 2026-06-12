---
title: "How to enable the flash plugin in google chrome native"
date: 2009-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by WitchCraft on 2009-08-01
Note (you need to have the flash plugin installed already (and verify that it works), for example with firefox):

then open gnome-terminal and go to /opt/google/chrome (or to wherever you installed chrome)

run the command updatedb (note: this might take some time and you might have to run it as root if sudo doesn't help)

now in the console, type:
```

locate libflash

```

You should get something like this:
```

/opt/google/chrome/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashlx.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```


now in /opt/google/chrome/
Create the "plugins" directory, so type:
```

mkdir plugins

```

Now go to the plugins directory:
```

cd plugins

```

Now copy the shared library over to this directory:
```

cp /usr/lib/flashplugin-installer/libflashplayer.so ./

```

go back to the google chrome root direcory:
```

cd ..

```

Now close all running instances of google chrome (otherwise it will just open a new tab, which won't work)
Now run google-chrome with the --enable-plugins option
```

./google-chrome --enable-plugins

```

Go to [www.youtube.com](www.youtube.com) and try running the first video you see.
It works!

---

