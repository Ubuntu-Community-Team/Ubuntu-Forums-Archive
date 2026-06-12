---
title: "How to Auto Run a Command"
date: 2009-09-18
forum: Programming Talk
---

### Post by huangyingw on 2009-09-18
Hello,
    I am building a mirror server using apt-mirror command. What I want to do next is to make it auto run after launching.
    The exact "auto- run" effect I would like is that: Just a simple press on the power button of my PC, then, go to work.
    Maybe someone would recommend me to update the ~/.bashrc or other file, etc. But, the prerequisite for this method, is that, at least, I have to log in. And once, that session is closed, the apt-mirror command would also be terminated.
   There is a good app, named sysv-rc-conf, which could set some service to be auto-run. But, I could not see, apt-mirror in the sysv-rc-conf's setting menu:(.

---

### Post by lensman3 on 2009-09-18
To trap power events and keyboard events, like CNTL-ALT-DEL, are usually trapped in the "init" system.  "init" is run when the kernel go multi-tasking.  

Sorry I can't tell you more than this.  I have seen the "trap" in /etc/inittab file.  The linux groupies have mucked around in inittab and has changed in the last couple of years.

Hope this helps.

---

### Post by huangyingw on 2009-09-18
> **lensman3 said:**
> To trap power events and keyboard events, like CNTL-ALT-DEL, are usually trapped in the "init" system.  "init" is run when the kernel go multi-tasking.  

Sorry I can't tell you more than this.  I have seen the "trap" in /etc/inittab file.  The linux groupies have mucked around in inittab and has changed in the last couple of years.

Hope this helps.

Still, thanks for your clues. I suddently have a new idea: could use a "find" command to see what files have been changed, after running the sysv-rc-conf command. So, maybe I could try to "copy" the action.

---

### Post by phrostbyte on 2009-09-18
You have to make an init script for it.

Basically when your computer boots

GRUB (or other boot manager) starts -> executes the Linux kernel -> Linux kernel executes init (in Ubuntu it's called "upstart")

Then upstart runs a bunch of scripts located in /etc/init.d

I have never written an init script before, but you can take a look at what's there and maybe make your own.

---

### Post by huangyingw on 2009-09-20
> **phrostbyte said:**
> You have to make an init script for it.

Basically when your computer boots

GRUB (or other boot manager) starts -> executes the Linux kernel -> Linux kernel executes init (in Ubuntu it's called "upstart")

Then upstart runs a bunch of scripts located in /etc/init.d

I have never written an init script before, but you can take a look at what's there and maybe make your own.
Yes, thank for your valuable clues. My clue is to install an auto-runable application, like mldonkey-server, which could be set as auto-run after booting.
then I use following shell to see what ever have been changed since installation of that particular application
```

find / \( -path "/proc" -o -path "/sys" -o -path "/var/lib/mldonkey" -o -path "/root" -o -path "/var/log" \) -prune -o -mmin -140 -type f > ${script_path}/find.lo

```
the result is as follow:
```

/sys
/root
/proc
/tmp/fileApPAez
/tmp/libgksu-Oul31W/.Xauthority
/home/huangyingw/.gksu.lock
/home/huangyingw/.nx/C-TryUbuntu-1014-FEC6441D7AA68EE7714CDD92EE3823DE/clients
/home/huangyingw/.gconfd/saved_state
/home/huangyingw/.gconf/apps/gnome-screensaver/%gconf.xml
/var/lib/update-notifier/dpkg-run-stamp
/var/lib/mldonkey
/var/lib/apt/extended_states
/var/lib/apt/periodic/update-success-stamp
/var/lib/sysv-rc-conf/services
/var/lib/dpkg/status-old
/var/lib/dpkg/status
/var/lib/dpkg/lock
/var/lib/dpkg/available-old
/var/lib/dpkg/info/mldonkey-server.list
/var/lib/dpkg/available
/var/lib/dpkg/triggers/Lock
/var/lib/ucf/hashfile
/var/log
/var/cache/man/index.db
/var/cache/apt/pkgcache.bin
/var/cache/apt/srcpkgcache.bin
/var/cache/debconf/templates.dat-old
/var/cache/debconf/templates.dat
/var/cache/debconf/passwords.dat
/var/cache/debconf/config.dat-old
/var/cache/debconf/config.dat
/var/run/motd
/var/run/sudo/huangyingw/unknown
/var/run/update-motd.lastrun
/var/run/updates-available
/var/run/update-motd/99-reboot-required
/var/run/update-motd/90-updates-available
/var/run/cups/certs/0
/var/run/hald/acl-list
/var/run/console/root
/var/run/ConsoleKit/database
/var/run/utmp
/etc/shadow-
/etc/group
/etc/apt/sources.list
/etc/apt/sources.list.save
/etc/passwd-
/etc/shadow
/etc/gshadow
/etc/passwd
/etc/default/mldonkey-server

```
The only valuable findins is the content of /etc/default/mldonkey-server as bellow:
```

# This file is managed using ucf(1).

MLDONKEY_DIR=/var/lib/mldonkey
MLDONKEY_USER=mldonkey
MLDONKEY_GROUP=mldonkey
MLDONKEY_UMASK=0022
LAUNCH_AT_STARTUP=true
MLDONKEY_NICENESS=0

```
The result is a little strange, only such a file was changed? Or, there is something changed, while my "find" command did not show me?
I will try more...

---

### Post by huangyingw on 2009-09-23
I have just found a simple answer to my need:
just to add one line:"apt-mirror", in this file: "/etc/rc.local". Then, what I need is satisfied.

---

