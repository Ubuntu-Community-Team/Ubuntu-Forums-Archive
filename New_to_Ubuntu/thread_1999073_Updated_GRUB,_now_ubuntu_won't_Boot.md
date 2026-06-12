---
title: "Updated GRUB, now ubuntu won't Boot"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by cbrem on 2012-06-07
I'm using EasyBCD to decide which OS (Windows 7 or Ubuntu 12.04) to boot into. I recently updated GRUB on my Ubuntu partition, and now when I select the GRUB boot option I get GRUB4DOS and a command prompt, and it asks me to load a kernel before I can boot.

Any suggestions?

---

### Post by Cavsfan on 2012-06-07
> **cbrem said:**
> I'm using EasyBCD to decide which OS (Windows 7 or Ubuntu 12.04) to boot into. I recently updated GRUB on my Ubuntu partition, and now when I select the GRUB boot option I get GRUB4DOS and a command prompt, and it asks me to load a kernel before I can boot.

Any suggestions?

If you can get into your Ubuntu recovery, go to root terminal and enter ```
sudo grub-install /dev/sdx
```Where x is the drive Ubuntu is installed on. E.g. sda

---

### Post by cbrem on 2012-06-08
> **Cavsfan said:**
> If you can get into your Ubuntu recovery, go to root terminal and enter ```
sudo grub-install /dev/sdx
```Where x is the drive Ubuntu is installed on. E.g. sda

Okay thanks -- should I have to give /dev/sda#, or is /dev/sda enough?

---

### Post by wilee-nilee on 2012-06-08
Run this command set from a live cd and go to home and copy and paste all the text from the results.txt

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by Cavsfan on 2012-06-08
> **cbrem said:**
> Okay thanks -- should I have to give /dev/sda#, or is /dev/sda enough?

sda should be all you need. I had been installing 12.04 about 4 times before I got it right and each time, I had to 
restart, go into my 10.04 installation and enter 
```
sudo grub-install /dev/sda
```
myself. I tried sda3 once and it did not work.
I wanted the grub to be installed on my main OS which is Lucid.
I am checking Precise out and after 12.04.1 comes out in July I will upgrade to that.
Hope this helps.

---

### Post by cbrem on 2012-06-08
Thanks Cavsfan, that worked! 

I got a warning during the install that FlexNet (apparently associated with Adobe DRM) was installed on the MBR where Grub was supposed to go, but it seems to work fine.

---

### Post by wilee-nilee on 2012-06-08
> **cbrem said:**
> Thanks Cavsfan, that worked! 

I got a warning during the install that FlexNet (apparently associated with Adobe DRM) was installed on the MBR where Grub was supposed to go, but it seems to work fine.

If you have any more problems the boot-repair app has a flexnet tick in the advanced section.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by drs305 on 2012-06-08
> **cbrem said:**
> Thanks Cavsfan, that worked! 

I got a warning during the install that FlexNet (apparently associated with Adobe DRM) was installed on the MBR where Grub was supposed to go, but it seems to work fine.

Flexnet and some other apps presented problems with earlier versions of Grub 2 as they competed for the same disk space. At least with version 1.99 (and maybe later versions of 1.98) the devs provided a workaround for situations where Grub finds information in the area to which it normally writes. I don't know where it places the information in these cases but it is transparent for the user and no action is required.

---

