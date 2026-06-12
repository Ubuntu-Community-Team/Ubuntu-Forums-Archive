---
title: "Icon sizes in Nautilus and desktop"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by jermza on 2011-12-08
Something I noticed is that the default size of icons in Nautilus are, let's say, 100%. Why is it, then, that the default size of icons on the desktop is considerably bigger (even at 100%)?

Is there a way to make the desktop icons smaller (or the same size as Nautilus ones?)

---

### Post by PPN13 on 2011-12-08
The 'icon' in the Desktop is an image file and so its really a thumbnail and not an actual icon. I think icons are the same size in Nautilus and Desktop. 

 You can check by creating a folder on the desktop and comparing its icon to a folder icon on Nautilus

---

### Post by jermza on 2011-12-08
I've checked. They're sized differently (much like my screen shot).

Is this normal behaviour?

---

### Post by PPN13 on 2011-12-08
OK i have an idea. Open up Nautilus and navigate to your home folder. From there go to your desktop **IN A NAUTILUS WINDOW** right click on some empty space there and select normal size. At least that's they way i can change size icons in 10.10

---

### Post by jermza on 2011-12-08
Apologies. I explained wrong.

The icons are the correct size and match up with Nautilus. However, the TEXT underneath the icons don't match up. That is, the the text in Nautilus is, say, Arial 9pt while the text under the icons on the desktop is a whole lot bigger and untidy.

I'd like the text under the desktop icons to be smaller (and matching Nautilus icon text size).

---

### Post by PPN13 on 2011-12-08
You can change Font sizes (including desktop's) from the appearance menus. I 'm running 10.10 (gnome2) so maybe you have to access it differently but I can get there from System => Preferences => Appearance or via right click on the desktop change Desktop Background. 

Then switch to the 'Fonts' tab in the new window. No need to apologize I focused wrongly on the picture :P

---

### Post by jermza on 2011-12-08
I'm using 11.10 and the font options are a little different. If I adjust the fonts in the Gnome-tweak tool, then ALL fonts are adjusted, making it difficult to adjust JUST the desktop fonts.

---

### Post by mcduck on 2011-12-08
> **jermza said:**
> I'm using 11.10 and the font options are a little different. If I adjust the fonts in the Gnome-tweak tool, then ALL fonts are adjusted, making it difficult to adjust JUST the desktop fonts.

As far as I know Gnome3 doesn't have a separate option for desktop font, like Gnome2 had. Probably because Gnome Shell doesn't use desktop icons by default.

I suppose there might be some trick to control this anyway, something like the ~/-gtkrc-2.0 file that could be used to tweak various theme settings with GTK2. And of course you could try loooking through the config files of the theme you are currently using, perhaps the font size is defined there?

---

