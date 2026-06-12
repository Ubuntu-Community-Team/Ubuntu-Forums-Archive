---
title: "Strange - Filesystem is &quot;unknown volume&quot;?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by pablolie on 2008-06-20
I am surprised by the fact that main hard drive in my system, aka "Filesystem", shows "unknown" for volume information when I click on its properties. Consequently, properties also does not show the graphic representation of drive usage (see attached image, Filesystem is to the right, the other drive shows perfectly). 

Thus far, this is rather cosmetic, the system works like a charm!

Anyone know how to make Filsystem show up with the volume info and utilization pie chart?

---

### Post by newwork1 on 2008-06-20
You are really something

---

### Post by pablolie on 2008-06-20
> **newwork1 said:**
> You are really something

What do you mean?

---

### Post by pablolie on 2008-06-20
> **newwork1 said:**
> You are really something

Never mind. You obviously are nothing.

---

### Post by cariboo on 2008-06-20
I don't think it really means anything as the volume has no name it is just mounted as /

Jim

---

### Post by ad_267 on 2008-06-21
Hmm I've never noticed that before. For better info on your file systems go to System - Administration - System Monitor and go to the File Systems Tab. Under Applications - Accessories there's also a handy Disk Usage Analyzer.

I have a drive mounted at /home and windows partition at /windows. These don't even show up at all under "computer:///"

And yes that person who replied first obviously is nothing, only one post. Sad that they replied before anyone else though.

---

### Post by pablolie on 2008-06-21
> **ad_267 said:**
> Hmm I've never noticed that before. For better info on your file systems go to System - Administration - System Monitor and go to the File Systems Tab. Under Applications - Accessories there's also a handy Disk Usage Analyzer.

I have a drive mounted at /home and windows partition at /windows. These don't even show up at all under "computer:///"


Thanks a lot. Attached the results from System Info, looks OK to me based on other threads that analyze such output. I still find it odd the *other* volume shows the pie chart info shows the pie chart, and the main volume doesn't, but it seems I have nothing to worry about.

Thanks!

---

### Post by ad_267 on 2008-06-21
> **pablolie said:**
> Thanks a lot. Attached the results from System Info, looks OK to me based on other threads that analyze such output. I still find it odd the *other* volume shows the pie chart info shows the pie chart, and the main volume doesn't, but it seems I have nothing to worry about.

Thanks!

I think it's because of the way the Linux filesystem works. Your root file system doesn't necessarily have to reside all on one partition or hard drive. Like I said under / I have /windows and /home which are both on other partitions or drives and /windows uses a different file system (ntfs). It would be kind of confusing trying to give a graphical summary for this. It's a bit different when you have just one drive mounted in /media or /mnt as you know it's just one partition.

---

