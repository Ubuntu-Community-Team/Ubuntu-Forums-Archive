---
title: "Reboot instead of shutdown"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by dejan_87 on 2013-11-18
Hi,
I use ubuntu 13.10 on acer aspire v5-571 laptop.When i try to shutdown my laptop restarts.I try on battery and on ac power but always happens the same. How to fix this?
Thanks.

---

### Post by BBQdave on 2013-11-18
Are you attempting shutdown with the **Shut Down** button (located in top right menu of Unity)?

On some hardware, if you press the hardware power button, it intiates a reboot. To do a hard shutdown, you hold the hardware power button. Though it is best to shutdown from your OS (using **Shut Down** button in menu).

---

### Post by newb85 on 2013-11-18
Try running the following command from a terminal and see which it does:
```
sudo shutdown -P now
```

---

### Post by dejan_87 on 2013-11-19
@new85 I've tried that. Same problem...

---

### Post by dejan_87 on 2013-11-19
> **BBQdave said:**
> Are you attempting shutdown with the **Shut Down** button (located in top right menu of Unity)?

On some hardware, if you press the hardware power button, it intiates a reboot. To do a hard shutdown, you hold the hardware power button. Though it is best to shutdown from your OS (using **Shut Down** button in menu).

When i use the shut down menu it shutdown and after 3 sec laptop starts by itself. I can only shutdown when i hold the hardware power button.

---

### Post by philinux on 2013-11-19
Is there some setting in the bios that's causing this.

---

### Post by dejan_87 on 2013-11-19
I don't think so, on windows everything works fine.

---

### Post by philinux on 2013-11-19
> **dejan_87 said:**
> I don't think so, on windows everything works fine.

There is a thing called "wake on lan motherboard" IIRC.

Try switching off the router and then see if it shutsdown as it should.

---

### Post by DuckHook on 2013-11-19
Please provide following info:

1. Is this your first experience with Ubuntu? If not, did it happen with previous versions?
2. Was behaviour okay prior to some update, or has this been the behaviour from the start?
3. Did you change any settings? eg. configuration files? If so, what did you change?
4. Do you have external devices attached to your laptop? eg. USB drive? Name all.
5. Are you running 32-bit or 64-bit? Please post back output of```
uname -a
```

Google shows that there can be any one of half a dozen reasons for this behaviour. You may wish to start with the least disruptive options first:

1. Install laptop-mode-tools which may install enough laptop config settings to allow Ubuntu to poweroff elegantly. After install, choose laptop mode.```
sudo apt-get update && sudo apt-get install laptop-mode-tools
```2. If above doesn't solve your problem and you don't need the wake-on-lan feature, then go into BIOS and turn this feature off.

3. Set ACPI to not route IRQs. A captured IRQ that the kernel doesn't release could cause BIOS to always cycle rather than power off. Using either "sudo nano" or "gksudo gedit", add "acpi=noirq" to GRUB as follows:```
gksudo gedit /etc/default/grub
```Find the line starting GRUB_CMDLINE_LINUX_DEFAULT and add *acpi=noirq* to the end between the quote marks so that it resembles```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=noirq"
``````
sudo update-grub
```This change cannot take effect until after at least one full reboot cycle, so don't expect it to power off your machine the first time. If problem remains, then reverse procedure and take out the change. No point in diminishing functionality if it doesn't do anything.

There have been reports in other distro [forums]("https://bbs.archlinux.org/viewtopic.php?id=170111") of the 3.11 kernel being wonky with shutdowns. Version 13.10 is relatively new, so it's not surprising to hear that bugs are still cropping up. If so, then no solution may exist until it's fixed in a future update.

---

### Post by dejan_87 on 2013-11-27
> **DuckHook said:**
> Please provide following info:

1. Is this your first experience with Ubuntu? If not, did it happen with previous versions?
2. Was behaviour okay prior to some update, or has this been the behaviour from the start?
3. Did you change any settings? eg. configuration files? If so, what did you change?
4. Do you have external devices attached to your laptop? eg. USB drive? Name all.
5. Are you running 32-bit or 64-bit? Please post back output of```
uname -a
```

Google shows that there can be any one of half a dozen reasons for this behaviour. You may wish to start with the least disruptive options first:

1. Install laptop-mode-tools which may install enough laptop config settings to allow Ubuntu to poweroff elegantly. After install, choose laptop mode.```
sudo apt-get update && sudo apt-get install laptop-mode-tools
```2. If above doesn't solve your problem and you don't need the wake-on-lan feature, then go into BIOS and turn this feature off.

3. Set ACPI to not route IRQs. A captured IRQ that the kernel doesn't release could cause BIOS to always cycle rather than power off. Using either "sudo nano" or "gksudo gedit", add "acpi=noirq" to GRUB as follows:```
gksudo gedit /etc/default/grub
```Find the line starting GRUB_CMDLINE_LINUX_DEFAULT and add *acpi=noirq* to the end between the quote marks so that it resembles```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=noirq"
``````
sudo update-grub
```This change cannot take effect until after at least one full reboot cycle, so don't expect it to power off your machine the first time. If problem remains, then reverse procedure and take out the change. No point in diminishing functionality if it doesn't do anything.

There have been reports in other distro [forums]("https://bbs.archlinux.org/viewtopic.php?id=170111") of the 3.11 kernel being wonky with shutdowns. Version 13.10 is relatively new, so it's not surprising to hear that bugs are still cropping up. If so, then no solution may exist until it's fixed in a future update.

1.I use ubuntu since 8.04 version but not on this laptop.On my new laptop my first ubuntu was 13.04 and i got the same problem.
2.From the start.
3.No i don't change anything.This is happend right after new installation.
4.No i don't.
5.I run 64 bit version of ubuntu.
```
dejan@dejan-Aspire-V5-571:~$ uname -a
Linux dejan-Aspire-V5-571 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
I installed laptop-mode-tools and i can shutdown laptop but only on AC power, on battery still restarts.Also i disabled "wake-on-lan" feature in BIOS but nothing changed.Then i put "acpi_noirq" as boot parameter like you suggested and i can shutdown now but can't connect to internet.If i remove "acpi_noirq" from grub it connects to network but laptop restarts.

