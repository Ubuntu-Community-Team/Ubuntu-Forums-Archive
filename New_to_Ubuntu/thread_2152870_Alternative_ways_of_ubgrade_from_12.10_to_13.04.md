---
title: "Alternative ways of ubgrade from 12.10 to 13.04?"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by ENigma885 on 2013-06-09
*I have a Lenovo S10-3t with Ubuntu 12.10 installed. Knowing that I have limited Internet access where the machine is ([COLOR="#FF0000"]and will be[/COLOR]), my 13.04 upgrade ways seem to be as limited. Here's the issue I need some help with;*

**Internet Access:**
- ONLY through a cell phone as a modem.

**The Problem:**
- I have a decent quota through my 3G connection, but the only problem is the speed which ranges from 5-20 kbps in the area where the machine is; most probably due to bad coverage. 
- With this speed it's impossible to do the whole upgrade through Internet; appr 1 g download will take ages.
- So, I booted from a 13.04 live CD and established Internet connection using the cell phone as a modem, as it's required for the upgrade to have Internet connection even if it is using a live CD.
- The upgrade installer does **NOT** recognize the established connection for some reason. Despite the fact that I can browse the Internet at the very same time using FF.

**Questions:**
1- Is there a way to make the cell phone modem a recognizable connection to the Live CD upgrade installer?
2- Can [building an off-line repository]("https://help.ubuntu.com/community/AptGet/Offline/Repository") on a flash memory with some decent Internet speed somewhere be of any use? If it is, how can I use it for the upgrade?

---

### Post by T.J. on 2013-06-09
Hi!  Hope I can help!  Please understand that this answer might be vague or possibly frustrating since I don't know any of your specifics.  I hope it will be useful as a starting point.

I'd think that if you can browse than you already have a usable connection.  What is preventing the installer from using it is probably the more relevant problem that I'd look at first.   

You need to have the knowledge of the alternative installer to load the necessary setup if you take the hard route and try to change the install process.  The alternate setup is/was (have not used in ages) based on the original Debian disc and can be used to load special drivers into the installer before downloading.    

Building your own offline mirror is not a trival task, but it is possible.  You need a large amount of disk space a (a few hundred GB) and lot of bandwidth if you want to make a totally complete mirror within a reasonable time, which you then have to sync to keep current.  Ubuntu doesn't seem to provide a complete set of offline images on DVD/Bluray like Debian does.  There are several tools to make a mirror, such as apt-mirror, and lots of documentation around the net.  If you are not detoured we can discuss it further.

---

### Post by T.J. on 2013-06-09
The best way to upgrade - keeping in mind that 13.04 is not an long term support version  and therefore not as stable - is to backup your data and reinstall wiping the disk.   I always separate my /home directory on a different partition from / so that I do not have worry when I upgrade.

---

### Post by hamishmb on 2013-06-09
Okay there are several ways: The first would be downloading an alternate cd and then launching the upgrade program (doesn't work for release newer than 12.04 :( ), then there is using update-manager (software updater), and the only other I know is booting off a livecd/usb and upgrading from that, which will wipe all your files :(

---

### Post by Sef on 2013-06-09
> [COLOR=#000000]13.04 is not an long term support version[/COLOR]

12.10 is not an LTS either; its EOL is April 2014; 13.04 EOL is January 2014.  The latter is the first one supported for 9 months instead of 18 like before.

I would suggest installing 12.04, which is an LTS that is supported until 2017.

---

### Post by ENigma885 on 2013-06-09
> **T.J. said:**
> What is preventing the installer from using it is probably the more relevant problem that I'd look at first.
I guess it's a bug, that I have to report. Will do soon.

> **T.J. said:**
> The alternate setup is/was (have not used in ages)
There's no alternate setup basically now; it's all in the Live CD. It's pretty simple to upgrade using a Live CD, but an Internet connection is required for some reason. Most probably to install an updated version of other applications not installed by default, but it makes more sense to make it an optional process.

> **T.J. said:**
> Building your own offline mirror is not a trivial task,
True; I think using a 20kbps connection to upgrade causes less pain.

> **T.J. said:**
> The best way to upgrade[...]is to backup your data and reinstall wiping the disk.
I agree but upgrading through a functional Internet connection has become way more stable and more reliable than it was before. Personally, I have upgraded from 12.04 to 12.10 when it was first released then to 13.04 (on my desktop) as soon as it was released very smoothly and without any problems.

_______________________

> **hamishmb said:**
> ....the only other I know is booting off a livecd/usb and upgrading from that, which will wipe all your files :(
I'm not pretty sure about the "wipe all your files" part. It keeps them as long as you didn't start a clean install. Check [this]("http://askubuntu.com/questions/279620/how-do-i-upgrade-from-12-10-to-13-04") under "Upgrading by using the CD or USB image".
_______________________

> **Sef said:**
> I would suggest installing 12.04, which is an LTS that is supported until 2017.
I'm more interested in 13.04; mainly because of the new Unity features. Thanks for the suggestion anyway.

---

