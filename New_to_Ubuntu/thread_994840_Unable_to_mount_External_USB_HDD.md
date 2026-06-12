---
title: "Unable to mount External USB HDD"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Naomi-Chan on 2008-11-27
[COLOR="Magenta"]I am trying to mount my External USB HDD to my Desktop and every time I try, i get an error. (See picture)

How do I mount my drive so I can backup all my information and wipe the drive?

Ugh, I can't Upload the Picture... I will add it once I get home from school... But could someone help me out? I'm really new to this and suck at programming... And I can't google worth a damn.[/COLOR]

---

### Post by overdrank on 2008-11-27
> **Naomi-Chan said:**
> I am trying to mount my External USB HDD to my Desktop and every time I try, i get an error. (See picture)

How do I mount my drive so I can backup all my information and wipe the drive?

Ugh, I can't Upload the Picture... I will add it once I get home from school... But could someone help me out? I'm really new to this and suck at programming... And I can't google worth a damn.

Hi and welcome, please do not use that color as it is hard on the eyes :)
Can you post the text of the error and what version of Ubuntu are you using.

---

### Post by rlzyoner on 2008-11-27
As overdrank asked, we will need the error to assist but its probably just tha the device was not safely unmounted / removed from a previous machine.
You should try mounting manually from the command line

---

### Post by vanadium on 2008-11-27
I agree with the assumption of rlzyoner, but not with his solution.

If the assumption is correct (you will need to confirm that), then you can solve the issue by connecting the drive to an MS Windows system. Preferably have the drive checked using the Windows tools, then use the "Safely remove hardware" icon or shut dwon Windows completely. After that, the drive should mount automatically when you connect it in ubuntu.

If you do not have Windows, then you can use the "ntfsfix" command line tool to "fix" the drive and have it automount. You should consider reformatting the drive to ext3 or fat32, though, if you do not have Windows.

This all in the assumption that the drive is ntfs formatted and has not been safely unmounted at one time.

---

### Post by Naomi-Chan on 2008-11-27
I don't want to format the drive, as it is a 40G HDD and it is full of programs and other things I need. I hastily installed Ubuntu on my Desktop because I was fed-up with windows. When I get home from school, I will put the error I get... the only thing is, I can't copy the text in the window, for some reason... so I took a screenshot. [[IMG]http://img148.imageshack.us/img148/9827/screenshotuu6.th.png[/IMG]](http://img148.imageshack.us/my.php?image=screenshotuu6.png)

I did what it said and no work...

The second option confuses me.,.. I'm not sure how to make the coding stuff work.

---

