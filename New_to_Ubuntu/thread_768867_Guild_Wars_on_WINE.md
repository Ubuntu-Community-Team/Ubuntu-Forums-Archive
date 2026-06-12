---
title: "Guild Wars on WINE"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Crope on 2008-04-26
After installing Linux and Compiz, and getting my drivers squared away, I tried installing some games. I successfully installed and ran doom3 and ut2004, with no problems at all. I recently tried installing Guild Wars, which I had laying around, with WINE. After the installation, when I try starting it up, the installer crashes, and my resolution changes to 1024-768 with 80Hz, and my monitor gives me a warning message that it's not optimum resolution.

I tried ```
metacity --replace
```Because I know that Compiz can be annoying when you're playing some games. It still crashed, but this time I looked in console and got this warning message:

```
Window manager warning: Treating resize request of legacy application 0x500000b (Guild Wars) as a fullscreen request

```

I'm running Ubuntu 7.10 64 bit, with an ATI x1900xt video card and fglrx drivers. I tried googling the problem for a few hours and found nothing to my interest. Everyone else seems to have excellent luck with Guild Wars on wine... 

Any ideas are appreciated.

---

### Post by Crope on 2008-04-26
bump

---

### Post by Crope on 2008-04-26
=(

---

### Post by Can+~ on 2008-04-26
Can you set guildwars to not run in fullscreen?

Also, winedb has a lot of comments on the bottom, maybe you should look at it, or try a different version of wine, or try some flags on the howto, or regedit:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

---

### Post by Crope on 2008-04-26
How do I make it run windowed?

---

### Post by ghost_ryder35 on 2008-04-26
there is an option in the wine settings under the wine menu

---

### Post by Crope on 2008-04-26
There's an option to run windows applications in a virtual desktop with a specified size, but it's greyed out and wont let me select it.

---

### Post by Crope on 2008-04-26
Alright, I found it, but it still does the exact same thing. Help, anyone?

---

### Post by Can+~ on 2008-04-26
> **Crope said:**
> Alright, I found it, but it still does the exact same thing. Help, anyone?

But did you tried everything on the WineDB? I already posted a link

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

Below all the information there's a section called "HOWTO", it has the following instructions. I can't help you any much, since I never played Guild wars, maybe you should ask on Wine.

---

