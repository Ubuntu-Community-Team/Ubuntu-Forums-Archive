---
title: "Unbuntu Installs but no Grub Loader"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Musical4Ever on 2012-08-28
OK, I've used Windows for 17 years, but I am new with Linux so please understand my crass stupidity: 

I have had Unbuntu on this desk PC for 8 months or so & actually did a couple of re-installs at the beginning as I messed up, sorted the swap partition OK, re-sized the Linux partition OK & things when smoothly including the update in April. I use Linux along with Windows 7, Unbuntu is installed on the second of two 1TB drives, Windows resides on the first drive, on a 50 GIG partion along with a large partition for music. Drive two has 3 partitions, one for Acronis images, another for files & one that has nothing in it.

This arrangement worked perfectly until I messed around with Mint. I ended up with no loader of any kind & no Linux or windows. I replaced the Windows boot & deleted the Linux partitions & just had Windows again intending to do a clean install of Unbuntu again, I have yet to achieve this goal.

I want Linux back but subsequent attempts to install Unbuntu fail. I must be doing something wrong as it installs OK adds a Linux partition to drive 2 & a swap partition but after rebooting I don't get the Grub loader. I formatted drive 2 and redid my NTFS partitions in case there was issues with drive 2 it but an install of Unbuntu goes through all the motions & says setup fine but no loader on re-boot. I have a good working knowledge of windows partitioning but seems at level -zero with Linux. What I don't understand is why I was able to sort the partitioning with version 11 of Unbuntu twice yet no can't work it out with 12.xx (doh) :p

I've attached a view of my drives viewed from Acronis Disk Director from Windows with Linux installed yet with no Grub loader. I have everything I have backed up in several places & many images of Windows no nothing can go horribly wrong. Thanks for any help - ):P

---

### Post by SlugSlug on 2012-08-28
check the boot order of your drive in BIOS 
Maybe swap the order and try boot

---

### Post by Musical4Ever on 2012-08-28
[Digg]("http://digg.com/submit?phrase=2&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2049210&title=Unbuntu+Installs+but+no+Grub+Loader") - I'm only down the road in Chesterfield :-) I'll have a mess with that & report back!

---

### Post by nativehound on 2012-08-28
Boot from a live cd and install Boot-Repair
It's quick and painless.

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Musical4Ever on 2012-08-28
Well I was able to get Linux to boot by selecting SATA1 by pressing F12, though why I didn't think of that eludes me --> Me Edjit ~

But I wasn't able to change the settings in BIOS to use SATA 1 as first hard drive boot, though I'm not sure why.

So I used the Boot Repair disc 'nativehound'  recommended:  Wow what an amazing disc! Sorted the issue, & now Ubuntu setup nicely & I'm happy & Jolly again. I think the more youv'e used Windows in your life the more chance of making an idiot of yourself with Linux! 

Thanks for the help much appreciated! I will most likely be back at some point! Not sure how you  mark a thread as solved though.
):P

---

### Post by YannBuntu on 2012-08-29
Good job :)

[Solved] can be added via the Thread tools button at the top of the page.

---

