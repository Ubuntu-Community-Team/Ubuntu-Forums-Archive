---
title: "TIP: Starting new X sessions from the command line with KDM"
date: 2008-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by sapphirecat on 2008-08-12
I have been setting up a user with Fluxbox, but the default menu lacked any user switching items. The "Start a new session" item that is in the K menu when running KDE+KDM doesn't exist in Fluxbox.

After searching the Web to no avail, I grabbed the source to find out how KDE itself does things, and discovered that what I wanted already exists. It's a command called kdmctl, which provides an interface for remote control of kdm.

In order to start a new session, all we need to do is launch the command:
```
kdmctl reserve
```

To get this into the Fluxbox menu, it simply goes in as a regular command:
```
[exec] (New Login) {/usr/bin/kdmctl reserve}
```

For more information, consult the [Fluxbox menu customization HOWTO](http://ubuntuforums.org/showthread.php?t=371144), or the documentation for your favorite window manager.

The only wart in the process is that it tends to send a lot of ENTER keypresses to the active window. Often, I'll come back to the original session and find Konsole full of blank command prompts.

kdmctl does lots of other things; it's documented well in its man page. I'm not sure if kdmctl is the exact equivalent of gdmflexiserver, but it does provide the ability to control KDM from the command line. Have fun!

---

