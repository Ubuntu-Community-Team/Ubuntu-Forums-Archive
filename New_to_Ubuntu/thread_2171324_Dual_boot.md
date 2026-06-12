---
title: "Dual boot"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by RussellXPD on 2013-08-30
I'd like to start by saying how much I appreciated the help I received from Forum members when I raised an earlier version of this question.

Last November I asked for guidance setting up Ubuntu 12.0.4 on a memory stick alongside W7. That works perfectly on my newer PC (it was marked SOLVED) and I can paddle my own boat now and do much of my work within either system.

I deferred one problem I couldn't tackle then - getting Ubuntu 12.0.4 on the hard drive of my older PC. (It didn't have the USB option.)

So, I'm running XP with Sp3, Pentium 4, 2Gb RAM, plenty of capacity on my second drive (E) and I've installed Ubuntu 12.0.4, using a DVD copy from the USB stick that I use on the Windows 7 computer.

 What I see are these folders: **Ubuntu Transfer**  735 Mb - includes the **wubi-exe** file; **Ubuntu on E**, 694 Mb, which contains the one **iso** file; and **Ubuntu**  14.6 Gb  Disk, Install and Winboot plus **uninstall-wubi.exe**      

After the transfer from DVD to drive E, the system confirmed that it had been installed correctly and needed to reboot.
Which I did without getting the bootup I needed.

After all that my question may be simple: how do I boot up to run Ubuntu?

With thanks

RussellXPD

---

### Post by oldfred on 2013-08-30
Did you want wubi?
Wubi is a version that runs inside a NTFS partition and uses the Windows boot loader. It is for new users who want an extended test (over just liveCD) and is updateable. It is not intended for long term installs.
Also since wubi does not currently work the the new UEFI systems which all Windows 8 have, wubi is being discontinued. You can now only install wubi from inside Windows not from an install ISO or DVD.

       wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)

 Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

      
 [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

If you want a full partitioned install you have to create a live installer either DVD or USB flash.  If system is so old as to not boot from USB, then you may want Lubuntu or Xubuntu. While you may have enough RAM, Unity needs a good video system also.
What processor? Some Pentium M have to have non-PAE version.

 PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

      
 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by RussellXPD on 2013-08-31
Thanks oldfred

I've looked at these links, and particularly checked up on Lubuntu. It sounds good, suitable for what I've got. My system works well but it's got RAM max of 2Gb and HDD size (max) 120 Gb. 

I'm clear now about wubi and why there are drawbacks. However Lubuntu 12.0.4 and later versions are not set out yet for long term support, if I understand it right.  My aim would be to get a long term install. But immediately I don't mind messing about (trying out different distributions) with various Linux and Ubuntu CDs. I might not make the headway I want, often go two steps backwards, but I'll build up the learning curve so that when I do have the installed version. I'll be able to use it with confidence. 

I'm lined up to become a library instructor and may be able to do my bit to pay back the community. The more mistakes I make, the more I should be able to bail out beginners.

I'll mark the thread closed shortly, but I'll be interested in any comments on this.

---

### Post by oldfred on 2013-08-31
While I am running 12.04, I used to upgrade evey 6 months with a new clean install. My wife complained about too many changes, so I stopped at 12.04, but have each of the newer versions installed also. I will change to 14.04 and want to know what is coming down the pike.

A disadvantage of the long term support is that the software is not updated. That has changed somewhat that the kernel now is updated with each point release and some software like Firefox is updated rather than secuity fixes backported.  I think long term is more for a server where you may only need the security updates and want the stability that no changes would give.

---

### Post by whitesmith on 2013-08-31
An advantage of LTS is that tutorials are usually documented with LTS screenshots and procedures. For example, the method for setting up a VPN is well documented for 12.04 LTS, but might seem inscrutable to a recent 13.04 user. My personal experience is that LTS is better for newcomers to *nix. And definitely, as **oldfred** said, for servers.

---

### Post by RussellXPD on 2013-09-01
Thanks to both. 
I mentioned messing about. It's more that my experiences in the last few hours have messed me about. But, hey, I take it in good spirit. For example I used the file system on a USB stick that works on my newer PC (12.0.4)  copied onto a DVD and found I was barred from entry on the older machine by a Username\password demand - I hadn't previously specified any. And the desktop showed 13.0.4. Where had that come from? And then I was able to Create and Save a document on an almost blank and unusable desktop.
What I need to do is go back to school which in this case means reading up my Ubuntu book more thoroughly and finding out on this forum what all the other absolute beginners are up to. 
Meanwhile I have one good working system (USB boot) on the other PC and am making progress by the day. 
I'll mark this as Solved which reflects the fact I need more know-how and data before I trouble you fellows again.
Russ

---

### Post by oldfred on 2013-09-01
Just to get you started. One of the security advantages of Linux is ownership & permissions on every folder & file. So if you try to mount file system from another system, you may not have correct ownership & permissions. You can use sudo for admin tempory permissions or reset those permissions. Or if shared, you can like on servers set up groups and group permissions, but I do not even understand all of that without lots of research.

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by RussellXPD on 2013-09-01
Thanks OldFred

I'll bear that in mind for later.

Russ

---

