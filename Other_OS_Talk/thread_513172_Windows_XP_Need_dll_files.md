---
title: "Windows XP Need dll files"
date: 2007-07-30
forum: Other OS Talk
---

### Post by Programmerer on 2007-07-30
I have Ubuntu and Windows, and after beeing on Ubuntu for some months I had to do something on Windows.
But before boot up gets I a message in Norwegian, my language: "Load trenger DLLer for kjernen", and means something like this: "Load needs DLLs for the kernel/core" Any suggestions for whats dll-files I need?

Please help, because I need Windows for some programs that can't be run in WINE.

---

### Post by Hallvor on 2007-07-30
Why am I not surprised that the Windows error message makes no sense...? I`ve never seen one that *does* make sense.

---

### Post by margni on 2007-07-30
Sounds like your  Windows partition is corrupted...  You can try a repair...

[http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx)

If this repair works, then be careful that this doesn't wreck (and that doesn't mean wreck, it means overwrite) your MBR, where Grub is residing...   There are several articles here in the forum on repairing your Grub file...

If it were me,  I'd make sure I'd had all my Ubuntu-side files/data backed up completely (and tested to make sure they worked) before I tried this...

Second, If you have a second computer so you can use the forum/google/etc it would be a plus...

I'm sure there are others here in the forum with much better ideas and answers than mine, but you're ultimately going to have to repair your XP partition if you need it...

---

### Post by darksong on 2007-07-30
> **Hallvor said:**
> Why am I not surprised that the Windows error message makes no sense...? I`ve never seen one that *does* make sense.

nor have i ever seen a linux one that makes sence!

if you ever find out the problem or what dll's you need - here is a good site for them [http://www.dll-files.com/](http://www.dll-files.com/)

---

### Post by Programmerer on 2007-07-30
> **margni said:**
> Sounds like your  Windows partition is corrupted...  You can try a repair...

[http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx](http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/doug92.mspx)

If this repair works, then be careful that this doesn't wreck (and that doesn't mean wreck, it means overwrite) your MBR, where Grub is residing...   There are several articles here in the forum on repairing your Grub file...

If it were me,  I'd make sure I'd had all my Ubuntu-side files/data backed up completely (and tested to make sure they worked) before I tried this...

Second, If you have a second computer so you can use the forum/google/etc it would be a plus...

I'm sure there are others here in the forum with much better ideas and answers than mine, but you're ultimately going to have to repair your XP partition if you need it...

Thanks, I'm gonna try that, but does this delete any files one my Windows partition?

Thanks for your link darksong.
> 
[http://www.dll-files.com/](http://www.dll-files.com/)

---

### Post by darksong on 2007-07-30
no problem :KS

---

### Post by smoker on 2007-07-30
> **Programmerer said:**
> Thanks, I'm gonna try that, but does this delete any files one my Windows partition?

a repair shouldn't delete your data files or programmes, but it is always wise to have crucial data backed up!

---

### Post by Hallvor on 2007-07-30
> **darksong said:**
> nor have i ever seen a linux one that makes sence!

OK. Have actually had a cople with good tips on how to solve the problem in Ubuntu. That is my experience anyway.

---

### Post by xpod on 2007-07-30
Hows about  a simple.....start>run
```
sfc /scannow
```

It`s it`s missing system files(dll`s) that should replace them as long as you have the XP cd or at least a copy of the i386 directory you can direct it towards.

---

### Post by darksong on 2007-07-30
even though i don't have a problem with windows install, thanks for that - im sure it will come in handy somewhen :D

---

### Post by xpod on 2007-07-31
> even though i don't have a problem with windows install, thanks for that - im sure it will come in handy somewhen

It never ceased to amaze me how quickly even a fresh install of XP would end up missing systems files....:)

I used to run that thing at various stages after installing an XP and it would never be long before it was...
>  "XP requires missing system files...please insert you XP cd"

---

### Post by Programmerer on 2007-07-31
> **xpod said:**
> Hows about  a simple.....start>run
```
sfc /scannow
```

It`s it`s missing system files(dll`s) that should replace them as long as you have the XP cd or at least a copy of the i386 directory you can direct it towards.

But since I can't boot up Windows then I can't do a start>run :(

---

### Post by xpod on 2007-07-31
> But since I can't boot up Windows then I can't do a start>run

Not even in safe mode??
What about the other suggestions??

I`d have re-installed by now i think and the problem would have been but a distant memory:)

---

### Post by holihue on 2007-10-21
...A new reason to switch to Ubuntu.:)

If you really need Windows you should take backup of files in your partition, and format it.
And then reinstall Windows.

---

