---
title: "[SOLVED] Organization of stuff"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by fballem on 2008-05-12
Need some advice:

1. Assuming my username is fballem on my system, I have some additional resources that I would like to locate properly so that they can be easily found.

2. I have an NAS with both media (music, pictures, and video). I am thinking that the right place to mount these is under /home/fballem/music, /home/fballem/pictures/, and /home/fballem/video.

3. I have a private drive on NAS that I am thinking of mounting under /home/fballem/documents.

4. I have a second disk drive on my system that I'm thinking of putting under /mnt/drive2

I think (dangerous) that for those items in 2, they will show as subfolders of music, pictures, and video and be much easer to find. I'm hoping that they will show up in the Places menu, or at least be more easily accessible.

Any thoughts or problems that your experience would indicate?

Thanks,
Flavelle

---

### Post by Bruce M. on 2008-05-13
> **fballem said:**
> Need some advice:

1. Assuming my username is fballem on my system, I have some additional resources that I would like to locate properly so that they can be easily found.

2. I have an NAS with both media (music, pictures, and video). I am thinking that the right place to mount these is under /home/fballem/music, /home/fballem/pictures/, and /home/fballem/video.

3. I have a private drive on NAS that I am thinking of mounting under /home/fballem/documents.

4. I have a second disk drive on my system that I'm thinking of putting under /mnt/drive2

I think (dangerous) that for those items in 2, they will show as subfolders of music, pictures, and video and be much easer to find. I'm hoping that they will show up in the Places menu, or at least be more easily accessible.

Any thoughts or problems that your experience would indicate?

Thanks,
Flavelle

I'm not sure what NAS is but here's a start:

**EDIT:** OK ... I learned something, and there is no reason I can think of as to why this won't work.

> 
A NAS unit is essentially a self-contained computer connected to a network, with the sole purpose of supplying file-based data storage services to other devices on the network. The operating system and other software on the NAS unit provide the functionality of data storage, file systems, and access to files, and the management of these functionalities. The unit is not designed to carry out general-purpose computing tasks, although it may technically be possible to run other software on it. NAS units usually do not have a keyboard or display, and are controlled and configured over the network, often by connecting a browser program to their network address.

To continue:

Create the directories if they don't exist and then in "Nautilus" drag the directories to the bottom of the left panel. I use "Thunar" but it works the same. (See attached)

As you see I have two "Volumes" the 38G one is a partition on the same HD that Ubuntu is on and the 40G Volumn is my second HD. Everything below the line from BruLoo to ZIPS-Ubuntu are directories in those two Volumes. Once in Thunar (Nautilus) they will show up in "Places"

Hope this helps.
Bruce

---

### Post by Het Irv on 2008-05-13
That will work for nautilus as well.

Bruce, NAS = Network Area Storage?
At least that fits with the scenario.

---

### Post by Bruce M. on 2008-05-13
> **Het Irv said:**
> That will work for nautilus as well.

Bruce, NAS = Network Area Storage?
At least that fits with the scenario.

Hi Irv, buddy of mine....

Hahaha you wrote this as I popped in the Edit, good timing.

Have a nice day
Bruce

---

### Post by fballem on 2008-05-13
Thanks for the encouragement.

I was able to set the mount points inside my /home/fballem/ folder, and the mounted items now show up in places and on my desktop as well.

Many thanks,
Flavelle

---

