---
title: "Can not get CUPS to run, unable to print"
date: 2013-09-23
forum: New to Ubuntu
---

### Post by mark58 on 2013-09-23
My first linux install -- fresh Lubuntu 13.04 Live USB install. Only changes so far: got the wireless working on an old Gateway/Acer netbook. Also applied a zillion updates. 


Start - System Tools - Printer brings up printers - localhost which says: Printing service not available. Start the service on this computer... The Start Service button is grayed out. 


Doing Help - Troubleshooter says: CUPS Service Stopped The CUPS print spooler does not appear to be running. To correct this, choose System->Administration->Services from the main menu and look for the 'cups' service. However, I see no Administration->Services option. 


Browsing around the forum, it is often asked to check the CUPS log. That directory is completely empty!

What am I doing wrong? Any advice for noobs on starting from the beginning? 
Yes, it is plugged in!

---

### Post by Cbjaxx on 2013-09-23
Did you by chance make any changes to the configuration? You could try: sudo service cups restart from the command line to see if it restarts.. It also might be related to the cups config.. see if this post helps solve your problem:[http://ubuntuforums.org/showthread.php?t=2139407]("http://ubuntuforums.org/showthread.php?t=2139407")

---

### Post by tgalati4 on 2013-09-23
Make sure you have *avahi-daemon* installed and running.

---

### Post by Dennis N on 2013-09-23
The CUPS problem with Lubuntu 13.04 is discussed here:

[http://ubuntuforums.org/showthread.php?t=2139407](http://ubuntuforums.org/showthread.php?t=2139407)

with solution in post #9.

---

### Post by mark58 on 2013-09-23
Thanks for the assistance. I saw that but did not think it applied at first. My cups.config looks like:

> #!/bin/sh


set -e


# Debconf library
. /usr/share/debconf/confmodule


db_get cupsys/raw-print
OLD_RET=$RET

So does that start..stop..respawn code go in the beginning of the cups.config file?

---

### Post by Dennis N on 2013-09-23
The file to edit is at:

/etc/init/cups.conf

and begins with:

```
# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

start on (filesystem
          and started avahi-daemon
          and (started dbus or runlevel [2345]))
stop on runlevel [016]
```

In the solution, the line containing "and started avahi-daemon" was removed.

Post #18 of the same thread gives exact directions for fix the problem using nano, a command line text editor.

---

### Post by mark58 on 2013-09-23
Got it, Thanks! I'm such a noob.

I used "locate" to try an find the file. For some reason it didn't locate it in /etc/init. But it pointed to one in /var/lib/dpkg/info
Now that I have edited it, locate finds it just fine. Also, the printer works. Yea! Thanks!!!

---

