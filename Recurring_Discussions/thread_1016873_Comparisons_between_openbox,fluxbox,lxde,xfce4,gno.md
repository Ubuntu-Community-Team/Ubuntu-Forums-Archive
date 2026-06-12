---
title: "Comparisons between openbox,fluxbox,lxde,xfce4,gnome.... | whats better filemanager ?"
date: 2008-12-20
forum: Recurring Discussions
---

### Post by egon1987 on 2008-12-20
Hi,

The best desktop environment to use is GNOME ! 
(for me my needs at last - check my needs below...)
(but nautilus sucks in detailed view)

Now most posts on desktop environments i found with google (many were from this forum), considered too few aspects to judge a desktop environment. 
For example there was this thread where it was said "kde-core is faster than gnome-desktop" - which is true, but not accurate - he should have compared kde-core with gnome-core and gnome would have won this one.

Im gonna try better in my post. I used 8.10 with generic kernel for testing. It took like 3 days to test all of this. Hope it helps others that seek "the one" for themselves. 
Some limitations are amazingly stupid/weird for a long time windows XP user as myself.

For every major component...
# I will list my "Needs"
# I will list what software i tried
# I will list the advantages / disadvantages per software
[U][B]
### "Login Manager" the software to start a desktop session:[/B][/U]
* Needs:
1.Must be easy to edit
2.As fast/light as possible
3.Remote capabilty

I found these to consider: GDM, KDM, XDM, SLIM

***XDM **
+ seemed light enought
- is hard to edit (no GUI configurator)
***SLIM **
- no remote capability (i didnt have time to try it out)
- is hard to edit (no GUI configurator)
***GDM vs KDM ?**
+ both are easily configurable
- not very light 
KDM for KDE, GDM for GNOME - becuase then they share libraries with desktop manager software and are lighter.
So in the end i chose GDM because i chose GNOME.

_**### "Window Manager"+"taskbar" the software to manage your windows and some desktop aspects:**_
* Needs:
1. As fast/light as possible
 1.1 While moving/resizing "dont show window content" - makes any window manager surpringly fast 
 (i know its an illusion :P, but really - seeing the border(s) is enought ! )
2. Must be easy to edit
 2.1 Changing theme
 2.2 Canging menu
3. Dual Monitor capability (the weak spot of any linux).

I found these to consider: 
openbox, fluxbox, lxde, xfce4, gnome-core, kde-core

***kde-core 4.1**
I read by googling a lot, tat kde 4.1 uses less memory than kde 3.5.
 - too heavy.. i have used kubuntu desktop.. 
   it took around 400MB ram without activating any application somehow.
   It starts slower than any gnome variant.
   kde-core took 285MB of ram and also started slow.. 
   ..besides some taskbar icons were broken, panels were with wrong sizes...
   Felt alot like testing "Windows Vista"
   Tooo raw.
 - needs too much practise to remaster the new 4.1 Desktop
So i discard all KDE variants from futher testing. 
(at work we still have some 512MB ram PC-s)

***xfce4 **
"xubuntu" desktop environment was my second try to use linux in everyday tasks.
 + light/fast enought (near 200 MB ram usage) 
   (i mesaured ram in the end with all window managers installed
    i didnt make clean install for every test.. so its +/- 20Mb ? maybe)
 + "Opaque move and resize" option, "No window content while move and resize"
 + themes are easy to edit (GUI confiurators)
So why did xfce4 make me mad ?
 - no "copy, paste, create new" under right click on Desktop
 - no group select under Desktop !!! wtf !!!
 - no dual monitor GUI configurator
 (the default filemanager "thunar" made me also mad... read below "Filemanager")

***lxde**
It uses openbox for window manager, lxmenu for taskmanager and pcmanfm for filemanager.
 + light/fast enought (near 170 MB ram usage)
 + openbox themes and menu are easy to edit (GUI confiurators)
 - openbox "No window content while move and resize" is 100% broken
 - cant move Desktop icons (pcmanfm manages it).. only sort (not a very big minus in my eyes)
 - no dual monitor.. tryed lxrandr, but it doesnt detect external monitor,tv,projector.

