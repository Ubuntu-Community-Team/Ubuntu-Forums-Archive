---
title: "How to boot Ubuntu from a live cd with windows?"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Cor. Dunn on 2012-09-12
Hi All:

So this is a pretty general question, and I think I know how it works, it's just I want to check to make sure I got it right.

I have this laptop that I use the most, and I decided to run Ubuntu on it too so I can constantly practice using Ubuntu. The thing is, I don't think I want to install Ubuntu (as a dual boot) alongside Windows, so I'm going the Live CD route. 

For the Live CD thing, do I just burn the image to the disc, restart the computer, go into BIOS and select Boot from CD Drive, and select Try Ubuntu using Live CD on the installation menu? 

Thanks,

---

### Post by Shadius on 2012-09-12
You got it.

---

### Post by Cor. Dunn on 2012-09-12
That was quick, thanks!

One more question, I'm still in the process of learning Unix and Ubuntu, so is it a better idea to use a Live CD where each session would be fresh from the last (in case I break anything) or is a full installation of Ubuntu better?

---

### Post by Hadaka on 2012-09-12
Hi, while the live CD "Try Ubuntu" will allow you to get a general feel
of Ubuntu, it's slow and lacks the ability to save any files you may create, such as bash
scripts,web links, or whatever. You can load a complete working full 12.04 os, 
complete with all the updates  and be totally functional, while never touching any
windows files or the computers windows hard drive. By loading to a USB stick. The
total os is about 5 gig with updates, so I'd suggest minimum 16 gig stick, it will be
a bit slower than if you loaded to the hard drive, but, for a 20 buck investment for
a usb stick..what the heck. and you can plug the stick into a different machine and
viola, ubuntu os.

---

### Post by Shadius on 2012-09-12
> **Cor. Dunn said:**
> That was quick, thanks!

One more question, I'm still in the process of learning Unix and Ubuntu, so is it a better idea to use a Live CD where each session would be fresh from the last (in case I break anything) or is a full installation of Ubuntu better?

While learning how Ubuntu and Unix works, I definitely suggest using the LiveCD first so that you can "play" around without worrying about breaking anything. It's a good way to "test drive" Ubuntu. That is how I first started. Just a way of getting familiar with Ubuntu until you become comfortable with it enough to install it and have a dual-boot. You might try to do things with Ubuntu that are done in Windows and learn that things are done differently. After all, Ubuntu is not Windows. 

I believe there is a way to create the image to save the changes you've made to the live session. I believe it's called "persistent" or something like that. I think you can use it with the LiveCD and the LiveUSB. I'm not sure how it's done though, as I've never tried it.

---

### Post by mips on 2012-09-13
Cor. Dunn,

Instead of writing to a cd you can also write it to a USB stick which generally boots faster than a cd. From windows you can use [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) for this, just point it to the image you downloaded.

Unetbootin will also allow you to create a persistant usb stick which means it reserves space on the usb stick allowing you to save files, changed system settings or newly installed applications, you just specify the amount of space where it says "Space used to preserve files across reboots (Ubuntu only):"

All you have to do on your laptop is to tell the bios to boot from USB.

---

### Post by asifnaz on 2012-09-13
You are right

---

### Post by mastablasta on 2012-09-13
another good otpion if you have enough ram is to use virtual box. you can then install it in virtual disk which is like safe area and you can easilly breake  the os in there: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
you can also make snapshots there so in case you break but would liek to return to exact previous state you then just reload the snapshot.
 
or you can launch it live via virtual box directly from the image (you mount the iso image as CD rom and then tick the liveCD box in vbox settings)
 
for virtual box install you will need at least 2GB ram in windows XP maybe a bit more in windows 7.

---

