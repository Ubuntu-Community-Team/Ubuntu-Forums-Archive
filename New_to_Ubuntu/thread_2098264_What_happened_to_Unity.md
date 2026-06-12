---
title: "What happened to Unity"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by JHawk56 on 2012-12-26
I tried logging into Ubuntu 11.10 and the icons along the left are gone. There is no speaker icon, wireless network meter, session menu icon, or anything else except the wallpaper and a menu at the top: "File  Edit View  Go  Bookmarks  Help"

From the contents of the menus, it appears to be some kind of file manager or desktop manager.

---

### Post by fdrake on 2012-12-26
> **JHawk56 said:**
> I tried logging into Ubuntu 11.10 and the icons along the left are gone. There is no speaker icon, wireless network meter, session menu icon, or anything else except the wallpaper and a menu at the top: "File  Edit View  Go  Bookmarks  Help"

From the contents of the menus, it appears to be some kind of file manager or desktop manager.
try to update :
```
sudo apt-get update
```

edit:
i just noted now is 11.10 not 12.10 . You should upgrade to 12.04

---

### Post by Baldrick_NZ on 2012-12-26
I think you'll find 11.10 has reached EoL, meaning there's no longer any support for it. 

It might be a good idea to consider upgrading to, or doing a fresh install of 12.04.

---

### Post by JHawk56 on 2012-12-26
I had video issues with 12.04, so I went to 11.10> **fdrake said:**
> try to update :
```
sudo apt-get update
```How can I get to a terminal window? Is there a keystroke combination for that?

Wait. I also have Lubuntu DE and it works normally. I can do it in there. But it would still be a good thing to know.

---

### Post by fdrake on 2012-12-26
> **JHawk56 said:**
> I had video issues with 12.04, so I went to 11.10How can I get to a terminal window? Is there a keystroke combination for that?

Wait. I also have Lubuntu DE and it works normally. I can do it in there. But it would still be a good thing to know.

you can use the console "ctrl +alt+f1"
to get back into the dekstop env use ""ctrl +alt+f8""

---

### Post by Jay Nnib on 2012-12-26
To open the terminal, press Ctrl+Alt+T

---

### Post by monkeybrain2012 on 2012-12-26
> **Baldrick_NZ said:**
> I think you'll find 11.10 has reached EoL, meaning there's no longer any support for it. 

It might be a good idea to consider upgrading to, or doing a fresh install of 12.04.


??? 11.10 is supported til April next year.

@OP, did you accidentally log into classic desktop?

---

### Post by JHawk56 on 2012-12-26
It worked! Thanks, both of you!

---

### Post by fdrake on 2012-12-26
> **JHawk56 said:**
> It worked! Thanks, both of you!

glad to hear you fixed it.

---

