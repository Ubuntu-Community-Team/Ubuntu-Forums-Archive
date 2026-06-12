---
title: "Changing system icons (Shutdown, Trash, etc.)?"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by theragingking on 2008-08-16
Hey all,

I've just reverted back to 7.10 after a particularly nerve-wracking go at 8.04. I'll probably go back once it gets a wee bit less buggy. But for now, I'm trying to customize my display as much as possible. Currently, I'm looking for a way to switch up the default system icons (the red shutdown, the orange trash, etc) for more theme appropriate blue ones. Is there a way to do this? I know how to change folders and whatnot through System->Preferences->Appearance, but this doesn't seem to be covered.

Any help?

Thanks,
TRK~!

---

### Post by TJCIB on 2008-08-16
you should look for new themes and icon sets.

You can find them at pages such as art.gnome.org
or [www.gnome-look.org](www.gnome-look.org) is real good one.

Of course, that assumes your using gnome, there are other ones out there for kde.

Installing them are pretty easy and well documented.  Do a quick search for installing themes.  A lot of the pages will give you instructions right on them.

---

### Post by theragingking on 2008-08-17
Right. Am using gnome, do dig on the gnome-look. I have a few single icons that I want to replace the system icons with, i.e. awonderful blue power icon for shutdown and bin icon for trash. These I want to replace specifically, amongst others, without, say, throwing off the ones for folders and such that I already have. As I know, install under appearence only really replaces the entire pack, not just individually.

I'll look for tutorials on the topic on gnome-look, but specific advice is welcome too.

---

### Post by TJCIB on 2008-08-17
I'm not on my Linux box now, but if I remember correctly:

Right click on the icon you want to replace and click Properties.
You should be able to then click on the picture of the icon and a window will pop up and you can browse for the icon you want.  
Sorry I can't be more specific, if you need more help, I'll check back when I'm on Ubuntu.

Some file types work better than others because of scalability.

---

### Post by tibellus on 2008-08-17
Once you get your favorite icons, you can copy them in /usr/share/icons as root, for system wide access. Actually, you should replace the icons from your current theme with the ones you want.

---

### Post by theragingking on 2008-08-17
> I'm not on my Linux box now, but if I remember correctly:

Right click on the icon you want to replace and click Properties.
You should be able to then click on the picture of the icon and a window will pop up and you can browse for the icon you want.  
Sorry I can't be more specific, if you need more help, I'll check back when I'm on Ubuntu.

Some file types work better than others because of scalability.

Well, yes, that works for folders and files icons, but when it comes to, say, the trash and shutdown icons on the panel, not so effective. Could be wrong, but that's what I'm seein'.

> Once you get your favorite icons, you can copy them in /usr/share/icons as root, for system wide access. Actually, you should replace the icons from your current theme with the ones you want.

Could you be a little more clear on this one? Do you mean actually overwrite the icons that are in the current theme?

---

### Post by TJCIB on 2008-08-17
would this work?
change trash.png to trash1.png
then move the icon you want into the location and rename it trash.png

that might be going around your elbow to get to your other elbow...

I've never tried it, so I'm interested to see what you do.  I'm just taking shots...

---

### Post by shinero on 2009-06-21
i think this works... when replacing  an icon with another icon with the same name, your new icon would be displayed then... but i thin that you have to type a command in the terminal after replacing the icon for this to take action...

for example when replacing an icon of the panel like the* "start here.png"* you have to type
    **  *killall gnome-panel***
i dont know if the same works for other icons

---

### Post by hyperdude111 on 2009-06-21
> **shinero said:**
> i think this works... when replacing  an icon with another icon with the same name, your new icon would be displayed then... but i thin that you have to type a command in the terminal after replacing the icon for this to take action...

for example when replacing an icon of the panel like the* "start here.png"* you have to type
    **  *killall gnome-panel***
i dont know if the same works for other icons

Dude this thread was last posted on "Aug 26 2008"

---

### Post by sadaruwan12 on 2009-06-21
Wouldn't it be easier if you select a good icon pack from GNOME-look and replace the whole thing with out trying to mess up your default icon sets in the root and about Ubuntu 8.04 I'm using it for ages but I never had run in to any trouble only time I'd trouble was when I upgraded my OS in to 9.04 but I came back to 8.04 'cos it's LTS it gives very little trouble and with the new updates it has got more and more steadier. Another thing I've used gnome look icon pack to fully change my desktop experience when I installed it was brown now it's completely blue.

---

### Post by ametalguitarist on 2009-06-21
[quote=]Dude this thread was last posted on "Aug 26 2008"[/quote]

Information never expires

---

