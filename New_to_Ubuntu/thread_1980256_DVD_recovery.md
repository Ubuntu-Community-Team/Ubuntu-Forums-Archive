---
title: "DVD recovery"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by mlempenau on 2012-05-14
I have a DVD that will mount and even play but I can't copy it or make an iso image.  I downloaded Dares from the s/w repository but when I search for info on how to use it I get nothing.  I'm probably not using the correct word to search.  

If someone knows a good program to use ...

If someone knows where to find instructions on using Dares ...

I would be most grateful.  Thanks,  Mike

---

### Post by matt_symes on 2012-05-15
Hi

There are a load of applications that can rip DVD's.

Here is a link

[http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html](http://www.cyberciti.biz/tips/linux-dvd-ripper-software.html)

From the man page for dares.

> NAME
       dares - rescue files from damaged CDs and DVDs

Is this what you really want though ? Anyway the man page ...

[http://manpages.ubuntu.com/manpages/lucid/man1/dares.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/dares.1.html)

You can also use the dd command.

```
dd if=/dev/dvd of=/path/to/dvd.iso
```

You may need to change the /dev/dvd parameter above as on my install it's called dvd1. You can do this with

```
ls -l /dev/dvd*
```

Here is mine as an example.

```
matthew@matthew-Aspire-7540 ~/my_documents/my_logons
 % ls /dev/dvd* -l
lrwxrwxrwx 1 root root 3 May 15 12:53 /dev/dvd1 -> sr0
lrwxrwxrwx 1 root root 3 May 15 12:53 /dev/dvdrw1 -> sr0
matthew@matthew-Aspire-7540 ~/my_documents/my_logons
 % 
```

Kind regards

---

### Post by mlempenau on 2012-05-17
Thank you for your help.  You gave me several things to consider and I'm grateful.  But I only have so much time :( so  it will take a few days to get through this.  I'll post what worked  when I have time.  Thanks so much.

---

