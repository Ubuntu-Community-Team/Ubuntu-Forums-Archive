---
title: "Boot CD Not working properly."
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Tokokono on 2008-08-16
Okay, I freakin' burned the image onto a CD-RW, popped it into my laptop's CD drive, and restarted the computer. Then, I ran the BIOS, set the CD drive to boot first, yadda yadda yadda. I restarted the computer, just like I'm supposed to, and I the boot CD ran, just like it should.

I was greeted with a screen that showed the Ubuntu logo, and gave me the option to either 'Try ubuntu without installing', 'Install Unbuntu, 'Check CD for defects,' 'Test Memory,' and 'Boot from first hard disk'. I've tried trying ubuntu without installing it, installing it, and checking the CD for defects, all of those of the same thing; Show me that it's loading the Linux Kernel, and once it gets to 100%, it sits there for about a half-hour, and then restarts the computer, and brings me back to the same screen. I can't do anything beyond that, so... what the futch am I supposed to do!?

If this is at all useful; I'm dual booting from Windows XP 32bit. And my laptop meets the minimum requirements to run Ubuntu.

---

### Post by overdrank on 2008-08-16
> **Tokokono said:**
> Okay, I freakin' burned the image onto a CD-RW, popped it into my laptop's CD drive, and restarted the computer. Then, I ran the BIOS, set the CD drive to boot first, yadda yadda yadda. I restarted the computer, just like I'm supposed to, and I the boot CD ran, just like it should.

I was greeted with a screen that showed the Ubuntu logo, and gave me the option to either 'Try ubuntu without installing', 'Install Unbuntu, 'Check CD for defects,' 'Test Memory,' and 'Boot from first hard disk'. I've tried trying ubuntu without installing it, installing it, and checking the CD for defects, all of those of the same thing; Show me that it's loading the Linux Kernel, and once it gets to 100%, it sits there for about a half-hour, and then restarts the computer, and brings me back to the same screen. I can't do anything beyond that, so... what the futch am I supposed to do!?

If this is at all useful; I'm dual booting from Windows XP 32bit. And my laptop meets the minimum requirements to run Ubuntu.

Hi and welcome, not a great way to make a first impression. :)
Ok did the check cd for errors return any errors? Did you burn the cd as slow as possible?
 You may want to do a checksum on the iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Could you tell us some system specs like the memory and graphics? Though they meet the minimum requirements there maybe some other issues.

---

### Post by Tokokono on 2008-08-16
Sorry, but I'm kinda here just to ask this question and get the dang OS to load! :)

I tried the check sum thingy, they match. Checking the CD for errors just did what every other option did, it loaded the Linux Kernel, and once it hit 100%, it sat there for half an hour, and then it restarted the computer and brought me back to the boot screen...

The laptop just did the same thing once more, it finished trying to load the Kernel, and then sat there for half-hour, and restarted, bringing me back to the Ubuntu screen.

This is a picture of the screen it's giving me: [http://i118.photobucket.com/albums/o112/shippou120/100_1444.jpg](http://i118.photobucket.com/albums/o112/shippou120/100_1444.jpg)

---

### Post by overdrank on 2008-08-16
> **Tokokono said:**
> Sorry, but I'm kinda here just to ask this question and get the dang OS to load! :)

I tried the check sum thingy, they match. Checking the CD for errors just did what every other option did, it loaded the Linux Kernel, and once it hit 100%, it sat there for half an hour, and then it restarted the computer and brought me back to the boot screen...

The laptop just did the same thing once more, it finished trying to load the Kernel, and then sat there for half-hour, and restarted, bringing me back to the Ubuntu screen.

This is a picture of the screen it's giving me: [http://i118.photobucket.com/albums/o112/shippou120/100_1444.jpg](http://i118.photobucket.com/albums/o112/shippou120/100_1444.jpg)

Hi and on the F6 option you can try and remove the splash and this will allow you to see any errors. Also the system specs please?

---

### Post by Tokokono on 2008-08-16
Remove the splash? Whaddya mean by that? Remove the word splash?

---

### Post by overdrank on 2008-08-16
> **Tokokono said:**
> Remove the splash? Whaddya mean by that? Remove the word splash?

Yes :) If you choose the F6 option you should be able to edit the kernel line. Remove the words quiet splash before the --.

---

### Post by Tokokono on 2008-08-16
Okay, I did that, but now it's just doing the same thing after I hit enter. It's sitting on the 'Loading Linux Kernel' window at 100%.

---

### Post by overdrank on 2008-08-16
> **Tokokono said:**
> Okay, I did that, but now it's just doing the same thing after I hit enter. It's sitting on the 'Loading Linux Kernel' window at 100%.

Ok **what are the system specs** and replace the quiet splash with noapic.

---

### Post by Tokokono on 2008-08-16
Ai, hold on.... stupid thing takes forever to load windows... which is part of the reason I'm switching...

Ugh, 10 minutes later... ANYWAYS: Microsoft Windows XP Home Edition Version 2002 Service Pack 2, Intel Pentium M Processor 1.70GHz,795MHz, 504MB of RAM.

---

### Post by overdrank on 2008-08-16
> **Tokokono said:**
> Ai, hold on.... stupid thing takes forever to load windows... which is part of the reason I'm switching...

Ugh, 10 minutes later... ANYWAYS: Microsoft Windows XP Home Edition Version 2002 Service Pack 2, Intel Pentium M Processor 1.70GHz,795MHz, 504MB of RAM.

Ok then the memory is not a issue, you can try the noapic option and hope it works. :)

---

### Post by Tokokono on 2008-08-16
Well... that didn't work, but I have another question; I noticed that with each of the 5 original options, the code listed next to 'boot options' (The F6 thingy) was diffrent, but they all had quiet splash at the end, so... do you want me to do the noapic thingy with a specific option of the 5?

---

