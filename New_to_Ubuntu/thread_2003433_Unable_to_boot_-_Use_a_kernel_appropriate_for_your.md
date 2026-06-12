---
title: "Unable to boot - Use a kernel appropriate for your CPU?"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by duracella on 2012-06-14
Hi.

I have 4 Dell Mini10 laptop's running win xp. 
I want them to run Ubuntu 12.04, so i downloaded the .iso file, and made a bootable usb-stick with start-up disk creator.

When i try to boot from the usb-stick, i get following message:
"This kernel requires an x68-64 CPU, but only detected an i686 CPU.
Unable to boot -  please use a kernel appropriate for your CPU."

I thought I might picked wrong ISO, so I tried again, but exactly the same.

Now I have tried 64bit & 32bit ISO (and alternate ISO for both), but exactly the same.

So I googled a bit, and found that 12.04 does not support some old CPU's, so I thought that might be the problem. 
I also found [this]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html") article, tried out the mini ISO, got the same message.

Any clue for a solution?
__

---

### Post by prshah on 2012-06-14
> **duracella said:**
> I have 4 Dell Mini10 laptop's running win xp.
Now I have tried 64bit & 32bit ISO (and alternate ISO for both), but exactly the same.

The Dell Mini 10 runs off an Intel NM10 chipset, which supports Atom series 400 and 500 processors.

These support 64bit (Example: Intel Atom N450 @1.66Ghz), so you should be able to use 64bit. You should also be able to use 32bit PAE / non-PAE.

At the worst case, please try with lubuntu 32-bit, which has a non-pae kernel installed. If you get a similar error with this, then there is some other issue at play.

Summary: You SHOULD be able to use either 64bit or 32bit, PAE or non-PAE. You DEFINITELY CAN use lubuntu-32 bit. 

Please post back your results with lubuntu 32 bit.

Regards,

---

### Post by sanderj on 2012-06-14
Easy answer (as said above): try the 32-bit version of Ubuntu.


Longer answer:

[http://en.wikipedia.org/wiki/Dell_Inspiron_Mini_Series](http://en.wikipedia.org/wiki/Dell_Inspiron_Mini_Series) says there are different versions of the Mini 10:

1010: It has the Intel Atom Z520 and Z530 processor configurations.
1012: newer Atom n450 processor
1011: ...

As you can see on [http://en.wikipedia.org/wiki/Intel_Atom#History](http://en.wikipedia.org/wiki/Intel_Atom#History) , the Atom Z5xx has no 64-bit features. 

So possibly/probably you have a 1010 version of the Dell Mini 10. So use the 32-bit version. That should boot

---

### Post by sanderj on 2012-06-14
PS: with an i386 Ubuntu image, you can't get the message "This kernel requires an x68-64 CPU, but only detected an i686 CPU." 

So check the image you downloaded, and check what you've written to the USB stick.

---

### Post by duracella on 2012-06-14
Hi again and thanks for all the answers.

Yes, it is 1010.
The 64bit version won't work in any way.

I ended up using the torrent link for the ISO, then it booted like a charm.
I have no idea what was making the big problem.
I downloaded the right file, and I had written correct file.

Anyway, now it boots up perfectly, except...

When I get to the screen where I choose live or install... Only half of the screen shows, by that I mean, the half part that does not show, contains black or background colour... though, the whole screen shows when I boot into live.

---

