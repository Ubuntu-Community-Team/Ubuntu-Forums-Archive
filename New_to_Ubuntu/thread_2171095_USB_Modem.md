---
title: "USB Modem"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by jipbuntu on 2013-08-29
Hi 
I have a USB Modem in India
My modem is not recognized by Ubuntu 13.04 (Ubuntu Studio) and I have stried several guides online including 
[http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html](http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html)

My device appears in the lsusb output but when I use the command
$ cat /etc/usb_modeswitch.d/**[vendor code]**\:**[product code]** | grep MessageContent

I get a reply that there is no such file or directory. I opened my usb_modeswitch.d directory and it is empty.

My device works fine in windows but not in linux ( ive tried several distros)

Thanks in advance

---

### Post by eternal243 on 2013-08-29
> **jipbuntu said:**
> Hi 
I have a USB Modem in India
My modem is not recognized by Ubuntu 13.04 (Ubuntu Studio) and I have stried several guides online including 
[http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html](http://www.greplinux.net/2012/07/everything-you-need-to-know-about.html)

My device appears in the lsusb output but when I use the command
$ cat /etc/usb_modeswitch.d/**[vendor code]**\:**[product code]** | grep MessageContent

I get a reply that there is no such file or directory. I opened my usb_modeswitch.d directory and it is empty.

My device works fine in windows but not in linux ( ive tried several distros)

Thanks in advance

It is probably fine in windows because it was designed to be used in Windows. Please post the output of **"lsusb"** so that we can see what that gives. I'm guessing you are missing drivers for it. You could check on the manufacturers website to see if they have any linux drivers for your device. Otherwise you might need to find 3rd party drivers somewhere, which might or might not exist.

I have never used an USB modem in linux so I can't really help much, but I'm sure there are plenty of other people that can give better advice! :)

---

### Post by Barkester on 2013-08-29
I dealt with the same here in Cambo. Trick is to get the right hardware from the start. Never get the latest thing. Takes a while for people to get around to free work making drivers and if the company is small or the product rare noone gets around to it.

   If you buy new, look at the package. Most list the OSs its made for.

   If you hit a second-hand shop. Make sure you can trade for another if it don't work. 3rd world pawnshops usually have a half dozen and one'll work plug and play.

   The above has made my Linux life easier. Same holds true for every widget they got. Get the right hardware first. All available everywhere.

   Best 'O luck.

---

