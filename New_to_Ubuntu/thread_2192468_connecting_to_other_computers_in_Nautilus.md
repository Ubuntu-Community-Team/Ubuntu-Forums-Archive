---
title: "connecting to other computers in Nautilus"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by squakie on 2013-12-08
My dumb question #1 billion:

I don't remember what it's called, but the default file manager in Mint let me connect to another computer - not just a server, but any computer.  Using that method I could choose ssh, enter in the path, userid and password and the file manager would show that computer via icons for the folders, etc..  In nautilus I only see "connect to server".  Is there an add-on or some other method of just connecting to another computer in Nautilus (non-Samba)?

---

### Post by 3rdalbum on 2013-12-08
Not a dumb question.

The "Connect to server" function in Nautilus also lets you do the same thing through SSH. The default file manager in Mint is actually a fork of Nautilus.

When most people think of a server, they think of a big-iron system mounted in a rack inside a datacenter. Actually, a server is any program running on any computer that accepts incoming connections. SSH is a server, even if you run it on a desktop computer.

---

### Post by shahanakhter on 2013-12-08
Yeah, open Nautilus **File -> Connect to Server**  and for like your ssh type stuff it's the url in this format:

```
sftp://username@ServerName/dir
```

^idk this wasn't intuitive to me at first, but yeah you could be using, not this, so that's another thing.

I think you can do this is in Nemo and nautilus, I bookmark mine so I can 1-click connect.

---

### Post by squakie on 2013-12-08
Not working - nautilus returns no error message but doesn't do anything with the sftp - the wireless adapter on the other system doesn't show any traffic.  I can ssh from a terminal, so the networking is ok.

It never asks for a password either.  I found an example on the net using nautilus in this manner but it shows the screen coming up like the one I had in Mint:  a new window where you enter server address, username and password.  I don't get this via my Nautilus.  I tried ssh://root@otherpcname  and that at least created activity on the net adapter at otherpcname but never prompted for a password and again Nautilus did nothing.

Help?  (I know I'm beyond it but please try ;) ).

---

### Post by Mopar1973Man on 2013-12-08
Well... I gone a bit farther and setup bit more advanced. First off I've provided domain names to all PC of my LAN. So morningstar.com in the LAN name and the PC I'm on is michael.morningstar.com and my laptop is laptop.morningstar.com. So if I was to call for ssh to the lapto from the PC.

```
ssh michael@laptop.morningstar.com
```

If you knew the IP address...

```
ssh michael@192.168.1.1
```

Typically ssh command is (username)@(address of other computer). That being said root is not a safe username nor should it be used. You would want to use a username that is present on the other SSH server. So lie since I've got michael as a user name on all PC's I can call.

```
ssh laptop
```

This is still valid but very short. 

Nautilus should follow the same connection path as terminal SSH. Since you not getting logged in something is a miss yet. As for the diagnostics of how to fix I'm bit green yet but I would take a peek at the system logs maybe there is a clue to what is wrong or missing.

---

### Post by steeldriver on 2013-12-08
I *think* that the functionality is provided by gvfs - for example when I use 'Connect to server...' to connect to my local laptop running sshd as

[ATTACH=CONFIG]248429[/ATTACH]

Then if I look at [this will be different for newer systems, e.g. /run/user/*username*/gvfs]

```

$ ls ~/.gvfs/
SFTP for steeldriver on think60p.local

```

and you should see a gvfsd-sftp 'helper' in your process list e.g.

```

$ ps -fu steeldriver | grep [g]vfsd-sftp
steeldriver  12303     1  0 11:10 ?        00:00:01 /usr/lib/gvfs/gvfsd-sftp --spawner :1.7 /org/gtk/gvfs/exec_spaw/6

```

If that's *not* happening, then I don't know whether there's a configuration switch that might have turned gvfs (or those bits of it) off - I don't see anything obvious in the dconf database - or whether it indicates that the actual packages are broken or missing - you could check 

```
dpkg -l | grep 'gvfs'
```

The gvfsd-sftp binary should be part of the gvfs-backends package, I think

```

$ apt-file search '/usr/lib/gvfs/gvfsd-sftp'
gvfs-backends: /usr/lib/gvfs/gvfsd-sftp

```

---

### Post by squakie on 2013-12-08
Interesting - when I ssh (via terminal) to another PC, this is all that show in the .gvfs folder - and I need root permission to see it:
```
dave@davePC:~$ sudo ls -al .gvfs
[sudo] password for dave: 
total 4
dr-x------  2 root root    0 Dec  8 00:08 .
drwxr-xr-x 28 dave dave 4096 Dec  8 05:31 ..
```

Which is no different than after I exit the ssh session:```

dave@davePC:~$ sudo ls -al .gvfs
total 4
dr-x------  2 root root    0 Dec  8 00:08 .
drwxr-xr-x 28 dave dave 4096 Dec  8 05:31 ..
dave@davePC:~$ 
```

What's more, I personally don't know what this directory entry means for the .gvfs folder when listing all in my home folder:

```
d?????????  ? ?    ?             ?            ? .gvfs
```

The check for sftp help shows nothing:```
dave@davePC:~$ ps -fu dave | grep [g]vfsd-sftp
dave@davePC:~$
```

Was I supposed to be trying sftp again?

Never got that or the other things to work - if I specify the userid and password in the statement the wireless adapter at the other PC flashes, but nothing happens.  If I omit the password, or if I omit both, then nothing happens but if I shrink the window there is a message box behind it saying the connection timed out - I assume waiting for a response that never shows.

---

### Post by steeldriver on 2013-12-08
If gvfsd is trying to use ~/.gvfs but it is root-owned, that could explain why it fails. But before going down that route, what version of Ubuntu are you running? Can you post the output of

```

uname -a

cat /etc/lsb-release

ls -l /run/user/dave

```

---

### Post by squakie on 2013-12-08
Here are those outputs (it should be 64-bit 13.04 -> tried 13.10 but didn't allow dragging from Unity menus to desktop).

```
dave@davePC:~$ uname -a

Linux davePC 3.8.0-34-generic #49-Ubuntu SMP Tue Nov 12 18:00:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
dave@davePC:~$ cat /etc/lsb-release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"
```

```
dave@davePC:~$ ls -l /run/user/dave

total 0
drwx------ 2 dave dave  60 Dec  8 17:32 dconf
dr-x------ 3 dave dave   0 Dec  6 20:00 gvfs
drwx------ 2 dave dave  40 Dec  6 20:00 gvfs-burn
drwx------ 2 dave dave 120 Dec  6 20:00 keyring-RdsUak
drwx------ 2 dave dave  80 Dec  6 20:00 pulse
```

---

