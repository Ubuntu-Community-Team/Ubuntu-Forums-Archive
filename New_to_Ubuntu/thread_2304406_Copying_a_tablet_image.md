---
title: "Copying a tablet image"
date: 2015-11-26
forum: New to Ubuntu
---

### Post by Stuart_McArthur on 2015-11-26
Hello all,

This could well be in the wrong forum, my apologies if it is.

We have a Dell Venue 11 Tablet running Windows 8.1 and are in the midst of purchasing 50 or so more. We want to use the existing unit we have as a template for the other 50, to use it to create an image that we can copy over. After a week or so of fruitless searching for a method of doing this within Windows (or indeed getting the tablet to boot into a Linux OS, the keyboard and mouse don't work) it was suggested that we use the dd command and copy the image from the 'template' machine to a new one using a third machine running Linux. Does anyone know how we would go about this?

Thanks,

Stuart.

---

### Post by yancek on 2015-11-26
I would think your best source of information would be either Dell or microsoft.  If you are purchasing that number of tablets I would think they would be able to explain how to do it since you will need to get a license from microsoft for each in addition to purchasing the hardware.

---

### Post by Stuart_McArthur on 2015-11-27
Hi Yancek,

Thanks for replying, you would think that would be the case, but I spoke to Dell and they said they'd never imaged a tablet with a bespoke image. Each of the tablets will come with Windows 8.1, licenses won't be an issue, if it comes to it we'll have to fall back on our open licenses.

Thanks,

Stuart.

---

### Post by yancek on 2015-11-27
I'm not really sure what you want to do.  You are buying these tablets with windows 8.1 already on them.  Do you want to modify the installations, add software and then clone them overwriting the original install?  You can do this with the dd command.  See the link below which has an explanation but understand that if you are not familiar with it and make an error you can pretty much destroy the installation.  Getting the wrong device to write to for instance.  Another option is to use the clonezilla software to make a clone of the original system and then copy it to another drive.  If all the machines will have identical hardware, it should work but I'm not really sure that is what you want?

[https://wiki.archlinux.org/index.php/Disk_cloning](https://wiki.archlinux.org/index.php/Disk_cloning)

---

