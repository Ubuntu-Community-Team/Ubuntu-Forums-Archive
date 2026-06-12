---
title: "Will my data be formatted when the system crashes ?"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by quecoder on 2008-10-16
Hello ,  because linux file system is not like windows one that has drives where I can install windows in one drive and my important data on the others , so when I format and reinstall windows, I just format the first and the remainders will be untouched  ....

I was wondering if my data ( mp3s , movies ..etc ) in ubuntu or linux generally  will be formatted if the system has crashed or because I messed with system files accidentally and unable to log in .. When I have only ubuntu on my system  , and tried to reinstall it 


Any ideas?

---

### Post by Commander_Keen on 2008-10-16
If you PC just crashes and you do a Hard boot ( turning yoru PC off and then back on) then the answer is no, You will not lose your data (Mp3, Jpgs) Doc's a differeent, If you were in the middle of writing a document, and restarted your pc, you will lose the document (if you did not save).
  Now if you are re-installing hte OS, durrign the install there is a tab that states to use the entire HD.  If you enable this tab, you will lose all of your data.

---

### Post by hyper_ch on 2008-10-16
You have one directory from which everything else comes and that's called "root" or also represented as "/".

What you can do now, is mount any partition or another harddisk or even a harddisk on the network in any path. Normally the user directories are located in  "/home". Let's say your username is "quecoder" then you should have a directory "/home/quecoder".

What you can do now, is mount a different harddisk or partition as "/home" or even as "/home/quecoder".

You can even during the installation say, that the "/" directory shall be harddisk1 and and that harddisk2 shall be mounted as "/home" AND that harddisk2 shall not be formatted.

Have a read here on how to make a seperate home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by philinux on 2008-10-16
> **hyper_ch said:**
> Have a read here on how to make a seperate home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

+1 for a separate home partition. Easy reinstall.

---

### Post by jerome1232 on 2008-10-16
Actually Linux is much better at moving things to seperate partitions than windows is.

If you want to keep your personal data seperate from the system just put your /home on a separate partition.

Personaly I would go with something more complex in your case (haveing a totally seperate data partition shared by both os's.

Now this is how I would do it in your case actually

```

/dev/sda1  /media/windows 30GB              NTFS
/dev/sda2  /mnt/data      Remaining space   NTFS
/dev/sda3  EXTENDED
    /dev/sda5  /          12GB              EXT3
    /dev/sda6  swap       1GB               swap
```

Then create symlinks in you ~/ to the appropriate locations in /mnt/data (like make a Music symnlink that points to /mnt/data/My\ Music or whatever it is you have in there)

---

### Post by LowSky on 2008-10-16
> **quecoder said:**
> Hello ,  because linux file system is not like windows one that has drives where I can install windows in one drive and my important data on the others , so when I format and reinstall windows, I just format the first and the remainders will be untouched 

You can do the same on LINUX. Windows uses Drive letters like C and D as a way to easily denote a pathway to a portion of data being an entire a Hard Drive or a part of one, While linux designate everything as a single pathway from the file system but that pathway can invovle multiple dirves or partitions. Windows and Linux have the ability to install without formating anytihng, saving all your data to where you had it. Both can also format the entire drive and you can start fresh.

---

### Post by quecoder on 2008-10-16
Wow , thank you guys , that was a perfect explaination ... :)

---

### Post by Sarmacid on 2008-10-16
If you messed with system files and can't get in Ubuntu, you can always use a live cd to recover the data before you format.

---

