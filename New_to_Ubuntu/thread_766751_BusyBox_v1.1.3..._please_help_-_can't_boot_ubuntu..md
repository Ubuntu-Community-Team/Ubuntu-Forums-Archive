---
title: "BusyBox v1.1.3... please help - can't boot ubuntu."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by shedokan on 2008-04-25
I just installed ubuntu in windows and after the installation I booted to ubuntu but I got a dos screen telling me BusyBox v1.1.3...
please help.
thanks.

---

### Post by shedokan on 2008-04-25
please.

---

### Post by aeiah on 2008-04-25
this error seems to occur when people have errors with the cd they're using and things like that. maybe wubi didnt download all the data it needed due to the servers being very busy these past two days. you could consider downloading the iso and going through a normal installation, or try using wubi again.

did any other errors come up whilst you were installing, or does the command line shell (what you're calling the dos screen) tell you anything about an error?

---

### Post by aeiah on 2008-04-25
oh, and if you're going to try installing it again, i suggest defragging your hard drive first, this can help i think. ive never used wubi before though to be honest, i always install from the cd and set up partitions and such for dual boot. there are plenty of howtos and tutorials for it on these forums if you fancy doing that.

---

### Post by shedokan on 2008-04-25
I had errors like "[ 274.966874]Buffer I/O error on device fd0, logical block 0" before busybox...
 so I disabled my floppy from Bios settings an no errors, but I still get to the BusyBox.

---

### Post by shedokan on 2008-04-25
and I checked the iso image using md5sum and it matched!
and I didn't even get to finishing the installation, it told me to reboot to finish the installation and then I got the error.

---

### Post by avkhatri on 2008-04-25
Do you have an ATI video card? I heard that could be one of the reasons if the md5sum matched I had the exact same problem I had to reformat to 7.10 because of this. 

It seems to be a problem with the kernel since I updated from the update manager in Ubuntu and I was able to boot 8.04 with the 7.10 kernel fine but not from the 8.04 kernel.

This is ridiculous, brand new OS and this is happening to people :(

---

### Post by Kilz on 2008-04-25
You might be experiencing a known issue with 8.04. [Please read the instructions for wubi here.]("http://www.ubuntu.com/getubuntu/releasenotes/804")

---

### Post by shedokan on 2008-04-25
I'm using windows XP, and I have an nvidia card.
I installed ubuntu before but not in windows

---

### Post by shedokan on 2008-04-26
please!!!

---

### Post by Solrac924 on 2008-04-26
hang in there shedokan. i'm having a similar problem. we'll get it taken care of. in the meanwhile, have you edited your boot with the following:
irqpoll
all_generic_ide
ide=nodma
acpi=off noacpi

---

### Post by shedokan on 2008-04-27
I don't have boot options, I have finish installation options.

---

### Post by Solrac924 on 2008-04-29
i mean when you boot up & see GRUB, highlight Ubuntu & press 'E'. then highlight the kernal "...vmzlinuz..." & press 'E'. after deleting "quiet slash", add the following boot parameters: "noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317"
this should mount the filesystem. does it boot all the way now?

---

### Post by shedokan on 2008-04-30
never mind the problem is a broken disk detection.

---

### Post by Solrac924 on 2008-05-03
ok, sorry to hear that. best thing to do now is a CD re-burn using a slower speed. your patience & persistence will prevail in the end. :mrgreen:

---

