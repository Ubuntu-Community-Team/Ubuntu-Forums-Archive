---
title: "why cant i put ubuntu 11.04 on mp3 player ?"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by tommyleeds on 2011-09-17
hi dudes
ubuntu wont let me make a startup disk on my 2 gb mp3 player
[IMG]http://ecx.images-amazon.com/images/I/11Q2%2B3xr1bL._SL160_SL90_.jpg[/IMG]i'm using the startup disk creator programme in ubuntu 11.04.......i can see my mp3 player in 'disk to use' but i cant select it. i have tried formatting the player but it still dont work.
can anybody help me ?

---

### Post by psrdotcom on 2011-09-17
Does it detecting the MP3 Player as storage device?

Please see in the device list.

install in the proper drive?

---

### Post by tommyleeds on 2011-09-17
no i think it says its a music player......but i can put mp3's on it like a usb stick
where is the device list ?
cheers

---

### Post by anewguy on 2011-09-17
I really don't see how this is going to work - ubuntu is distributed by default in x86 or MAC binaries.  I doubt your mp3 player has any kind of cpu that is supported.

Dave ;)

---

### Post by cap10Ibraim on 2011-09-17
> **anewguy said:**
> I really don't see how this is going to work - ubuntu is distributed by default in x86 or MAC binaries.  I doubt your mp3 player has any kind of cpu that is supported.

Dave ;)

I think he just want to use it as a live usb :)

---

### Post by kerry_s on 2011-09-17
If it did that your mp3 wont work no more cause it would wipe it, part of the memory is the mp3 system.

---

### Post by P05TMAN on 2011-09-17
> **tommyleeds said:**
> hi dudes
ubuntu wont let me make a startup disk on my 2 gb mp3 player
[IMG]http://ecx.images-amazon.com/images/I/11Q2%2B3xr1bL._SL160_SL90_.jpg[/IMG]i'm using the startup disk creator programme in ubuntu 11.04.......i can see my mp3 player in 'disk to use' but i cant select it. i have tried formatting the player but it still dont work.
can anybody help me ?

Forgive me for how this may seem, but couldn't you just buy a flash drive for a live usb? Flash drives are ridiculously cheap these days & you can get 4gb (MORE than enough for what you're wanting) for under $10. OR you can buy a flash with live usb image of Ubuntu installed from the Canonical store, but it's cheaper to buy your own flash.

---

### Post by anewguy on 2011-09-17
> **P05TMAN said:**
> Forgive me for how this may seem, but couldn't you just buy a flash drive for a live usb? Flash drives are ridiculously cheap these days & you can get 4gb (MORE than enough for what you're wanting) for under $10. OR you can buy a flash with live usb image of Ubuntu installed from the Canonical store, but it's cheaper to buy your own flash.

You're right!  I didn't realize they just wanted this as a boot device for ubuntu.  Indeed, flash drives are really inexpensive now - if nothing else check microcenter.com or tigerdirect.com.  Sometimes you can find them cheap in some unexpected places as well - drug stores come to mind.

Dave ;)

---

### Post by P05TMAN on 2011-09-17
here's a Kingston 8GB for under $10 & free shipping! (free shipping may only be for US though). Still....VERY very good price. [http://www.newegg.com/Product/Product.aspx?Item=N82E16820139246](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139246)

---

### Post by pqwoerituytrueiwoq on 2011-09-17
> **P05TMAN said:**
> here's a Kingston 8GB for under $10 & free shipping! (free shipping may only be for US though). Still....VERY very good price. [http://www.newegg.com/Product/Product.aspx?Item=N82E16820139246](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139246)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820139251](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139251) or [http://www.newegg.com/Product/Product.aspx?Item=N82E16820139292](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139292)
how about one of those for 1$ less

---

### Post by 3rdalbum on 2011-09-17
> **P05TMAN said:**
> here's a Kingston 8GB for under $10 & free shipping! (free shipping may only be for US though). Still....VERY very good price. [http://www.newegg.com/Product/Product.aspx?Item=N82E16820139246](http://www.newegg.com/Product/Product.aspx?Item=N82E16820139246)

It's not such a good deal when you consider that Kingston memory tends to go bad very quickly. Anyway, that's off-topic.

Can anyone help the OP at all? The only two things I can think of are "temporarily run a different desktop environment such as XFCE that doesn't treat the MP3 player as an MTP device" or "Use Unetbootin to make the startup disk" - which doesn't support persistence.

---

### Post by P05TMAN on 2011-09-17
> **3rdalbum said:**
> It's not such a good deal when you consider that Kingston memory tends to go bad very quickly. Anyway, that's off-topic.

Can anyone help the OP at all? The only two things I can think of are "temporarily run a different desktop environment such as XFCE that doesn't treat the MP3 player as an MTP device" or "Use Unetbootin to make the startup disk" - which doesn't support persistence.

