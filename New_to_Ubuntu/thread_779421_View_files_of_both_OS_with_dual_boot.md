---
title: "View files of both OS with dual boot"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by kilrizzy on 2008-05-02
Is it possible to view my windows files while running ubuntu as well as the other way around?

---

### Post by Joeb454 on 2008-05-02
Simple answer: Yes :)

Your Windows drive should be under "Places" in Ubuntu, next to Applications.

And for Windows you'll need a driver. Just google ext3 driver for Windows

---

### Post by Tatty on 2008-05-02
Yes.  If you are using Gutsy or Hardy then you can view your windows files already.  Simply mount your windows partition (right click it in nautilus and selet mount, if it isnt already), then browse.

If you are using an earlier version of ubuntu then you will need to install th ntfs3g driver.

If you want to browse your ubuntu file in windows then you need to install an ext2 driver in windows [http://www.fs-driver.org/](http://www.fs-driver.org/).  Iit will work with both ext2 and ext3.

---

### Post by TeoBigusGeekus on 2008-05-02
Assuming that ubuntu is on ext3 and window$ on ntfs:

1)Win files from ubuntu
From Places->Computer you should see your window$ partition and navigate in it. 
If you want it to be mounted on startup:
Install ntfs-3g and ntfs-config through Synaptic. Go to Applications->System Tools->Ntfs configuration, choose your win volume/partition and check all boxes.

2)Ubuntu files from win
Install ifs driver
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
in window$ and you are done.

---

### Post by kilrizzy on 2008-05-02
Thank you everyone for your quick help, neither of the solutions worked for me. It may be because I used wubi to install, im not sure how it sets the partitions up? When I look at my partitions I only have my C drive and an empty 16mb dell one. When I go to my computer in Ubuntu I only have my cdrom drive and the 'my files drive' (forget what its called, in windows right now)

---

### Post by kilrizzy on 2008-05-02
Just did some reading up on it. I think I will do this - [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

to upgrade it to its own partition so the above steps will probably work for me then...that also explains why I wasnt able to put my comp into hibernation :) thanks all

---

### Post by dartdog on 2008-05-02
I see that kilrizzy has chosen to do a partition thing. 

I'd like to be able to access the NTFS partition on my "C" drive without doing as she says, 

I used the Wubi install and the file/computer browser does not show the NTFS system on "C" at all. I do see my other pysical drives and they seem to mount and show files. How can I find the rest of my NTFS formatted "C" drive?

---

### Post by kilrizzy on 2008-05-02
I was able to find this:

```

Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.

```

Although I didnt find anything from the other way around. It gets installed as a program but I couldnt find the folder.

---

### Post by Joeb454 on 2008-05-02
I'm not sure exactly how Ubuntu would see the Windows C:\ Drive, as Ubuntu is basically installed in a big file/folder on that drive.

I guess this could be filed as a bug with the Wubi developers, but I don't imagine it would be easy to fix either

---

### Post by dartdog on 2008-05-02
That is it!!!
When I went to my File system, I found the Host file and it was the rest of my "c" drive, now I have to figure out how to use it all and save the right stuff as my favorite places...(or what ever it is I do to make it convenient!!!

---

