---
title: "Before I re-install .............."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by bolex100 on 2008-09-19
Dell 1525 laptop 10 days old.  I've apparently done something dumb in my quest to get my head around it, because it has slowed to a crawl.  3-4 mins to boot.  15 seconds to open a file window!

So before I give up and start over, one basic clarification.  Is my understanding correct on this basic point? 
Unlike windows, Ubuntu has no registry and all program data is stored in the program folder.  So, installing a program does not affect the speed of the system if its not running.

correct me if I'm wrong.

---

### Post by Delirium_Trigger on 2008-09-19
"Registry" is more a Windows term than anything else.
Ubuntu does have the gconfig-editor however.
So you could say that is the registry.
And it doesn't affect performance at all to the best of my knowledge.

As far as installing a program affecting speed, it all depends on the speed of your hard drive and how full it is.

Hope this helps.

---

### Post by Titan8990 on 2008-09-19
> Unlike windows, Ubuntu has no registry and all program data is stored in the program folder. So, installing a program does not affect the speed of the system if its not running.

correct me if I'm wrong.

This is somewhat correct. I would not say that adding things to the registry alter the speed of a Windows machine. People that sell registry cleaners just want you to believe as so.

---

### Post by Delirium_Trigger on 2008-09-19
> **Titan8990 said:**
> This is somewhat correct. I would not say that adding things to the registry alter the speed of a Windows machine. People that sell registry cleaners just want you to believe as so.

Ah okay, I was sure that the registry being bogged down wouldn't hinder performance.

---

### Post by anotherdisciple on 2008-09-19
How long have you been using Ubuntu? How long has it been slow?
What are the specs of your computer?

---

### Post by bolex100 on 2008-09-19
Dell inspiron 2Ghz Celeron.  Anyway done deal. Ubuntu is back in.  Trying to figure out the webcam now.

---

### Post by Elfy on 2008-09-19
Have a look in your logs - system >admin >system logs - messages and see if you can find anything that fails.

If you can't find anything - you could boot in recovery mode and watch the screen for where the boot slows down or install bootchart and it will produce a chart which shouls show the bottleneck

```
sudo apt-get install bootchart
```

The chart will be in /var/log/bootchart

Edit- next time then :)

---

