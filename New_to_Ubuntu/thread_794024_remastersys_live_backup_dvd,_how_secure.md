---
title: "remastersys live backup dvd, how secure?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by srossnz on 2008-05-14
I finally figured out this remastersys app and it's awesome.  I now have a live bootable dvd of my entire system.  <wohoo>  Now.. it boots up to the password box as it should, but how secure is this?  If someone got hold of my dvd would it be easy for them to hack into my data on the disk even if they do not know the password?

Thanks

---

### Post by candtalan on 2008-05-16
> **srossnz said:**
> I finally figured out this remastersys app and it's awesome.  I now have a live bootable dvd of my entire system.  <wohoo>  Now.. it boots up to the password box as it should, but how secure is this?  If someone got hold of my dvd would it be easy for them to hack into my data on the disk even if they do not know the password?

Thanks
Probably fairly easy. Once they have physical access to - say - your machine, they can do what they like and take as much time as they like if they know what they are doing. With your live cd, the worst they have to do is keep trying passwords. I suspect you can make a live CD boot into a terminal also, which gives them easy options. 

One thing which comes to mind from a security point of view is that you have now made an instance of your whole Pc on a *very* portable little disk! As you imply: what happens if it gets 'lost', much more likely than the PC itself getting 'lost'?

Apart from being obviously careful with the backup dvd storage, the thought of using a level of encryption on your pc comes to mind. Hard drive or partition encryption, if such exists?
hth

---

### Post by nicedude on 2008-05-16
Your remaster sys disk will only have what data is on your ubuntu partition so if in future you divide your disk and have system partition and data storage partition you could then use your disk where ever you want and your stored data would be safe at home. In general it is no less secure than an unencrypted computer hard drive itself is. You can easily use a live cd to boot your pc and then mount your partitions and view all its data unless the disk is encrypted. But unless you are up to something more than movie downloading type activity I wouldn't worry about it. And as far as credit card and other financial details I personally recommend that they not be stored on the PC period and only used in a session ( I.E don't go letting firefox remember your online bank login info for example ). The extra time to enter these few vital pieces of info without storing them is worth the extra security it will bring. Also I would recommend never using credit card info over wireless networks if there is any way possible to do so with an Ethernet hardwired connection.

Hope this helps you out man.

---

### Post by srossnz on 2008-05-16
Thanks guys!  How about this idea.  I make a remastersys backup and these are in the form of an iso file.  I then encrypt this file and burn to cd.  If my system dies i can decypt the iso, burn it to dvd and use it.  Is there a gui tool that can encrypt this file or make a file that self decrypts on password?

---

### Post by nicedude on 2008-05-16
try searching in the synaptic package manager for seahorse and look to see if that will do what you want.

---

