---
title: "Netbook Remix for Netbook only?"
date: 2009-08-09
forum: Philippine Team
---

### Post by killer_d76 on 2009-08-09
i would like to try NBR i already have the Ubuntu NBR image and install it on my 2GB Flash drive.. but everytime i try to boot from the flash/USB/Thumbdrive i get "boot error", by the way i was testing it on my 14.5" Neo Laptop! (Not exactly the Netbook you have in mind) .. ;) so does this mean that the NBR is only bootable on Netbooks like the Asus EEE Pc, HP Mini and others?

---

### Post by rjmdomingo2003 on 2009-08-09
Try mo 'to sir baka makatulong: [http://ubuntuforums.org/showthread.php?t=1144684&highlight=boot+ubuntu+netbook+remix+error](http://ubuntuforums.org/showthread.php?t=1144684&highlight=boot+ubuntu+netbook+remix+error)

---

### Post by wersdaluv on 2009-08-09
The problem is with the USB. Use the "USB Startup Disk Creator" app that comes with Ubuntu to properly create a live USB.

Laptops, in most cases, are more powerful than netbooks. Laptops should run everything that netbooks can, and even more, depending on the power of the hardware. The titles like "netbook" and "laptop" are based on form factor and hardware capability. Netbooks are more compact and are designed just for broswing the 'net (as the name implies) while Laptops are... of course, you know what they are. hehe. 

In other words, it doesn't matter if you're running it on a "netbook" or a "laptop". It (live USB) should work on both if properly configured.

---

### Post by frustphil on 2009-08-09
Are you test driving the new UNR? BTW, it's not NBR but UNR. :)

---

### Post by zeroseven0183 on 2009-08-10
> **wersdaluv said:**
> The problem is with the USB. Use the "USB Startup Disk Creator" app that comes with Ubuntu to properly create a live USB.

@wersdaluv
I haven't tried USB Startup Disk Creator on a .IMG file, in this case UNR. I'm not sure if the file extension is supported because as far as I know, Ubuntu Netbook Remix is in .IMG, not .ISO. There are two applications, however, mentioned in the link below to create a bootable flash drive. 

[quote=killer_d76]i would like to try NBR i already have the Ubuntu NBR image and install it on my 2GB Flash drive.[/quote]

@killer_d76

Have you used Ubuntu Imagewriter to create a bootable drive [https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)?

I was able to install UNR on an Asus Eee PC last month smoothly.

---

### Post by killer_d76 on 2009-08-10
yes i have used the usb-imagewriter applications on my Jaunty and i install it using sudo apt-get install usb-imagewriter.

as i understand it, the only time that i need to install phyton -glade2 (sudo apt-get install python-glade2) if the usb-imagewriter fails to launch.

by the way the UNR (thanks frustphil :D) only comes in .IMG and not .ISO on the ubuntu site.

---

### Post by zeroseven0183 on 2009-08-10
So now, you're left with one option (at least for now) -- the Disk Image Writer for Windows: [https://launchpad.net/win32-image-writer/+download](https://launchpad.net/win32-image-writer/+download)

---

### Post by killer_d76 on 2009-08-10
oh i haven't tried the OSX way!.. i guess installing windows on Virtualbox would be my last option though. :(

---

### Post by killer_d76 on 2009-08-10
guess what?.. i was able to install it now on my laptop!.. it just so happened that the .IMG file that i have downloaded from one of the ubuntu mirror is corrupted :confused: i tried downloading it again from another mirror and use the usb-imagewriter that i have installed on my jaunty and VOILA!.. UNR boots for the first time!.. very nice interface.. medyo mabagal lang for my taste!.. parang may slight delay ba.. but hey it's working now.. pano kaya to mai-install sa Virtualbox?

---

### Post by wersdaluv on 2009-08-11
On virtualbox, just mount the image. The virtual machine will detect it as an optical drive.

---

### Post by zeroseven0183 on 2009-08-11
> **killer_d76 said:**
> guess what?.. i was able to install it now on my laptop!.. it just so happened that the .IMG file that i have downloaded from one of the ubuntu mirror is corrupted :confused: i tried downloading it again from another mirror and use the usb-imagewriter that i have installed on my jaunty and VOILA!.. UNR boots for the first time!.. very nice interface.. medyo mabagal lang for my taste!.. parang may slight delay ba.. but hey it's working now.. pano kaya to mai-install sa Virtualbox?

Congratulations! Magpa-kape ka naman.

---

### Post by Nhatz on 2009-08-11
Nainstall ko na UNR sa Desktop ko. hehehehe.. kakatuwa lang sya.

ASTIG!!! :guitar:

---

### Post by killer_d76 on 2009-08-11
@zeroseven0183  - pa-kape?!.. oo ba basta wag lang sa Starbucks ha ;) hehehe.. dito na lang tayo sa bahay para Coffee with Rum bro masarap yun! :D

@Nhatz - astig di ba bro?!.. and you have an option to go back to regular desktop if sawa ka na sa UNR!.. kaso parang may delay lang ng konti i'm not quite sure if it is my laptops video card or something..

---

### Post by Nhatz on 2009-08-11
Wierd lang yung panels nya minsan pag nag switch ka sa default gnome desktop. pero ok na rin. ang inaabangan ko yung gnome slides.. hehehe

ASTIG!!! :guitar:

---

### Post by killer_d76 on 2009-08-12
now if anyone knows how to convert .img to .iso patulong naman.. gusto kasing i-install to on VMWare sa OSX hehehe.. i don't know if it is possible to install .img on VMWare Fusion eh tried it but it did not install :(

found one on google ([http://www.yasasoft.com/press_release/convert_img_to_iso.htm](http://www.yasasoft.com/press_release/convert_img_to_iso.htm)) but its on windows version :(

---

### Post by killer_d76 on 2009-08-12
ok no worries.. i found one! :D

---

### Post by Edgar Ilaga on 2009-08-12
I'll see if installing the ubuntu-netbook-remix meta package works. Be right back after a few minutes.

Yep. Works like a charm. See attached.

Edit: Ugh. Screencapped the application taking the screencap.

---

### Post by frustphil on 2009-08-12
Just in case no one knows.. [Karmic UNR]("http://ubuntuforums.org/showthread.php?t=1235268") has a new slick interface and it's out in the wild. I would install it if I were you guys so I can help out testing... :)

---

### Post by killer_d76 on 2009-08-13
@Edgar Ilaga.. could you tell me how you were able to install UNR on your virtualbox?.. i can't seem to make it work! :confused:

@frustphil - count me in bro! ;)

got this pic from a different thread and its Karmi UNR!.. very nice! 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124086&d=1249783920[/IMG]

---

