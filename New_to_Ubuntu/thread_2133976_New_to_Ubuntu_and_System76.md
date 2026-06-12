---
title: "New to Ubuntu and System76"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by dlrose on 2013-04-09
Hello to All,

I just received my new System76 Gaxelle Pro and geting it set up.

I'm not new to Linux (20 years Military Computer and Comms and 17 years SunMicroSystem/Oracle), but I am new to Ubuntu.

I am alredy in love with all the newness of my new laptop

One  of the first things I will need to do is install a Windows 7 virtual machine to have compatability with some of Oracle's network and tools.

Does anyone have any advice for me ?

Thanks

Darrell

---

### Post by arpanaut on 2013-04-09
This should get you started, and you can get support for your questions there too.
[URL="http://ubuntuforums.org/forumdisplay.php?f=308"]http://ubuntuforums.org/forumdisplay.php?f=308   
[/URL]
Here too: [https://help.ubuntu.com/community/Virtualisation](https://help.ubuntu.com/community/Virtualisation)

---

### Post by slickymaster on 2013-04-09
[Virtualbox]("http://www.virtualbox.org/") is probably the simplest to set up and use. It's available in the Ubuntu Software Centre for easy installation.

Also, see  this[ tutorial on installing windows 7 through virtual box in ubuntu]("http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box-in-ubuntu-12-04").

---

### Post by GameX2 on 2013-04-09
Check "Integrated" mode (VirtualBox) and "Unity" mode (VMware) of the virtualisation softwares.  They're essential, to me.

VirtualBox will hide your VM desktop, and only show the Windows taskbar, while VMware completely hide the Virtual machine, but has better integration.  Unlike VirtualBox, it does not rely on his own and only windows (Not sure if you understand).

One the feature I love the most about VMware (VirtualBox doesn't support this), is the ability to drag and drop a shortcut in the VM.  Example: you're using Adobe Photoshop in the VM.  With VMware, when you enter "Unity" mode, it hide your Desktop, and add an additionnal "Start menu" at the top (With auto-hide).  You can drag your Photoshop shortcut for the VMware menu, and drop it on your Ubuntu desktop.  It will work.  You'll now have a "Photoshop" shortcut on your Linux desktop.
When you'll double-click this shortcut, VMware will automatically start the virtual machine, and when the virtual machine will be on the Desktop, "Unity" mode and Photoshop will both start on their own!

That's an awesome feature, seriously.  It's even more effective/faster when you have a snapshot of your VM.

---

