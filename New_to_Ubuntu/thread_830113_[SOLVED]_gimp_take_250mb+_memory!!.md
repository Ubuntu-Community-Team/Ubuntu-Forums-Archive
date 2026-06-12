---
title: "[SOLVED] gimp take 250mb+ memory?!?!?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-15
it gimp supposed to do this? this is insane!!!

---

### Post by Joeb454 on 2008-06-15
It depends on the size of the image you're trying to edit. Bigger image = more memory :)

Also the way Linux handles RAM is different to Windows, so that could partly be why, though I'm guessing its the image size. How big is the image you're trying to edit?

---

### Post by chewit on 2008-06-15
on my pc it only uses about 30 to 50mb

---

### Post by dnns123 on 2008-06-15
Maybe he set it up to a very high resolution. Also, if your running under 64-bit, it's common to have a high RAM usage. Although, 250+MB is uncommonly large...

---

### Post by vajorie on 2008-06-15
you can change memory usage with file>preferences>environment in gimp
PS. that kind of memory usage is normal with large files. still, check your gimp settings using above

---

### Post by adamorjames on 2008-06-15
The numbers of undos could effect the memory usage I think.

---

### Post by Zopiac on 2008-06-15
ok. 64bit, with a 2560x2048 image :P i think thats it. maybe.

---

### Post by Zopiac on 2008-06-16
well i was editing a 7.599 image, and the computer froze again! what does this mean?

---

### Post by markbuntu on 2008-06-16
You should save the image more often and reduce the number of undos. The undos are piling up in the memory and running out of space. Every time you change something a snapshot of the image is placed in the memory, either in ram or swap. With an 8meg image, you can run out of memory fairly quickly if you make a lot of rapid changes without saving.

How big is your swap?

If you are gong to do a lot of this, making your swap bigger will help but more ram would help more. You can also disable your desktop effects and other things that grab a lot of ram.

---

### Post by Zopiac on 2008-06-16
> **markbuntu said:**
> You should save the image more often and reduce the number of undos. The undos are piling up in the memory and running out of space. Every time you change something a snapshot of the image is placed in the memory, either in ram or swap. With an 8meg image, you can run out of memory fairly quickly if you make a lot of rapid changes without saving.

How big is your swap?

If you are gong to do a lot of this, making your swap bigger will help but more ram would help more. You can also disable your desktop effects and other things that grab a lot of ram.

well, im updating ram soon 8x, but i have no swap...couldnt figure out how to do it (was an ubuntu n00b when i installed), but i had like 2 undos >.< and that in a 7 by 599 pixel image, even if it had been half an hour since saving (didnt want to save anyways, was testing functions for a web page background [my dad's bad at picking out background, i was helping]) i wouldnt call that an eternity, so does swap space matter that much?

---

### Post by markbuntu on 2008-06-16
If you have less than 1GB of ram then yes, swap is very important. It is like an extension of your ram just a little slower because it is on the disk. If you use any graphical editor/drawing program it is critical. 

You can use one of the partition programs to make a swap sector from part of your existing partition/drive without any troubles. You should do it as soon as possible.

Gimp will also use a lot of ram if you start it up with all the addons and plugins and extensions. It is a program that has become huge with all these. You do not need to have these on all the time and can easily enable them when you do need them. Try turning a bunch of them off and closing some of the extra windows that open with it if you don't need them.

Image size is one thing but gimp can make a huge file from a small image when it is storing all the information about changes made to it.

---

### Post by Zopiac on 2008-06-16
ok. i have 7.45 gigs of swap now. enough? also, how fast is it? i have 1gig ddr2 ram, plus this. is this more equivanent to pc100? some sort of gddr(1)?

---

### Post by Zopiac on 2008-06-16
based on [this site]("http://people.debian.org/~psg/ddg/node81.html"), i can deduce that 3gigs is recommended, for i have 1 gig of RAM. is this accurate?

again, what is the relative speed of this swap? additioinally, does more swap mean faster, slower, more/less stable 'virtual ram', or what?

---

### Post by markbuntu on 2008-06-17
You don't want your swap to be too big because it will take more search time on the hard drive. The whole idea of swap is to have a fast dedicated section on your hard drive that can help out the ram. 

The speed depends on your drive, (SATA is faster than PATA), the sectors used, their location relative to the read write heads parking position, and the size of the swap. As I said, large swap can mean slower swap but too smalll a swap will cause even bigger slowdowns because when ram and swap are full, the os unloads and reloads apps which can be really really slow and cause crashes.

If you have an on board video, you can immediately subtract up to 256MB from your ram since this is dedicated to the video and basically unavailable to the os. So, a system with 1GB of ram and onboard video like a ATI 200M actually only has 750MB available. When you remove the dedicated ram for the processor, you are getting pretty constrained on free ram if you run a lot of high grade graphics or memory intensive programs.

When I had XP on this machine with 1GB of ram it was often very slow and I was thinking it was the cpu (AMD 3800+) but when I put in another 2GB of ram it ran much much faster. The cpu was constrained by the lack of ram. 

Now, with Ubuntu, I feel no need for a faster processor or even so much ram as I have because everything runs really fast and it never uses more than 700MB of ram. I also got a new video card with 1GB of ram on it.

On board video seems to be not such a good thing performance wise because it ties up the system ram and must share the bus with the cpu.

---

