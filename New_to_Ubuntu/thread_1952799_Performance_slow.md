---
title: "Performance slow"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-04-05
Hi Friends,

Iam using ubuntu, everthing is good except when i open document or excel, its taking too many time to open, while opening windows go black and then it will open.

1GB ram
Pentium 4, 3.0GHZ Processor 

Where is the problem?

---

### Post by santosh83 on 2012-04-05
> **pmohankumar said:**
> Hi Friends,

Iam using ubuntu, everthing is good except when i open document or excel, its taking too many time to open, while opening windows go black and then it will open.

1GB ram
Pentium 4, 3.0GHZ Processor 

Where is the problem?

There could be many reasons for such slow down.

One big thing you've to be aware is that when you import document files originally written with MS Office (or another program) into OpenOffice, the import process will take quite some time. It is especially slow with some .docx files I've observed.

There's nothing that can be done about this, since MS Office format is alien to all other Office programs and they must go through hoops to read/write it. MS simply don't play well in terms of standards.

If you're experiencing slowdown even while loading a blank window in OpenOffice or you're seeing overall slowness with your system, usually the most common issue is insufficient RAM. One Gb is the absolute minimum for modern Ubuntu running Unity/GNOME shell with all the bells and whistles I'd guess.

Make sure that you've also allocated a swap partition and that it's turned on. The output of command 'free' should have a row beginning 'swap' with non-zero values for 'total.'

---

### Post by pmohankumar on 2012-04-05
Hi,

Its correct.
How can i verify swap memory turned on or not?

---

### Post by santosh83 on 2012-04-05
> **pmohankumar said:**
> Hi,

Its correct.
How can i verify swap memory turned on or not?

If the command

```
$ sudo swapon -s
```

reports a device as being used for swap (i.e., it will show /dev/hda or /dev/sda etc.), then swap partition is being used.

If you did a normal Ubuntu install, then you should automatically have swap. But swap will not speed up your system if your working set exceeds available physical memory. It'll simply start thrashing and slowing down.

Swap is useful when running lots of large programs which are used **one at a time**. If too many large programs are used simultaneously, or in quick succession, then swap or not, system will slow to a crawl.

When just 1 Gb RAM available, I suggest that when you're using huge programs like OpenOffice, to close all other non-essential programs. For example if you've got Firefox with multiple tabs open, Chrome with another set of tabs, and a PDF viewer running, try closing one or more of these which aren't of immediate use, before opening OpenOffice.

---

### Post by mastablasta on 2012-04-05
1GB should be fine, but the quesiton could be the graphics card. if it has poor support the whole thing might work slow. if you are using Ubuntu try to use Unity2D instead. that should speed it all up.

---

### Post by pmohankumar on 2012-04-10
Hi Friends,

How could i increase swap memory after ubuntu installed.

---

### Post by santosh83 on 2012-04-10
> **pmohankumar said:**
> Hi Friends,

How could i increase swap memory after ubuntu installed.

If your swap partition has free space adjacent to it, you can expand it using a tool like gparted. You needn't do so from LiveCD, as you could simply turn off swap, unmount the partition, expand it, and remount it, taking to check that it's UUID still matches the one in /etc/fstab.

Alternatively create a new swap partition and add it to /etc/fstab.

---

