---
title: "[SOLVED] Does the tool in Ibex for making a bootable USB stick work?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by crjackson on 2008-11-12
I just used the new tool that installs Ubuntu on a USB stick for booting. I tried it on my labtop. 1st boot device (in BIOS)is set to boot removable storage device.

My system boots to GRUB on the HD instead, and the USB stick doesn't seem to be bootable.

Laptop is an emachines M6809, AMD64 2GHZ, 1.25MB.

I'm wondering if it's the laptop having an issue, or the stick not being bootable.

If you have tested it, and it works, can you tell me if it looks like the LiveCD with install options. That's what I'm looking for so I can use it to install on a system that has no CD/DVD drive.

Thanks

---

### Post by jualin on 2008-11-12
Check the Bios options again, because even if the USB Flash drive is having problems, it should say report an Error.

---

### Post by bumanie on 2008-11-12
I have not used the 8.10 tool yet, but from past experience with bootable usb sticks, I found it would boot some computers (ie ones at work) and not others (ie my home computer). Try a couple of different computers.

---

### Post by crjackson on 2008-11-12
> **jualin said:**
> Check the Bios options again, because even if the USB Flash drive is having problems, it should say report an Error.

The BIOS options on this lappy leaves a lot to be desired. It seems it's a option that is always on, only the boot order can be changed. Also there are NO settings in this BIOS specifically mentioning USB. It only mentions removable storage. I can only hope that includes USB.

---

### Post by Anzan on 2008-11-12
USB-creator works great. The USB key I created saves changes and has alrready been used to install on four Eees.

---

### Post by C.S.Cameron on 2008-11-12
Can you set your flash drive as the first hard drive in BIOS?
Some BIOS sees a flash drive as just another hard drive.
Make sure that if your flash drive is over 2 GB that it is formatted FAT32.

---

### Post by crjackson on 2008-11-12
> **Anzan said:**
> USB-creator works great. The USB key I created saves changes and has alrready been used to install on four Eees.

Sweet - That's exactly what I wanted to know. If you make changes on the stick (i.e. restricted-extras etc...) does it install those on any target computers?

---

### Post by crjackson on 2008-11-12
> **C.S.Cameron said:**
> Can you set your flash drive as the first hard drive in BIOS?
Some BIOS sees a flash drive as just another hard drive.
Make sure that if your flash drive is over 2 GB that it is formatted FAT32.

Removable storage is already the first boot device. It's 1GB and formated FAT32.

---

### Post by crjackson on 2008-11-12
Okay, so the bad news is I can't get the stick to boot after trying on 2 different laptops. The only error reported on one of the laptops is that the pin drive isn't bootable.

I reformated the USB drive again, and ran the tool again. Same result. Not bootable...

---

### Post by Cushie on 2008-11-18
Yes it worked fine for me BUT,
[COLOR="Red"]**it does not format the drive**[/COLOR], so first format vFat or fat16****, make '**active**' and '**bootable**' before you load the OS.

My friend is also struggling to get those correct as the 'make USB' option does not produce all of the above.
  
I have read that the USB boots from the 'first slot',  mine works fine from the front facing usb slots but I have not tried others.

I had previously used 'Pendrivelinux' guides to format the USB stick so Intrepid had no problem putting on the new OS and leave existing files intact.

Remember to choose 'Persistant' so after you reboot onto the USB your settings, keyboard, wifi, wallpaper, themes and additional downloads will be saved. 
 
Note after installation to usb I removed what I took to be irrelevant language files and other unwanted files (wubi) as 4 GB did not leave much room for use.  Be careful with updates as there are too many to load all in one go and I have hesitated to update the kernel which will also require additional space. I would be interested the learn if you could make a USB stick minimum installation from the updated system you are currently running, one that included all the updates.

I was very pleased that the same usb booted up fine on two different computers with totally different hardware and one a laptop.

---

### Post by Sirkey on 2008-11-20
> **Cushie said:**
> Yes it worked fine for me BUT,
[COLOR=Red]**it does not format the drive**[/COLOR], so first format vFat or fat16, make '**active**' and '**bootable**' before you load the OS...


