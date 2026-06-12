---
title: "VLC media player on my desktop?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-08-03
i know ive seen this somewhere, vlc media player can be a part of your desktop similar to a conky or terminal... anyone know what im talking about and more importainly how to do it.

---

### Post by cybrsaylr on 2008-08-03
I used to use VLC player in Gutsy, it was included in add/remove section of Gutsy but it is not listed in Hardy add/remove section. I don't know why it's not listed in Hardy.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-08-03
sudo apt-get vlc
????
or do you want something else

---

### Post by cybrsaylr on 2008-08-03
Does VLC run OK with 8.04?
I read some comments where some had problems with VLC on HH but not on GG.

---

### Post by drs305 on 2008-08-03
> **cybrsaylr said:**
> Does VLC run OK with 8.04?
I read some comments where some had problems with VLC on HH but not on GG.

I use VLC for just about everything. Hardy 32 and 64 bit. Can't answer the desktop question though.

---

### Post by PatrickMoore on 2008-08-03
> **drs305 said:**
> I use VLC for just about everything. Hardy 32 and 64 bit. Can't answer the desktop question though.

im going to find out i swear its the missing link to utilize the last of my wasted space ha

---

### Post by easybake on 2008-08-04
> **PatrickMoore said:**
> im going to find out i swear its the missing link to utilize the last of my wasted space ha

You can do this with almost any program.

Start by going into CCSM>Effects>Windown Decoration 
Change 'Decoration Windows' from 'any' to '(any) & !(class=BLAHBLAH)'

NOTE if you dont' know the class, have the program open, click the + button, 'grab' the window (by clicking on it) but be sure to also check the 'invert' box.

Then go into CCSM>Window Management>Window Rules 
Add the (class=BLAHBLAH) to whatever lines you want to apply.
Things like adding it to the 'sticky' line adds it to all the workspaces.

NOTE to not include the '!' on the lines.

If you have a size you want to keep it at go to the 'size rules' tab and set it there. 

You'll also probably want to add the program to your start-up. 

Go into System>Preferences>Sessions. Add it. In this case input vlc into the command line.

---

### Post by adobrakic on 2008-08-04
I think he means he wants to have VLC embedded into his desktop. Pretty sure easybake explained how to do it.

---

