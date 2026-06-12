---
title: "running ubuntu from cd"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by 901 on 2013-06-14
I have tried to load version 12.04 from a CD. I'm getting text that I don't understand. What does the following mean that i need to try next?

[0.032001] Kernal Panic-not syncing: IO-APIC +timer doesn't work! Boot with apic=debug and send a report. Then try booting with the 'noapic' option.
[0.032001]
[0.032001] Pid:1 comm: swapper/0 not tainted 3.5.0-23-generic #35" precise 1-Ubuntu
[0.032001] Call time:
[0.032001] [<c15cd72b>] panic + 0x81/0x189
[0.032001] [<c18ea290>] setup_IO_APIC + 0x592/0x5cb
[0.032001] [<c18e66cc>] native_smp_prepare_cpus + 0x177/0x169
[0.032001] [<c18d8b36>] kernal_init + 0x78/0x129
[0.032001] [<c18d8abe>] ? do_basic_setup + 0xa3/0xa3
[0.032001] [<c15ea3be>] kernal_thread_helper + 0x6/0x10

---

### Post by BioHazardTM on 2013-06-14
I think this might help: [http://ubuntuforums.org/showthread.php?t=917687](http://ubuntuforums.org/showthread.php?t=917687)

---

### Post by 901 on 2013-06-16
The thread might help if I knew enough about linux to understand what it was telling me? I don't know how to enter the bios let alone edit the lines that are called out in the thread. Is there a location that is lower than absolute beginers where we can get that type of info?

---

### Post by billcecil on 2013-06-17
I would say no. I've been using ubuntu for a long time, and none of it makes sense to me. I'm switching now.

---

### Post by Impavidus on 2013-06-17
Entering the bios: When you switch on the computer you can hit a key to enter the bios. Usually it says which key on a screen with the manufacturer's logo. On most systems it's either escape, F10, F12 or delete.

Change that line: If you're trying to boot the live disk you'll get a screen with a graphical representation of a keyboard and a human. Then hit any key and you'll get a menu where you can add boot options like these.

---

### Post by mastablasta on 2013-06-17
> **901 said:**
> The thread might help if I knew enough about linux to understand what it was telling me? I don't know how to enter the bios let alone edit the lines that are called out in the thread. Is there a location that is lower than absolute beginers where we can get that type of info?

BIOS has nothing to do with operating system. well what i mean is that BIOS boots before any operating system loads. It is in a ROM chip on motherboard. And therefore how to access it is found in motherboard manual (or notebook manual). it is also often written how to access it on the start up screen when you turn on your mashcine.

anyway to get ubuntu boot option you need to press F6:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

in your case it says:
> Boot with apic=debug and send a report. Then try booting with the 'noapic' option.

so just try to boot with 'noapic' boot option. you can later set is permanent if you decide to install the OS.

and it would be good to give us some system specs.

---

### Post by grahammechanical on 2013-06-17
Just to put the instructions a little bit clearer.

When the Ubuntu DVD starts to load we get a purple screen with an icon of a keyboard and an icon of a human. Press Enter. The next screen will offer a language selection. Press Enter to accept English as the language. The next screen will give us options to TRY UBUNTU; INSTALL UBUNTU and a couple of other options. Press F6 and a small menu will appear. Like this

> acpi=off
noapic
nolapic
nodmraid
nomodeset

Select one and press Enter. Then press Esc and we are back to the TRY - INSTALL screen. Make sure TRY UBUNTU is selected and then press enter. You may find that you need to experiment with the F6 options even using a combination of more than one option.

The nomodeset options sometimes works if there are issues with video drivers.

Regards.

---

