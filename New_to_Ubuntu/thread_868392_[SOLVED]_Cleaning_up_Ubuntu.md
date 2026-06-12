---
title: "[SOLVED] Cleaning up Ubuntu"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-07-23
When I used XP and Puppy Linux I prefered Opera browser over Firefox.  I would like Firefox off my system but when I went to the synaptic package manager there were 1000s of files.  I didn't know what to removoe or if it would be a file I would later miss.  

This is probably a simple procedure.  But how do I go about removing Firefox?

---

### Post by PmDematagoda on 2008-07-23
You could either just search for the "firefox" package in Synaptic and remove it, or just execute:-
```
sudo apt-get remove firefox
```
in a terminal.

---

### Post by Rolcol on 2008-07-23
There may still be files after you remove it using apt-get.
```
sudo apt-get autoremove
```

---

### Post by Polish Rifle on 2008-07-23
Thanks.  That was way easier than go through the package manaager.  Is it a good idea to uninstall programs on Linux if you're not using them?  I figure it could free up the HD for speed.  

Another Q.

Can I make it so Pidgen automatically loads at start up?

---

### Post by Joeb454 on 2008-07-23
System &#8594; Preferences &#8594; Sessions

You can add it in there :)

---

### Post by Rolcol on 2008-07-23
> **Polish Rifle said:**
> Thanks.  That was way easier than go through the package manaager.  Is it a good idea to uninstall programs on Linux if you're not using them?  I figure it could free up the HD for speed.  

Another Q.

Can I make it so Pidgen automatically loads at start up?
Yep.  System > Preferences > Sessions.  In Startup Programs, click add.  Name it "Pidgin" with the command "pidgin"

**Edit:**  Dang... He beat me ^^

---

### Post by Polish Rifle on 2008-07-23
> **Rolcol said:**
> Yep.  System > Preferences > Sessions.  In Startup Programs, click add.  Name it "Pidgin" with the command "pidgin"

**Edit:**  Dang... He beat me ^^

Haha, he beat you to it but you actually told me what to enter in the fields.  Thanks to both!

Let's see....can't think of anything now.  I'll go for a few more mods later.

---

### Post by Joeb454 on 2008-07-23
> **Polish Rifle said:**
>  I'll go for a few more mods later.

Sounds a little ominous being as you're a rifle...

---

### Post by rossjman1 on 2008-07-23
> **Polish Rifle said:**
> Thanks.  That was way easier than go through the package manaager.  Is it a good idea to uninstall programs on Linux if you're not using them?  I figure it could free up the HD for speed.  

Another Q.

Can I make it so Pidgen automatically loads at start up?
I may be wrong, but freeing up HD space will not speed up your Ubuntu. Unlike Windows, Ubuntu uses a separate partition for swap.

---

### Post by zoobean on 2008-07-23
What to do then???
:confused::confused::confused:

---

### Post by Polish Rifle on 2008-07-24
> **PmDematagoda said:**
> You could either just search for the "firefox" package in Synaptic and remove it, or just execute:-
```
sudo apt-get remove firefox
```
in a terminal.


So I did the sudo apt-get remove firefox, and it said it removed it.  But Firefox is still installed on my computer.

---

### Post by PmDematagoda on 2008-07-24
Do you mean the quick launch button? Did you try running Firefox to see if it still works? If it doesn't, then all you need to do is just remove the launchers.

---

### Post by Polish Rifle on 2008-07-24
I ended up going into the package mananager and uninstalling it.  Hopefully all the files from it are gone.  

Now I'm trying to set up my Logitech Trackball mouse like it was in XP.

---

### Post by thecircusb0y on 2008-07-24
Freeing up disk space is always a good idea. If you want to get more performance, I'm sure there are tutorials for tweaking disk seek times, services, cache, and all those great things. 

Hardware-wise, RAM is very cheap, and an easy upgrade to do for performance.

---

### Post by cardinals_fan on 2008-07-24
> **Polish Rifle said:**
> So I did the sudo apt-get remove firefox, and it said it removed it.  But Firefox is still installed on my computer.
Try ```
sudo aptitude purge firefox
```

---

### Post by tiachopvutru on 2008-07-24
> **Polish Rifle said:**
> So I did the sudo apt-get remove firefox, and it said it removed it.  But Firefox is still installed on my computer.

That's because the actual package you need to uninstall is something err... I forgot. I'm not on my Ubuntu partition right now, but if I remember correctly, it's something like **firefox-3.0**

Search for it inside Synaptic.

EDIT: Yup, that's the package. Do:

```
sudo apt-get remove firefox-3.0
```

---

### Post by El Conquistador on 2008-07-24
dont know if this will help exactly with your firefox issue but it will help as far as the cleaning up goes. 

sudo apt-get install gtkorphan

A graphical tool to find and remove orphaned libraries

---

### Post by philinux on 2008-07-24
> **El Conquistador said:**
> dont know if this will help exactly with your firefox issue but it will help as far as the cleaning up goes. 

sudo apt-get install gtkorphan

A graphical tool to find and remove orphaned libraries

Don't forget to look in Tips and Tutorials forum. A mine of info.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Polish Rifle on 2008-07-24
> **philinux said:**
> Don't forget to look in Tips and Tutorials forum. A mine of info.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Wow that's the second time I've crossed paths with you on this forum philinux.  Thanks for the help.  My name is Phil and I am also a guitar man.

---