I booted my Dell Inspiron 1501 from the LiveCD, and did the Bootable USB thing from there. Initially I had an error, so then reduced the persistent file space, and it seemed to work. I didn't try it that night.

Today, I plug the 2GB USB stick into my EEE 4GB, and try to boot from it. I am then told `Missing operating system` followed by a blinking cursor more or less instantly. That's it.

Maybe I'll have to try it first on another computer (like my Dell 1501), then see if it's formatted correctly, and somehow do that `active` and `bootable` thing you talked about...(How do you do that? Do I do it to the USB when on the Dell (Windows) machine, or to the USB in the EEE's boot menu?)

Cheers again guys! (Sorry if this has been answered somewhere else.)

EDIT: It doesn't work on any computer, and I've been told to reformat it...so I'll do that, and try booting it again...unless anyone has anything else to say!

~ Sirk

---

### Post by Flynn555 on 2008-11-20
mine worked...but it took **forever** to boot... like 1min+

---

### Post by crjackson on 2008-11-21
I still haven't gotten it to work here. I'm going to give it one more try tomorrow and give it up if I don't have some luck after that. I would love to make this happen.

---

### Post by Sirkey on 2008-11-21
> **Cushie said:**
> 
...[COLOR=Red]**it does not format the drive**[/COLOR], so first format vFat or fat16, make '**active**' and '**bootable**' before you load the OS.

My friend is also struggling to get those correct as the 'make USB' option does not produce all of the above....


I believe the `bootable` or `active` thing is my problem. Could you share how the USB drive is made `bootable`, `active` or vFat/Fat16? I've had a bit of a look around the interwho, but no real luck...
Also, will Fat or Fat or Fat32 do the trick?

~ Sirk

---

### Post by crjackson on 2008-11-21
> **Sirkey said:**
> I believe the `bootable` or `active` thing is my problem. Could you share how the USB drive is made `bootable`, `active` or vFat/Fat16? I've had a bit of a look around the interwho, but no real luck...
Also, will Fat or Fat or Fat32 do the trick?

~ Sirk

I think this is my problem as well. I used gparted to make the USB stick a primary/active partition, but I'm not sure a boot record was transfered when putting the OS image on the stick. It doesn't seem to be recognized as a bootable device.

---

### Post by Keen101 on 2008-11-21
I havn't tried the 8.10 tool. But the launchpad one works great!

I think it will do what you want.

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)


The launchpad tool formats the drive, and set's up everything good. Give it a try from a running Live-CD.

---

### Post by Cushie on 2008-11-21
I have just installed to a new USB stick.  In 'Partition Manager' for the USB stick /dev/sdc1,the info row says FAT32, mount point CD rom, 4.30 GB used, Flag=BOOT.

---

### Post by Sirkey on 2008-11-21
> **Keen101 said:**
> I havn't tried the 8.10 tool. But the launchpad one works great!

I think it will do what you want.

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)


The launchpad tool formats the drive, and set's up everything good. Give it a try from a running Live-CD.

Humm...that site broke me, and I couldn't find where to download it...=S

But, I have found something that worked!!

[UNetbootin]("http://unetbootin.sourceforge.net/") did the job very well! All I had to do was tell it where my ISO file for Ubuntu was and where my USB drive was, and it did all the work. Then I plugged it into my EEE, pressed ESC, selected it, and away we went!! Excellent!!

Although I haven't got my wifi working...and the battery thing abuses me...+ I can't see all of windows...=S Which is why I'm now downloading eeebuntu! xD

So, crjackson, you know what to do now!! :)

Thanks for all the help guys!! ;-)

~ Sirk

---

### Post by crjackson on 2008-11-23
I finally got it to work using tools that come with Intrepid.:) I used Gparted to to ensure format was fat32, I THEN set the flags section to BOOT. I used the built in tool to load an Intrepid ISO and it boots in my wifes laptop (new HP) just fine. What's even better, all of her hardware was support right out of the box. No issues.

My laptop? Well that's another issue. It still won't boot from USB but I guess that's a bios matter, and since the bios for my eMachines M6809 was never updated, I guess I'm stuck with that. :(

---

