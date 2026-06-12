---
title: "Gnome SSH / telnet client manager"
date: 2006-02-19
forum: Programming Talk
---

### Post by ChrisC on 2006-02-19
I know I can telnet / ssh from the command line.  I would like to have a graphical manager of my usual ssh / telnet destinations, like gFTP does for ftp.  I didn't find anything in Synaptic that was in the ubuntu repository.  Suggestions?

---

### Post by sapo on 2006-02-19
gftp works for ssh too, i dont know about telnet.. but i always used gftp with ssh and it works fine.

---

### Post by nanotube on 2006-02-20
gftp does give you a gui frontend to sftp (just choose port 22, and protocol ssh), but it does not give you a remote shell, just file transfer. if that's what you were looking for, then have fun. :) if you were looking for an actual shell, then i do not understand why you would want a gui for it...

---

### Post by ChrisC on 2006-02-20
[QUOTE=nanotube]if you were looking for an actual shell, then i do not understand why you would want a gui for it...[/QUOTE]

I connect to a half dozen machines routinely, and I don't want to have to drop to a shell prompt, remember the exact ssh command syntax, hostname and username.  In other words, I want a front end to remember all that for me, so I can just say "connect to WorkMachine" and a shell screen pops up asking for the password.

It's a pretty basic tool ... think "Zap-O-Comm for OS/2" or "PuTTY for Windows".  In fact, I'd think this would be one of the first Gnome apps developed :)

---

### Post by majikstreet on 2006-02-20
hm.. Well I know you can make a bash alias for say:
ssh [email]majikstr@majikstreet.org[/email]

then make that say majikorgssh
then all you'd have to do is enter a password.

here's the thread (there may be more though) [http://ubuntuforums.org/showthread.php?t=89732&highlight=bash](http://ubuntuforums.org/showthread.php?t=89732&highlight=bash)

majikstreet

EDIT: I know that comes out as an email address, but let me underscore that that is _not_ an email address :D


EDIT2: Another _wonderful_ thread is this one: [http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)
          That thread has multiple parts, and here's the one that has bash aliasing: [http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)       hmm now that I look at it I don't see much about it, but anyway...

---

### Post by kaamos on 2006-02-20
Putty is one choice also in linux.
```
sudo apt-get install putty
```

---

### Post by ChrisC on 2006-02-20
[QUOTE=kaamos]```
sudo apt-get install putty
```[/QUOTE]

Holy crap, I didn't even consider that.  Outstanding!  It's not gnomified, but I'll take it.  Thanks!

---

### Post by majikstreet on 2006-02-20
sudo apt-get install pterm

I haven't tried it yet but I'm installing those two as we speak.

eek.. looks as if I was fooled by apt-cache..

forget about pterm..

---

### Post by racefan88 on 2006-02-27
[QUOTE=ChrisC]Holy crap, I didn't even consider that.  Outstanding!  It's not gnomified, but I'll take it.  Thanks![/QUOTE]
I'm new to ubuntu, and have been trying to get some packages loaded, and with putty I get the following:

The following packages have unmet dependencies:
  putty: Depends: libglib1.2 (>= 1.2.0) but it is not installable
         Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
E: Broken packages

---

