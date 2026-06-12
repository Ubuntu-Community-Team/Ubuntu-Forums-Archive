---
title: "Remote Boot Manager"
date: 2006-06-21
forum: Programming Talk
---

### Post by krypto_wizard on 2006-06-21
I was wondering if there can be something like remote boot manager.

I have to remotely start a computer. It has dual boot (WinXP and Linux).
My remote computer is Linux which will send command to remotely boot the other computer.

Can we write script or some utility which would let us select the Operating System to boot ? For example If we send parameter "WIN" it boots into Windows and if we send "NIX" it boots into Linux.

Every help is appreciated.

Thanks

---

### Post by ape on 2006-06-21
'man grub-reboot'

This command allows you to reboot to a specific entry in your menu.lst file.

---

### Post by krypto_wizard on 2006-06-21
I hope you read that I wanted to do it from a remote computer. I tried  man grub-reboot and it said " Reboots into the specified OS entry in menu.lst.

[QUOTE=ape]'man grub-reboot'

This command allows you to reboot to a specific entry in your menu.lst file.[/QUOTE]

---

### Post by ynef on 2006-06-21
If that doesn't suit you, perhaps you can use PXE boot or something? PXE is booting from the network card, so your BIOS and NIC have to support this feature.

If that doesn't work, you could make a pretty simple solution: if the computer is running Linux at the time you wish to change what OS to boot next, use the grub-reboot command in a ssh session. If it's running Windows, you need to have access to grub's boot menu somehow (ext2 driver for Windows, for instance) and can change the appropriate value in menu.lst that way.

---

### Post by ape on 2006-06-21
[QUOTE=krypto_wizard]I hope you read that I wanted to do it from a remote computer. I tried  man grub-reboot and it said " Reboots into the specified OS entry in menu.lst.[/QUOTE]

Actually, I did read that you wanted to do it from a remote computer.  That's what SSH is for.  Using SSH you can run any command remotely.

---

### Post by Cue2 on 2010-01-03
Sorry for dragging up a very old thread but I did a search and this was the most relevant.

I too want to be able to select what to boot remotely.
The method now is to use grub-set-default to toggle between OSes. The only drawback to this is that you have to wait for the current OS to boot before you can change it. 

Is there a very small bare bones distro which can act as a boot manager only and supports ssh?
That way I can use it as the default for GRUB and get it to boot automatically, then from there choose the OS I'd like to boot into.

I've been looking at Plop boot manager but from what I read it doesn't seem to allow remote access.


I'd like to learn more about PXE too since I have a PXE Motherboard. from what I understand it boots from a network i.e the OS itself is installed somewhere else other than the local HDD. is that correct? how would I choose which OS to boot remotely that way and does it have a performance cost.

Thanks in advance.

---

### Post by stn21 on 2012-02-09
> **Cue2 said:**
> Sorry for dragging up a very old thread but I did a search and this was the most relevant.

No need to be sorry, I find this thread most relevant :)

If you have a server that is locked away or at a different location it is very helpful to have some way of influencing the boot-process. Otherwise if something goes wrong you can end up with an unbootable PC and no way to repair it.

> Is there a very small bare bones distro which can act as a boot manager only and supports ssh?How about the alternate-CD of lubuntu or xubuntu? A partition of 3GB is big enough.

A remote bootmanager is helpful if your normal OS does not boot anymore. Then it should be possible to boot the small barebone distro as an emergency option. Otherwise the normal OS should boot.

Unfortunately setting the grub-default does not really help here because this configuration still boots one specific OS. If that becomes broken there is no way to change the grub-setting because that can only be done **after** a successful boot.

So I would say this is still kind of unsolved :|

---

