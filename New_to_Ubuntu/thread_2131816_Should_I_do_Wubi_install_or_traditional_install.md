---
title: "Should I do Wubi install or traditional install?"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by Supremeroses on 2013-04-02
Wubi install successfully with DAEMON tools, it is the latest version. My laptop is Acer Aspire One 722, it's a Netbook. but I'm worried that I could potienally damage my computer.. I don't want to damage it if Wubi is the cause of it.. what should I do? I don't even have a flash drive nor exertnal drive since it is a netbook.. I installed inside windows 7 through wubi with the 12.10 ios.. should i parition or what?

---

### Post by Bresser on 2013-04-02
Wait so did you or did you not already use Wubi to install it?

---

### Post by Supremeroses on 2013-04-02
I already used Wubi to install it with the ios file using the Daemon tools that creates the virtual CD drive.

---

### Post by Bresser on 2013-04-02
Okay then maybe I misunderstood the problem here. What is the question you are asking here? And while your at it could you give me your computer specs?

---

### Post by Supremeroses on 2013-04-02
My question is that can Wubi damage my computer without paritioning it if I plan to dual boot both Ubuntu and Windows 7 for a long period of time or do I have to a traditionial install? What are the benefits betwwen those two? I purchased this computer two years ago from Target.. I just thought if I try out Ubuntu maybe I could use it as the primary OS instead of windows, using it for my iPod and rooting/upgrade my android phone. I already got the norton 360 purchased, it's an anti virus software also..
The specs of my computer:
1.0GHz AMD C-60 APU
ATI Radeon HD 6250 Graphics
2 GB RAM - 250 GB
Windows 7 Home Premium

---

### Post by nerdtron on 2013-04-02
> **Supremeroses said:**
> My question is that can Wubi damage my computer without paritioning it if I plan to dual boot both Ubuntu and Windows 7 for a long period of time or do I have to a traditionial install? 

No. Wubi will not damage your Windows 7, it's basically just another application installed in windows just like firefox, office, chrome etc. Just be careful when applying updates on Wubi. Some updates can cause problems when using Wubi install. Wubi is really intented for testing purposes.

But since you plan to use it for the long run, I suggest you uninstall wubi on windows (via the control panel add or remove programs) then use the partitioning tool of Windows 7 to shrink a partition and make another partition to create a full install of ubuntu on that partition

---

### Post by Supremeroses on 2013-04-02
Oh so, after that how can I do a full install on the parition with CD or USB.. I can try on put the ios on my phone while using USB storage if it's neccessary?

---

### Post by nerdtron on 2013-04-02
> **Supremeroses said:**
> Oh so, after that how can I do a full install on the parition with CD or USB.. I can try on put the ios on my phone while using USB storage if it's neccessary?

Sorry, my bad. You don't have to create a new partition on Windows7 to install Ubuntu.
After uninstalling Wubi, create a bootable USB flashh drive or SD card and "burn" the ISO. Follow this tutorial. [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb) 
Then boot your netbook from the USB disk you created and from the Ubuntu installer choose "Install Alongside Windows" option. As from this tutorial [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by oldfred on 2013-04-02
Do not create partitions with Windows 7, but use Windows Disk tools to shrink your Windows partition and reboot, so it can run chkdsk or make other repairs. 

If you create partitions with most Windows 7 systems, it will convert to dynamic partitions which does not work with Linux (and even causes issues with some Windows repair tools). 

If the only external access you have to your system is by flash drive, you need to have several. One a Windows repair flash drive that you make from Windows and the Ubuntu live installer. You should also have a large flash drive or exernal hard drive for  backup, unless all your data is not valuable. Hard drives do fail,  usually are the wrong time.

Many Windows 7 systems use all 4 primary partitions. That is a problem as you can only have 4 primary partitions and will have to delete one to let you create an extended partition. The extended partition can have many logical partitions.

       [URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot
[/URL]
 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[URL="https://help.ubuntu.com/community/GraphicalInstall"]https://help.ubuntu.com/community/GraphicalInstall

[/URL]
 Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

[URL="https://help.ubuntu.com/community/GraphicalInstall"]
[/URL]

[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