***fluxbox**
It does not come with Desktop- and File- manager.. but it has its own taskbar.
 + light/fast enought (near 155 MB ram usage)
 + fluxbox themes and menu have GUI configurators
 + "No window content while move and resize" is working.
   (although this function clitched with default (not the manufacturer nvidia) video driver)
 - no dual monitor GUI

***gnome-core + openbox** (this takes some configuring to set up)
... very few (maybe acceptable) minuses for this combination :)
 + light/fast enought (near 195 MB ram usage)
 + openbox themes and menu are easy to edit (GUI confiurators)
 + let Neutilus handle Desktop to be able to move icons on it...
   (or pcmanfm to not)..
 + for Dual Monitor gnome has "gnome-display-properties" applet which works fine with openbox.
   (NB!, if i installed nvidia drivers, then gnome applet broke.. 
    nvidia-settings worked everywhere... but thtats not the point...
    i also have a PC which has SIS graphics and no such "nvidia" or "ati" custom app works for it)
 - openbox "No window content while move and resize" is 100% broken

***gnome-core + fluxbox** (this takes some configuring to set up)
 + light/fast enought (near 196 MB ram usage)
 + fluxbox themes and menu have GUI configurators
 + let Neutilus handle Desktop to be able to move icons on it...
   (or pcmanfm to not)..
 + "No window content while move and resize" is working.
 - for Dual Monitor gnome has "gnome-display-properties" applet which DOES NOT WORK with fluxbox.
   (only mirroring was possible - i saw many clitches, and one xserver crash with testing this)

***gnome-core**
 + light/fast enought (near 230 MB ram usage)
   (i remember that first install gnome-core was 155MB ram... 
    i was surprised because openbox and fluxbox were near that ram usage)
 + metacity (gnome window manager) themes and gnome menu are easy to edit (GUI configurators)
 + let Neutilus handle Desktop to be able to move icons on it...
   (or pcmanfm to not)..
 + "No window content while move and resize" is working but not easy to set (needed to google more than usual).
 + for Dual Monitor gnome has "gnome-display-properties" applet which works fine with metacity.
 (the default filemanager "nautilus" made me angry... read below "Filemanager")

[U][B]
### "Filemanager" the software to manage files.. browse, move, copy,[/B][/U] delete:
* Needs:
1. Must have "Detailed view"
 1.1 NB! i consider "Detailed view" the only view to use anywhere. Why ?:
 * Icon view is a chaos - 
[INDENT]  (the default view.. thats why all newbies use it, 
   maybe thats why some ppl hate computers?) 
  * not sorted, 
  * icons are huge.. so browing many files is a chore. 
  * gives no info on things you see. 
  (you see by extension, thats its image, but how big ? (hover tooltip is not an option))[/INDENT]
 * List view is a bit less chaos - 
  [INDENT]* things are more sorted, but items go from up to down and from left to right... a bit bad listing.
  * gives no info on things you see.[/INDENT]
 * Detailed view -
  [INDENT]* things are sorted from up to down. you get a good overview.
  * very easy to resort.. by name, size, owner, filetype, date[/INDENT]
2. Right click function must have "Create new", "Copy", "Paste"
 (on every view previously mentioned)
3. Network browsing. (ftp, windows shares, linux shares).

I tested those: Thunar, Dolphin, Nautilus, Pcmanfm
Because they came from above testing.

***Dolphin** - came with KDE 4.1
+ Detailed view functioned properly
+ Network browsing was there
+ Right click funtions worked
- many usuless space taking sidepanels by default (easily removable)
- comes with KDE, so i assume it uses KDE libraries... 
  which makes it not a good idea to use in GNOME environment.

***Nautilus** - comes with GNOME
+ Network browsing is there
- Detailed view is broken ... cant right click Copy/Paste items in this view.

***Thunar** - comes with xfce4
(sorry, i dont remember about network browing)
- Detailed view is broken ... cant right click Copy/Paste items in this view. Same as in nautilus. That makes me mad.

***Pcmanfm** - comes with lxde
+ Detailed view is OK - not as good as in dolphin.. 
  it like in nautilus, but with a quick hotfix - good enought :D
  (people use right click copy/paste/create new more often than group select anyway) 
  (I mean group select is not totally broken - 
  but you cant select all with one stroke.. always one unselected)
+ Right click functions work
- no Network browsing (promised in new versions)
- It hase some permission issues mith mounting partitions 
  (in sudo mode it works, in user mode it displays a unreadable errormessage)
  For removable device mounting it works in user mode as in sudo mode.

