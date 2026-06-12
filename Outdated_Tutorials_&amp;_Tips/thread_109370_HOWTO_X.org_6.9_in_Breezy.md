---
title: "HOWTO: X.org 6.9 in Breezy"
date: 2005-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by TTL on 2005-12-28
Ok, after three days of trouble, I finally got x.org 6.9 running onto Kubuntu Breezy. :)
In short: Yes you could get x.org 6.9 running, but it is not easy so I suggest you should try it only when you have serious problems with the x.org release you are currently using AND have already some experience with Linux.
I would describe the risk of upgrading as follow:
Loss of data: low (but not zero!)
That you throw your PC from the table: medium
That you become crazy: high
That you don't get x.org 6.9 running: very high
That you end up with a PC which does not has a running x-server anylonger: very high
So everyone who do not need 6.9 immediately should wait until Dapper is out :)

For those who still want to upgrade, will follow the HOWTO now.

1: Firs we need the sourcecode of x.org 6.9
go to ** [http://wiki.x.org/wiki/Mirrors](http://wiki.x.org/wiki/Mirrors) **select a mirror near you and download
you will need the file ** X11R6.9.0-src.tar.bz2 ** which is located on the ftp server at ** pub/X11R6.9.0/src-single/ **. After downloading uncompress the file into a folder wit a few hundred free MB.

2: We will need some tools for building x.org 6.9, so ** apt-get install bison flex libpam0g-dev **
it might be possible that I have forgotten some, so refer to the file BUILD in the source directory if you need to apt-get some more programs.

3: Working around a bug in Breezy
There is a bug in Breezy, which would us prevent from compiling:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18157](http://bugzilla.ubuntu.com/show_bug.cgi?id=18157)
[http://ubuntuforums.org/showthread.php?t=80678](http://ubuntuforums.org/showthread.php?t=80678)
The bug is fixed in the Dapper packages, so we need them.
Add to your ** /etc/apt/sources.list **
** deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper main restricted **
save and do ** apt-get update **, and then ** apt-get install libc6 libc6-dev **. This will install
libc6 libc6-dev libc6-i686 from Dapper. After that comment 
** deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper main restricted **
out and do ** apt-get update ** again to prevent future not planned upgrade accidents.

4: make lmdir
I don't know wether this is necessary or not, but I followed the introduction in the file ** BUILD **.
Go into the directory ** xc/config/util ** and do ** make -f Makefile.ini lndir ** then copy (as root) ** lndir ** to ** /usr/local/bin **
After that create a new folder (as normal user again) at the same level as ** xc **, go into it and do
** lndir ../xc ** or similar. This will create some directories and links.

5: compiling
So now we will know if all above worked.
In one xterm do make World > World.log 2>&1 which will direct all messages to World.log. If all goes well the logfile will be 5MB big an hour later. You can watch the messages with tail -f World.log in a second xterm.
At the end my logfile contains a lot of warnings and some error messages. The error messages complains about a missing fcfreetype.h but it looks like this file is not really necessary. No other error are written in the logfile.

6: Now the risky part starts and I suggest you to read the full HOWTO until the end before proceed with this point!!!!
Login as root without a running x-server. Then remove your existing x.org installation.
** apt-get -s remove xserver-xorg xorg-common **. This will show you that (at least on my machine) 63 packages will be removed. Do it
** apt-get remove xserver-xorg xorg-common **.

7: Installing the new x.org 6.9
Go into the directory where you did make World > World.log 2>&1 before. Now take a breath (_from this point there will be no way back_) and enter ** make install ** (as far as I know there is no uninstall available). Then he will start copying a lot of files. On my machine he aborts the process, complaining that ** /usr/X11R6/lib/X11/xkb/symbols/pc ** is not a directory where he can copy files in. Yes, ** pc ** is a file and not a directory, so I simply renamed pc to pc.file and generated a directory pc. **mv pc pc.file** ; **mkdir pc ** Now just rerun ** make install **, at least for me it ran successfully until the end.

8: Starting x.org 6.9
Entering startx might shock you because it did not work (at least for me). It complains that there is no ** /usr/bin/X11/X **. But when did a reboot kdm started automatically as always. :D Just startx still did not work. I tried to make a link from ** /usr/bin/X11/X ** to ** /usr/X11R6/bin/Xorg ** but I made a mistake and linked /usr/X11R6/bin/X to /usr/X11R6/bin/Xorg and now nothing worked. But for some reason suddenly there was a executable /usr/bin/X11/X which I simply copied back to /usr/X11R6/bin/X. startx now got much further but aborted with some missing ** xterm **. Fortunately ** startx icewm ** did work (you have to apt-get install icewm), so nothing completely lost. I figured out that startx did not start kde anylonger but tries ** twm ** by default and that ** /etc/X11/xinit/xinitrc ** was wrong configured. I corrected the path to ** xterm ** in the file and now startx starts twm but not kde - I can life with that at the moment.

9: What works:
Finally i got x.org 6.9 working and with the new release I am able to play videos without crashing the x-server and there is some _ 2D _ acceleration support for my * ATI Radeon Xpress 200M *  now (I had to use ** noaccel ** as option before). The disadvantage is that startx does not start kde (but the login manager does). I am sure this could be corrected if I would know where to look ;)

So do this on _ your own risk _ and only when you need it and have already some experience with Linux.

Having fun with 2D acceleration now :D

---

### Post by ShiftyPowers on 2005-12-31
for such an advanced X server it just seems like a very complicated install process.  Why does it have to be so hard.  Also, what are the advantages of 6.9/7.0?

---

### Post by limit223 on 2005-12-31
Cool experience...worth it a try after a complete image of my system...
I'll be back with some results after..:KS

---

### Post by yaztromo on 2005-12-31
I have an unused machine with Kubuntu on. Will try in next couple of days.

---

### Post by Rob2687 on 2005-12-31
Working okay here.
I had to copy the X file too and compile my touchpad drivers again but that's about it.

---