### Post by JHawk56 on 2012-12-26
> **fdrake said:**
> you can use the console "ctrl +alt+f1"
to get back into the dekstop env use ""ctrl +alt+f8"""ctrl+alt+f8" is not working for me.> **monkeybrain2012 said:**
> @OP, did you accidentally log into classic desktop?No, definitely the "Ubunto" option. I replicated it several times.

---

### Post by zero2xiii on 2012-12-26
> "ctrl+alt+f8" is not working for me.

Hay,

Some systems have less terminals. Just run through ctrl + alt + {F1 to F12} one of them will take you back to the graphical environment.

Cherz

---

### Post by fdrake on 2012-12-26
> **JHawk56 said:**
> .
was f7 not f8. my bad.

---

### Post by JHawk56 on 2012-12-26
I had already tried f9, but it just opened a second console. Then I did some research and tried 'exit' but that didn't work. ctrl-alt-del worked, albeit for a reboot.

---

### Post by oldos2er on 2012-12-26
> **Baldrick_NZ said:**
> I think you'll find 11.10 has reached EoL, meaning there's no longer any support for it. 

11.10 is supported until April 2013.

---

### Post by JHawk56 on 2012-12-27
> **fdrake said:**
> try to update :
```
sudo apt-get update
```
> **JHawk56 said:**
> It worked!
I spoke too soon. Miraculously, the problem disappeared after simply retrieving the list of available updates and rebooting. Seemed unlikely, but I was not about to look a gift horse in the mouth.

Alas, it was not to be. The problem resumed, and even installing all the updates did not help. Thanks, though -- it did solve another problem I was having!

---

### Post by fdrake on 2012-12-27
can you post a screen shoot of it. If you cannot find the icon of firefox, do:

ctrl +alt+t >> type "firefox" .
the screenn shoots are  saved into ~/Pictures

---

### Post by JHawk56 on 2012-12-28
> **fdrake said:**
> can you post a screen shoot of it.There's really not much to see. Nothing but the default Ubuntu wallpaper. The menu line I mentioned in the first post is no longer there. If I right-click, I get a menu, but I can't grab a screen shot while it is present. The menu reads:

Create New Folder
Create New Document       >
Organize Desktop by Name
Keep Aligned
Paste
Change Desktop Background

It's intermittent now; I got to the full GUI desktop on an earlier try. I am starting to suspect a hardware problem (motherboard or power supply), since I am also having random boot problems into both Ubuntu and Windows (it's a wubi installation), unwanted resets, and once in a while a problem getting to my alternative Lubuntu desktop (although once I get there, it is complete and functions well). The Ubuntu problem is not a really big issue, since I prefer Lubuntu on this older machine.

I also looked at the fragmentation status of the partition on which wubi is installed, and it was highly fragged. Major parts of the wubi are not movable, so I have a highly fragged OS. That certainly can't be helping. I think I'll try deleting Ubuntu/Lubuntu, defragging, and starting over.

---

### Post by fdrake on 2012-12-28
> **JHawk56 said:**
>  I think I'll try deleting Ubuntu/Lubuntu, defragging, and starting over.
wecan stay here to conspire for hours trying to find out the reasons. If you have nothing i mportant i suggest you to just reinstall everything. good luck.

---

### Post by audiomick on 2012-12-28
> **fdrake said:**
> you can use the console "ctrl +alt+f1"
to get back into the dekstop env use ""ctrl +alt+f8""

This install is 11.10, and that didn't work. ctrl+alt+f1 does get me out into a console, but ctrl+alt+f8 does not get me back into the GUI.
Edit: wait on, I just noticed some posts in the middle here that explain that...

@ the OP. I agree: if you can re-install without losing anything drastic, that is probably the easiest. You might also consider moving on the a proper dual boot if you are using Ubuntu a lot. Wubi is intended for trying out Ubuntu, but not for long term use.

---

### Post by JHawk56 on 2012-12-28
> **fdrake said:**
> wecan stay here to conspire for hours trying to find out the reasons. If you have nothing i mportant i suggest you to just reinstall everything. good luck.I agree. Thanks.

> **audiomick said:**
> You might also consider moving on the a proper dual boot if you are using Ubuntu a lot. Wubi is intended for trying out Ubuntu, but not for long term use.I can't burn DVDs or boot from a flash drive, so I've been using wubi. Once I have a distro and version that I like for my setup, I'll find a way around that and go with a normal dual-boot

---

### Post by audiomick on 2012-12-28
> **JHawk56 said:**
> I can't burn DVDs or boot from a flash drive, so I've been using wubi. Once I have a distro and version that I like for my setup, I'll find a way around that and go with a normal dual-boot

Fair enough.

---

### Post by Horbo on 2012-12-29
> **JHawk56 said:**
> I agree. Thanks.

I can't burn DVDs or boot from a flash drive, so I've been using wubi. Once I have a distro and version that I like for my setup, I'll find a way around that and go with a normal dual-boot

Install Plop on your hard disk.  It will boot first and allow you you boot from a flash stick: [http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

---

