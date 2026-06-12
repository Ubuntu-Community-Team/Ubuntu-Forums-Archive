---
title: "Device driver debugging - where am I going wrong?"
date: 2008-03-11
forum: Programming Talk
---

### Post by Mr StevieP on 2008-03-11
Hi, 

I am trying to get going with some device driver stuff. 

Basically, I can not find my debug messages from my module in any of the files in /var/log, i.e. my KERN_ALERT and KERN_INFO messages are not there. If I run dmesg then I can see them. However, this is not ideal, as I would like to be able to do something like tail -f /var/log/messgaes to be able to observe my modules behavior. Can anyone point me in the right direction for making this happen? I am running Ubuntu 7.10, the dell version for inspiron 1525 if that makes any difference. 

I am still relativly new to writing stuff for linux, so I appreciate this will probably a really silly question. That said, if anyone can give me some general pointers / items to read about getting setup for linux programming and stuff about where system messages are posted, I would be very greatful. 

Thanks

Steve

BTW, does anyone use an IDE for kernel module devel? If so which is it and do you like it? More importantly, is it realtivly simple to get going? I was thinking about maybe using eclispe? Any thoughts?

---

### Post by wblancqu on 2008-03-11
Try using:

```
tail -f | dmesg
```

Or when you want to follow something in particular (e.g. for fglrx driver):

```
tail -f | dmesg | grep fglrx
```

Grtz

---

### Post by wblancqu on 2008-03-11
If I'm not wrong, kernel modules are written in C, so yes you can use eclipse with the CDT plugin. You can also try Anjuta, but haven't use that one before.

Good luck!

---

### Post by Mr StevieP on 2008-03-11
Thanks for the reply, 

I tried 

```
tail -f | dmesg
```

but it doesnt update. I.e. it runs dmesg once, and then sits there waiting...

---

### Post by WW on 2008-03-11
> **Mr StevieP said:**
> Thanks for the reply, 

I tried 

```
tail -f | dmesg
```

but it doesnt update. I.e. it runs dmesg once, and then sits there waiting...

That command doesn't look right.  Why feed the output of tail (with no argument, only the -f option)  *into* dmesg?  Try this:
```
tail -f /var/log/dmesg
```

---

### Post by Mr StevieP on 2008-03-11
> **WW said:**
>   Try this:
```
tail -f /var/log/dmesg
```

Thanks for the reply. That doesnt work either. It seems that the kernel messages just arent going into any of these files. But if I run dmesg I see them with no problem.....weird!

---

### Post by wblancqu on 2008-03-11
Indeed you're right tail -f with a pipe doesn't sound logic. Normally you should be able to follow output like you said by using tail -f /var/log/messages, strange that doesn't work, I'll try it tonight on my ubuntu box.

Grtz

---

### Post by Mr StevieP on 2008-03-12
Any luck?

---

### Post by Mr StevieP on 2008-03-12
got it. my printk debug level was not high enough. echo 8 > /proc/sys/kernel/printk sorted it out!

---

