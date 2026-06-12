---
title: "Faulty down load or disk"
date: 2018-07-05
forum: New to Ubuntu
---

### Post by dave6 on 2018-07-05
Hi all
Is this looking like a dud disc or failed down load or would this effect be some thing else.

I am trying to do a full clean install of Ubuntu Mate 18.04 lts and the computer just hangs here for hours.

thanks
Dave

---

### Post by Autodave on 2018-07-05
What kind of computer is this? What was on it before?

---

### Post by dave6 on 2018-07-05
Hi Autodave
Standard cream colored computer use to have Ubuntu 12 on it, very stable then upgraded to Ubuntu 16.04.04 with the silly stupid side bar thing "useless to me" and I want to do a clean install to Ubuntu 18.04 Mate version which is close to what version 12 looked like.

Dave

---

### Post by Autodave on 2018-07-05
"Cream colored" leads me to believe that it is a quite old computer. You may not have what is needed to run 18.04 of any flavor.  IF this is going to work at all, you may have to live with a desktop not exactly to your liking.  If it were my machine, I would try running it from a boot disc/USB stick.  I would try your Mate as both 16.04 and 18.04 to see if either/both of them will run. Whatever runs from from the boot disc *should *install and run.

You may also want to look at Xubuntu 18.04: I have that running on a couple rather old machines (not cream colored tho :-)) and it runs OK.

---

### Post by dave6 on 2018-07-05
This ?

---

### Post by Autodave on 2018-07-05
OK. That chip was designed in 2005. Certainly not state of the art, but I would think that 18.04 would run on that.  Have you tried booting to the install medium and running it from that? Does it work?

---

### Post by dave6 on 2018-07-05
Does not boot as far as that

Dave

---

### Post by Autodave on 2018-07-05
OK. Seeing as how you cannot boot from an install medium, then we can rule out you hard drive since it really isn't doing anything while the machine is running from the install medium.

You say that you have tried 16.04 boot medium? If that will not work AND you had 16.04 running previously, then we need to figure out what failed. My first test would be the memory: have you tried running the memory test from the boot disc? Run it for at least 5 hours minimum. Of course, ANY error on that test tells you that you need further diagnosis on the memory.

Next test would be the power supply. That is easy for me since I have quite a few new and used ones here, but you probably don't have that luxury. You can get a new, cheap one online for probably $25 or less. The third test would be the motherboard.

Try running the memory test6. Also, you may want to make sure that all of the connections are tight on the MB and HD.

---

### Post by dave6 on 2018-07-07
> **Autodave said:**
> OK. Seeing as how you cannot boot from an install medium, then we can rule out you hard drive since it really isn't doing anything while the machine is running from the install medium.

You say that you have tried 16.04 boot medium? If that will not work AND you had 16.04 running previously, then we need to figure out what failed. My first test would be the memory: have you tried running the memory test from the boot disc? Run it for at least 5 hours minimum. Of course, ANY error on that test tells you that you need further diagnosis on the memory.

Next test would be the power supply. That is easy for me since I have quite a few new and used ones here, but you probably don't have that luxury. You can get a new, cheap one online for probably $25 or less. The third test would be the motherboard.

Try running the memory test6. Also, you may want to make sure that all of the connections are tight on the MB and HD.

I have tested all you said, and it is all working, At this point autoDave there is a wee oopps I did not read all of what you had typed "Have you tried booting to the install medium and running it from that? Does it work?".....My reply, Does not boot that far :oops:..

It seems to be the disk, but I have now burned 3 disks and all stop at the same point, last disc has been a fresh download and as I had replaced the DVD drive I had thought that the old DVD drive and the new may be working or burning at different track gaps.
So the last disc was a fresh download od an ISO file then burnt using the newer installed sata DVD drive but same result.

But there IS a conflict in this computer caused by an "upgrade" from ubuntu 12 to 16, above screen shot... During the upgrade the MBR file moved from a sata hard drive to an IDE drive and the computer will not / did not boot when the IDE drive was disconnected, ( I am just about to try it again with 18 mate ) 

Will keep you posted

Dave

---

### Post by dave6 on 2018-07-07
Up-date on booting from new disc

With the IDE drives off, the computer still does not fully boot to install Ubuntu Mate 18.04 LTS 64bit 

Any advice on what to do next to get a clean install from a disc

Dave

---

### Post by Autodave on 2018-07-07
Running out of ideas here. The one thing that gets me is that on both screen shots, it stops at the sound card.  Is this an added card or the built in sound?

---

### Post by dave6 on 2018-07-07
Sorry the camera has been out on a time lapse job and I had set it to NEF files only and have not set it back to NEF + jpeg files

So here is the latest jpeg and it has stopped lower down, ie it got past the sound card

Dave

---

### Post by Autodave on 2018-07-07
That is different: at the top there is a bus error. That isn't good. However, you have got me to the end of my expertise at the moment. *I* would be looking at loose connections or possible motherboard. But again, I have a motherboard to try and you probably don't. :-(

Hopefully, someone else will have more help for you.

---

### Post by dave6 on 2018-07-08
Good News AutoDave
Just had to wait for a Sunday for it all to work.  If only that was the truth.  I burnt a new disc (again) but I first ran the Simulating ISO  image to check then the burn, all good.
Turned computer off with the new disc still in DVD drive

Restarted computer this morning and gone a clean install, opened fireox, closed it, copied firefox backup file from USB stick, paste into hidden mozilla file and here we are all bookmarks passwords working

Dave

---

### Post by Autodave on 2018-07-08
Fantastic!  Please remember to mark the thread as closed!

---

### Post by rickdiaz on 2018-07-10
[COLOR=#545454][FONT=arial]Might be missing some inconsequential program[/FONT][/COLOR]

---

