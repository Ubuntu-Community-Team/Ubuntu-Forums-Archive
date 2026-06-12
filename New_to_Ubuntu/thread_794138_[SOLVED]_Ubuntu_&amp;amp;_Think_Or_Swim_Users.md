---
title: "[SOLVED] Ubuntu &amp;amp; Think Or Swim Users"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-14
I am new to Ubuntu And interested if anyone on the forum is using Ubuntu with an Option trading firm/program call 'Think or Swim'. It works closely with Java 6 for the graphics. If anyone has experience with their software & can offer advise on installation & use, please advise. Thanks, Cal

---

### Post by SunnyRabbiera on 2008-05-14
I am not sure on this application, but it does have a web based version it seems...
It might work under ubuntu but as for the installer, if its a windows exe only you may have to install wine.

---

### Post by CoCoKnots on 2008-05-14
Hi Sunny, You're correct... They do have a web Based version of their program. However, it is missing important risk/reward analysis information. Like I said, I am new to this... so excuse me if this is a dumb question... How do I install 'Wine' & would doing this enable me to install their 'Windows XP' version ? Thanks, Cal

---

### Post by RiceMonster on 2008-05-14
to install wine, run this command in a terminal:
```
sudo apt-get install wine
```

Wine MIGHT let you run their windows XP version. Sometimes wine runs the application, sometimes you have to do some tweaking to get it to work right, and sometimes it won't work at all. It's allways worth a shot though. You can try searching the [wine appdb](http://appdb.winehq.org/) to see if other people have had success with it.

---

### Post by SunnyRabbiera on 2008-05-14
well then one can assume it doesnt have a linux version correct?
well like I said try wine, and make sure to install java for windows in it too...
hope it works, wine is tricky, but if this is a basic java based apllication it might work.

---

### Post by CoCoKnots on 2008-05-14
After I install 'Wine', Is there a place to insert a command line or does it activate automatically when I use the [www.thinkorswin.com](www.thinkorswin.com) address for a standard install process ?

---

### Post by SunnyRabbiera on 2008-05-14
> **CoCoKnots said:**
> After I install 'Wine', Is there a place to insert a command line or does it activate automatically when I use the [www.thinkorswin.com](www.thinkorswin.com) address for a standard install process ?

you should be able to just download the .exe installer, and then be able to open it up immediately with wine.
But as I said it might be best if you installed java for windows before you install it.
Wine pretty much doesn't need command line anymore, its gottten a lot better over the last few years.

---

### Post by aBitLater on 2008-06-28
They have a linux version.  Just download from their download link while in linux.  the website will automatically give you the proper linux install package (a shell script).  

Go to your terminal, type:

sh thinkorswim_installer.sh (from the directory where you saved the download)

to avoid installing as root, add "/home/your_user_name" to the beginning of the suggested install path. (optionally, install as root)

Think Or Swim is a really nice program that is free for paper-trading.  Good Choice.

---

### Post by alb.perjet on 2009-02-15
I tried that and it said permission denied any other ideas?

---

### Post by RomeReactor on 2009-02-15
> **alb.perjet said:**
> I tried that and it said permission denied any other ideas?

Hi. That usually happens when an installer is not marked as executable. You can right-click on it, select "Properties", and on the "Permissions" tab, check the "Allow executing file as program" box; then try installing it again.

---

### Post by alb.perjet on 2009-02-16
Thanks so much it works...

---

