---
title: "Been playing with vmware"
date: 2006-06-28
forum: Other OS Talk
---

### Post by matthew on 2006-06-28
And I like it. I've installed FreeBSD and Debian Sarge (which I upgraded to Etch, then to Sid just for kicks). Anyway, I was noticing that the VM website has links to various virtual appliances (link: [http://www.vmware.com/vmtn/appliances/directory/](http://www.vmware.com/vmtn/appliances/directory/) ) and even a contest for the best one made. Guess who the judges are? Take a look: [http://www.vmware.com/vmtn/appliances/challenge/](http://www.vmware.com/vmtn/appliances/challenge/)

Anyone else been having fun with different OS's in vmware and have some tips?

---

### Post by entangled on 2006-06-28
Not exactly.
I hope I'm not too much off topic but I've run up parallels (low cost vmware wannabe) on my Intel Mac Mini and installed Ubuntu 6.06 using the 'alternative' CD. It all works but my 512MB is probably a bit light.
I also have a dual boot installation on the same machine so I can run Ubuntu two ways.
The Mac internal sound works (but strangely not on dual-boot Ubuntu). Bluetooth worked without configuration for both mouse and keyboard (again not on dual boot).
I found video on parallels to be too slow for normal use (but it is very good on the dual boot).
Although Ubuntu mostly works on parallels the video problem makes it unacceptable. I wonder if vmware has the same problem with Ubuntu?

I have also tried vmware at work on a 2MB + 3GHz P4, with Windows Server 2003. Again the mouse movement is a problem, though not as bad as on my Mac.

---

### Post by mhancoc7 on 2006-06-28
Here is a post on how to add Vmware to your GDM Sessions list. You can even set it up to launch a particular OS in fullscreen automatically!

[http://ubuntuforums.org/showthread.php?t=202166]("http://ubuntuforums.org/showthread.php?t=202166")

Jereme

---

### Post by matthew on 2006-06-28
[quote=mhancoc7]Here is a post on how to add Vmware to your GDM Sessions list. You can even set it up to launch a particular OS in fullscreen automatically!

[http://ubuntuforums.org/showthread.php?t=202166]("http://ubuntuforums.org/showthread.php?t=202166")

Jereme[/quote]Nice!

---

### Post by AndyCooll on 2006-06-28
Yeah, I've been playing with VMware, and I too like it. 

Now installed VMware Server. What I like about the Server edition is that it gives you more scope to edit the image configuration. It also gives you the capability to "roll your own" image. So, it's ideal for trying all these distros that appear on magazines. It's also great for trying other OS's too, I have a FreeBSD image, a ReactOS one and even a Minix one.

Finally, my copy of XP is a VMware image. I don't need XP very often (and I don't play games that require fast graphics) but when I do it seems to run really quick.

:cool:

---

### Post by rai4shu2 on 2006-06-29
I've been playing around with the latest ReactOS in VMware. I haven't really stress-tested it yet, but it looks promising.

---

### Post by matthew on 2006-06-29
[quote=AndyCooll]Finally, my copy of XP is a VMware image. I don't need XP very often (and I don't play games that require fast graphics) but when I do it seems to run really quick.[/quote]Did you make that image yourself from an install cd or did you find it somewhere?

---

### Post by AndyCooll on 2006-06-29
I actually made it myself using my install CD. At the time I wasn't aware of the existence of VMware Server (or it might not have been freely available). Anyway, I followed the instructions in a HOWTO from these forums! :)
This one: [HOWTO: Install Windows XP/2000 in VMWare Player]("http://ubuntuforums.org/showthread.php?t=84275")

