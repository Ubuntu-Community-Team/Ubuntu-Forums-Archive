---
title: "Grub doesn't load after Ubuntu restart"
date: 2022-04-17
forum: New to Ubuntu
---

### Post by pr0ph3te on 2022-04-17
Hello, 

I'm dual-booting Windows 10 and Ubuntu on two different SSD. Everything works as it should when I turn on the computer, I get Grub and I can choose to boot between ubuntu or windows. However, if I connect to Ubuntu and do a reboot, the computer restarts but it does not load Grub anymore, it remains stuck on the screen where you can press F2 or DEL to enter the BIOS (the input does not work either). So I have to shut down the computer and turn it back on if I want Grub to reload. I tried with Ubuntu version 20.04 as well as version 21.10 and even the beta of 22.04. I have also tried to completely erase all my hard drives and install only Ubuntu but there is always the same problem on reboot. If I reboot from Windows it loads Grub correctly every time. Have you ever encountered a similar problem or have any idea what it could be?

---

### Post by oldfred on 2022-04-17
What brand/model system?
What video card/chip?
If you want lots of details on hardware you can run this new script. Do not copy data from the screen as it may include data you do not want to share. The upload to pastebin site removes that type of data. Spacebar thru the screens & q to exit screens.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info

```

Some systems only want to boot "Windows" by name. This is an UEFI or UEFI settings type issue.

If you have Ubuntu installed you can run this report. It probably cannot fix issue, but report may show enough details if a configuration issue. Will not show UEFI settings.

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by pr0ph3te on 2022-04-17
[https://paste.ubuntu.com/p/j2Y36gzkqP/](https://paste.ubuntu.com/p/j2Y36gzkqP/)

---

### Post by oldfred on 2022-04-17
Your current install is the 22.04 Beta booted in UEFI mode with nVidia driver.

Have you updated UEFI & SSD firmware?
With my Samsung NVMe drive, I downloaded the update ISO. 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.


With one install, you do not normally get grub menu.
For UEFI, you have to press escape right after vendor logo but before grub menu would normally appear. If UEFI fast boot on, you may not have time to press any key and have to fully shut down and do a "cold" boot, so system does a full scan of what hardware you have and gives just enough time to press the correct key to get into UEFI settings or UEFI boot menu.

---

### Post by grahammechanical on 2022-04-17
As a curiosity, what happens if you restart using the terminal?

either of these commands will do something.

```
sudo shutdown -r now
```

```
 sudo shutdown --reboot now
```

Regards

---

### Post by pr0ph3te on 2022-04-17
It restarts the computer, but the same problem appears. It reboot the computer and directly stay blocked on the press DEL - F2 to enter UEFI Settings of my Motherboard (so it doesn't load GRUB and don't respond to any of my input). So I need to power off by pressing the power off button and then power on the computer and the GRUB menu load correctly. I have the choice to boot windows or linux from there. I've tried with some other debian based distros and I have the same problem, I tried with Fedora 35 and I don't have the problem (but I need to work with Ubuntu so switching to Fedora is not really a solution ahah). I tried updating the Firmware but everything is up to date.

---

### Post by oldfred on 2022-04-17
Did you try changing boot order in UEFI settings (not the UEFI boot menu)?

Post link to Boot-Repair's Summary Report.

---

### Post by pr0ph3te on 2022-04-17
Always the same problem. Here is the link : [https://paste.ubuntu.com/p/VndwkFCGJj/](https://paste.ubuntu.com/p/VndwkFCGJj/)

---

### Post by tea for one on 2022-04-17
[COLOR="#0000FF"]Line 78[/COLOR] - OS#1:   The OS now in use - Ubuntu Jammy Jellyfish on nvme0n1p2
[COLOR="#0000FF"]Line 309[/COLOR] - Blockers in case of suggested repair:
[COLOR="#0000FF"]Line 311[/COLOR] - Please use this software in a live-session (live-CD or live-USB). This will enable this feature.

It looks like you should use boot-repair in a [COLOR="#0000FF"]live[/COLOR] session

---

### Post by pr0ph3te on 2022-04-17
Here is the link of the pastebin I executed from Boot Repair from live USB : [https://paste.ubuntu.com/p/CzQpT9F93X/](https://paste.ubuntu.com/p/CzQpT9F93X/) . Maybe I'll try doing the Recommended repair from live USB Boot Repair.

---

### Post by grahammechanical on 2022-04-17
This suggestion is unlikely to be the cause but I give it anyway. Open /etc/default/grub. Does it have this line?

> GRUB_DISABLE_OS_PROBER=TRUE

If it does change it to

> GRUB_DISABLE_OS_PROBER=FALSE

If there is no reference to disable os-prober, then enter the line 

> GRUB_DISABLE_OS_PROBER=FALSE

That may fix things or not.

[https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix](https://www.omgubuntu.co.uk/2021/12/grub-doesnt-detect-windows-linux-distros-fix)

Regards

---

### Post by oldfred on 2022-04-17
I see this comment:
> Platform is in Setup Mode 

Not sure what that means. 
Some mention user mode and then changing Secure boot to custom or standard, but not really having UEFI Secure Boot on?
Do not know your motherboard settings. You may want to review manual as it often has a bit more explanation than what UEFI shows.

---

### Post by pr0ph3te on 2022-04-17
I tried to fix the boot with the live USB, it didn't change anything except that now I have a ubuntu BOOT entry on the SSD where Windows is also located. I also added the line GRUB_DISABLE_OS_PROBER=FALSE. That didn't change anything either. I read the manual of my ASUS x570-e motherboard, it does not indicate anything about the SETUP mode of the Secure Boot, this one is correctly disabled yet no Platform Key is loaded, and the OS Type of my motherboard is in Other OS and not Windows UEFI mode. I think I will put Windows as the main boot option so I don't have any problem loading GRUB and just go through the UEFI boot to choose Ubuntu every time when rebooting.  Thanks for your help to all.

---

