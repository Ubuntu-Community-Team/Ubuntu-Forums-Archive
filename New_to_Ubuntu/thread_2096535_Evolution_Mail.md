---
title: "Evolution Mail"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by MakeMineAPint on 2012-12-20
Hi, I have a Dell Inspiron 910 Netbook with an 8GB flash Hard Drive which is full even after deleting all unwanted programs and data. It runs well until I restore Evolution Mail from my main PC. Is it possible to have the Evolution data file on an external disc run from a USB port? If so how do I do it please?

---

### Post by vanadium on 2012-12-20
It will likely work when you replace the folder .evolution in your home directory with a symbolic link to a folder on your USB drive. You will need to make sure, though, that your USB drive is connected before launching evolution.

---

### Post by audiomick on 2012-12-20
Yes, I think vanadium is right. Haven't actually tried it, but I think a sybolic link might be the way.

You could also look into putting a larger drive in there, of course, if that is an option for you. 8GB is going to be tight for anything more that just surfing the web.

If you aren't already using it, you might want to look at Lubuntu. I believe it has a smaller footprint that Ubuntu, and it uses less resources to run. Should be a little faster on the netbook.

---

### Post by MakeMineAPint on 2012-12-20
> **vanadium said:**
> It will likely work when you replace the folder .evolution in your home directory with a symbolic link to a folder on your USB drive. You will need to make sure, though, that your USB drive is connected before launching evolution.
Having changed the "view" properties to show hidden items I eventually  found an "evolution" folder at Home/.local/share which looks like the one you are referring to. Is this the correct folder?  Other evolution folders were found at cache, gconf/apps, config, and gnome2/accels. Being a complete beginner can you give me a step by step guide as to what to do next please. Thank you.

---

### Post by vanadium on 2012-12-20
It is a long time I do not use evolution anymore - I switched to Thunderbird just before Canonical also decided Thunderbird should be their default email app :D .
The locations where applications store their data indeed has changed with more recent Ubuntu versions. Even I have a .local/share/evolution folder. It looks as if that one is containing the data, so that would be the one you would need to redirect tot the USB drive.

A step-to-step guide could be (make sure evolution is closed first):
- Open two nautilus windows side by side
- In the left one, navigate into .local/share so you see the evolution folder.
- Open the right nautilus window to where you want to move the evolution data.
- Move the evolution folder from the left to the right.
- In the right window, click the evolution folder you just moved, then hold down the keys Ctrl+Shift. Now drag the evolution folder to the left window, and release. This creates a link to the moved evolution folder in the original location, so evolution will know where to find the data.

---

### Post by MakeMineAPint on 2012-12-21
Great. Thanks very much for your help.
I will give it a go over the holiday break.
Merry Christmas.

---

### Post by philinux on 2012-12-21
> **MakeMineAPint said:**
> Hi, I have a Dell Inspiron 910 Netbook with an 8GB flash Hard Drive which is full even after deleting all unwanted programs and data. It runs well until I restore Evolution Mail from my main PC. Is it possible to have the Evolution data file on an external disc run from a USB port? If so how do I do it please?

You might want to try this.


[http://ubuntuforums.org/showpost.php?p=12412613&postcount=3](http://ubuntuforums.org/showpost.php?p=12412613&postcount=3)

---

