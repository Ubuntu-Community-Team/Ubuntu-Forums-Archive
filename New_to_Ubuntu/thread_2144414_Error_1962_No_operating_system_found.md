---
title: "Error 1962: No operating system found"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by adyb123 on 2013-05-12
Hi

I am new to ubuntu.  I installed ubuntu 11.10 and it works great but no updates as it's old hat now.  Upgraded to 12.04 64bit now can't boot.  All I get is error 1962: no operating system found.

I have trawled the forums and wiki answers and tried what they advise but it still does not work.

I ran boot-repair 64 and the url is [http://paste.ubuntu.com/5657252/](http://paste.ubuntu.com/5657252/).

Please help.  I don't want to use windows anymore but if this problem persists i can't see an alternative.

Lenova M91p with uefi.

many thanks

---

### Post by fantab on 2013-05-12
How did you upgrade? If you did an upgrade from 'Update-Manager' then it won't work. I don't think 11.10 supported UEFI boot.

EDIT: Did you install 32bit Ubuntu? Did you install it 'replacing Windows'? And your bootinfo script says you are using version 13.04 and not 12.04.

You are not using UEFI. I think the best solution will be to BACKUP all your Important DATA and reinstall. If you want to dual-boot Ubutnu and Windows (which I recommend) you have Install Windows first.

---

### Post by blackbird34 on 2013-05-12
Do you have important stuff on there? You could just try a new clean install of a fresh copy of Ubuntu from here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
The latest version of Ubuntu 12.04 LTS (Ubuntu 12.04.2) which is served up on that page supports UEFI completely (no need to mess about turning it off etc), whereas previous versions might have had odd problems. Be careful to choose the 64-bit version.

Also, have you any idea why your boot info script says you have Ubuntu *13.04* ?

EDIT: fantab beat me to it. But same advice. When you burn your new copy of Ubuntu to a CD/ USB stick you get the opportunity to try it out, so make sure everything works *before installing*.

Good luck :)

---

### Post by adyb123 on 2013-05-12
Ok. I have a blank drive no windows installed.

I installed 11.10 32bit and it works no problems and as far as I am aware 11.10 does support uefi.

Installed 12.04 64bit.  Fresh install over-writing 11.10. Error 1962

Installed 13.04 64bit.  Fresh install over-writing 12.04. Error 1962 - tried this as it was the latest upgrade and I thought the problems may have been ironed out.

I have tried the boot-repair disk (64 bit) and posted the url above.  I have tried the fixes by using the terminal as advised in boot-repair and that did not work.

I looked at several different links on google and finally tried a solution from ubuntu wiki page and it still does not work.

There is no important information on the disk and i have wiped it several times before re-installing the os.  

The BIOS is set to UEFI and quick boot turned off.

help please.

Many thanks

One more thing, it works when booting from cd

---

### Post by fantab on 2013-05-12
Ok..
AFAIK, windows will not boot in UEFI mode unless your Hard Disk uses GPT partition table. And from GPT Disk it will only boot in UEFI mode. Whereas Ubuntu can boot from GPT in both UEFI and NON-UEFI mode. We have to first ascertain whether Windows originally was booting in UEFI mode.

Did you change the partition table on your Hard Disk at any point in time? Was your Windows 32bit or 64bit? 32bit windows, i don't think, will install in UEFI.
Since you have Windows 7, UEFI is not an absolute must. Not at least for another few years. It will be easier to install both OS in Legacy Mode. Just turn off UEFI, or set it use either or auto. But if you insist on UEFI thats another matter.

Download and burn Ubuntu on a 'blank drive' you can find all relevant information on how to do this if you carefully follow the link blackbird gave you. Download 64bit Ubuntu.

Then boot with it and "Try Ubuntu", wait till the desktop loads. Then connect to internet. And check if all your hardware is working. Then Open a Disk management Utility called GPARTED and delete all partitions (I hope you have backed up all your data). 

In Gparted under "DEVICE" you will find "create new partition table". If you want UEFI then go to advanced and choose GPT/GUID. If you want to use legacy then use the default MSDOS table. (It will be simpler if you choose 'msdos', however its up to you).

Get back here and tell us what you got.

---

### Post by PegasusNY on 2013-05-13
Sorry for butting in, but I wanted to give you a FYI:
I too have a Lenovo M91p, that had Win 7 32bit, and tried to install 13.04 64bit.
I too received the "error 1962: no operating system found" error.
Fantab, I followed your instructions and Ubuntu loaded without any further issues.
Thank you for the info and I hope it works for adyb123 too.

---

