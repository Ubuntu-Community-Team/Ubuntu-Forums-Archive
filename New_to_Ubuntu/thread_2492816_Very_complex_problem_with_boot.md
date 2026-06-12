---
title: "Very complex problem with boot"
date: 2023-11-23
forum: New to Ubuntu
---

### Post by srsh-kh on 2023-11-23
I have an MSI all-in-one PC with windows 10 and ubuntu. Usually I would start it up and go to ubuntu booting page and I had configure it in a way so that if I don't select any options after 3 seconds it would start the first option which was Win 10. But after updating to ubuntu 23 my keyboard doesn't work anymore on the booting page and also the first option has changed to memory test (with a blue screen) so now there is no way for me to select any operating syste. What shouldnI do?

---

### Post by tea for one on 2023-11-23
Your keyboard should certainly be active to access UEFI settings
i.e. before Grub or Windows Boot manager is visible.

While you power on the PC, tap the dedicated key (the screen may display the answer - F2 or F10 or Esc or Del (see your PC manual)
Once in UEFI settings, can you change boot priority?

---

### Post by srsh-kh on 2023-11-23
> **tea for one said:**
> Your keyboard should certainly be active to access UEFI settings
i.e. before Grub or Windows Boot manager is visible.

While you power on the PC, tap the dedicated key (the screen may display the answer - F2 or F10 or Esc or Del (see your PC manual)
Once in UEFI settings, can you change boot priority?

I tried all the keys. There's no way for me to access Bios setting. I think it's because fast boot in on. But keyboard works in memory test mode which does nothing except testing memory. There's also no PS/2 keyboard slot on my PC. Can I fix it by taking out the motherboard battery?

---

### Post by srsh-kh on 2023-11-23
this is where it's stuck
[IMG]https://s6.uupload.ir/files/fiuzh_u0bf.jpg[/IMG]
[IMG]https://drive.google.com/file/d/10Z7izJkdq7IWLNUTP6_pjKk5JXDYHgwU/view[/IMG]
[IMG]https://drive.google.com/file/d/10Z7izJkdq7IWLNUTP6_pjKk5JXDYHgwU/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/10Z7izJkdq7IWLNUTP6_pjKk5JXDYHgwU/view?usp=sharing[/IMG]

---

### Post by tea for one on 2023-11-23
> **srsh-kh said:**
> I tried all the keys. There's no way for me to access Bios setting. I think it's because fast boot in on. But keyboard works in memory test mode which does nothing except testing memory. There's also no PS/2 keyboard slot on my PC. Can I fix it by taking out the motherboard battery?
Power off the PC
Remove the internal drives
Boot into  "Try Ubuntu" live session using your Ubuntu install usb
If successful, open a terminal and enter:-
```
sudo systemctl reboot --firmware-setup

```
Disable UEFI Fast Boot setting

Alternatively - Buy, beg, borrow a USB keyboard

---

### Post by srsh-kh on 2023-11-23
I finally fixed it by holding the power button which took me to BIOS setting directly.

---

### Post by tea for one on 2023-11-23
Well, we live and learn, don't we.

Now, disable all the fast boot settings:-
Fast Start Up (Widows system setting)
Fast boot (UEFI setting)
fastboot (grub setting to prevent file system check at boot) e.g.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fastboot"
```

Can you now set the boot priority for your preferred OS?

---

### Post by srsh-kh on 2023-11-23
> **tea for one said:**
> Well, we live and learn, don't we.

Now, disable all the fast boot settings:-
Fast Start Up (Widows system setting)
Fast boot (UEFI setting)
fastboot (grub setting to prevent file system check at boot) e.g.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash fastboot"
```

Can you now set the boot priority for your preferred OS?

Yeah now it goes right into windows each time. Linux is so delicate and potentially painful.

---

### Post by tea for one on 2023-11-23
> **srsh-kh said:**
>  Linux is so delicate and potentially painful.
All these years using Ubuntu, I must have been blessed by the Gods to avoid the Linux delicacy and pain.

Anyway, to help other forum users/searchers, it's a nice gesture to mark the thread as solved:-
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ian-weisser on 2023-11-23
> **srsh-kh said:**
> Linux is so delicate and potentially painful.

I find Linux systems to be robust, repairable, and reliable.

Any delicacy is self-inflicted by your choices.
Dual-boot is delicate (because of Windows)
Fast Boot problems are entirely due to Windows.

Every reputable guide for many years has warned that Windows makes dual-boot much harder than it needs to be.
And much harder than it used to be 15 years ago.

---

