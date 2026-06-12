---
title: "How to View attached Windows 8.1 HDD files?"
date: 2015-03-21
forum: New to Ubuntu
---

### Post by jordan40 on 2015-03-21
Okay so this should be simple but I can't seem to access my secondary HD that has windows 8.1 installed, I want to view the files etc 

but it has bad sectors and can no longer boot so cant simply use flash memory to transport files. The faulty HD can be hooked up to the 

computer, but Ubuntu doesn't even recognize a new drive being connected...

Ideas?

---

### Post by yancek on 2015-03-21
Check the BIOS to see if it is recognized there.  If it is not, then it won't be recognized by the operating system.  Did you try to manually mount the partition(s)?

---

### Post by Mark Phelps on 2015-03-21
Windows 8.1 automatically "hibernates" when you shut it down -- unless you specifically went to the trouble to disable FastStartup -- which is NOT the same as Fast Boot.  If the partitions are hibernated, Linux will not be able to mount them.

---

### Post by jordan40 on 2015-03-21
> **yancek said:**
> Check the BIOS to see if it is recognized there.  If it is not, then it won't be recognized by the operating system.  Did you try to manually mount the partition(s)?

yes the bios does recognize it but ubuntu wont read it

would I be able to mount it on another computer running windows?

Ubuntu finds it under the devices app, but there is no way to open it to view files (that I am aware of).

---

### Post by Vladlenin5000 on 2015-03-22
> **jordan40 said:**
> Ubuntu finds it under the devices app, but there is no way to open it to view files (that I am aware of).

Read post #3 again.

---

### Post by Mark Phelps on 2015-03-22
> **jordan40 said:**
> would I be able to mount it on another computer running windows?

If the other computer is also running Win8 or Win8.1 -- maybe. But, you would only be able to open the partition in Windows, not in Linux.

If you then disabled FastStartup in the other Win8 PC, and did "shut down", that should prevent hibernation from kicking in and then, you should be able to mount the partitions back in the original PC.

Also, you might be able to mount the partitions read-only in the original PC.

---

