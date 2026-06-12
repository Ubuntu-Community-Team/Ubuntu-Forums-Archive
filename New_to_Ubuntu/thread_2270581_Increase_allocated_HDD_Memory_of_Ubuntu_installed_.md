---
title: "Increase allocated HDD Memory of Ubuntu installed within Windows"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by Nachiketkumar on 2015-03-24
Hello I am new to Ubuntu , I installed Ubuntu 14.04 LTS inside Windows 7 by mounting image.
At the time of installation I allocated 11Gb of Memory for Ubuntu  
but after installation of many software I feel like bottleneck and want to increase the memory allocation.
Is there a way to increase the memory now.

---

### Post by dino99 on 2015-03-24
i've no clue about mounting an other OS 'inside' Windows; but why not using virtualbox or similar app ?
i suppose that starting from scrash again is the best solution.

---

### Post by Bucky Ball on 2015-03-24
You have created a Wubi install (Ubuntu inside Windows). Although Wubi is available on some install media, it hasn't been supported in some time and you are unlikely to get much support for it (namely because hardly anyone uses it and hasn't for awhile).

I suggest you install Ubuntu to its own partition using a supported release and have a look [here]("http://ubuntuforums.org/showthread.php?t=2229766"). Wubi was only ever intended to try Ubuntu, not as a permanent solution (and you can try Ubuntu directly of the install media anyhow). Good luck.

---

### Post by Nachiketkumar on 2015-03-24
Thanks after searching a bit more I found solution [here  ]("http://askubuntu.com/questions/118300/increase-size-of-root-partition-after-installing-ubuntu-in-windows")and [here]("http://ubuntuforums.org/showthread.php?t=1625371&highlight=resize2fs%20wubi") will try the same now.

---

### Post by Mark Phelps on 2015-03-25
> Thanks after searching a bit more I found solution here and here will try the same now. 

Those are two entirely different solutions for entirely different problems. You need to determine which one is the correct one for you.

If you installed from inside Windows, you used WUBI -- and a quick way to confirm that is to look for a file "root.disk" inside the Windows filesystem partition in which you did the installation.  IF that file is there, it's a WUBI setup and only the second solution will work, as there is no Linux filesystem partition created with that particular kind of install.  And, as others have indicated, WUBI is not supported anymore -- it was dropped back in the Ubuntu 12.x days.

Also, it's not HDD "memory"; instead, it's HDD "disk space".

---

### Post by Nachiketkumar on 2015-03-25
yes it was WUBI and second solution worked I have new root.disk with more memory. Thanks

---

### Post by Mark Phelps on 2015-03-25
> with more memoryIt's not "memory"; it's "disk space".

---

