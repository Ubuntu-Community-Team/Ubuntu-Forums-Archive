---
title: "has latest ubuntu killed 2 laptops? please help"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by tongueman on 2011-11-17
this is strange...

having been running ubuntu 10.04 for a while, downloaded and installed latest ubuntu on my emachines. worked for a day and now will not boot, nor will it run the disk to reinstall, I just get a faint clicking noise. I thought it was hardware and resigned myself to buying a new machine.

forward on 1 week, my sister says she would like ubuntu on her acer, no problem, installed, worked for a day and the same thing has happened. surely this cannot be a coincidence? 

on the emachines I can access the bios but go no further.
on the acer I cannot even access the bios, the laptop just turns off after about 5-10 seconds. 

I cannot for the life of me think how an OS can do this, let alone pretty much cause identical issues with 2 completely different machines? 

please please help... not only could this save me from working out for a new laptop but could save the double expense of buying my sister one too! I know I'm repeating myself but how can this happen on 2 different machines???

---

### Post by matt_symes on 2011-11-17
Hi

Do you have a LiveCD/USB handy ? Can you boot into that ?

If you can, check the hard drives smart status to start with.

What message do you get after the POST test when you first switch the laptop on ?

Kind regards

---

### Post by tongueman on 2011-11-17
thanks for your reply...

acer displays nothing then turns off after about 5 seconds
emachines eventually returns error

 hd0 read error
 grub rescue>

I only can access bios on emachines and live cd does not work on either despite cd being number 1 in boot sequence

neither will boot from live cd

---

### Post by coldraven on 2011-11-17
On the emachines the hard drive has probably died. If you remove the drive you should be able to boot from CD. 
If that works just buy a new hard drive
The Acer is kaput, maybe she was using it on a bed or soft furnishing and it overheated.
If so, you are off the hook!

---

### Post by BillyBoa on 2011-11-17
Check the BIOS if everything is ok.

HDD failure is not a problem of the OS, at least most of the times. 11.10 has a problem with the fan of the laptops, working constantly, but this cannot affect the HDD.

Just check everything, from the connection to HDD to the computer, up to the screws of the back of your laptop. If the screws are not fixed well, the computer doesn't boot.

There are tenths of hardware problems responsible for the inability of the boot. Google for that.

---

### Post by matt_symes on 2011-11-17
Hi

> hd0 read errorOn both machines ? May well be a hard drive failure. It is a least booting to GRUB rescue though so there may be hope.

At the grub rescue prompt type

```
ls
```

What does it say ?

In the BIOS what does it say about your hard drives ? Post a picture from a camera phone if you can.

Kind regards

---

### Post by tongueman on 2011-11-17
thanks everyone...

ok.. I have removed the hd from the emachines and will now boot from live cd :)  I'm ok with that and will replace the hd.

the acer shows nothing.. turns on for about 5 seconds, displays nothing then shuts down.

---