I installed windows 7 it shutdown fine.I tried arch linux and opensuse 13.1 and same thing happend.With laptop-mode-tools installed opensuse shutdown fine on AC power and on battery.

Thanks and sorry for my bad english.

---

### Post by thewillbowles on 2013-11-28
I'm having the same problem on my desktop running 12.04. I've found the cause to be hardware related. I have a PCI-E card installed which I need for my work. When I remove it, I can shutdown fine but when it's in, the shutdown button just logs me out or if I use sudo shudown -P now it will restart. Why it does it I have no idea!

---

### Post by Sef on 2013-11-28
Had a similar problems years ago and had to go change something in the BIOS.  If i remember correctly, it was under power management.

---

### Post by ML7rcEx on 2013-11-28
I also have an Acer Aspire V5-571 laptop and was plagued with this problem. Now the cure for this problem i found was, i have a pen drive inserted into the usb drive where it resides on a permanent basis. When i have this pen drive inserted into the usb drive i can shut down Lubuntu 13.10 without any problem what so ever. But if i remove the pen drive prior to an attempt to shut the laptop down results in the laptop continually restarting. Make of this what you will but it definitely works for me.

---

### Post by DuckHook on 2013-11-28
Hi dejan_87,

Just stumbled across this thread again and purely by chance. After 48 hrs without response, I unsubscribe from threads, so don't get notified of further replies.

According to my research, many of these issues stem from the way BIOSes implement ACPI and, in turn, the interplay between ACPI and I/O-APIC. I don't really know what these acronyms even truly involve, but ACPI is the subsystem that handles power management, and APIC is the system architecture designed to assign high IRQs to multi-core CPUs. Some BIOSes don't interpret these system calls properly in Linux but work correctly in Windows. In fact, sometimes certain BIOSes must be kludged in order to work with Windows and it is this process that actually breaks them with Linux. Therefore, in situations like yours, one of the first recommendations is to update the BIOS. Often, this will solve the problem and no further action is needed.

If BIOS is already the most recent, or updating the BIOS is not possible or practical, then some BIOSes allow you to fine-tune their power parameters. Since they are all so different, I can't guide you on this one. Perhaps one of the HW gurus in the HW forum can. If you are feeling adventurous, you can experiment systematically, by changing one setting, trying to power off, changing it back and trying another, and so forth. The settings you should concentrate on will have something to do with "power". If they are actually called "ACPI" then this is a dead giveaway.

Some people have also had success changing card slots for their various PCI cards. This actually makes some sense. If the problem arises from an IRQ conflict or a Bus overlap, then changing a card slot may be just enough to set the IRQ to an unused one, or free up a Bus address. Some of the other contributors have noted that loopy things like having a USB stick connected, or a certain PCI card either brings on the problem or resolves it. If so, then it's probably an IRQ/Bus issue. I was especially tickled by ML7rcEx's experience with the magic USB stick, although I'm sure that ML7rcEx is none too thrilled having to resort to such workarounds. Try disabling your NIC altogether. You can't work without connectivity, but it's an attempt to isolate the problem.

If none of the HW techniques work, then it's time to try fiddling with the kernel. You've already done so, to some extent, by trying the boot parameter "acpi=noirq". [Here]("https://wiki.ubuntu.com/DebuggingACPI") is the page with the various boot parameters. You can try each of them, but some may take away too much functionality, or your system may not even work. Therefore, before doing anything, be sure you know how to edit GRUB at boot before changing any further boot parameters.

Aside from the above, I'm afraid I'm out of ideas.

---

### Post by grobar87 on 2013-12-01
I think i finally fix this! I check everything that you suggested here... with no luck.Than i decide to reinstall ubuntu again and i install laptop-mode-tools.Now it shutdown fine on battery and on AC power.I don't know why this solusion not work before.Anyway thanks to all for help.I mark this solved.

---

### Post by NilPointer on 2014-08-02
I know resurrecting old threads isn't good, but I'll leave this to (possibly) help people, who might have the issue.

I had same problem on my Lenovo M5400 laptop (with Ubuntu 14.04). Nothing suggested in this thread helped me, however I've managed to find a solution. My laptop has one Always-On USB (yellow) port for charging devices while laptop is powered off and it was enabled in the BIOS. After disabling this option in the BIOS (Config->USB->Always On USB) laptop began to shutdown correctly, instead of rebooting.

---

### Post by Webmasters_Pride on 2014-08-02
Is the same thing happens with 32bit version of ubuntu?

---

### Post by NilPointer on 2014-08-03
Didn't check, don't have a 32-bit version of Ubuntu. However, I doubt it would make any difference. The problem seems to be BIOS/ACPI related, so result should be pretty much same on both 32-bit and 64-bit kernels.

---

