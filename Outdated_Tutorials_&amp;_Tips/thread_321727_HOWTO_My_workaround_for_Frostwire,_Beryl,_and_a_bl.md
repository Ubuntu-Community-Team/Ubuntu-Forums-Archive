---
title: "HOWTO: My workaround for Frostwire, Beryl, and a blank window"
date: 2006-12-19
forum: Outdated Tutorials &amp; Tips
---

### Post by mia1dolfan on 2006-12-19
[SIZE="2"]4/20/07:  The original post was written while I'll was running Edgy.  Using the frostwire version included in Feisty Fawn I don't experience the blank window issue, and can run it normally.  I suspect this is because of the newer of java it depends on resolves the issue that caused this in the first place.  I will keep these instructions on here for historical purposes.[/SIZE]

[COLOR="Silver"]
Before attempting this howto, verify that this is the issue you are having.  This specific issue occurs with frostwire when running the Emerald window manager that is part of [_Beryl_]("http://en.wikipedia.org/wiki/Beryl_(window_manager)").  Within the beryl manager, if you change the window manager to something other than Emerald frostwire functions properly.  This workaround launches a separate nested X session for frostwire within your X session and uses [_blackbox_]("http://blackboxwm.sourceforge.net/AboutBlackbox") as the window manager for the session.  I am running (K)Ubuntu Edgy, [_frostwire-4.13.1_]("http://www.frostwire.com/blog/2006/11/21/try-frostwire-413-ubuntu-installer-now-with-bittorrent/"), XGL, beryl-syn, fglrx.

1. Get the prerequisite packages out of the [_universe repository_]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")
```
sudo apt-get install blackbox 
sudo apt-get install xserver-xephyr 
```

2. Edit /usr/bin/frostwire with your favorite text editor

Ubuntu users
```
gksu gedit /usr/bin/frostwire
```

Kubuntu users
```
kdesu kate /usr/bin/frostwire
```

3. Modify the contents of the /usr/bin/frostwire file to make it look something like the script below.  You can change the screen dimensions to your liking, frostwire will not be able resize past the size listed here.
```

Xephyr :2 -ac -screen 950x600 &
export DISPLAY=:2
blackbox &
bash /usr/lib/frostwire/runFrostwire.sh
killall Xephyr
```

4. After launching frostwire change the option "System Tray" to "Shutdown Immediately" located under Tools -> Options.  This is done because blackbox does not have a systray.

You can apply this workaround with other Java applications that experience this issue running under Emerald.

Credits for the original solution go to [_superpat_]("http://blogs.sun.com/roller/page/superpat") for his [_posting_]("http://blogs.sun.com/superpat/entry/access_manager_7_1_beta#comment1") on blogs.sun.com[/COLOR]

---

### Post by DREMA on 2006-12-23
Hello! Check the script on this thread, is easier and works! :D

[http://ubuntuforums.org/showthread.php?t=316398&highlight=beryl+frostwire](http://ubuntuforums.org/showthread.php?t=316398&highlight=beryl+frostwire)
> #!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

save as whatever you want, chmod +x, and run.

---

### Post by mia1dolfan on 2006-12-26
I tried that originally and it didn't work for me.  The error I get is listed below after declaring AWT_TOOLKIT.

[SIZE="1"]TRAY_TOOLTIP:::FrostWire
Error: Couldn't find per display information[/SIZE]

---

### Post by mjpoetic on 2007-01-03
> **mia1dolfan said:**
> I tried that originally and it didn't work for me.  The error I get is listed below after declaring AWT_TOOLKIT.

[SIZE=1]TRAY_TOOLTIP:::FrostWire
Error: Couldn't find per display information[/SIZE]

Same here....so thanks for the workaround!  I was trying to figure out how to do something like this.  That's what's good about these forums...if one method may not work, there are usually other methods posted to help. :)

---

### Post by mjpoetic on 2007-01-03
As a followup both methods are working for me (after installing blackbox and xephyr?).  So go figure! ;)

---

### Post by NickPresta on 2007-01-11
This method worked for me. Thanks!

---

### Post by detectiveinspekta on 2007-03-06
For the  export AWT_TOOLKIT=MToolkit command to work you have to have libgcj7-awt installed.
So to install:
```

sudo apt-get install libgcj7-awt

```

This worked for me.

Im guessing its using something from GCC. Works anyway.

---

### Post by mia1dolfan on 2007-03-13
I installed libgcj7-awt and still received the same error message as described in one of prior posts.

---

### Post by zachalekos on 2007-08-11
As of today it's happening again in Feisty

---

