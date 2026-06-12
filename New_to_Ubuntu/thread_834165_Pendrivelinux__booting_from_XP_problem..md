---
title: "Pendrivelinux  booting from XP problem."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by drifter2502 on 2008-06-19
I followed the tutorial on pendrivelinux 2008 here http://www.pendrivelinux.com/2008/02/13/pendrivelinux-2008-install-from-windows[/url]
and performed the USB boot compatibility test on a 2GB pen driver. The pen driver is capable of booting. However on installation and re booting my XP does not offer a boot choice but loads up directly into Windows. So I am currently using the alternative method of booting the pendrive from within windows without rebooting. This method is tediously slow.  I am not tech minded in some areas and one of them is the Boot Settings Utility which I have only just found via `del´on boot start up. To be honest it frightens me a bit and it took me ages to get out of there. I feel sure that I have to delve in there to configure XP to give me a boot choice but I am worried about exactly what to do from the initial BSU screen. Can someone kindly help me out please. I will need a step by step tutorial on this I think!

---

### Post by alexandremrj on 2008-06-19
The main problem here seems to be that your PC is booting straight to hard disk instead of checking for CD or USB boot.

You have to enter thru boot with the Del key as you said and check an option that says Boot Order or something like that but we can't help you if you can't at least give us the maker of the PC, because there are several kinds of Bios out there.

---

### Post by drifter2502 on 2008-06-19
The Bios is American Megatrends Inc,V 0403,Jan 2006. I think I have seen this boot order page. I will go back in and post what I see, whilst leaving the pendrive in a port I presume
I have tentatively gone back. I found `Boot Settings`. 1st Boot Device (CDRom). 2nd. ..HDD: PM-HDS728...etc.
3rd. ..1st Floppy Drive.
Still in dark at moment.
What I am aiming for is to be given an election choice on boot, either Drive c or usb pendrive. I am sure my box is capable of doing this somehow.

---