Never once had an issue with Kingston memory personally, hence my recommendation... I believe the best thing the OP can do is use an actual Flash memory device, not an MP3 player. Just my opinion.

---

### Post by tommyleeds on 2011-09-17
cheers dudes but i want to put it on my mp3 player
i know you can do it coz this dude on youtubes done it......[ http://www.youtube.com/watch?v=yJ2j4jf9ZUE]("http://www.youtube.com/watch?v=yJ2j4jf9ZUE")..........only its puppy not ubuntu

can anybody help ?

---

### Post by anewguy on 2011-09-17
I would *think* you would need to use unetbootin (install it from synaptic package manager) to create the USB "disk".  As already mentioned by others, I *think* you would also need to be aware of the following:

- the flash disk portion of your MP3 player needs to be visible as a disk device
- you'll probably lose the ability to use your MP3 player for other things

I was going to try to do some testing of this on an old MP3 player, but the battery appears to be dead and it's not worth replacing in that old one.

Dave ;)


EDIT:  I think there's a way to make it persistent as well - I seem to remember a post on that, done after the "disk" is created.  I'll have to do some hunting and see if I can find that again.

EDIT-EDIT:  Found it:  [Live Usb Pendrive Persistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by cap10Ibraim on 2011-09-17
is the formatting completing successfully ?

---

### Post by SirDrexl on 2011-09-17
Is this for Rockbox?

---

### Post by tommyleeds on 2011-09-17
dudes......i'm using startup disk creator in ubuntu 11.04, it lets me make a booting usb stick with ubuntu, it works with my 1 gb usb stick but not my 2 gb mp3 player, when i put it into my pc i can see it but the startup disk creator wont let me select it :(

@ cap10Ibraim.....formatting the player is successfull

---

### Post by holycow131415 on 2011-09-17
Is the mp3 player itself set on the storage setting? I put fedora on my old mp3 player 3 years ago for school because the audio jack on it didnt work anymore but the storage did.

---

### Post by tommyleeds on 2011-09-18
theres no storage setting......my mp3 player works like a usb stick.....i use it to carry my pics and movies like any usb stick
it must be possible coz this dude has done it with puppy [http://www.youtube.com/watch?v=yJ2j4jf9ZUE](http://www.youtube.com/watch?v=yJ2j4jf9ZUE)

---

### Post by SirDrexl on 2011-09-18
What is the brand and model of the player?

---

### Post by tommyleeds on 2011-09-18
theres no name.......it looks like this
[IMG]http://ecx.images-amazon.com/images/I/11Q2%2B3xr1bL._SL160_SL90_.jpg[/IMG]

---

### Post by Lisiano on 2011-09-18
Try using [UNetbootin]("http://unetbootin.sourceforge.net/"). Either download from [SourceForge]("http://sourceforge.net/projects/unetbootin/files/UNetbootin/555/unetbootin-linux-555/download") or use this command ```
sudo apt-get install unetbootin
```

---

### Post by anewguy on 2011-09-18
+1 - see my previous post in this thread (#14?).  I mention using unetbootin and some things you would need to be aware of when doing so.

Dave ;)

---

### Post by Lisiano on 2011-09-19
Well, also should point out that latest UNetbootin has persistence.

---

### Post by anewguy on 2011-09-19
Hummmmm......guess the Ubuntu wiki page for that hasn't been updated.

---

### Post by 3rdalbum on 2011-09-19
> **Lisiano said:**
> Well, also should point out that latest UNetbootin has persistence.

Thanks for updating my knowledge. In that case I'd highly recommend Unetbootin.

---

### Post by tommyleeds on 2011-09-28
cheers dudes
i tried unetbootin but it did'nt work :( got a error saying sdc1 not mounted....its like the error i got in startup disk creator
what is sdc1 ?

---

### Post by tommyleeds on 2011-09-29
unetbootin is still not working
it says sdc1 is not mounted.....i dont know what sdc1 is
can any body help me ?
cheers

---

### Post by SirDrexl on 2011-09-29
Sdc1 is the first primary partition of the third hard drive detected at bootup.  The S stood for SCSI but typically today means SATA, and it covers USB flash drives which are treated as hard drives by many systems.  The first two drives are referred to as sda and sdb, and the numbers after each refer to their partitions.

Did you go into Disk Utility and see if the drive is mounted?  You might have to format it first and then mount it.

---

### Post by tommyleeds on 2011-09-30
cheers SirDrexl
theres sdc but no sdc1
sdc must be mounted coz i can open it and use it like a usb stick
what is sdc ?

---

### Post by mikechant on 2011-09-30
If sdc is showing up in this way it probably means the USB stick is not partitioned, so the whole device is mapped as sdc instead of being split into sdc1/sdc2 etc.

Does unetbootin allow you select sdc (instead of sdc1) as a device? I've done this sort of install successfully before.

---

