---
title: "Where is system -&gt; preferences?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by allene222 on 2008-06-09
I can find it on my Fedora machine but for the life of my not on my Mythbuntu 8.04 machine.  Lots of solutions I find tell me to click something under system -> preferences but there is no preferences option under the system menu.

I am embarrassed to ask such a simple question so please be kind in  your reply.

Allen

---

### Post by tamoneya on 2008-06-09
it may have been hidden via the menu editor.  Right click on applications in the panel and select "edit menus" make sure that the preferences box is checked when you are under the "system" menu.

---

### Post by allene222 on 2008-06-10
Thanks for your help.  It seems to be a bit more complicated.

The menu that I can edit after clicking "edit menus" seems to have a sub menu that I cannot edit.  
The entry:
-- include-- system
probably has "accessories", "multimedia", "network", and "system" as they don't show up in the main menu and the layout matches this assumption.

So, I guess I need to know how to edit this system entry.

Thanks again for the help.

Allen

---

### Post by SunnyRabbiera on 2008-06-10
Doesnt mythbuntu use xfce?

you can tell if it has right click menu that says "about XFCE"

---

### Post by llama320 on 2008-06-10
> **allene222 said:**
> Thanks for your help.  It seems to be a bit more complicated.

The menu that I can edit after clicking "edit menus" seems to have a sub menu that I cannot edit.  
The entry:
-- include-- system
probably has "accessories", "multimedia", "network", and "system" as they don't show up in the main menu and the layout matches this assumption.

So, I guess I need to know how to edit this system entry.

Thanks again for the help.

Allen

I'm taking a bit of a stab in the dark here, but I know that Hardy initiated an "unlock" feature so that you could "see, but not touch" certain apps while not unlocked. It should be a little box to click on in a lower corner of the app.

This may be the case with your machine, but again, I'm really just making a (hopefully) educated guess

Good Luck

EDIT: SunnyRabbiera posted as I was writing my response so I didn't see it, but yeah..do that first...I think my thing just applies to GNOME

---

### Post by allene222 on 2008-06-10
When I right click on "Applications" it says Xfce menu.  The "systems" tab is inside the area marked "system" in the menu.xml file below.  There is no "preferences" tab under "systems" in the actual menu.  The tab "Settings Manager" has many of the icons that my Fedora machine has under "preferences" but not near all.    The issue I am having is that I look for solutions to problems that tell me to click something under "preferences" and that thing is never in the "settings manager" thus my quest for the "preferences" menu.  Is it possible that they have renamed "preferences" to "settings manager"?  If so, all the preferences I am looking for would have to be missing from "settings manager".  There are far more icons in "preferences" on the Fedora machine than there are under "settings manager" so I may still be missing the "preferences" menu.  I don't know, which is why I posted in the beginners forum :)

Allen

PS.  Below is the contents of menu.xml.  


<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome
-settings" snotify="true"/>
	</menu>
	<separator/>
	<include type="system" style="simple" unique="true" legacy="true"/>
	<separator/>
	<app name="About Mythbuntu" cmd="xfbrowser4 file:///usr/share/mythbuntu/
home/index.html" icon="gnome-info"/>
	<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>

---

