---
title: "[SOLVED] Multibooting"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by talsemgeest on 2008-07-17
I have been multibooting, but everything seems to be going wrong.

I have two SATA hardrives in a fake raid 0 config with vista on it, and one IDE hardrive with Ubuntu 8.04 on it.

Right now I have grub installed on the IDE drive, and vista bootloader on the RAID, but would like both entries on the same bootloader.

I installed vista first, and then Ubuntu, but Vista was not added to my menu.lst automatically during installation. So I tried adding it manually, and that gave me errors every time I tried to boot into windows.

Next I tried adding Ubuntu to the Vista bootloader using easybcd. I added an entry for linux, grub, and pointed it to the partition that Ubuntu is installed onto. But when I try to boot onto Ubuntu it gives me an error about no system disks.

If anyone wants any more info, just ask.

Thanks in advance for your help.

---

### Post by logos34 on 2008-07-17
> **talsemgeest said:**
> 
I installed vista first, and then Ubuntu, but Vista was not added to my menu.lst automatically during installation. So I tried adding it manually, and that gave me errors every time I tried to boot into windows.

I have no experience with raid yet, but did you use mapping [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")?

>  Next I tried adding Ubuntu to the Vista bootloader using easybcd. I added an entry for linux, grub, and pointed it to the partition that Ubuntu is installed onto. But when I try to boot onto Ubuntu it gives me an error about no system disks..

Did you write the Grub IPL code to the ubuntu root partition?

---

### Post by talsemgeest on 2008-07-17
> **logos34 said:**
> I have no experience with raid yet, but did you use mapping [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")?
Mapping?
> **logos34 said:**
> Did you write the Grub IPL code to the ubuntu root partition? I tried my best. I wrote it to (hd0,0) instead of the usual (hd0), but that made no difference so I went back to (hd0).

---

### Post by logos34 on 2008-07-17
> **talsemgeest said:**
> Mapping?

it's explained in the link (..."like this")

Did you follow [this EasyBCD guide]("http://neosmart.net/wiki/display/EBCD/Linux")? (-->method 2: Neogrub.  Did you try that too?)

---

### Post by talsemgeest on 2008-07-17
Yeah, I followed that guide, and tried neogrub, but that gives me even more errors.

---

### Post by logos34 on 2008-07-17
You might want to post your disk layout

sudo fdisk -l

So, as far as menu.lst is concerned, you've tried an entry something like this:

>  title           Windows Vista
rootnoverify    (hd1,0)
makeactive
map             (hd0) (hd1)
 map             (hd1) (hd0)
chainloader     +1?  Or maybe (hd2,0)?

---

### Post by talsemgeest on 2008-07-17
It looks like that menu.lst entry did it. Thank you very much for your help.

Just one little quirk now. I would prefer to be using the vista bootloader because of a little program I just found. It sits in the taskbar, and when right clicked it gives a list of os's in the bootloader, and when clicked it will boot into that os.

So does anyone have any ideas or links on how to get Ubuntu into the vista bootloader?

---

### Post by logos34 on 2008-07-17
no prob, my pleasure.  Glad it's working now.

try one of these links to manually add ubuntu to vista bootloader since Easybcd doesn't seem to want to cooperate:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)
(-> steps 1,2 and 4)
[http://ubuntuforums.org/archive/index.php/t-569506.html](http://ubuntuforums.org/archive/index.php/t-569506.html)

Or maybe someone else can suggest a better howto.

good luck!

---