_So what meets my needs ?_

gnome-core desktop and window managing is enought for me.
But joggling between tho filemanagers - pcmanfm with default view to detailed for file managing and nautilus for network browsing is not very good solution.

_**The question for this thread..**_.

Anyone knows how to "hotfix" the nautilus and thunar "detailed view" bugs ?
Or is there another better filemanager (i mean besides pcmanfm upcoming versions) ?

:confused:
To answer you dont have to read the whole post... start from "Filemanager" to understand the thread question.
All fack corrections are welcome. Picking on my unperfect english - not.

---

### Post by jrusso2 on 2008-12-21
Best file manager for basics is Konqueror.  Best one for more complex tasks is Krusader.  Best command line file manager is MC.

PCMan would be nice if it did not crash all the time. Nautilus, I just don't know what to say about it, its just awful, always has been.

---

### Post by egon1987 on 2008-12-21
As i remember Konqueror and Krusader use KDE libs... but i use GNOME.

I checked Konquerro website..
[http://www.konqueror.org/](http://www.konqueror.org/)
Its also a web brauser.. i emember i tryed to use it as web browser.. I hated the start screen.. And it lacked the power and speed of firefox. It also tries to be a universal viewing application.. Sorry.. im not a fan of software which tries to do everything :(

Now krusader seems interesting..
Did Aptitude install.. 42 MB with KDE dependencies :) .. i expected worse.

So my first impressions...
-It didnt integrate to my Gnome darkish themes.
+It is integrated to archivers for example.. the initial setup was helpful.
+It has "Detailed view" as default and group select works.
-Its very painful to "Right click" copy/paste/move ..
(the same problem as with thunar and nautilus.. it takes the whole row as an element.. so if the folder is full (there is a scrollbar) its impossible)
-If i did "right click create txt" then it opened it right away..
 (it tries to be too smart)

I think i stick with pcman.. 
I liked mc also.. but its not graphical.
PCman has jet never crashed for me :o

_**Fixing PCmanfm errors on mounting internal drives :**_

And to fix the partition mounting error... you can use System > Authorizations... and org > freedesktop > hal > storage > Mount sile systems from internal drives. Set for this "Active console" to Yes.

Then user mode PCmanfm doesnt complain on mounting internal drives.

---

### Post by egon1987 on 2008-12-21
As i remember Konqueror and Krusader use KDE libs... but i use GNOME.

I checked Konquerro website..
[http://www.konqueror.org/](http://www.konqueror.org/)
Its also a web brauser.. i emember i tryed to use it as web browser.. I hated the start screen.. And it lacked the power and speed of firefox. It also tries to be a universal viewing application.. Sorry.. im not a fan of software which tries to do everything :(

Now konqueror seems interesting..
Did Aptitude install.. 42 MB with KDE dependencies (42 was compressed... uncompressed was over 100MB)

So my first impressions...
-It didnt integrate to my Gnome darkish themes.
+It is integrated to archivers for example.. the initial setup was helpful.
+It has "Detailed view" as default and group select works.
-Its very painful to "Right click" copy/paste/move ..
(the same problem as with thunar and nautilus.. it takes the whole row as an element.. so if the folder is full (there is a scrollbar) it impossible)
-If i did "right click create txt" then it opened it right away..
 (it tries to be too smart)

I think i stick with pcman.. 
I liked mc also.. but its not graphical.
PCman has jet never crashed for me :o

_**Fixing PCmanfm errors on mounting internal drives :**_

And to fix the partition mounting error... you can use System > Authorizations... and org > freedesktop > hal > storage > Mount sile systems from internal drives. Set for this "Active console" to Yes.

Then user mode PCmanfm doesnt complain on mounting internal drives.

---

### Post by kyle_white on 2009-09-06
A little late for this reply, but using fusesmb or smbnetfs allows easy browsing of networks in any file browser. Google it.

---

### Post by kerry_s on 2009-09-06
> **kyle_white said:**
> A little late for this reply, but using fusesmb or smbnetfs allows easy browsing of networks in any file browser. Google it.

dang, 2008, yeah just a little late. :lolflag:

---

### Post by bapoumba on 2009-09-06
Thread closed ;)

---

