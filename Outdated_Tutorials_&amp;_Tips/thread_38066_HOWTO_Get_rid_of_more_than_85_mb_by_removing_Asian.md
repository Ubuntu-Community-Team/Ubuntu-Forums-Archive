---
title: "HOWTO: Get rid of more than 85 mb by removing Asian fonts"
date: 2005-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by SGC on 2005-05-29
Both Kubuntu and Ubuntu came with a few Asian fonts that occupid about 86mb of hard disk space, here is away to remove them:

Open the terminal and copy and paste the following commands: 

***** If you want to do it in one step, see the last command *****

**Removing chinese fonts (33.4mb):**
```
sudo apt-get remove ttf-arphic-gkai00mp ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-bkai00mp
```

**Removing Korean fonts (28.7mb):**
```
sudo apt-get remove ttf-baekmuk
```

**Removing Japanese fonts (17.2mb):**
```
sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic
```

**Removing Malayalm fonts (242 kb):**
```
sudo apt-get remove ttf-malayalam-fonts
```

**Removing Indian fonts (1417 kb):**
```
sudo apt-get remove ttf-indic-fonts
```

**Removing Arabic fonts (5465 kb):**
```
sudo apt-get remove ttf-arabeyes
```

**If you want to do it in one step:**
```
sudo apt-get remove ttf-arphic-gkai00mp ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-bkai00mp ttf-kochi-mincho ttf-kochi-gothic ttf-malayalam-fonts ttf-indic-fonts ttf-baekmuk ttf-arabeyes
```

If you think there are more fonts or local specifc packages that most people will not need, please post them here.

---

### Post by Spudgun on 2005-05-29
Apt wanted to remove Ubuntu-Desktop aswell, so I decided not to.

---

### Post by SGC on 2005-05-29
[QUOTE=Spudgun]Apt wanted to remove Ubuntu-Desktop aswell, so I decided not to.[/QUOTE]
 ubuntu-desktop and kubuntu-desktop is both meta packages, remove them will not remove any packages.

---

### Post by derrick1985 on 2005-05-29
Copy and paste wont' work because you don't have sudo in front of the commands.

Just as a note.

---

### Post by McQuaid on 2005-05-30
Thank you for this tip, removed them all.  

I don't have any of hand but if anyone has other stuff that can be removed similar to this, please post it here.

---

### Post by garnertr on 2005-05-30
thanks, very useful; next time place the "full delete" list @ the top not the bottom!

I know, next time I should just SCROLL! har har...

Great job!

---

### Post by SGC on 2005-05-30
[QUOTE=derrick1985]Copy and paste wont' work because you don't have sudo in front of the commands.
[/QUOTE]

Thanks, I fixed it.

[QUOTE=garnertr]thanks, very useful; next time place the "full delete" list @ the top not the bottom!
[/QUOTE]

Thanks, I add a note about the full list at the begining.

---

### Post by kxs on 2005-06-24
great tip  :)

---

### Post by skoal on 2005-06-24
avatar thief! ^^^^^^

\\//_

---

### Post by Zhukov on 2005-07-20
Yeah, i also saw the "remove them all" after ive removed the fonts one by one... :P

Nice tut.

---

### Post by malmjako on 2005-10-06
Is there a way to "hide" fonts that I don't use, so applications don't see them? I want to keep the ubuntu-desktop meta package in case more dependencies get added to it, and space is not critical.

I guess I could delete the actual files, but it doesn't seem to me to be a good solution. A control panel in gnome which allows me to choose which fonts to display would be nice...

---

### Post by mgor on 2005-10-06
great tip.

but after i've copy pasted halft of them, then i saw "If you want to do it in one step:", heh ;-)

*note to self* read the whole first post in a thread

---

### Post by videodrome on 2005-12-04
You can aslo type less by doing things like this:

sudo apt-get remove ttf-arphic-*

Then you don't have to type every arphic font name, it just uninstalls them all.

Loomis

---

