---
title: "/boot/grub is missing a large amount of files?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Kaspersky_ on 2008-08-04
I'm currently using GRUB to boot Ubuntu but Ubuntu fails to boot. When I try reinstalling GRUB using this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) I keep getting an error so I decided to check /boot/grub to see which files are missing. To my dismay only device.map exists.

[img]http://img229.imageshack.us/img229/8553/screenshotbs9.png[/img]

Is this right? If not, how can I fix it?

---

### Post by phidia on 2008-08-04
That howto may or may not work depending on the specifics of your install.

It's a good guide though. When you get to the grub prompt and enter this: > find /boot/grub/stage1 what is the output?

---

### Post by Paqman on 2008-08-04
> **Kaspersky_ said:**
> 
Is this right? If not, how can I fix it?

Nope, that's not right at all. Is this a new install, or has the problem suddenly popped up?

---

### Post by Kaspersky_ on 2008-08-05
I get this when I look for /boot/grub/stage1:

```
(hd0,0)
```

Shouldn't GRUB be installed on one of the partitions? If I'm right (hd0,0) is saying that it's on the drive :/

@Paqman: This problem has affected me since the the first time I installed Ubuntu.

---

### Post by cariboo on 2008-08-05
(hd0,0) indicates that grub is installed on the first partition of the first hard drive.

Jim

---

### Post by Kaspersky_ on 2008-08-05
How would I locate the GRUB files using a live cd? For some reason when I use sudo grub-install /dev/sda it gives me this:

```
Could not find device for /boot: Not found or not a block device.
```

And when I try using this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to install GRUB from the live cd I get this:

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
```

And when I try installing to my root partition I get this:

```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... failed

Error 22: No such partition
```

---

### Post by caljohnsmith on 2008-08-05
When you took that screen shot, Kaspersky_, were you using the Live CD? Because if you were, then that screen shot just shows the contents of the /boot/grub on your Live CD, not your HDD. :) That is probably what is going on here, because when you searched for the Grub stage1 file within the Grub CLI, it said it existed in (hd0,0). That means if you mount your (hd0,0) partition while in the Live CD, probably all your grub files are there (or at least the stage1 file is for sure). 

When you say "it fails to boot", what exactly do you mean? What do you get when you start up your computer? Do you get the Grub menu at all, do you get a certain Grub error, etc?

---

### Post by Elfy on 2008-08-05
When you installed did you go into the advanced option towards the end and tell it not to install the bootloader - my intrepid boot is exactly the same after I did that (deliberately I might add)

---

