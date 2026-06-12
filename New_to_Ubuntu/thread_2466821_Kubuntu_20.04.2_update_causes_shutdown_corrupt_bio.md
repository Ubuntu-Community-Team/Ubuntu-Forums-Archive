---
title: "Kubuntu 20.04.2 update causes shutdown corrupt bios, reboot hangs, won't wake from sl"
date: 2021-09-06
forum: New to Ubuntu
---

### Post by thenorthwestgrid on 2021-09-06
Installed Kubuntu from the 20.04.2 LTS ISO. Shutdown, reboot, wake from sleep worked fine. Updates for 20.04.2 caused issues where it wouldn't wake from sleep, rebooting hangs, and never actually shutdowns for the reboot, and shutdown causes an audible hardware clicking noise (somewhere to the left side of the computer underneath the keyboard) and corrupts the BIOS. The corrupted BIOS causes the computer to not boot at all and I have to do a BIOS reset via CMOS (Hold the power button for 2-3 sec while pressing the WIN+v keys until it begins to boot). This gets more difficult each time it's done, where I have to wait longer before trying it and it seems to take longer to work. I have tried shutdown from the GUI menu, from the log-out menu, from Konsole, and from a TTY (CTRL+ALT+F2).
I also have tried reinstalling a couple of times. 

I know that 20.04.3 is out and these issues persist even after updating to that version.
Computer specs:
```
Host: HP Pavilion dv7-2180us Notebook PC Rev 1
Kernel: 5.8.0-59-generic
Resolution: 1600x900
CPU: Intel Core 2 Quad Q9000 (4) @ 2.001GHz
GPU: AMD ATI Mobility Radeon HD 4650/5165
Memory: 6 GB
```

I have an opened bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1942008").

---

### Post by mastablasta on 2021-09-07
clicking noise usually indicates some moving part malfuctioning. either fan and it then overheats or hard disk drive if you have a spinning disk. to eliminate the disk, boot up and use smartmon tools to check the disk. 

also you could try 20.04.1 with LTS kernel 5.4. you only really need newer kernel if you want one of the new features or need support for new hardware.

---

### Post by ActionParsnip on 2021-09-07
Make sure you have the latest BIOS too. If you look online for "click of death" it is nothing to do with Ubuntu and a failing piece of hardware

---

### Post by thenorthwestgrid on 2021-09-07
@mastablasta & @ActionParsnip

Thanks for responding. 

This has never happened while running Windows Vista, 7 or 10. When I put my Windows 10 HDD back in, I have no problems with any of these. The drive in question is a SSHD&#8203; (Solid State Hybrid Drive), which I also had Windows installed on. I have recently checked the disk in both Windows and Linux prior to using to be sure it was OK.[COLOR=#C8C3BC][FONT=DDG_ProximaNova]

[/FONT][/COLOR]If I try [COLOR=#E8E6E3]20.04.1 with LTS kernel 5.4 or just reinstall from the 20.04.2 LTS ISO, how do I prevent it upgrading? Or is there some way to downgrade the kernel, if that's what the issue likely is. I certainly wouldn't need the most up-to-date kernel as the laptop is old.[/COLOR]

The laptop is from 2009, so the BIOS is definitely the latest it could possibly have as I updated it many years ago. Click of death is interesting, but it doesn't seem to be that's what's happening here. The sound is not coming from where the disk drive is. I have never heard that sound before, and it happens regardless whether the drive is placed inside the laptop or attached via USB cable.

---

### Post by thenorthwestgrid on 2021-09-08
Thanks for the suggestion to downgrade the kernel version. I followed the instructions [here]("https://www.reddit.com/r/Ubuntu/comments/nuhurp/downgrading_linux_kernel_ubuntu_2004/") and [here]("https://askubuntu.com/questions/1310622/downgrade-to-kernel-5-4-0-because-kernel-5-8-45-doesnt-like-my-bluetooth-contro") and it worked! All the options now work once again! :) I used Muon to remove all the newer kernel versions and their respective modules and headers. I am wondering about the future and kernel upgrades with the next LTS version. Is this something I need to plan for? Thanks!

Edit: I should mention that I used this command to see installed kernels: ```
dpkg --list | grep linux-image
``` and this command to see the kernel in use: ```
uname -r
```

---

### Post by mastablasta on 2021-09-08
yes, upgrades are always something you need to plan for. especially kernel upgrades that holds most of drivers. hopefully they will resolve your issue before the next kernel version.

---

### Post by thenorthwestgrid on 2021-09-08
Thanks. Yeah, hopefully this issue will get resolved. :)

---

