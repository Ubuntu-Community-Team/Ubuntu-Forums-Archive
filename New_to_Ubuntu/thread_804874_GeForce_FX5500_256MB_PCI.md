---
title: "GeForce FX5500 256MB PCI"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by n7iqy on 2008-05-23
I read speechtactics posting about his NVIDIA GeForce FX5500 video card and I have the same problem, but with different circumstances.

I am running Ubuntu 8.04 inside Windows Vista Home Basic.  It operates fine when using the Intel Video chip on the motherboard, but when I install my NVIDIA GeForce FX5500 256MB PCI video card it hung up at the 3rd bar in the yellow scan bars.  I read speechtactics solutions and  performed "sudo apt-get install nvidia-glx" using the Intel onboard chip.  I shut down and installed the NVIDIA card and rebooted and selected "ubuntu" and the startup went well as it cleared the 3rd scan bar and ran thru the last bar and started over and hung up on the 13th bar.

I tried booting up in the recovery mode and it started up and I received and error, which was too fast to read, and it rebooted.  Then it went down thru the "scan" section and hung up with "=======".

The good thing is that when I removed the card and rebooted everything worked.  This is much better than when I used EnvyNG and install the top NVIDIA driver which crashed the computer and I had to use windows to remove Ubuntu 8-04 and reinstall it.

I hope there is a solution I can perform while in the Intel onboard chip mode so that I can then reinstall the NVIDIA card and reboot.  I have not tried using BIOS as everything works in Windows Vista with or without the board.  One thing though, Windows Vista does not uninstall the Intel drivers but deactivates them on its startup.

Many thanks.

n7iqy

---

### Post by HotShotDJ on 2008-05-23
> **n7iqy said:**
> I am running Ubuntu 8.04 inside Windows Vista Home Basic.I'm sorry.  I don't understand what this means.  Do you run something like VirtualBox or VMWare with Windows as Host and Ubuntu as guest?

---

### Post by diablo75 on 2008-05-23
What do you mean you're running Ubuntu 8.04 "inside of Windows Vista"?  Do you mean to say you have Ubuntu running along side Windows in a dual-boot configuration?

---

### Post by n7iqy on 2008-05-24
> **HotShotDJ said:**
> I'm sorry.  I don't understand what this means.  Do you run something like VirtualBox or VMWare with Windows as Host and Ubuntu as guest?

I used the download to disk and ran it in Windows and selected the option of running inside Windows rather than a separate partition.  This way I can debug before setting up another partition.  Windows Vista gives the option of booting either Windows or ubuntu at startup.

I hope this answers your question as this is a new option in Hardy.

Thanks, n7iqy

---

### Post by n7iqy on 2008-05-24
> **diablo75 said:**
> What do you mean you're running Ubuntu 8.04 "inside of Windows Vista"?  Do you mean to say you have Ubuntu running along side Windows in a dual-boot configuration?

Hardy (Ubuntu 8.04) gives the option of installing Ubuntu inside Windows and also the old method of using a separate partition.  This way you can uninstall Ubuntu as a program in Windows without any possibility of partition damage.  I used this as a way to debug the installation and later if all runs well used a separate partition.

I hope this answers your question.

Thanks,  n7iqy

---

### Post by n7iqy on 2008-05-25
> **n7iqy said:**
> Hardy (Ubuntu 8.04) gives the option of installing Ubuntu inside Windows and also the old method of using a separate partition.  This way you can uninstall Ubuntu as a program in Windows without any possibility of partition damage.  I used this as a way to debug the installation and later if all runs well used a separate partition.

I hope this answers your question.

Thanks,  n7iqy

Well I tried to use BIOS and after installing the NVIDIA FX5500 video card I selected "Internal video chip" (Intel 82915G/GV/910GL) and then rebooted Ubuntu and installed ENVYNG and used "Nvidia auto card install" and all seemed to go well.

I then rebooted Ubuntu after changing BIOS to "PCI" and it failed to complete reboot.  I then changed back to the internal video chip in BIOS and rebooted Ubuntu and it came up, but in low resolution (800x600). I used ENVYNG to uninstall "auto detect of Nvidia card".  I tried many of the video cards in "versa" but to no avail.

This is where installing Ubuntu inside Windows comes into play, as all you have to do is remove the program in "Control Panel" and there are no problems.  I then reinstalled Ubuntu by inserting the CD while in Windows and selected "Install inside Windows" from the login screen.

It only takes 33 minutes to completely install Ubuntu with the 89 updates on my HP a820n computer.

Any suggestions?

n7iqy

---

### Post by Anduu on 2008-05-25
> Well I tried to use BIOS and after installing the NVIDIA FX5500 video card I selected "Internal video chip" (Intel 82915G/GV/910GL) and then rebooted Ubuntu and installed ENVYNG and used "Nvidia auto card install" and all seemed to go well.

Your problem is you installed the nVidia drivers while using your intel onboard chip.

you need to start from scratch...uninstall Wubi in windows and shutdown.

Install the PCI nVidia card and fire up the PC and enter the bios.
Change it to use the PCI card.
Exit and shut down.Connect your monitor to the new card.
Reboot and let Windows start up...it should let you know the nVidia card is installed and ask you to install the drivers.

Once you have the nVidia card working properly in Windows you can then install Ubuntu.Boot into Ubuntu and then use EnvyNG to install the nVidia drivers.

---

### Post by n7iqy on 2008-05-26
> **Anduu said:**
> Your problem is you installed the nVidia drivers while using your intel onboard chip.

you need to start from scratch...uninstall Wubi in windows and shutdown.

Install the PCI nVidia card and fire up the PC and enter the bios.
Change it to use the PCI card.
Exit and shut down.Connect your monitor to the new card.
Reboot and let Windows start up...it should let you know the nVidia card is installed and ask you to install the drivers.

Once you have the nVidia card working properly in Windows you can then install Ubuntu.Boot into Ubuntu and then use EnvyNG to install the nVidia drivers.

Thanks for the answer ANDUU, but I did do that and I failed to mention that Windows works fine with the card installed.  This problem exists in Ubuntu 7.10 as well as 8.04.  I believe that the problem is surly in that Ubuntu has yet to modify the drivers NVIDIA has made for Linux.

Again thanks, n7iqy

---

### Post by n7iqy on 2008-05-26
> **n7iqy said:**
> Thanks for the answer ANDUU, but I did do that and I failed to mention that Windows works fine with the card installed.  This problem exists in Ubuntu 7.10 as well as 8.04.  I believe that the problem is surly in that Ubuntu has yet to modify the drivers NVIDIA has made for Linux.

Again thanks, n7iqy

After I wrote this note I received 19 more updates in Ubuntu, one of which was "nvidia-glx".  So I installed it and it replaced the older version.  So I tried booting up with the nvidia card installed, first in Windows and everything worked fine and then in Ubuntu.  It looked better as the orfange scroll bars completed, but then it went into terminal mode, which it always does after I installed "nvidia-glx".  Here is the message at the end of the screen I received; "init.rc-default main process(4919) killed by SEGV signal".

I hope this gives someone enough info to come up with an answer.

n7iqy

---

