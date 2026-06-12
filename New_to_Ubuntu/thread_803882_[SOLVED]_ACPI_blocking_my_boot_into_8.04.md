---
title: "[SOLVED] ACPI blocking my boot into 8.04"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by BlakTygr on 2008-05-22
Hi you doing everybody? I hope better than I am.

Well, I finally figured out how to get my "Live CD" to work on my ASUS P4P800S Machine. I battled with it for three straight days now and I'm embarassed to say that the answer was on the menu the whole time. Right in front of my face ](*,) . The "F6" boot options to be precise. 

acpi=off
nolapic

I was able to boot the Live CD option and test to see if my hardware was compatible. I didn't get a chance to test all yet, but sound, graphics, and internet work fine from Live CD. Which is most important to me. So I chose to install Ubuntu to the whole hard drive. That worked fine. Until I rebooted to complete the install and could not get back into Ubuntu. I don't have the F6 boot options to bail me out this time. I turned off ACPI/APIC SUPPORT in the Bios, but it seems to want to work when it feels like it ( which is never most of the time). I know there has to be some code to get around this issue, but I don't know the first thing about source code. I want to learn how to code, so feel free to give me my first lesson as you help me with my problem. Oh...and here is some info to help.

Motherboard: ASUS P4P800S
Processor:   Intel Pentium 4 3.00 GHz
Graphics Card: Nvidia Geforce FX 5200 (Microshyte Corporation WDDM)
Sound:       SoundMAX Integrated Digital Audio
Hard Drive: Western Digital Enhanced IDE 80 GB  (Master) with Ubuntu
Hard Drive: Western Digital Enhanced IDE 160 GB  (Slave) with Vista HB

I'm writing this thread through the Live CD option right now. But I got to get into the installed version so I can finish dual booting these two hard drives. I really want to keep the 80 gig Ubuntu drive as the master drive. Teach me some code....ppllllleeeeeeeeeaaaaaaaaasssssee!!!! :(  

I appreciate any help. :)

---

### Post by spiderbatdad on 2008-05-22
Edit the 'Kernel' line in the file /boot/grub/menu.lst below the section: ####END DEFAULT OPTIONS####
```
gksu gedit /boot/grub/menu.lst
```

Remove "--quiet splash" from the end of the line, and add "acpi=off nolapic"
Save and reboot.

---

### Post by Patb on 2008-05-22
> **spiderbatdad said:**
> Remove "--quiet splash" from the end of the line, and add "acpi=off nolapic"
Don't you mean "acpi=off noapic"?

Cheers Pat

---

### Post by BlakTygr on 2008-05-22
> **spiderbatdad said:**
> Edit the 'Kernel' line in the file /boot/grub/menu.lst below the section: [COLOR="Red"]####END DEFAULT OPTIONS####[/COLOR]```
gksu gedit /boot/grub/menu.lst
```

Remove "--quiet splash" from the end of the line, and add "acpi=off nolapic"
Save and reboot.

I don't see the "####END DEFAULT OPTIONS####" in grub at all. But I do see this when I press "e" to edit Ubuntu boot options in grub.

root (hd0,0)
[COLOR="DarkRed"]Kernel  /boot/vmlinuz-2.6.24-16-generic
 root=UU ID=f1877f46-e8a6-485-initrd /boot/initrd.img-2.6.24-16-generic[/COLOR]

The one that's highlighted is the only "kernel" line that I see. but it seems to have two parts in it the has "boot". Which one do I edit or is that even the right kernel line you were talking about?

---

### Post by oedha on 2008-05-22
or....boot from livecd...then press F6
and follow what spiderdad asked you to add and erase
press enter to boot in

---

### Post by spiderbatdad on 2008-05-23
> **BlakTygr said:**
> I don't see the "####END DEFAULT OPTIONS####" in grub at all. But I do see this when I press "e" to edit Ubuntu boot options in grub.

root (hd0,0)
[COLOR="DarkRed"]Kernel  /boot/vmlinuz-2.6.24-16-generic
 root=UU ID=f1877f46-e8a6-485-initrd /boot/initrd.img-2.6.24-16-generic[/COLOR]

The one that's highlighted is the only "kernel" line that I see. but it seems to have two parts in it the has "boot". Which one do I edit or is that even the right kernel line you were talking about?

This change is made on an installed file system. The name of the file is /boot/grub/menu.lst. The command to edit the file is```
gksu gedit /boot/grub/menu.lst
``` So, boot the system and open a terminal: Applications>>Accessories>>Terminal. If you cannot boot, you can use the same parameters from the grub menu by pressing 'e' to edit then moving to the kernel line and pressing 'e' again, make your changes to the end of the kernel line, ie. acpi=off nolapic (taken from your original post) Then enter, then 'b' to boot...this method is not permanent...only for the one boot. Editing the file /boot/grub/menu.lst, will make the change permanent.
Here is an example of my kernel line in /boot/grub/menu.lst...look at the end of the line, where I have highlighted in bold:
```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=(some #'s) ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

```

---

### Post by BlakTygr on 2008-05-23
Hey that did it. Thank you spiderbatdad.

---

### Post by txcrackers on 2008-05-24
Unfortunately, that solution will only last until a newer kernel is released - which is quite likely to happen over the lifetime of HH... What you need to do to keep your changes through kernel updates is find this line:
```
# defoptions
```
Add your *noapic acpi=off* options on that line - **do not remove** the leading "#"

This particular line is used by the Debian kernel upgrader to "persist" kernel options across updates.

---

### Post by kenno69 on 2008-06-12
Thanks for this thread ..helped me overcome a new instal.
Needed to do the F6 option ie turn APIC off.
Ta fellas 
:):):)

---

