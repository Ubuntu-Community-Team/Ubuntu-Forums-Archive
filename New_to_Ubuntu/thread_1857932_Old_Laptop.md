---
title: "Old Laptop"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by Merisi on 2011-10-11
A friend of mine was given an old laptop which has no boot record on it and I have been asked how to install Ubuntu onto it.  It is a HP laptop with a dual core processor and it did have Vista but it appears to have been completely wiped.  How would I go about things could I literally boot up from disc?

Another problem is that I'm not sure how I will be able to connect it to the internet and therefore not sure how well the install would go.  I'm guessing I could do a basic install and once it's running connect it to the internet and get it up and running.

---

### Post by roger_1960 on 2011-10-11
Hi

Yes, download an iso file for say ubuntu 10.04LTS.  Burn the CD (right click the iso file and use the "write to disk"option) and then boot the old laptop with the CD in the drive. (You may have to  change the boot order in the BIOS on the laptop first) It should boot into ubuntu off the CD.  If it works (wifi should work) then you can install it from the CD with the "use whole disk" option.

If you don't understand please do post back with questions.

---

### Post by roger_1960 on 2011-10-11
Hi

Yes, download an iso file for say ubuntu 10.04LTS.  Burn the CD and then boot the laptop with the CD in the drive. (You may have to  change the boot order in the BIOS on the laptop first) It should boot into ubuntu off the CD.  If it works (wifi should work) then you can install it from the CD with the "use whole disk" option.

If you don't understand please do post back with questions.

---

### Post by mörgæs on 2011-10-11
No, by far the best is to install having wired internet access. Wifi comes at a later step.

---

### Post by Merisi on 2011-10-11
> **roger_1960 said:**
> Hi

Yes, download an iso file for say ubuntu 10.04LTS.  Burn the CD (right click the iso file and use the "write to disk"option) and then boot the old laptop with the CD in the drive. (You may have to  change the boot order in the BIOS on the laptop first) It should boot into ubuntu off the CD.  If it works (wifi should work) then you can install it from the CD with the "use whole disk" option.

If you don't understand please do post back with questions.
 
What I'm best off doing is to try and start off the process and then post back if I have any problems.

---

### Post by ld114 on 2011-10-11
I recently installed Ubuntu 11.04 on a 5/6 year old Asus laptop belonging to a friend. I used a CD for the install as the USB option didn't work (in fact the laptop would not boot with any USB devices plugged in due to a bug in the bios). 

I would also suggest doing the install with an ethernet cable plugged in - I had to install a wireless driver from the software centre afterwards.

The biggest issue was getting the Ubuntu installer to work. It might be OK on your HP laptop, but I needed to disable ACPI to get the installer to run. If you have problems this can be done either in the Bios (F2 on startup) or by pressing F6 at the first Ubuntu installer menu and amending the boot instruction.

Good luck - my friend is now very happy with his revived laptop running Ubuntu 11.04 classic mode (or Unity 2d) instead of windows which had become almost unusable.

---

### Post by Johnb0y on 2011-10-11
> **mörgæs said:**
> No, by far the best is to install having wired internet access. Wifi comes at a later step.

+1 how i do all my builds

---

### Post by Merisi on 2011-10-11
I've just tried installing 11.04 on the laptop I've just received but unfortunately it only has about 1.7gb which really surprised me and means I can't use Ubuntu. Any suggestions?

---

### Post by wolfen69 on 2011-10-11
The laptop only has 1.7gb hard drive?

---

### Post by amjjawad on 2011-10-11
> **Merisi said:**
> I've just tried installing 11.04 on the laptop I've just received but unfortunately it only has about 1.7gb which really surprised me and means I can't use Ubuntu. Any suggestions?

With 1.7GB HDD? are we talking about the total size? or a partition size? even my 12 years old HP has 4GB HDD.

Perhaps your best choice will be SliTaz. I don't think even Lubuntu will fit on 1.7GB Only.

---

### Post by smurphy_it on 2011-10-11
Post here the "model" and "manufacturer" of the laptop, so specs can be gained.

Ex.  Dell Latitude d600

---

### Post by Merisi on 2011-10-11
It's a HP G60 with Intel duo core and it did have Vista.  I don't know what's been done to it but it doesn't have the space for Ubuntu and when I checked for disk space I could only see something saying 1.7gb.


