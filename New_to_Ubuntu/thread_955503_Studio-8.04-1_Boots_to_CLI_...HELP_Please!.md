---
title: "Studio-8.04-1 Boots to CLI ...HELP Please!"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by wetinwales on 2008-10-22
Ubuntustudio-8.04.1 will not boot to GUI. It only boots to a prompt.

Installed on a dedicated HDD and machine.
DVD tests good. MD5SUM good.
Installation goes well.
Then final re-boot... nothing just a prompt at the user $

can anyone help??

Daf

---

### Post by Teamgeist on 2008-10-22
try typing ```
startx
```

---

### Post by Sarmacid on 2008-10-22
> **Teamgeist said:**
> try typing ```
startx
```

That or ```
sudo gdm start
```

---

### Post by wetinwales on 2008-10-22
Thanks. Here's what happened:-

We are [user@'host':$] I type strtx

<startx> comes up withcommand not found. You need to install 'xstart xinit' (or something similar - the screen will not scroll back)

installed requested programe.

startx now gives:-
/usr/bin/startx: line 139: xauth: command not found
/usr/bin/startx: line 149: xauth: command not found
/usr/bin/startx: line 151: xauth: command not found
/usr/bin/startx: line 149: xauth: command not found
/usr/bin/startx: line 151: xauth: command not found
X: cannot stst /etc/X11/X (no such file or directory), aborting.
xinit: server error.
/usr/bin/startx: line 166: xauth: command not found
[user]@{me}host:[tiny upper mark]$

'sudo gdm start' gives:-
sudo: gdm: command not found
[user]@{me]host:[tiny upper mark]$


btw [me]host refers to the hostname I was required to provide during installation. I created a name which ended in'host' so I could identify it

Over to anyone...????

Thanks
Daf

---

### Post by wetinwales on 2008-10-22
Further to above.

Tried another install. same again.

so did sudo apt-get install xinit

Seemed to install.

....$ startx  ....Nothing.

tried sudo apt-get install gdm

Seemed OK up to end where it said:-

adduser: Warning: The Home Directory '/var/lib/gdm' does not belong to the user you are currently creating
*Reloading GNOME Display manager configuration...
*[orange star] Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[user]@[blah blah]: $

another attempt at startx gave:-

xauth creating new authority file /home/user/.Xauthority
xauth creating new authority file /home/user/.Xauthority
X: cannot stat /etc/X11/X (No such file or directory), aborting.
xinit: Server error
[back to user@comp..$]

SO  I AM LOST !!!

can anyone help?

DVD burned today in Ubuntu 8.04 Fresh DVD test OK during install.
Install goes without visible hitch.
Just won't go to GUI

Thanks
Daf

---

### Post by cwmoser on 2008-10-22
I run Ubuntu Studio and something similar to this happened to me.
I think it was an errant update - not sure though.

I found this in /boot

$ ls -l vm*
-rw-r--r-- 1 root root 1955960 2008-04-10 13:03 vmlinuz-2.6.24-16-rt
-rw-r--r-- 1 root root 1949176 2008-05-01 14:11 vmlinuz-2.6.24-17-rt
-rw-r--r-- 1 root root 1949080 2008-05-28 22:57 vmlinuz-2.6.24-18-rt
-rw-r--r-- 1 root root 1921464 2008-08-21 00:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1960312 2008-08-21 00:58 vmlinuz-2.6.24-19-rt
-rw-r--r-- 1 root root 1920376 2008-08-25 17:00 vmlinuz-2.6.24-21-generic
-rw-r--r-- 1 root root 1960504 2008-08-25 17:12 vmlinuz-2.6.24-21-rt
-rw-r--r-- 1 root root 1987704 2008-08-25 17:05 vmlinuz-2.6.24-21-server


Note the "server" -- it was my default boot kernel.  Reboot and select some other selection in the boot menu.  If it boots successfuly, you can change the default via the "default" variable in /boot/grub/menu.lst

Carl

---

### Post by wetinwales on 2008-10-24
Hi

Still trying to find out how to run Ubuntu Studio from the text prompt - the only screen I get after what seems to be a good install.

I've tried all the above solutions but nothing works.

Please Ubuntu Studio people... a convert is being lost to Fedora...

Should I not have used Canonical download?

Should I use bit torrent?

If the DVD says it tests good - do I believe it?

Am I posting to the wrong place?

Help Obie One Canobies... You're my only hopes...

Thanks
Daf

---

### Post by cwmoser on 2008-10-24
Hey don't give up.  I run Ubuntu Studio 8.04 and its great.

I wonder if you are getting the recovery console.  Do you see the grub boot menu?  Press the escape key at the start of boot up if you don't see it.

Once you get that menu, highlight something other than the Recovery Console and something other than one that says "Server".

I once installed Ubuntu on a PC that gave me trouble and had to use the version of Ubuntu that was not a live CD.

Carl

---

### Post by wetinwales on 2008-10-26
Thanks
You gave me 'the clue..'

It is this simple...

DVD iso installing........

I get to the window which says words to the effect of:-

 *"...the basic core is installed. Now choose the appropriate applications etc.."*

The little red cursor moves up and down with the scroll keys. I put the red dot on the application I choose, and hit the Return Key...

I failed !

Nowhere on that page does it say:-

* "...highlight your desired application using the scroll keys, then press the space key when the red dot is beside the application of your choice - which will then show an asterisk. Choose another application, if you wish, in the same way using scroll keys and spacebar. Only then do you hit enter."*

So My fault !

Soooooo many thanks for your clue

Daf:)

---

