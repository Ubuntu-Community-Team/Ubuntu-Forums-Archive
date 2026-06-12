---
title: "windows problems with wubi?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by rickywear on 2008-05-06
I installed Ubuntu ( feisty fawn ) with Wubi. Everything worked fine, and then, Windows became impossible to work with. Ubuntu worked fine, no problems. When I defragged in Windows, my Ubuntu files were shown to be fragmented ( in red ). I go to school online, and I needed Windows for my classes, so I had to completely wipe off my hard drive and re-install Windows. My question is; is there a possibility that having Ubuntu installed, affected Windows, or was it just an issue with Windows? I would much rather have Ubuntu, but like I stated; I need Windows for certain classes. Thanks in advance for any help.

---

### Post by AndrewTheArt on 2008-05-06
What were the nature of the problems you were experiencing in Windows? Was anything specifically going haywire?

---

### Post by Gripp on 2008-05-06
having wubi installed is about the same as have an ISO file/image on your computer... about the only only problem it can create with windows is corrupting your files, but that is rare and is a very obvious problem (i.e. cant boot)

it may have simply been that you needed to run chkdsk on windows...

boot into windows, start>run "cmd" then "chkdsk C: /F" (then read through prompts and select 'Y' to run at boot.)

otherwise i would think it best to post your problems, and details, to the [wubi forum]("http://ubuntuforums.org/forumdisplay.php?f=234")

---

### Post by kansasnoob on 2008-05-06
Why install Feisty inside Windows with Wubi?

Wubi was my #1 itch as far as just trying Hardy (I jumped on the beta), but maybe I missed something ................ was Wubi designed to handle any Linux/Ubuntu install inside Windows?

I thought it was purely a hardy thing.

---

### Post by AndrewTheArt on 2008-05-07
No, Wubi has been available since 7.04 or 7.10 (can't remember which).

---

### Post by phr0ze on 2008-05-07
Using Wubi should not cause any problems in windows. 

What parts of windows do you need for your classes? Maybe we can help you break the chain.

---

### Post by rickywear on 2008-05-08
I have to have Windows for MathLab, nothing else will work. Now I get the news that I need MS Project for a class. This school must be owned by MS. I am new at computers ( about 1 yr. ), and after using Linux for the short time I had it, I can certainly see the difference in these two OSs. I would much rather have Ubuntu. I just saw something about MS Virtual Machine 2007,( I think ), which is a free download, to run multiple OSs. Is anyone familiar with this?

---

### Post by rickywear on 2008-05-08
> **kansasnoob said:**
> Why install Feisty inside Windows with Wubi?

Wubi was my #1 itch as far as just trying Hardy (I jumped on the beta), but maybe I missed something ................ was Wubi designed to handle any Linux/Ubuntu install inside Windows?

I thought it was purely a hardy thing.

I installed Feisty first and upgraded to Hardy. I had some problems with Hardy ( nothing major ), but I un-installed Hardy, and went back to Feisty. I think Wubi may have been for Hardy originally, but I found Feisty somewhere, I can't remember where. I used Feisty because I thought it might be more stable, and I'm not too computer savvy, at this time.

---

### Post by rickywear on 2008-05-08
> **AndrewTheArt said:**
> What were the nature of the problems you were experiencing in Windows? Was anything specifically going haywire?

Windows would take a very long time to open any file, or connect to the Internet. When it did open a file, or connect, I could not close out of anything, without hitting Ctrl + Alt + Delete, then it would just freeze for about 30 min. It would go crazy, and start opening other programs. I may have been hit with a virus, but Ubuntu worked just fine. I do not have a clue what might have happened, that's why I'm wondering if anyone else may have experienced this same type of problem. Thanks for your help.

---

### Post by Gripp on 2008-05-09
there are a lot of mathlab like programs out there, and i believe mathlab itself will work in linux. you may need Wine for that.  

my big prob is a prog like mathcad!  that a little taller of an order..

---

