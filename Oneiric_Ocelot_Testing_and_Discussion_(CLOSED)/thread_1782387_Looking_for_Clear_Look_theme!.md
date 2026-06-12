---
title: "Looking for Clear Look theme!"
date: 2011-06-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-06-14
Hello,

I installed June 13 i386 daily-live CD build on my PC with Nvidia 7300GT graphic card yesterday. Only Unity 2d works, but not Gnome or Ubuntu session choices. I am looking for the Clear Look theme that exists in Natty and previous Ubuntu versions (Appearance > Preferences).  This is to remedy the current situation in Firefox 5.0 where the color of bookmark items and bookmark menu background is dark brown, which looks awful and is hard to read/discern the bookmarks. I did install gnome-themes via Synaptic Package Manager but afterwards I cannot find Clear Look or Appearance anywhere. In the mean time I am using Chromium which does not have such problem as in Firefox.

Any suggestions?  Thanks for your help.

---

### Post by jerrrys on 2011-06-14
did you load the extra themes package?  and don't know why FF5 can't be adjusted.  i got mine looking exactly like my old 3.x...

---

### Post by iClouseau88 on 2011-06-14
Hi jerrrys,

After reading your post, I installed Gnome-themes-extras as well.  Still no luck!

---

### Post by jerrrys on 2011-06-14
just looked and synaptic tells me that you got it.  look in "icons" and see if its there

---

### Post by Starks on 2011-06-14
Clearlooks doesn't work GTK3.

End of story.

---

### Post by jerrylamos on 2011-06-14
On all my installations that will do it, I use clearlooks.

Any hope or is it in the bit bucket?

Jerry

---

### Post by Rasa1111 on 2011-06-14
I delete clearlooks whenever i install! 
Soo fugly. lol

But I believe starks is right.
> Clearlooks doesn't work GTK3.

End of story.

---

### Post by iClouseau88 on 2011-06-14
Hi everyone,

Whenever I reboot into [COLOR="red"]Onerous[/COLOR] (?) Oneiric, GNOME session fails to load,and Ubuntu only shows a wallpaper.  Only Ubuntu 2D (aka Unity) loads.  At the present, Firefox 5.0 beta on my deskbox has 2 problems:

1. Bookmarks shows only 3 columns of bookmark items with white print on a black background, and a total of A-F bookmarks only.  My 100+ bookmarks extend to Z.

2. Selecting any object or item on the taskbar shows white print on a black background, i.e.same color as that of the taskbar.  This could be a poor color design or unfinished work.  I don't know.  

Chromium on the same system has no such color problems.

I did un-install and re-install Firefox but this color problem still persists!

---

### Post by CreativeReach on 2011-06-15
Well firefox is still a beta so that might explain it..........

---

### Post by Quadunit404 on 2011-06-16
> **Starks said:**
> Clearlooks doesn't work GTK3.

End of story.

/thread

---

### Post by t.rei on 2011-06-16
I actually gave up on finding a really god, working gtk3 theme that won't break within a weeks system updates for now.

Things are still under intense development.

---

### Post by screaminj3sus on 2011-06-16
> **t.rei said:**
> I actually gave up on finding a really god, working gtk3 theme that won't break within a weeks system updates for now.

Things are still under intense development.
This is by far the best gtk3 theme I've found:

[http://lassekongo83.deviantart.com/art/Zukitwo-203936861](http://lassekongo83.deviantart.com/art/Zukitwo-203936861)

It also has a gtk2 theme for apps look nice and unified.

---

### Post by t.rei on 2011-06-17
Yep, thats the one I am using right now. It has some weird "this is pink" bugs on my current system, though. :(

---

### Post by lucazade on 2011-06-17
> **t.rei said:**
> Yep, thats the one I am using right now. It has some weird "this is pink" bugs on my current system, though. :(

It is due to the unfinished and under development Adwaita gtk engine and also the theme is not updated to fit latest engine changes :)

---

### Post by t.rei on 2011-06-17
I still think this might be one of the first really good gtk3 themes, once the engines mature.

---

### Post by Hairy_Palms on 2011-06-17
aye most themes seem borked with the latest adwaita engine, ive got the libadwaita.so from the last working version that i just copy to the gtk3 folder after each gnome-themes-standard update (after checking if the update fixed it or not) i can attach it here if people want

---

### Post by iClouseau88 on 2011-06-18
Yes, please do attach it.

By the way, yesterday I installed the June 17 i386 alternate CD version of Oneiric Kubuntu and have no problem with Firefox bookmarks.  Everything seems nicer than Unity.  One thing I dislike about Unity2 is that the vertical band (or dash?) on the left side column sometimes move briefly to the right and interferes with the backward arrow or the File menu item of Firefox or other browser.

---

### Post by Hairy_Palms on 2011-06-18
sure, heres the working libadwaita.so
```
sudo cp libadwaita.so /usr/lib/gtk-3.0/3.0.0/theming-engines/libadwaita.so
```

---

### Post by screaminj3sus on 2011-06-18
> **t.rei said:**
> Yep, thats the one I am using right now. It has some weird "this is pink" bugs on my current system, though. :(

That should be fixed according to the themes Deviantart page.

---

### Post by LarsKongo on 2011-06-21
> **screaminj3sus said:**
> That should be fixed according to the themes Deviantart page.
They removed the adwaita-inset feature which caused this from the start. Now they've done some other changes which causes some other things to look weird. I can only suggest that people use the recent most stable version of the package gnome-themes-standard. If some changes are made to the stable one I'll probably update the theme to fix it. At the moment though I'm looking into the possibility of using the Unico engine instead of the Adwaita engine.

---

