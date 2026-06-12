---
title: "No boot options, opens right into Win7"
date: 2014-02-09
forum: New to Ubuntu
---

### Post by SpazCool on 2014-02-09
Back story: 
After a few months of trying to deal with Ubuntu I gave up, this was partly due my residing in China and have a whole host of internet related problems...without google Linux is a bear to deal with. Prior to my giving up I had Ubuntu 12.something dual booting alongside Win7 with its very own partition. 

The now story:
Being back in the good ole US of A I have decided to give Ubuntu another go. Using a USB with Ubuntu 13.10 I went through all of the steps I thought required and did finally meet the "you have succesfully installed ubuntu...now restart" screen. Except when I restart, I boot directly into Win7. That is, there is no boot load screen to choose which OS I want to run with, like I had the last time I had tried Ubuntu.

Where I think I f*^(% up:
Again, I already had a partition that Ubuntu had used just fine a few short months ago but, I don't/didn't have a clue what to select to get Ubuntu to use that partition this time around. I googled a couple of solutions that mentioned setting the desired partition to "/" and "ext4" which I dutifully followed but, all I got was Win7 greeting me on boot up. 

**I suspect that whatever is required to boot Ubuntu needs to be placed in the same place as Win7, where I probably chose to place it in the same partition as the rest of Ubuntu (sorry about the lack of terms, new to Linux). **

So, how do I fix this mess? Because the partition has been reformatted to ext 4, I can't even see it listed anymore in Win7. And I don't think booting from the USB will solve this either. Heck, I'm not even sure how to phrase this issue to search for it in google. 

Thanks in advance,
Doug

---

### Post by UltimateCat on 2014-02-09
It sounds like the bootloader didn't get installed.

When you start your computer do you have a GNU GRUB Menu with Ubuntu first and your Windows 7 partition listed second?

It might help to post the output of this command so we can see all the partitons on your computer.
Use the Ubuntu distro that you have on your usb stick and post the output of this cmd:
```
fdisk -l

```
Run this cmd as 'root' and with the small letter L--

> 
Again, I already had a partition that Ubuntu had used just fine a few  short months ago but, I don't/didn't have a clue what to select to get  Ubuntu to use that partition this time around. 

If it were my case I would of deleted the old partition and created a new one. create one 20 GB(/) journaling file fs ext 4 partition and a 1 to 2 GB partition for the swap.
I prefer manually partitioning when performing an installation for a dual boot : Ubuntu & Windows 7.

Another thing that is important to do is to shrink the Windows 7 partition before you install your Linux.

Before I could install Linux on my Sony Vaio I had to shrink Win's 7 in order to have room for Fedora--

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by fantab on 2014-02-09
Boot with Ubuntu DVD/USB and 'try ubuntu without installing'.
Establish internet connectivity.
Install [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") and run it. Run '*Create Bootinfo Summary*', note down the http:// link it creates and post the link here.

---

