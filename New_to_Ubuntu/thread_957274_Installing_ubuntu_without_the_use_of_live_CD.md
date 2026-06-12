---
title: "Installing ubuntu without the use of live CD"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by RoyHobbs on 2008-10-24
Hi

I am trying to install ubuntu 8.04 on an old laptop that I have which has no operating system on it.  The laptop is a NEC Versa Premium, circa 2002 I think.  I am currently Running Puppy 4.1 on it and it appears to be working fine, however the rest of the pc's on my network run Ubuntu so, for ease of use, I would like to put ubuntu on this one as well.  I have partitioned the 30gb hard drive into 3 using gparted and was planning to run Ubuntu in one these 10 gb partions.  When I have tried to run the live cd there have been numerous problems during installation related to the cd / harddrive (live cd has worked fine in 3 other installs), I have been able to run ubuntu off of the live cd however it is painfully slow!

Any advice would be greatly appreciated.

---

### Post by hyper_ch on 2008-10-24
download the alternate install cd

---

### Post by starcannon on 2008-10-24
I've not done this yet, but I've been intrigued, and one of these days I'll finally get around to it "just because I can"; so anyway, a net install may be just the thing.
[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)
a couple to get you started, and there is also one from the Ubuntu Help Documentation(I'd try this one first):
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

GL and have fun, let us know how its going, I'm very interested in following your project.

---

### Post by pastalavista on 2008-10-24
You can download [UNetbootin]("http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fwww.linux.com%2Ffeature%2F124684&ei=vZ0BSZmbKIi0eaC3jeYN&usg=AFQjCNEelzIqlW2uBpecnKAOeEupyQrqfA&sig2=-IOLm06F8SW1y6NcOWwOkw") and use it to make a copy of a live CD (several distros) on a 1GB or larger USB flash drive. I did this with Intrepid beta and was amazed at how fast and smooth it works.. as fast as if it was on the hard disk.

---

### Post by C.S.Cameron on 2008-10-24
If you can boot off of USB I second using a Live USB created with Unibootin or usb-creator.
Usb-creator comes with 8.10 and can be found in System.

---

### Post by Duck2006 on 2008-10-24
If you go the usb way, this may help.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by northern lights on 2008-10-24
> **pastalavista said:**
> You can download [UNetbootin]("http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fwww.linux.com%2Ffeature%2F124684&ei=vZ0BSZmbKIi0eaC3jeYN&usg=AFQjCNEelzIqlW2uBpecnKAOeEupyQrqfA&sig2=-IOLm06F8SW1y6NcOWwOkw") and use it to make a copy of a live CD (several distros) on a 1GB or larger USB flash drive. I did this with Intrepid beta and was amazed at how fast and smooth it works.. as fast as if it was on the hard disk.

+1 for Unetbootin

2 additions:

Since the above link points to a google search, download unetbootin directly from [http://lubi.sourceforge.net/unetbootin]("http://lubi.sourceforge.net/unetbootin")

Unetbootin is an amzing app indeed. So powerful infact, that the route via a USB flashdrive is not even necessary. Unetbootin can be installed under almost any platform, Windows included. Download the version you need and execute it (in Windows: double-click the .exe, in GNU/Linux: right-click the .sh script, give yourself execution permissions, then run it). In Unetbootin select "Ubuntu 8.04 NetInstall" and choose the apropriate drive. Apply. Reboot. Now you should be given an extra Unetbootin bootoption. Select that. You can now install directly from the net with the Alternate CD's interface.

Another point might be, that given that the new Intrepid release is 6 days away, you might want to wait for a week and install 8.10. Also, if you can't wait, the newest unetbootin already supports the beta install candidate, it will automatically update to the standard release in 6 days.

---

### Post by Duck2006 on 2008-10-24
> Another point might be, that given that the new Intrepid release is 6 days away, you might want to wait for a week and install 8.10

The new release will be out soon so it may pay to wait till then. As with a new release i find it better to do a clean install, and not update your old one.

---

### Post by pastalavista on 2008-10-24
the real link for UNetbootin is [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)...
sorry about the Google link.. I was in a hurry

---

### Post by RoyHobbs on 2008-10-25
> **hyper_ch said:**
> download the alternate install cd

Hi

Thanks, I tried that before with no luck :(

---

### Post by RoyHobbs on 2008-10-25
> **pastalavista said:**
> You can download [UNetbootin]("http://www.google.com/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fwww.linux.com%2Ffeature%2F124684&ei=vZ0BSZmbKIi0eaC3jeYN&usg=AFQjCNEelzIqlW2uBpecnKAOeEupyQrqfA&sig2=-IOLm06F8SW1y6NcOWwOkw") and use it to make a copy of a live CD (several distros) on a 1GB or larger USB flash drive. I did this with Intrepid beta and was amazed at how fast and smooth it works.. as fast as if it was on the hard disk.

Hi
I did this, however whenever I reboot, nothing happens, ie there is no Unetbootin options etc and also the thumbdrive has nothing on it?  In media it is showing, but the thumbdrive it self has nothing?:(

---

