---
title: "How to make a RW CD"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by s1baker on 2011-10-03
hi,
can Unubtu make a RW CD?
Windows has a feature where one can take a RW CD and make it to where you can make directories on the CD and add or delete files on the fly, much like on a HD. I haven't found anything like that on Ubuntu yet. I can 'burn' files to a RW CD, but if I want to add only 1 file to a directory on that CD, I have to blank the CD and burn the CD all over.

---

### Post by mibart on 2011-10-03
I think that wodim can do what You demand, but I am not sure how exactly call it to do so. See manual (man wodim).

Anyway, what is the reason for use CD-RW disc nowadays? CD-Rs are cheap as chips.

---

### Post by spiky001 on 2011-10-03
I remember doing this a while ago on windows. Can it be done with nero?? there is a download here [http://www.brothersoft.com/nero-for-linux-59627.html](http://www.brothersoft.com/nero-for-linux-59627.html)

---

### Post by s1baker on 2011-10-03
I have another linux box that doesn't have an internet connection.
I want to be able to download music periodically from my box that does have an internet connection so that I can play the CD on my box that doesn't have internet. I don't want to have to go and select out hundreds of music files and directories from the internet box so that I can burn just one file that I want to add to that CD. 
Besides, as often as I do this, if I used only a R CD, I have have a pile of CD's a foot high before I knew it.

---

### Post by haqking on 2011-10-03
I think brasero and k3b support drag and drop and erasable on a cd rw ? i think.

thing is nowadays it is easier to have a 4 or 8GB USB key.

I havent bought a CDRW in years

---

### Post by spiky001 on 2011-10-03
You could network the boxes

---

### Post by jonnyboysmithy on 2011-10-03
You could just get yourself a flash drive.

---

### Post by s1baker on 2011-10-03
I have a old 2.0 USB that I have had for ages that I used on Windows XP.
It has a 2 Gig SD disk in it now that is formatted fat32 ( that I need to leave formatted fat32 ). I can use it now, in a roundabout way, to copy Linux files to the VirtualBox shared folder, and then run Windows XP in VirtualBox and copy files to the SD disk that is formatted fat32. I can then move that SD disk to the other Linux box that doesn't have an internet connection and read/write/delete those files, as Linux can read fat32. Lot of trouble though.

I have an extra 1/2 Gig SD disk that I am not using though.

Question:
Can I set that 1/2 gig SD disk to be formatted just for linux so that I could use it to transfer files back and forth between the two boxes? ( the other box is puppy 5.2.8 ). Would the SD disk in Linux work like the fat32 SD disk?

---

### Post by jonnyboysmithy on 2011-10-03
If you mean SD as in SD memory card, then yes of course you can use it with linux!
Ubuntu will take fat32 format and a whole range of other formats and if it doesn't than there's probably a package out there that will make sure you can use it.

---

### Post by s1baker on 2011-10-03
I found I had another 2 gig SD card and I formatted that card as ext4 using Ubuntu ( 10.10 32bit Maverick ).
But when I tried to copy files back and forth to my Puppy 5.2.8 box using that SD card, I got errors. Some text files that I tried to open in Puppy were completely blank. I formatted the SD card in Ubuntu as fat32 and I was able to get the transfer of files back and forth ok. I wonder what's up with that. It's funny that two latest versions of Linux in different boxes ( Ubuntu 10.10 and Puppy 5.2.8 ) have problems with the same latest Linux format ( ext4 )

Also, I tried to put the fat32 SD card that I formatted with Ubuntu in my old Win98 box and Win98 did not recognise it. 

Anyway, goodbye CD's, hello SD's from now on.

---

### Post by mcduck on 2011-10-04
What you are looking for is called **packet writing** (as opposed to normal CD writing modes that either write the whole disc at once or larger data sessions that need to be closed before the disc is compatible with most systems).

Ubuntu doesn't include packet writing support by default, probably because such discs even at their best have compatibility issues compared to normal CD's, but here's a thread about it that might help: [http://ubuntuforums.org/showthread.php?t=129093]("http://ubuntuforums.org/showthread.php?t=129093")

---

