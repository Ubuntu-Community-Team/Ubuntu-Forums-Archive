---
title: "HOWTO:Flash Your Bios Using Only A CD"
date: 2006-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by John.Michael.Kane on 2006-06-06
**Note: please use the guide posted  here** [**[SIZE="3"][COLOR="DarkOrange"]HOWTO: Flash BIOS, The Ubuntu Way[/COLOR][/SIZE]**]("http://ubuntuforums.org/showthread.php?t=318789&highlight=Flash+Your+Bios") **as the links in this guide no longer work.**

I found a little document wich tells a way to flash your motherboard bios in a floppiless way. 
                                                                                **[COLOR="Red"]Please be careful when flashing any bios because you can kill your mainboard[/COLOR]**

[COLOR="RoyalBlue"]**Step one**[/COLOR]
First thing you need is a dos/windows bootdisk image. You can get one [here]("http://colt.projectgamma.com/bios/win98-boot.img")

[COLOR="RoyalBlue"]**Step two**[/COLOR]
Now you need to mount the image you will need to be root ie: sudo
```
mkdir tmp
```
```
mount -o loop -t vfat win98-boot.img tmp
```

[COLOR="RoyalBlue"]**Step three**[/COLOR]
Now you will need to get the latest bios image update from your mainboard manufacturer's site,and also get the latest awdflash available there.
Next copy the files into the dir where you mounted the bootdisk image. 
```
cp AWDFASH.EXE biosupdate.file tmp/
```
Unmount dir after files are copied
```
umount tmp 
```
You will then have a bootdisk image with all the necessary files.

[COLOR="RoyalBlue"]**Step four**[/COLOR]
let's make an iso image from the bootdisk image and burn it to cd.

```
mkisofs -o image.iso -b win98-boot.img win98-boot.img
```
Now you have an .iso ready to burn with your favorite burning application. (use a cd-rw no need to waste a cd-r with such a small file). 

[COLOR="RoyalBlue"]**Step five**[/COLOR]
Now you just need to make sure that your cd drive is the first in the boot sequence. Go into your bios setup and make sure it's the first boot drive.
insert the cd in your drive, reboot and you'll be dropped into an old dos prompt like this one.
```
A:/>
```

[COLOR="RoyalBlue"]**Step six **[/COLOR][COLOR="Red"](OPTIONAL)[/COLOR]
This step is for award bios owners.
After you're in the dos prompt, you just need to run awdflash.exe, and follow the on-screen instructions. You can't save your old bios image though it's a small price for floppiless bios installs.


[B]This howto: was made using this document by [Davor Ocelic]("http://colt.projectgamma.com/bios/flashing.html") thanks goes to him for it.

[/B]Hope this helps.

---

### Post by telmo on 2006-06-14
Excuse me... i'm wondering if there aren't any replies to this post because they all burnt the motherboard... :rolleyes:

---

### Post by ÄlveKatt on 2006-08-19
Thank you for the Howto, I might use it. I am sitting with an Asus A6Jm laptop. 

I think you should add that you are supposed to replace AWDFASH.EXE with the flash program that the manufacturer of your computer tells you to use with your specific model. 

Did it work for you?
Edit: It worked for me! I flashed successfully and Ubuntu started up again just fine. Yay me!

---

### Post by sagyvolkov on 2007-06-22
anyone knows where i can download the win98 image? the colt.projectgamma.com site is down/gone.
Any help will be appriciated.

Thanks!!

---

### Post by VMC on 2008-05-25
> **sagyvolkov said:**
> anyone knows where i can download the win98 image? the colt.projectgamma.com site is down/gone.
Any help will be appriciated.

Thanks!!

As on May 25th, 2008 you can "Save Link as..." from here:
[http://www.voltar.org/images/win98-boot.img.gz](http://www.voltar.org/images/win98-boot.img.gz)

---

### Post by Silvr2008 on 2009-05-07
How do you resize a floppy image so that you can fit more on it? My .bin and flashing .exe total 1.1MB and won't fit in the image that I have.

---

### Post by deep_ on 2009-11-16
Thank you very much for this guide.

---