Looking around, I've also recently come across these if you're interested:
[HOWTO: Install Windows Vista Beta 2 (With Vmware without burning ISO file) On Dapper]("http://ubuntuforums.org/showthread.php?t=192328")
and:
[HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://www.ubuntuforums.org/showthread.php?t=183209)

:cool:

---

### Post by AndyCooll on 2006-06-29
[QUOTE=rai4shu2]I've been playing around with the latest ReactOS in VMware. I haven't really stress-tested it yet, but it looks promising.[/QUOTE]

Yeah, I've got a ReactOS image too. It's a bit flaky, and I think you'll find it won't stand up to too much stress. I agree, it does indeed look promising.

:cool:

---

### Post by rodnod on 2006-06-29
Just installed vmware server on ubuntu 6.06. Installation went ok but when I tried to create a new virtual machine it crashes with error say "User does not permission to create new virtual machine". Checked permissions in users and groups, seems OK. Logged in as root to test and all worked OK.. Any ideas?

---

### Post by Paerez on 2006-06-29
Try creating the machine in your home dir. So when it asks you where you want to put the image, put like /home/{you}/vmware/imagename so that you use a dir you have +W on.

p.s. I am loving the WinXP Fullscreen inside my ubuntu for Flash and other stuff.

I haven't tested it yet, but will usb stuff and bluetooth stuff work through ubuntu to xp in vmware?

---

### Post by matthew on 2006-06-29
[quote=rodnod]Just installed vmware server on ubuntu 6.06. Installation went ok but when I tried to create a new virtual machine it crashes with error say "User does not permission to create new virtual machine". Checked permissions in users and groups, seems OK. Logged in as root to test and all worked OK.. Any ideas?[/quote]Change the default location for virtual machines to a folder in your home directory and it should work fine. For example: /home/matthew/vmware

EDIT: got beat to the answer. :)

---

### Post by josys36 on 2006-07-07
VMWare is great! I have been using it now for weeks on my IBM thinkpad, and have had very few issues at all. However, I do have a few comments.

1. The PC Clock can run slow. This is a known issue for VMWare and they say they are working on a fix. This can effect some sound applications. I know I had tons of trouble using AOL radio until I installed Firefox under wine.

2. VMWare Server does not have as nice a full screen feature as VMWare player. I hope that someday Server and Player come bundled like Workstation.

3. I finally have a way to run Ubuntu all the time, yet can still use windows for those pesky windows apps. Some of which I cannot get working under wine.

Jason

---

### Post by AndyCooll on 2006-07-09
> **josys36 said:**
> 3. I finally have a way to run Ubuntu all the time, yet can still use windows for those pesky windows apps. Some of which I cannot get working under wine.

Totally agree with your comments. All my boxes have been Linux only since I discovered VMware, since I can use my XP image for the few things that are M$ only. 
As I've mentioned earlier in this thread, I also use it to look at other OS's and distros. I've got a test box which I use to install other distros, however since I installed VMware I no longer use it ...much easier to power up a distro within VMware Server.

:cool:

---

### Post by Paerez on 2006-07-10
> **josys36 said:**
> 3. I finally have a way to run Ubuntu all the time, yet can still use windows for those pesky windows apps. Some of which I cannot get working under wine.

Same here. I run Adobe Flash 8 Pro under vmware, and I also use XP for watching online stuff that needs Flash 8 Player. Also I use it to encode to WMA for myself.

One problem I noticed is that sometimes Ubuntu hogs the sound, and I have to kill esd and exit amarok, firefox, or anything that is making sound, then reboot my vmware xp to get xp to make noise. I think I may be overkilling the problem, anyone know what the deal is with this?

---

### Post by mandible on 2006-07-25
I opened up my vmware image of xp as root to change some RAM levels and now I can't open up the xp image as normal user any longer, I tried chown on my .vmware folder and also on the folder I have my xp image in.  It was working as a normal user before I opened it as root :(  any help for the sad panda?

---

### Post by Paerez on 2006-07-25
you have to do a recursive chown:
```
sudo chown -R YOU:users ~/.vmware
```

---

### Post by gruffy-06 on 2006-10-01
> **josys36 said:**
> VMWare is great! I have been using it now for weeks on my IBM thinkpad, and have had very few issues at all. However, I do have a few comments.

1. The PC Clock can run slow. This is a known issue for VMWare and they say they are working on a fix. This can effect some sound applications. I know I had tons of trouble using AOL radio until I installed Firefox under wine.

Jason

First off, install VMware Tools into your guest OS. This should definately increase the performance.

Next, type:

vmware-toolbox

into a terminal and check the "time synchronisation" box. The clock should be ok now.

Read the VMware manuals for details on how to install VMware Tools.

N.B. You cannot distribute a Linux guest with VMware Tools installed because this will violate the GPL.

---

