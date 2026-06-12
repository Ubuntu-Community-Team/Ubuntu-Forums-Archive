---
title: "Problems with study material"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by awatkins1971 on 2013-04-15
Below is the course material and when enter get total 0, I am running Ubuntu inside Oracle's VMware box. Can anyone put a light what is going wrong as the material supplied by the OU states the total should be 8 etc. kevin@VAIO:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root 6 2009-10-25 14:47 cdrom ->          cdrom0
drwxr-xr-x 2 root root 4096 2009-10-25 14:47          cdrom0
lrwxrwxrwx 1 root root 7 2009-10-25 14:47 floppy ->          floppy0
drwxr-xr-x 2 root root 4096 2009-10-25 14:47          floppy0 (Some direction advice of where do I find the answer why this isn't working?) Text book? etc?

---

### Post by squakie on 2013-04-15
looking at what you posted, I can't tell where the 0 is you're talking about, nor where you think the 8 should be.  You'll need to post a lot more.  Also, don't be surprised if much if any help is forthcoming - most of us prefer not to work on someone's homework - that's what school and teachers/profs are for. ;)

---

### Post by Mark Phelps on 2013-04-15
From the Ubuntu Forums Code of Coduct (Which you agreed to in order to post here) ...

Section II - Posting Tips, When asking for technical support, part 7: 

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued. 

---

### Post by nothingspecial on 2013-04-16
> **awatkins1971 said:**
> (Some direction advice of where do I find the answer why this isn't working?) Text book? etc?

Pointing in the right direction is fine.

---

### Post by Cheesemill on 2013-04-16
You're not looking in the right directory.
If your CD is being automatically mounted correctly then it should be in the /media/cdrom0 directory, not the /media directory. What is the output of...
```
ls /media/cdrom0
```

However, there should be no reason at all that you have to use the terminal. When you insert a CD/DVD it should automatically appear in the left-hand pane of nautilus (the file manager).

I've done quite a few modules with the OU in the past, and I've never had any Linux compatibility issues. The material has all been pdf's, videos or html files so there shouldn't be a problem with accessing any of it.

---

### Post by Elfy on 2013-04-16
> **awatkins1971 said:**
> Below is the course material and when enter get total 0, I am running Ubuntu inside Oracle's VMware box. Can anyone put a light what is going wrong as the material supplied by the OU states the total should be 8 etc. kevin@VAIO:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root 6 2009-10-25 14:47 cdrom ->          cdrom0
drwxr-xr-x 2 root root 4096 2009-10-25 14:47          cdrom0
lrwxrwxrwx 1 root root 7 2009-10-25 14:47 floppy ->          floppy0
drwxr-xr-x 2 root root 4096 2009-10-25 14:47          floppy0 (Some direction advice of where do I find the answer why this isn't working?) Text book? etc?

You're certainly going to need to give people some idea what this 0 and 8 actually are. 

At the moment they are just numbers. 



(Good luck with the OU course whichever it is - I did some of those prior to going fulltime at a university.)

---

### Post by awatkins1971 on 2013-04-16
Thank you to all those who gave me positive feedback, and an idea where and why it isn't working correctly, Some parts of the code I'm picking up other bits not so, but i'm learning what bits needs to go where?

---

