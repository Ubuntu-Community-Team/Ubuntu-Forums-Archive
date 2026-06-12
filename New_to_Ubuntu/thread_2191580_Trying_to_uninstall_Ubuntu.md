---
title: "Trying to uninstall Ubuntu"
date: 2013-12-03
forum: New to Ubuntu
---

### Post by Silicon_Knight on 2013-12-03
So basically I am an Idiot and I messed up my install of Ubuntu 12.04 that i had dual booted with Windows 8.1. I tried to update to 13.04 and That's what messed it up at first. It wouldn't let me boot into Ubuntu anymore. Every time I chose Ubuntu it would go to a black screen and that's it. Entered the recovery a few times and attempted repair but to no avail. So I booted into windows. Got Ubuntu 13.04 iso and made a bootable DVD. 


Now here is where I am an idiot. For some reason I thought I should just delete all of the partitions Ubuntu was on so I could start fresh. So I did so and rebooted. Instead of booting into my DVD I got the grub rescue command line. And that's all I can get now. Won't let me go into bios or boot menu, so I have no way to set it to boot from disc drive in order to boot from either my boot-repair disc or Ubuntu DVD. So I have absolutely no idea what to do now. I'm usually pretty good at fixing PC's but this one is a bit above my pay grade. No


Any ideas ?

---

### Post by westie457 on 2013-12-03
Is this on a laptop or a desktop?

Was Windows8 pre-installed?

You will either have to reset the BIOS to factory defaults or reset Windows (yuk).

---

### Post by jdeca57 on 2013-12-03
> **westie457 said:**
> ... or reset Windows (yuk).
Why not? Start from a clean state and forget past errors. Now, personally I'd never upgrade from 12.04 since 14.04 is not far away, but that's another question.

---

### Post by jimmyh1972 on 2013-12-03
Reboot your computer - if its a laptop its got to have a boot menu option (something like f12 in Dell's or ESC button in Asus)
than choose your DVD and upload your new ubuntu.
p.s. - when you reboot your comp take a good look at the bottom of the screen it should show the BIOS option.
best thing TODO is to set boot order from BIOS:
1. DVD
2. flash drive / usb
3.Hard_disk

---

### Post by fantab on 2013-12-03
> **Silicon_Knight said:**
> So basically I am an Idiot and I messed up my install of Ubuntu 12.04 that i had dual booted with Windows 8.1. I tried to update to 13.04 and That's what messed it up at first. It wouldn't let me boot into Ubuntu anymore. **Every time I chose Ubuntu it would go to a black screen and that's it**. Entered the recovery a few times and attempted repair but to no avail. So I booted into windows. Got Ubuntu 13.04 iso and made a bootable DVD. 


Now here is where I am an idiot. For some reason I thought I should just delete all of the partitions Ubuntu was on so I could start fresh. So I did so and rebooted.** Instead of booting into my DVD I got the grub rescue command line**. And that's all I can get now. Won't let me go into bios or boot menu, so I have no way to set it to boot from disc drive in order to boot from either my boot-repair disc or Ubuntu DVD. So I have absolutely no idea what to do now. I'm usually pretty good at fixing PC's but this one is a bit above my pay grade. No


Any ideas ?

More info about your Laptop, especially Graphics card?
Were you using any 'proprietary Graphics driver', installed with "Additional Drivers"?

13.04 will end support in Jan'2014, so no point in installing that, download and burn 13.10.
In your case, re-installing can be a simple and easier solution.
By the way, if you are booting to Grub command line when booting from DVD, it means that Ubuntu.iso was NOT burned properly to the DVD.

You don't have to 'Delete' Ubuntu partitions, just reuse them after reformatting. When installing Ubuntu again, choose "Something Else" option at the 'Installation Type' dialog to manually format the Ubuntu partitions and install Ubuntu on it.

If you are not sure then after booting with 13.10 DVD, "Try Ubuntu Without Installing"... open Terminal and post the output of:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by westie457 on 2013-12-04
@[[COLOR=#000000]jdeca57[/COLOR]]("http://ubuntuforums.org/member.php?u=275746")[COLOR=#000000] 
The yuk part of the statement you quoted is aimed at the Windows update process **not **at Windows.

Until the OP can get into the bios to repair/reset Windows or boot from DVD/USB they have an expensive paperwieght.[/COLOR]

---

