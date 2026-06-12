---
title: "Cannot load gdm and cant redownload"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Caponetta on 2008-06-12
My sound driver was not working properly, so i removed three files and was planing on reinstalling those files (linux-sound-base alsa-base alsa-utils) but it also deletes gdm ubuntu-desktop. 

Now when i restarted i got no desktop or loign i got a terminal (obviously) so i typed  sudo apt-get install gdm 
it searched and prompted me to agree to installation, but i could not connect to the site. Infact i have no internet at all on that computer.

Is there a way i can get the files on a flash drive and type in a command to make it run the file off the flash drive?

or can i use the CD? is there a repair option with the CD?

Any help is greatly appreciated at this point.

---

### Post by Xiong Chiamiov on 2008-06-12
Just to make sure, you don't get a response when you run
```

ping google.com

```
?

You can download all of the packages that are in the official repos from [http://packages.ubuntu.com](http://packages.ubuntu.com).  You'll have to make sure that you get all the dependencies, though.  I'll look up how to do that, unless someone who actually knows can beat me to it.

---

### Post by Xiong Chiamiov on 2008-06-13
Ok, well, running
```

apt-cache search show gdm

```
tells (I think) which packages it depends on, but there are quite a few.  Let's make sure your internet's not up first.

EDIT: What am I thinking!  You can tell apt to use the CD as a source, and install gdm off of there.  Let me look it up.

EDITv2: Ok, try this, with the cd in the drive:
```

sudo apt-cdrom add
sudo aptitude update; sudo aptitude install ubuntu-desktop

```

---

### Post by Caponetta on 2008-06-13
ok awaiting the cd info. Thanks alot for the quick responses.

p.s. I cannot ping google.

---

### Post by Caponetta on 2008-06-13
It finished it tried to connect to us.archive.ubuntu.com and couldnt but it kept installing with:

```
Reading package lists... Done
Building Dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
```

Now do i restart?
and how do i restart via terminal?

---

### Post by Xiong Chiamiov on 2008-06-13
Did it install?  I suppose I should have had you run
```

sudo apt-get install ubuntu-desktop

```
instead, as it's a bit clearer as to whether or not things got installed or not.

You can restart by issuing the command
```

sudo shutdown -r now

```
though I think you should be able to just start gdm:
```

sudo /etc/init.d/gdm start

```

---

### Post by Caponetta on 2008-06-13
```
sudo /etc/init.d/gdm start
```

I got

```
Sudo: /etc/init.d/gdm: command not found
```

Im restarting now.



EDIT: Booting now, also i, for some reason, cannot get an internet connection so sudo apt-get   will not work.

---

### Post by Xiong Chiamiov on 2008-06-13
When you ran apt-cdrom add, it adds your CD as a repository in apt's list, just like all the others, with the exception that it is on a CD instead of on the internet.  So then, you'll get some connection errors when you update the listing, but it should install the packages off of the CD since it can't find them in the online repos.

You might need to install gdm, rather than ubuntu-desktop.  The ubuntu-desktop package *should* depend upon gdm, but who knows...

---

### Post by Caponetta on 2008-06-13
Hm, no go. How can i install ubuntu-desktop directly from the cd?
Last command had me trying to download from apt-get.

I tried to run gdm and ubuntu-desktop, it says 

```
The program "gdm" is not currently installed.
The program "Ubuntu-Desktop" is not currently installed.
```

---

### Post by Caponetta on 2008-06-13
just saw your last post. Ok ill try it with gdm.

---

### Post by Xiong Chiamiov on 2008-06-13
If necessary, you can edit the file and comment out all of the internet repositories:
```

sudo nano /etc/apt/sources.list

```
and put a # infront of all the lines except the CD one.  You'll have to run
```

sudo aptitude update

```
again.

---

### Post by Caponetta on 2008-06-13
Dang, im not using the sudo command when i add the cdrom.
I have to try that again. Thanks for your patience.

---

### Post by Xiong Chiamiov on 2008-06-13
> **Caponetta said:**
> Dang, im not using the sudo command when i add the cdrom.
I have to try that again. Thanks for your patience.
Ah, I didn't put it in there. >.<  Fixing.

---

### Post by cariboo on 2008-06-13
If you are connected to a router try:

```
sudo dhclient
```

and then try ifconfig to see if you've got an ip address.

Jim

---

### Post by darksizzle on 2008-06-13
if you're not having any luck with the cd you can just connect to the internet with the standard connection utilities.

```
ifconfig
```

will show you what cards you have available for connection, if you're using a ethernet connection you will most likely see something like eth0, and you can type.

```
sudo dhclient eth0
``` 

and get connected. then do an aptitude update ```
sudo aptitude update
``` and install gdm or ubuntu-desktop ```
sudo aptitude install gdm ubuntu-desktop
```

---

### Post by Caponetta on 2008-06-13
Im using a cisco wireless card.

And i get this error message after i edited the sudo nano /etc/apt/sources.list



```

No candidate version found for gdm
No packages will be installed, upgraded, or removed.
```

---

### Post by Xiong Chiamiov on 2008-06-13
Hmm.  Can you post your /etc/apt/sources.list for us, please?

You can, of course, try following the good gents suggestions to getting connected to the net.  It'll all be their responsibility, though, as I don't really know that much about such things.

---

### Post by darksizzle on 2008-06-13
mmm yeah you seem to have it still installed maybe? try

```
sudo dpkg-reconfigure gdm
```

and to connect to via wireless

```
sudo iwconfig eth1 essid 'YOUR NETWORK NAME HERE' key 'YOUR KEY' && sudo dhclient eth1
```

I'm pretty sure your card should be at eth1 but do an iwconfig just to make sure.  Of course leave the key 'YOUR KEY' out if you aren't encrypted.

---

### Post by Caponetta on 2008-06-13
```
deb cdrom: [Ubuntu 8.04 _Hardy Heron_ -Release i386 Mian Restricted
#deb http://us.archive.ubuntu.com/ubuntu/ Hardy Main Restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ Hardy Main Restricted

#deb http://us.archive.ubuntu.com/ubuntu/ Hardy Universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ Hardy Universe
#deb http://us.archive.ubuntu.com/ubuntu/ Hardy-updates Universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ Hardy-updates Universe

#deb http://us.archive.ubuntu.com/ubuntu/ Hardy multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ Hardy multiverse
#deb http://us.archive.ubuntu.com/ubuntu/ Hardy-updates multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ Hardy-updates multiverse

#deb http://us.archive.ubuntu.com/ubuntu/ Hardy-backports main restricted Universe Multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ Hardy-backports main restricted Universe Multiverse Universe

#deb http://archive.canonical.com/ubuntu hardy partner
#deb-src http://archive.canonical.com/ubuntu hardy partner

#deb http://secruity.ubuntu.com/ubuntu hardy-security main restricted
#deb-src http://secruity.ubuntu.com/ubuntu hardy-security main restricted
#deb http://secruity.ubuntu.com/ubuntu hardy-security universe
#deb-src http://secruity.ubuntu.com/ubuntu hardy-security universe
#deb http://secruity.ubuntu.com/ubuntu hardy-security multiverse
#deb-src http://secruity.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by Xiong Chiamiov on 2008-06-13
Well, Mian should be main, but that's the only thing I see wrong.  If that's a typo on your part, then I think I've done as much as I can do.

---

### Post by Caponetta on 2008-06-13
> **Xiong Chiamiov said:**
> Well, Mian should be main, but that's the only thing I see wrong.  If that's a typo on your part, then I think I've done as much as I can do.

Yes, typo.

Thanks for your help though.

---

### Post by darksizzle on 2008-06-13
Did you end up trying either one of the things I posted last?  Have you done an aptitude update since you commented out all of your lines in aptitude?

---

### Post by Caponetta on 2008-06-13
yes. It tells me gmd is not installed.

And i cannot connect to the internet.

---

### Post by Caponetta on 2008-06-13
does anyone have a link to the download for the Ubuntu-desktop file?
Can i save it to a cd and apt-get directly from that cd?

---

### Post by Caponetta on 2008-06-13
is it possible?

---

### Post by Caponetta on 2008-06-14
Can someone get me the direct download for Ubuntu-desktop gdm for 8.04 hardy heron i386 please?

Dont tell me to use sudo apt-get install gdm because i dont have internet connection on the ubuntu pc.So i need to save it to a CD and mount the cd onto the terminal and apt-get through there.

---

### Post by Caponetta on 2008-06-14
Can someone get me the direct download for Ubuntu-desktop gdm for 8.04 hardy heron i386 please?

Dont tell me to use sudo apt-get install gdm because i dont have internet connection on the ubuntu pc.So i need to save it to a CD and mount the cd onto the terminal and apt-get through there.

---

### Post by avtolle on 2008-06-14
> **Caponetta said:**
> Can someone get me the direct download for Ubuntu-desktop gdm for 8.04 hardy heron i386 please?

Dont tell me to use sudo apt-get install gdm because i dont have internet connection on the ubuntu pc.So i need to save it to a CD and mount the cd onto the terminal and apt-get through there.
[http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) you will need to look at the various packages to find the one(s) you want/need.

---

### Post by Rocket2DMn on 2008-06-14
Rather than hunting down packages and dependencies, you can download an alternate install cd and use that as a repository on the computer without internet connection.  This will have Gnome available on it.
Put the CD into the computer and run
```
sudo apt-cdrom add
sudo apt-get update
sudo aptitude install ubuntu-desktop
```

---

### Post by aysiu on 2008-06-14
It's right here:
[http://mirrors.kernel.org/ubuntu/pool/main/g/gdm/gdm_2.20.5-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gdm/gdm_2.20.5-0ubuntu3_i386.deb)

---

### Post by aysiu on 2008-06-14
It's right here:
[http://mirrors.kernel.org/ubuntu/pool/main/g/gdm/gdm_2.20.5-0ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gdm/gdm_2.20.5-0ubuntu3_i386.deb)

---

### Post by Caponetta on 2008-06-14
```
No candidate version found for Ubuntu-Desktop
```

Whats wrong with it?

---

### Post by aysiu on 2008-06-14
> **Caponetta said:**
> ```
No candidate version found for Ubuntu-Desktop
```

Whats wrong with it?
Are you trying to install *ubuntu-desktop* or *gdm*?

---

### Post by Caponetta on 2008-06-14
> **aysiu said:**
> Are you trying to install *ubuntu-desktop* or *gdm*?

ubuntu-desktop

---

### Post by Rocket2DMn on 2008-06-14
ubuntu-desktop allows you to install a GUI to an Ubuntu with only a terminal interface (like a server).  Installing the metapackage ubuntu-desktop includes everything you need to have a GUI with Gnome.

---

### Post by Caponetta on 2008-06-14
so.  ```
sudo aptitude install metapackage ubuntu-desktop
```
?

---

### Post by aysiu on 2008-06-14
Downloading each of the individual packages will be too much work.

Just download and burn the Alternate CD and type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

### Post by Rocket2DMn on 2008-06-14
> **aysiu said:**
> Downloading each of the individual packages will be too much work.

Just download and burn the Alternate CD and type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

EDIT: See post #29 :)

---

### Post by Caponetta on 2008-06-14
does anyone have a link to the alternative? i think i have the wrong one.

---

### Post by Rocket2DMn on 2008-06-14
Just go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom for the alternate install cd.

---

### Post by aysiu on 2008-06-14
> **Caponetta said:**
> does anyone have a link to the alternative? i think i have the wrong one.
When you visit the [Ubuntu download page](http://www.ubuntu.com/GetUbuntu/download), check the box next to *Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.* before you select a download location.

---

### Post by eriqjaffe on 2008-06-14
Do you still have the install CD?  If so, check to make sure that all the "deb cdrom" lines in /etc/apt/sources.list aren't commented out.  If they aren't, then apt-get should check the CD before looking for an internet repository.

---

### Post by aysiu on 2008-06-15
> **eriqjaffe said:**
> Do you still have the install CD?  If so, check to make sure that all the "deb cdrom" lines in /etc/apt/sources.list aren't commented out.  If they aren't, then apt-get should check the CD before looking for an internet repository.
If the install CD is the Desktop CD, it won't matter (unless the OP wants to reinstall the entire operating system). The Alternate CD (or a working internet connection) is needed in this case.

---

### Post by Caponetta on 2008-06-15
thanks a lot! I'm downloading now.

---

### Post by Caponetta on 2008-06-15
```
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc
```

This is what i get when ever i try to add the cdrom..

---

### Post by Rocket2DMn on 2008-06-15
Did you mount the cd first (if it didn't automount)?
```
mount -t iso9660 /dev/scd0 /media/cdrom0
```
of course, use the correct /dev location and mount point for your system.
Then run the 3 commands mentioned earlier
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

You can also add the cd as a repository from System->Administration->Software Sources.

---

