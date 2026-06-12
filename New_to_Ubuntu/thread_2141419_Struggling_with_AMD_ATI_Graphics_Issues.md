---
title: "Struggling with AMD ATI Graphics Issues"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by nranka on 2013-05-02
I desperately need help. I started out with ubuntu all starry eyed - and am now ready to pull those damn eyes out!!

The Problem:
Can't  seem to get the desktop on 12.10 server working properly. Issues have  been reported before in the many threads I read. Have tried many of the  suggested solution - but to no avail. I'm able to log into the  ubuntu-desktop and see the sidebar. But the screen flickers a lot.  Computer is terribly slow. Dashboard won't open. If I click on the icon  (the first one at the top of the sidebar) - I can see the "title bar"  with the icons on the upper left (i.e the close, minimize &  maximize) and any other window open goes out of focus - but the dash  itself won't open. The reason I was trying to open the dash is that I  have followed the instructions on the [NoobsLab website]("http://www.noobslab.com/2013/04/install-ati-amd-catalyst-drivers-in.html")  - about installting some AMD Catalyst Driver Installation Application.  All steps went on fine (I followed those steps before I installed the  ubuntu-desktop) only that I cannot get into the dash to start the  application. 

Informatioin that you may need for diagnosis:
1)  I installed the Ubuntu Server 12.10 amd64 build downloaded from the  ubuntu website via usb disk. Its the only OS installed on my comp.
2) uname -a give shows the following:
[COLOR=#0000cd]Linux 635NDR 3.5.0-28-generic #48-Ubuntu SMP Tue Apr 23 23:03:38 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/COLOR]
3) Kernet Version: 
cat /etc/lsb-release
[COLOR=#0000cd]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"[/COLOR]

4) lspci | grep VGA output is:
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS480 [Radeon Xpress 200G Series]

5) find /dev -group video output is:
[COLOR=#0000cd]/dev/fb0
/dev/dri/card0
/dev/dri/controlD64[/COLOR]



6) Xorg currently in use via the egrep -i "connected|card detect|primary dev" /var/log/Xorg.0.log

[COLOR=#0000cd][    23.372] (II) RADEON(0): Output VGA-0 connected
[    23.372] (II) RADEON(0): Output DVI-0 disconnected
[    23.372] (II) RADEON(0): Output S-video disconnected
[/COLOR]

7) Amout This computer on Ubuntu Desktop start button menu options shows the following:
AMD Athlon 64 Bit (3000) Processor
1GB Ram
80 GB HDD
Graphics: Unknown

8) The motherboard itself is a Kobian Mercury KAM48219 whose specific info can be googled


Please, please, please advise - what can I do????

I've  installed and re-installed the system over 4 times. Had another major  issue - everytime I re-installed - I had to opt for erasing the  partition (otherwise it would additionally install one more  ubuntu and  also would fail while trying to install packages). To erase the 80GB  drive - the installation process seemed to take more than 4-5 hours. I  dont understand this either????

Eagerly looking forward to the communities help.

---

### Post by QIII on 2013-05-02
Hello!

Your card is very old and is not supported by any current ATI driver.  The driver that would support it will not work with any version of X Server after late 2008/early 2009.

Give me a bit to look at the instructions you followed and see if I can get you back to the default Radeon driver you were using when you installed Ubuntu.

Regards.

---

### Post by QIII on 2013-05-02
EDIT:  Wait!

I didn't see that you can't get to the application, so it's not installed.  Good thing.  Your card is too old.

When you log in, what sort of session are you choosing on the login screen?

---

### Post by nranka on 2013-05-03
When I log in - I don't get any sessions to choose from. I just get the big orange-ish desktop screen with the login option on the left. I choose the username and type in the password. In an earlier attempt to install it - I had the dash opening up. Then I had installed XMBC via the installer. After that while logging in - I had the option of choosing either Ubuntu (Classic) or XMBC and then logging in. Is there any other information you need me to provide?

Is there any other GUI you suggest. I just need the basic graphics (since I'm not well versed to using linux via terminal). My idea is to use this as a server for XMBC, ZoneMinder, pfsense, etc...now really use this to do any form of logging in.

Thanks for the prompt response. Awaiting further updates!

---

### Post by nranka on 2013-05-04
Any suggestions folks?

---

### Post by 3rdalbum on 2013-05-04
Google can advise you how to turn off transparency in Unity (low graphics mode) which should make things faster. If that doesn't work well enough...

You could install Gnome Panel. When you log out and click your username, you will see an Ubuntu button next to the Password box. Click it and choose the Gnome Classic session.

This is for computers with no 3D capability. Your system has some 3D capability, but not much. Should be a perfect fit.

---

### Post by nranka on 2013-05-04
Now sure where I can find the "Ubuntu Button". See my screen shot attached. I don't have any such Ubuntu button. What can I do to get it? Can I just install GNome Classic? If so - how?
[ATTACH=CONFIG]242173[/ATTACH]

---

### Post by gifford on 2013-05-04
In the area you have blackened out, click on it and you should get the choice of what session to boot.

---

### Post by nranka on 2013-05-04
Hi gifford, thanks for your prompt reply. I blackened out only the login (full name). There was no options (Ubuntu Button) there. I don't think Gnome Classic is installed in Ubuntu Server 12.10 by default. I googled for instructions to install Gnome-Classic after you suggested the same and followed the instruction as listed in this [link]("http://linuxg.net/how-to-install-gnome-classic-on-ubuntu-13-04-12-10-12-04/").

After that my login screen showed the Ubuntu Button you were referring to (See Ubuntu Login Screen 2.jpg). On clicking the button I got the options of Gnome Classic, Gnome Classic (No Effects) & Ubuntu (Default) - see Ubuntu Login Screen 3.jpg.

Am now trying the GNome Classic GUI. I will update on whether this has solved the speed & flickering problem on the system.
Highly appreciate your responses
.[ATTACH=CONFIG]242187[/ATTACH][ATTACH=CONFIG]242188[/ATTACH]

---

