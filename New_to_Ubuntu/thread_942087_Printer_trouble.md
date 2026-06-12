---
title: "Printer trouble"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Delslayer on 2008-10-08
I'm having trouble getting my printer working in ubuntu for some strange reason. It worked all of last year but within the last two months it stoped printing in ubuntu.
My printer is a samsung ML-2510 series and it does in fact work with Vista, just no longer with Ubuntu. One thing I'm guessing is causing this is that, in windows anyway, there are two names for the same printer as a result of using the same model of printer at my parents house. If I pick the wrong name (ML-2510 (copy 1)) then it won't print in windows; however there are not two names in ubuntu so either this isn't the problem or for some reason it only selects the one titled copy 1.

Can anyone think of a fix for this?

---

### Post by taladan on 2008-10-08
For clarification -

Are you printing from linux to a shared printer on a windows box, or is the printer hooked directly to the linux box?  (or are we talking about a dual boot machine with Vista & Linux installed on it)

Tal

---

### Post by Delslayer on 2008-10-08
> **taladan said:**
> For clarification -

Are you printing from linux to a shared printer on a windows box, or is the printer hooked directly to the linux box?  (or are we talking about a dual boot machine with Vista & Linux installed on it)

Tal


My notebook is dual booting Vista and Hardy Heron, and the printer hooks directly up to the notebook.

---

### Post by taladan on 2008-10-08
Well, it shouldn't be pulling the drivers from vista to print, so the fact that it shows up twice in Vista shouldn't mean anything (unless you used Wubi or something weird like that)...

That said, try something like this and see what you can find out with it:

[http://theironlion.net/blog/gutsy-gibbon-meet-samsung-ml-2150/](http://theironlion.net/blog/gutsy-gibbon-meet-samsung-ml-2150/)

Tal

---

### Post by Delslayer on 2008-10-08
Well for starters thats the wrong model but I'll give that a try and see if it works.
second of all for some reason in windows the Copy is the default printer for some reason and that is the one that doesn't work, meaning the drivers aren't compatible with this printer. So if that's the first set of drivers that shows up for that printer then couldn't it be possible that it is relying on the incorrect set of drivers?
Third of all should it be the same solution for Gutsy as Hardy, I know there are a few things that differ with setting up other programs between the two.

---

### Post by Sef on 2008-10-08
> Well for starters thats the wrong model but I'll give that a try and see if it works.
second of all for some reason in windows the Copy is the default printer for some reason and that is the one that doesn't work, meaning the drivers aren't compatible with this printer. So if that's the first set of drivers that shows up for that printer then couldn't it be possible that it is relying on the incorrect set of drivers?

1) Sometimes the same drivers are used on more than one model of printer.

2) How did you set up the drivers in the first place?

---

### Post by Delslayer on 2008-10-08
> **Sef said:**
> 1) Sometimes the same drivers are used on more than one model of printer.

2) How did you set up the drivers in the first place?

I didn't. Just plugged it in when using Vista (before I got Hardy) and it got all the drivers for me. And, again, it worked perfectly with both ubuntu and Vista until I went home for the summer and had to use my parent printer of the same model.
Also the install disc is on the other side of the state, and the link provided within the first link directed me to what I can only assume was a japanese 504 error page.


EDIT--------------------------------------------

And I was right after all. All it took too fix was for me to go to modify printer at the website [http://localhost:631](http://localhost:631) under the administrator tab and sure enough it was using the (copy 1) printer rather than the standard one. all I did was change that and it works perfectly fine. thanks for the link. never would have figured that out on my own.

---

