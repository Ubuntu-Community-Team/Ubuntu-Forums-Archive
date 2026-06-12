---
title: "Boot ubuntu to RAM and Run from RAM"
date: 2017-10-18
forum: New to Ubuntu
---

### Post by ismewor on 2017-10-18
[FONT=Ubuntu]Hi All,[/FONT]
[FONT=Ubuntu]I did a search and couldn’t find any info except on Live CD.
I would like to boot the entire ubuntu (with 2 program) to RAM and Run from there.[/FONT]
[FONT=Ubuntu]Thanks,
Sam[/FONT]

---

### Post by deadflowr on 2017-10-18
Rather old now, but maybe it will give you some insights:
[https://ubuntuforums.org/showthread.php?t=1594694]("https://ubuntuforums.org/showthread.php?t=1594694")

---

### Post by Autodave on 2017-10-18
While not as fast, have you considered an SSD? That is what I use: a 60 GB ($40 on Amazon) to keep the OS and programs on, and a conventional HD to keep music, photos, documents, etc on. Very fast compared to a spinning HD.

---

### Post by HermanAB on 2017-10-18
Howdy,

Note that loading a bunch of files into a RAM disk, which will seldom or never execute, will only clog up your RAM and will not buy you any speed - it may even make your system slower.  Therefore some careful thought is required about what you actually want to happen and why.

For a program to run, it needs to be copied from disk to RAM.  This happens only once.  The program will stay in RAM, until the kernel is convinced that it will not be used again and there is a shortage of RAM.  The kernel manages the loading and unloading of programs very efficiently.  The system also has swap, which should be on HDD - using RAM for swap will defeat the whole idea behind swap.

Therefore the trick to speeding up your system is to put only the parts you really need to be fast into a RAM disk - which is typically your data files, since the programs are already managed properly.  If you want a program to appear to load 'instantly', load it once after startup - when you need it, it will be ready in no time.

Also note that the tmpfs is a RAM Disk.  Therefore, you could easily make a RAM disk and load whatever you want in there, or you can simply configure your programs to use /tmp (which is a RAM disk) for working data and only copy the final data to HDD.

If you want your system to start up instantly, then don't shut it down!  Use Suspend.

---

### Post by ismewor on 2017-10-19
> **deadflowr said:**
> Rather old now, but maybe it will give you some insights:
[https://ubuntuforums.org/showthread.php?t=1594694](https://ubuntuforums.org/showthread.php?t=1594694)

Thanks, i gone through the post, and it is beyond my skill to create such, and the author hasn't post for so long.
Yes, this is exactly what i'm looking for.

---

### Post by ismewor on 2017-10-19
Thanks Herman for suggestion. However i'm looking into loading the entire Ubuntu and 2 programs to RAM. And this is all and only that i need.

---

### Post by HermanAB on 2017-10-20
So, make a RAM disk with tmpfs and copy everything there, then do a chroot.

---

### Post by ismewor on 2017-10-24
Herman,

Thanks for the suggestion, can you give me an instruction to do such? 

Thanks,
ismewor

---

### Post by HermanAB on 2017-10-25
Nope, to give instructions on that, I would have to do it myself and I already know that it is not a good idea...

Read up of chroot for starters.

---

