---
title: "Unable to create bootable USB &quot;error code 0&quot;"
date: 2015-05-20
forum: New to Ubuntu
---

### Post by 4ntonio.p3r3ira on 2015-05-20
Hi. I'm new to Ubuntu, I'm trying to create a bootable USB but so long it isn't working. Don't really know why. 
The only part of the process that isn't working as it should, for what I'm able to tell, its the following error message. 

[http://s3.postimg.org/dbeqbx77n/Sem_t_tulo.jpg](http://s3.postimg.org/dbeqbx77n/Sem_t_tulo.jpg)



Besides that everything is smooth. I've tried to format the USB device (32gb) at least 8 times. Do the step by step described here: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows). But every time I restart the computer it doesn't recognizes the USB as it should. 1st time doing this so sorry for the ignorance.


Thanks for the help!

---

### Post by nerdtron on 2015-05-20
I would just like to verify since you said you already formatted the USB device, is it NTFS or FAT32?

Bootable USB needs to be FAT32. Just checking....

And also are you sure your downloaded Ubuntu ISO is not corrupted? 
And here's another link which uses unetbootin for windows to create a bootable USB, link with screenshots: [http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)

---

### Post by Vladlenin5000 on 2015-05-20
> **nerdtron said:**
> Bootable USB needs to be FAT32. Just checking....
^^^^
This.

And why are you trying to extract the ISO with 7-Zip? You're certainly NOT following the instructions in the web page you have open behind the 7-Zip windows...

---

### Post by nerdtron on 2015-05-20
> **Vladlenin5000 said:**
> ^^^^
This.

And why are you trying to extract the ISO with 7-Zip? You're certainly NOT following the instructions in the web page you have open behind the 7-Zip windows...

That's the behavior of the Universal USB installer utility from pendrivelinux.com

---

### Post by Vladlenin5000 on 2015-05-20
> **nerdtron said:**
> That's the behavior of the Universal USB installer utility from pendrivelinux.com

Live and learn :lolflag:
Needless to say I never did it in Windows...

Now, if that's the expected behaviour then the download is corrupt -or-, as you mentioned, something to do with the destination drive file system. However, if that's the case the utility is crap.

---

### Post by wildmanne39 on 2015-05-20
Please use url's or thumbnails when posting images, people with slow connections have trouble loading images.
Thanks

---

### Post by sudodus on 2015-05-21
Welcome to the Ubuntu Forums :-)

1. Please check that the downloaded file is correct. Check the **md5sum** versus the entry at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. I suggest that you try another tool to flash the content of the iso file to the USB pendrive. I find the method with [Win32DiskImager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") reliable. You will find more tips at the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by leunam12 on 2015-05-21
It seems from the picture that you are using a 32-bit version ISO, you won't be able to boot from it unless you change your BIOS to legacy mode.

---

### Post by 4ntonio.p3r3ira on 2015-05-22
Thanks for all the help guys. I've been working 12 hour shifts lately so I didn't had time to test anything yet. I formatted the pen to FAT32. SOrry for the image. Maybe I'll have time to test everything tomorrow.

It will be nice to be part of such a wonderful community.

---

### Post by Diandra on 2015-05-23
How about trying another multiboot creator, try YUMI or rufus. Both works for me

---

### Post by Vladlenin5000 on 2015-05-23
> **Diandra said:**
> How about trying another multiboot creator, try YUMI or rufus. Both works for me

I second the Rufus suggestion. It's modern, allows different setups and surely supports correctly newer UEFI systems (not that the other tools don't but Rufus - I thinks - allows more refined settings).

---

### Post by 4ntonio.p3r3ira on 2015-05-24
Thanks for the help guys. Rufus was the one that finally worked. I'm installing Ubuntu atm. Lets see if its works good enough or if I'll need to install LUbuntu.

---

