---
title: "My laptop, cant or wont load Linux  :S"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by mike4life on 2008-08-28
Hi,

My laptop is not too keen on ubuntu by the looks of things, 
Ive put the live disc in and tried it 4 times now and every time it does the same thing:

It will boot the linux kernel but wont do anything after that :S

And I've also tried 3 other dics of ubuntu i have (the disc i am wanting to install is correctly mounted coz i got it from the ubuntu website)

I've made a short vid so you get the idea, heres the link: [[COLOR=#444444]http://www.youtube.com/watch?v=tyeKIel1Uws[/COLOR]]("http://www.youtube.com/watch?v=tyeKIel1Uws")

Any help with this would be handy,
so pleaseeeeeeeee reply! lol :grin:




Mike. [x]

---

### Post by stunningman on 2008-08-28
have you made your partitions well:
ubuntu basically requires
a / partition -ext3 file system
and a swap partition which should be twice of your ram.

when a partitioner window comes up select manual partitioning
then choose a partition if it is one of fat partition delete it(caution :don't deletee your windows partition)delete it. then highlight the deleted partition click new partition button below

now give how much space you want to give for / partition
please note leave some space for swap partition i.e twice of your ram and give the remaining to / partition

a / partition is a root
select mount point as / from drop down menu
file system as -ext3 journalising file system

now your system will boot perfectly after installation.
happy linuxing!!!!!!!!!!!!!!

---

### Post by mike4life on 2008-08-28
> **stunningman said:**
> have you made your partitions well:
ubuntu basically requires
a / partition -ext3 file system
and a swap partition which should be twice of your ram.

when a partitioner window comes up select manual partitioning
then choose a partition if it is one of fat partition delete it(caution :don't deletee your windows partition)delete it. then highlight the deleted partition click new partition button below

now give how much space you want to give for / partition
please note leave some space for swap partition i.e twice of your ram and give the remaining to / partition

a / partition is a root
select mount point as / from drop down menu
file system as -ext3 journalising file system

now your system will boot perfectly after installation.
happy linuxing!!!!!!!!!!!!!!
But how can i install ubuntu without booting nito the live version, as my lapptop wont load from the live bit, it hangs just after the kernel loads, see the vid for what i mean  ::  [[COLOR=#444444]http://www.youtube.com/watch?v=tyeKIel1Uws[/COLOR]]("http://www.youtube.com/watch?v=tyeKIel1Uws")
 
 
thanks  x

---

### Post by Elfy on 2008-08-28
You say you've tried 4 discs - did you burn them all from the same download? Have you checked that the download is ok - either md5sum or at least checked the discs with the option in the menu you get when it boots.

---

### Post by mike4life on 2008-08-28
> **forestpixie said:**
> You say you've tried 4 discs - did you burn them all from the same download? Have you checked that the download is ok - either md5sum or at least checked the discs with the option in the menu you get when it boots.
2 are from downloads and they dont work and the other two are from ordered from the ubuntu website, the 2 from the website i have are 7.04 and 8.04  :s
 
 
 
Mike. [x]

---

### Post by tuxulin on 2008-08-28
whats your system specs ?

tuxulin

---

### Post by Ryadt on 2008-08-28
> **mike4life said:**
> 2 are from downloads and they dont work and the other two are from ordered from the ubuntu website, the 2 from the website i have are 7.04 and 8.04  :s
 
 
 
Mike. [x]
Did you try the alternate version?

---

### Post by OffAxis on 2008-08-28
you could always try the alternate cd and then install the desktop afterwards.

---

### Post by tuxulin on 2008-08-28
it sounds like some interrupt or bios situation

---

### Post by mike4life on 2008-08-28
> **OffAxis said:**
> you could always try the alternate cd and then install the desktop afterwards.
What is the alternate version? :S
 
 
Mike. [x]

---

### Post by Ryadt on 2008-08-28
> **mike4life said:**
> What is the alternate version? :S
 
 
Mike. [x]

The alternate cd is a text-based installer. You can download it from the ubuntu homepage. Just make sure to check the box where it gives you the option for the alternate version.

---

### Post by k3lt01 on 2008-08-28
I am having a similar issue, I just fitted a 250 Gig HDD to my Acer that is normally 40 Gig. I can install Ubuntu easily on the 40 Gig but when I try the 250 Gig is hangs before it gets to the 1st options screen. I know its not the hard drive because I can install Windows XP and RedHat 8.0, I know its not the CD because I have used it successfully on many occasions even on this laptop. I'm going to download the Alternate CD and try that tomorrow morning.

---

### Post by mike4life on 2008-08-28
> **Ryadt said:**
> The alternate cd is a text-based installer. You can download it from the ubuntu homepage. Just make sure to check the box where it gives you the option for the alternate version.
is is easy enough to install ubuntu via a text UI? :S
I'm not at all used to using terminal :S


Mike. [x]

---

### Post by Elfy on 2008-08-29
This is a good alternate install site - [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

