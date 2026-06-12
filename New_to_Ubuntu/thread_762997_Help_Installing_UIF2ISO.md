---
title: "Help Installing UIF2ISO"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Nodestar on 2008-04-22
I'm trying to convert a .uif file into a .iso file. I've been through the forums and it looks like it's either run MagicISO with Wine or use UIF2ISO. I'd like to use UIF2ISO but I cannot figure out how to install it. 

I've read allot of other post but the replies are always vague in certain areas. They assume I know how to do this or that. I've had Ubuntu for a couple weeks now but I'm still a complete noob when it comes to installing programs. If someone could give me a step by step that would be great. I can use the terminal. I'm just not sure how to do much with it. 

Thanks for any help.

---

### Post by mlentink on 2008-04-22
How safe do you feel compiling from source? Because I've looked at it, and that's just about the only way you're going to be able to install it.

---

### Post by Nodestar on 2008-04-22
I feel safe if you feel safe. If I can get good directions then I will follow them blindly to my doom. 

I'm pretty lost. Everything I've tried so far has failed so. I'll try anything. I just need all the directions. Not skipping any small parts that you assume I know about(because I don't).

---

### Post by Nodestar on 2008-04-22
Can anyone help?

---

### Post by mlentink on 2008-04-23
We seem to be in different timezones, so sorry for the delay.

I could guide you through it, but I won't presume..
A very good guide on how to install from source is [_here_]("http://www.psychocats.net/ubuntu/installingsoftware#source"), and I don't think I can do better.

Edit: your file seems to be in zip.format, which makes it a little bit easier. You can do away with the 'tar' command and simply unzip it with nautilus

---

### Post by abadr on 2008-12-01
Well, it's a bit late but let's put the how to up for future reference. 

The version currently on the authors website is 0.17 and currently it fails to compile on Kubuntu 8.04 so what I did was:

[LIST=1]
[*]Download and uif2iso RPM package
```
wget ftp://fr2.rpmfind.net/linux/dag/redhat/el3/en/i386/dag/RPMS/uif2iso-0.1.7-1.el3.rf.i386.rpm
```
[*]Install "alien" a tool to convert the RPM packages to deb counterparts
```
sudo apt-get install alien
```
[*]Convert the package
```
sudo alien uif2iso-0.1.7-1.el3.rf.i386.rpm
```
[*]Install the new deb package
```
sudo dpkg -i uif2iso_0.1.7-2_i386.deb
```
[/LIST]

Hope this helps.

The source file archive. Also includes a ready build windows version:
[http://aluigi.altervista.org/mytoolz.htm#uif2iso](http://aluigi.altervista.org/mytoolz.htm#uif2iso)

---

### Post by LitusMayol on 2009-03-23
**abadr**, you've saved me! 

Thanks, I've done it and it works perfectly. Thanks!

---

### Post by petesimon on 2009-07-16
> **abadr said:**
> Well, it's a bit late but let's put the how to up for future reference. 

The version currently on the authors website is 0.17 and currently it fails to compile on Kubuntu 8.04 so what I did was:

[LIST=1]
[*]Download and uif2iso RPM package
```
wget ftp://fr2.rpmfind.net/linux/dag/redhat/el3/en/i386/dag/RPMS/uif2iso-0.1.7-1.el3.rf.i386.rpm
```
[/LIST]
 That could work, but rpm and alien are not needed. I found a .deb package already available on ubuntu's website.
Look at [http://packages.ubuntu.com/karmic/uif2iso](http://packages.ubuntu.com/karmic/uif2iso)
and under "Download..." choose amd64 for 64-bit or choose i386 for 32-bit systems, and then choose a mirror to download from. After the file dl's, install it with GDebi GUI or use "dpkg -i <file.deb>" in Termina/command-line. A manual page is also included after installation.

---

### Post by nickby on 2009-12-27
thanx petersimon - you came to the rescue. Just what I needed, the amd64 deb package works fine.

---

### Post by Cincinnatux on 2010-05-03
Just as an update to this thread, uif2iso is installable via the Ubuntu repositories now.  Under Ubuntu 10.04 Lucid Lynx, I entered the following:

```
sudo apt-get install uif2iso
```

Then I navigated to the directory containing my target uif, which I will call 'sample.uif' for the sake of this comment.  The following CLI command then produced the .iso I wanted:

```
uif2iso sample.uif sample.iso
```

And I was done.  If you want to view the .iso contents without burning them to disk, see this thread:
[http://ubuntuforums.org/showthread.php?t=656369](http://ubuntuforums.org/showthread.php?t=656369)

---

### Post by LinuxHelper on 2010-08-26
An update for Linux newbies, I found a detailed explanation of how to install uif2iso in the latest Ubuntu, that will lets you [convert uif to iso]("http://wesleybailey.com/articles/uif-to-iso-converter") for free.

If you are new to linux and need to know why things need to be installed instead of just how, then give this guy a read.

---

