---
title: "[SOLVED] Cant install gnome partition manager"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by naggis on 2008-05-03
I have just installed Hardy after using Gutsy for 3 or 4 weeks - so I am still very much a newby
When I try to install gpart I get the message that this is not possible because there may be a hardware problem or I don't have the right.
It installed ok with Gutsy - can anyone tell me what the problem is now and how to overcome it?
Thanks

---

### Post by llamakc on 2008-05-03
```

sudo apt-get install gparted

```

Try the above, and cut/paste any errors back here in this thread please.

---

### Post by naggis on 2008-05-03
Thanks llamakc
Here is the report
roger@roger-laptop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate
roger@roger-laptop:~$ 

can you make any sense of this?

---

### Post by Sef on 2008-05-03
You can also download [GParted]("http://gparted.sourceforge.net/") from its website and burn it to a disk.

---

### Post by naggis on 2008-05-03
Hi sef
If I burn gparted to a disk, how would I install it?

---

### Post by llamakc on 2008-05-03
> **naggis said:**
> Thanks llamakc
Here is the report
roger@roger-laptop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate
roger@roger-laptop:~$ 

can you make any sense of this?

When was the last time you updated your package list? And what sort of machine are you running this on?

Do this:

```

sudo apt-get update

```

and then RETRY the earlier command I suggested. Do you get the same results?

---

### Post by naggis on 2008-05-03
The system was updated about an hour ago when I installed Hardy

---

### Post by naggis on 2008-05-03
I am using an Acer aspire 5630 laptop with an Intel T5500 chip, 1Gb RAM and a 160 Gb hard disk (which needs some resizing of partitions following the Hardy install)

---

### Post by forestpixie on 2008-05-03
Check that the sources  - universe, multivers and restricted are enabled in software sources

Edit - if you download it, burn it as an iso and boot with it

---

### Post by naggis on 2008-05-03
Got it sorted!! I needed to reload in Synaptic Manager. Then gparted became available and could be loaded 
Thanks for the input folks

---

### Post by naggis on 2008-05-03
Hi forestpixie
I really want to mark this thread as solved as you suggest. But when I click on the thread tools, I get only 4 options non of which are to show the thread solved. What am I doing wrong.
The other point is that under my name on the left it indicates that I have never thanked anyone for their help. I always include this in the text - should I note it somewhere else?
Sorry if this is outside the scope of this thread
Thanks

---

### Post by forestpixie on 2008-05-03
The mark thread solved tool is broken at the moment - hope it comes back - you can edit your first post and include [Solved] in the title.

Thanks are done with the blue/gold medal thing at bottom right of each post - other than your own of course :)

---

### Post by elderbuy on 2009-03-01
Just want to say "Thanks".  An install that I did several months ago on a rarely-used machine didn't have the gparted, so your replies solved my problem, i.e. I did a Reload in Synaptic, and was then able to install it.

---

### Post by mkvnmtr on 2009-03-01
If you have downloaded gparted and burned it to a disk be sure to save it. It can be a lot of help if you have to work on you partitions on your computer. You can't use it off of the same partition you want to work on.

---

