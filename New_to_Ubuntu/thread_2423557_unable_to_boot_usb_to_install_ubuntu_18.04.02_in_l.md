---
title: "unable to boot usb to install ubuntu 18.04.02 in lenovo laptop with &quot;dual&quot; boot"
date: 2019-07-25
forum: New to Ubuntu
---

### Post by vale96 on 2019-07-25
Hello everyone!

I have a lenovo ideapad 310 laptop with 1 TB space. It originally had Windows 10 installed, I tried to do a partition with ubuntu but failed. I mean, I successfully installed ubuntu but lost windows, so I currently have a lot of space that I left to windows that I cannot have access to. I wanted to get that space back by installing only ubuntu on my laptop.
I am trying to do it via usb, however I cannot boot it nor I can have access to the BIOS (I tried all the F keys, Esc and space but nothing worked). I tried to make my usb pendrive bootable by using both etcher and the default program in ubuntu, but nothing changed.
Can you help me? Tell me everything you need in case.
Thanks!

---

### Post by SeijiSensei on 2019-07-25
Did you do a Google search first?
> 
In lenovo laptops,

you can use F12 key to open boot menu.

Sometimes you will also have to use Fn+F12 key to open boot menu.


[https://www.quora.com/What-is-the-boot-key-in-Lenovo-laptops](https://www.quora.com/What-is-the-boot-key-in-Lenovo-laptops)

---

### Post by oldfred on 2019-07-25
If you have fast boot setting on in UEFI, you may not have time to press a key before it starts booting.
It assumes no system changes, so the normal startup of scanning system and writing data to drive is skipped. Often then you need a full cold boot to force the system to do the system scan and give time to press key to get into UEFI or UEFI boot menu.

If laptop you also may need to remove battery, turn system off & hold power switch for 10 sec to totally drain any power. On my desktop I know mainboard is powered down when monitor finally says no signal, but I still wait a bit.

---

### Post by CatKiller on 2019-07-25
> **oldfred said:**
> If you have fast boot setting on in UEFI, you may not have time to press a key before it starts booting.
It assumes no system changes, so the normal startup of scanning system and writing data to drive is skipped. Often then you need a full cold boot to force the system to do the system scan and give time to press key to get into UEFI or UEFI boot menu.

In those circumstances, if Ubuntu is already installed, one can use ```
sudo systemctl reboot --firmware-setup
``` to reboot into UEFI.

---

### Post by vale96 on 2019-07-25
> **SeijiSensei said:**
> Did you do a Google search first?


[https://www.quora.com/What-is-the-boot-key-in-Lenovo-laptops](https://www.quora.com/What-is-the-boot-key-in-Lenovo-laptops)


I absolutely did and never found the Fn trick -they were always about the other F keys. Thanks!

---

### Post by oldrocker99 on 2019-07-25
Here's a method from Lifewire.com:
```
Lenovo (formerly IBM)
ThinkPad, IdeaPad, Yoga, Legion, H535, 3000 Series, N Series, ThinkCentre, ThinkStation

Press F1 or F2 after powering on the computer.
Some Lenovo products have a small Novo button on the side (next to the power button) that you can press (you might have to press and hold) to enter the BIOS setup utility. You might have to then enter BIOS Setup once that screen is displayed.
Press F12 to access BIOS.
Older Lenovo products allow access to BIOS using Ctrl+Alt+F3, Ctrl+Alt+Ins, or Fn+F1.
```

Good luck!

---

