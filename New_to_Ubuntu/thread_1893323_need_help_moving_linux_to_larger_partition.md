---
title: "need help moving linux to larger partition"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by 450rOOST on 2011-12-10
when I partitioned my harddrive for 11.04, I allocated 100gb for linux.  When I installed 11.10, I don't remember seeing any options to select where it would install, I assumed it was replacing 11.04 and would go on the same partition.

Well, now I'm only using 18gb, 10gb for / and 8 for swap and I have 92gb sitting unallocated at the end.  How can I move linux to that unallocated partition?  I wouldn't mind rearranging things so that my 'os disk' (windows7) was using 400gb and the rest for linux.

Any help on how I can do this without formatting or erasing what I have now?

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/Screenshotat2011-12-09220017.png[/IMG]

---

### Post by 450rOOST on 2011-12-10
well ngjdew, thanks for the fashion tips, but I don't see how that's relevant to my question.

---

### Post by QIII on 2011-12-10
The first thing I will say is that if you change the size of the  Windows partition, use the **Windows** tools and **NOT gparted**!  Did I say **NOT**  **to use gparted** to resize the Windows partition?  If I didn't, then just  remember **NOT to use gparted** to resize the Windows partition.

I'm about to go to bed, but a clarification might be helpful for someone  else who comes along before I wake up (late, I hope, but we have one of  the wee ones staying over tonight) tomorrow over here in Beaverton:
 
 In the end, you wanted to have Windows on the partition labeled OSDisk and Ubuntu on the other ~100 GiB?

Do you want only Oneiric, or were you also expecting Natty to be there, too?

Did you save the contents of your /home folder from Natty before you started working on installing Oneiric?

Did you do anything on Oneiric that you would be saddened to lose?  (You may be out of luck with anything you had on Natty.)

Do you want to do this the quick, easy (and destructive - at least to your current Ubuntu install) way?

---

### Post by 450rOOST on 2011-12-10
hellow fellow NW'erner!  
Well, I don't need to mess with the windows partition for now.

As far at natty, oneiric, I don't even know what that means.  I haven't done much at all, pretty much just installed.  If I changed from natty to oneiric, that happened last night when joemills was trying to help me get my video card going. 

So in short, there is nothing to lose.  I would be satisfied with 100gb for now and leave windows alone.

I copy you on the 'do not use gparted for windows'.  I just know that 10gb isn't going to cut it.  I suppose I could go into windows, use their disk management utility to get things setup, then just reinstall again. 

good luck with the little ones.

---

### Post by QIII on 2011-12-10
I'll try to get into more detail tomorrow if you don't get help by then, but I'm beat right now.

I've seen far too many decades go by to fare very well when someone who has just barely finished half of one jumps on the bed in the morning after a short night to get an old fart up to play.  Fortunately, we have just the one over tonight!

---

### Post by 450rOOST on 2011-12-10
> **QIII said:**
> I'll try to get into more detail tomorrow if you don't get help by then, but I'm beat right now.

I've seen far too many decades go by to fare very well when someone who has just barely finished half of one jumps on the bed in the morning after a short night to get an old fart up to play.  Fortunately, we have just the one over tonight!

sounds good.  The 10gb will last me through the night.  I have some books to read about linux anyways.  Might help me understand what your talking about anyways.

---

### Post by fantab on 2011-12-10
> **450rOOST said:**
> when I partitioned my harddrive for 11.04, I allocated 100gb for linux.  When I installed 11.10, I don't remember seeing any options to select where it would install, I assumed it was replacing 11.04 and would go on the same partition.

Well, now I'm only using 18gb, 10gb for / and 8 for swap and I have 92gb sitting unallocated at the end.  How can I move linux to that unallocated partition?  I wouldn't mind rearranging things so that my 'os disk' (windows7) was using 400gb and the rest for linux.

Any help on how I can do this without formatting or erasing what I have now?



[Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php") can be use to manage windows Partitons. Just don't use Gparted from Ubuntu installation. 

Linux can read and write to NTFS Partitions. So in this sense you have plenty of space to save your data. 

Q. Did you loose any important Data? Do you need to rescue data?


18 gb of / partition is more than enough. I use 15gb for /.

If you have GParted installed in the Ubuntu then create a partition and format it to ext4.
If you don't have it then run this in Terminal: *sudo apt-get install gparted*

 This will create for you a Linux Partition, /dev/sda7 which you can use to store Data. Except that you will have to manually mount it every time you wish to use it. Or you can make it to auto-mount at the system start. This will also be very helpful as opposed to /home when you reinstall or upgrade to a newer versions. If anything goes amiss you don't have worry about losing your data. Also since upgrades to next version from Update Manager cause frequent problems having a separate Linux partition for Data makes much sense and paves way for fresh, clean installation each time you want to upgrade to a newer version.

To save your data directly to this data partition you have to set the save path from any application to this Partition or /dev/sda7. For instance, to save a Libreoffice documents to this partition you have set save path in LibreOffice. Just remember that you will have to keep this partition mounted when you are saving to it. (There is another way to do this using Binding, which mirrors back the files from Home directory to this data partition). If you like the idea, my strong recommendation is that you go for this kind of setup.

---

### Post by 450rOOST on 2011-12-10
fantab, right on, that sounds more like what I want to do.  Just a quick question, are you viewing this on a phone or something?  In the first post I have an image diplayed of my current partition layout and you should see that I'm using gparted.  I just want to know, cause if you can see the image, you might be able to help me better.  Here is another one.

I only have 10gb for / and 8gb for swap.  I am going to format the unallocated 92gb at the end to ext4, created as primary partition, aligned to MiB, is this correct?

Thanks a ton for the help!

---

### Post by 450rOOST on 2011-12-10
I went ahead and did it, this is what I ended up with.

---

### Post by fantab on 2011-12-10
> **450rOOST said:**
> I went ahead and did it, this is what I ended up with.

Yes it looks OK. You have created a Primary Partiton /dev/sda2, I thought you would create a Logical Partition, /dev/sda7. Not that it matters functionally but your Partition Scheme looks messy. 

Also you Don't have Windows D:, which IMO is a must. A small partition of about 25GB for C: and rest for D: - Primary - NTFS for DATA. This Partition you can SHARE between Windows and Linux. And your present /dev/sda2 exclusively for Linux. A separate C: with only Windows installation files will be safer.

I Also Dual Boot with Windows and this is how my partition Scheme looks like on 500GB HDD:

/dev/sda1 - Win7 C: - 25GB - Primary
/dev/sda2 - NTFS D: - 75GB - Primary
/dev/sda3- / ext4 - 15GB - Primary
/dev/sda4- Extended - 348GB approx.
/dev/sda5- ext4 - 344GB approx. - Logical
/dev/sda6- SWAP 4GB - Logical

Logical Partitions always take the Partition number from 5 onwards like, /dev/sda5 so if you make your fourth partition as Extended then logical partitions seem follow natural numbering. IMO the Partition Scheme looks neat. That is all.

NO, I didn't see that you were using Gparted.

To use BINDING see this[** thread**]("http://ubuntuforums.org/showthread.php?t=1859940"), especially posts [**#3**]("http://ubuntuforums.org/showpost.php?p=11342154&postcount=3") and [**#9**]("http://ubuntuforums.org/showpost.php?p=11342785&postcount=9") by **WorMZy**.

---