I just googled that laptop and it should have 320gb hd.  I must be using the RAM.

---

### Post by amjjawad on 2011-10-11
> **Merisi said:**
> It's a HP G60 with Intel duo core and it did have Vista.  I don't know what's been done to it but it doesn't have the space for Ubuntu and when I checked for disk space I could only see something saying 1.7gb.

How did you check that? I'm afraid you are using LiveUSB and you are reading the space of that USB.

Try to Open GParted and see what is the total size of sda.

---

### Post by wolfen69 on 2011-10-11
If it had Vista on it, it has to have *much* more than 1.7gb hd space. You could just fire up the installer and choose "use whole disk" (or something similar)

---

### Post by Rasa1111 on 2011-10-11
> **wolfen69 said:**
> If it had Vista on it, it has to have *much* more than 1.7gb hd space. You could just fire up the installer and choose "use whole disk" (or something similar)

Yeah, exactly what I would do. 

I think you're looking in the wrong place OP. 
If you don't care about what's on it...
just tell it to wipe and install..
then you'll see how much space you actually have.

Or just open Gparted and look.

---

### Post by Merisi on 2011-10-11
When I use the disc, I'm given a choice, try Ubuntu or install Ubuntu.  I click install Ubuntu and the next options menu has a cross against has at least 4.4gb available drive space.  Not sure what to do from here.

---

### Post by Merisi on 2011-10-11
> **Rasa1111 said:**
> Yeah, exactly what I would do. 

I think you're looking in the wrong place OP. 
If you don't care about what's on it...
just tell it to wipe and install..
then you'll see how much space you actually have.

Or just open Gparted and look.

When I open Gparted, it says failed to run Gparted as user root. Unable to copy the users Xauthorization file.

---

### Post by wolfen69 on 2011-10-11
```

```> **Merisi said:**
> When I open Gparted, it says failed to run Gparted as user root. Unable to copy the users Xauthorization file.

Run Gparted with
```
gksu gparted
```

---

### Post by mörgæs on 2011-10-11
When in doubt: Erase the drive completely using [www.killdisk.com](www.killdisk.com)

---

### Post by amjjawad on 2011-10-11
If you don't need any files on your HDD, I would do one thing if I were you.

1- Open GParted

2- From Device Menu > Create New Partition Table. That will wipe the whole thing in no time.

3- Start Creating your partitions (3 partitions: root, swap and home).

4- Start the installation and choose something else.

5- I prefer to use Lubuntu 11.04 OR WAIT until THU to try the new release of Lubuntu which is 11.10

6- If you decide to go Ubuntu Route then your call but the installer will be the same.


If you have some important files, PLEASE make sure to backup before you do anything.


Good Luck!

---

### Post by Merisi on 2011-10-11
> **mörgæs said:**
> When in doubt: Erase the drive completely using [www.killdisk.com]("http://www.killdisk.com")

After that should everything work okay when I put my Ubuntu install disc?

---

### Post by amjjawad on 2011-10-11
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by Merisi on 2011-10-11
> **wolfen69 said:**
> Run Gparted with
```
gksu gparted
```

I finally got Gparted open and I now see what the problem is, it says there are no devices.  Does that mean the hard drive is missing?

---

### Post by wolfen69 on 2011-10-11
> **Merisi said:**
> I finally got Gparted open and I now see what the problem is, it says there are no devices.  Does that mean the hard drive is missing?

Missing or broken.

---

### Post by Merisi on 2011-10-11
> **wolfen69 said:**
> Missing or broken.

The horrible smell coming from may suggest it's broken.  Well it explains why it's a freebie.

---

### Post by ld114 on 2011-10-11
> **Merisi said:**
> I've just tried installing 11.04 on the laptop I've just received but unfortunately it only has about 1.7gb which really surprised me and means I can't use Ubuntu. Any suggestions?
Have you used "gparted" to see what the hard disk looks like? It's usually on the live disk, or you can download a gparted live disk that boots up and lets you look at/partition/reformat the hard disk.

---

### Post by ld114 on 2011-10-11
Just caught up with previous posts! Looks like you need a new disk. They are usually not that expensive if it's a decent laptop otherwise.

---

