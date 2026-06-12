---
title: "Accessing hard drive from Ubuntu live"
date: 2018-03-22
forum: New to Ubuntu
---

### Post by cmcollins2 on 2018-03-22
Hi all.

I'm totally new to Linux so hoping you guys can help me out here.

My laptop was happily running Windows 10 until everything froze up on me the other day and I had to hard power off the system. Since then, I can't boot windows and can't seem to get any of the recovery utilities to work. I'm not sure if it's a hardware issue or a corrupt windows install, but my fear is that the hard drive has failed.

So, I've created a Ubuntu live USB which I've tested in an old laptop and works fine. I've tried running it on the problem laptop and after selecting the option to evaluate Ubuntu without installing, it threw up a load of errors, starting with "couldn't parse dbx signatures", then a whole load of "ATA1.00 exception emask" errors. Eventually it then progressed to the Ubuntu splash screen and after a VERY long time, the Ubuntu desktop launched. 

I tried looking for the hard drive in the file manager, however it's not showing up there. When I tested the live USB in my old laptop, I could access the whole hard drive straight away, but I appreciate that the problem laptop has completely different hardware, so is there something else I should be doing to access the hard drive?

After googling the ATA1.00 errors, it suggests a hard drive problem, but why would it show those errors if I'm launching Ubuntu from the USB?

I'm really hoping I can access the hard drive and recover some files, but I'm starting to fear the worst....

Any help anyone can provide would be very gratefully received!

---

### Post by SeijiSensei on 2018-03-22
Even in trial mode, Ubuntu will examine all the hardware on the machine.  It sounds like your hard drive died.

Take a look at the file /var/log/syslog after booting from the USB.  Do you see a lot of errors reported there when Ubuntu tries to mount your hard drive?

---

### Post by C.S.Cameron on 2018-03-22
Sometimes drives don't show up in "Files" if unmounted, have a look in "Disks", if it is there click the little triangle to mount it.

---

### Post by Mark Phelps on 2018-03-22
You can't get to the Win10 filesystem from Linux unless you went to the trouble to manually disable Fast Startup (NOT Fast Boot -- this is entirely different), and since you did not specifically mention that, then you're stuck -- as Win10 keeps the Windows filesystems mounted, even when not running.

So, with Win10, the days of routinely booting Linux distros to access Windows filesystems are over.

---

### Post by cmcollins2 on 2018-03-22
Thanks for the replies. I had a look at the syslog and it does show a load of errors relating to the hard drive. However, I've gone into the Disks area in settings and it shows the hard drive, reports all the partitions correctly and under Assessment it says "disk is ok". I can't see any triangle to click on to mount it. 

So, does this mean my hard drive is actually Ok but windows is stopping me from accessing it through Ubuntu?

---

### Post by oldfred on 2018-03-22
Probably.

You may be able to directly boot Windows from UEFI menu, and press f8 to get into its repair console.
Otherwise you need your Windows repair disk which has its repair console.

Almost always if you hard force a shutdown, file system gets corrupted. With Window then you have to run chkdsk, often multiple times or until no errors.
You can only run chkdsk from Windows.

---

### Post by cmcollins2 on 2018-03-22
Ok so after going in and out of the Disks menu a few times, it suddenly started displaying the labels of the partitions on the hard drive and allowed me to mount the main storage partition. I can access all the files but navigation through the folders is very slow, and although it's now allowing me to copy files across to an external hard disk, it's incredibly slow. Don't get me wrong, I'm super happy that I'm managing to get my files back, but is the super slow read speed indicative that the drive is still on its way out?

---

### Post by yancek on 2018-03-22
> but is the super slow read speed indicative that the drive is still on its way out?

It may be or may be that you have a corrupt windows filesystem partition.  I would expect that using windows to copy to/from a proprietary windows drive would work better than using another system such as Ubuntu/Linux.  Do you have a windows DVD to use to try to Repair, maybe run chkdsk?

---

### Post by C.S.Cameron on 2018-03-22
It seems only recent that you need to mount some partitions using Disks.
When using Windows 10 sometimes it takes ages for that green strip to run across the top of an explorer window when navigating folders. I'm not sure if this is only a Ubuntu thing.

---

### Post by Mark Phelps on 2018-03-23
OK, if you can access the files at all, then it is NOT a Fast Startup problem as that prevents the filesystem from even being mounted.

From your description, it sounds like the hard drive is failing -- as that really slow down the drive making it painfully slow to do anything!

---

### Post by cmcollins2 on 2018-03-23
> **yancek said:**
> Do you have a windows DVD to use to try to Repair, maybe run chkdsk?

I have tried a Windows recovery disc but couldn't get anywhere with it - just wouldn't boot past the Lenovo splash screen. Will maybe try downloading another copy to see if it makes a difference.

---

### Post by cmcollins2 on 2018-03-23
> **Mark Phelps said:**
> 
From your description, it sounds like the hard drive is failing -- as that really slow down the drive making it painfully slow to do anything!

Yeah I think I will press on with backing up the files (which will take all weekend I imagine at the speed it's going) and then maybe just ditch the drive and start afresh.

---

