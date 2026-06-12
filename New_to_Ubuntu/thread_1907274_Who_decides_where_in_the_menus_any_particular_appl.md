---
title: "Who decides where in the menus any particular application resides by default?"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-01-11
Recently I installed three different ISO mounting tools, which ended up in three different menus, by default:

[LIST]
[*] Applications -> Accessories -> Furius ISO Mount
[*] Sound & Video -> ISO Master
[*] System Tools -> Gmount-iso
[/LIST]
  Who decides these things?

What logic do they follow?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210618&d=1326267651[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210619&d=1326267651[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210620&d=1326267651[/IMG]

---

### Post by lisati on 2012-01-11
It can depend on a number of things. Sometimes an "ISO" file represents a system disk, sometimes it's a CD or DVD, sometimes it's something else....

---

### Post by spacecheck on 2012-01-11
> Recently I installed three different ISO mounting tools, which ended up in three different menus, by default:

[LIST]
[*] Applications -> Accessories -> Furius ISO Mount
[*] Sound & Video -> ISO Master
[*] System Tools -> Gmount-iso
[/LIST]
  Who decides these things?

What logic do they follow?

Why in heaven's name, do you assume logic is being used??
;-)

---

### Post by satanselbow on 2012-01-11
> **rocksockdoc said:**
> 
[LIST]
[*] Applications -> Accessories -> Furius ISO Mount
 *] Sound & Video -> ISO Master
[*] System Tools -> Gmount-iso
[/LIST]

Gotta agree that it is a bit bonkers BUT! It can all be fixed to your own personal ordering by editing the relevant .desktop file - which will be found in /usr/share/applications...

You think disk mounters are bad - the number of IDE / programming tools that appear in categories other than the very category designed for their very purpose (ie Programming) drives me mad.

When ever I fresh install I spend a fair bit of time editing .desktop categories to my liking...

... and since when has Alchemy been a programming tool? It's an image editor/generator ???

Could be worse and go the windows route where you about 37 layers of slide-out menu folders before you get to the actual app shortcut itself :D... oh yeah that was how Gnome 2 worked - how easily we forget :rolleyes:

---

### Post by rocksockdoc on 2012-01-11
> **spacecheck said:**
> Why in heaven's name, do you assume logic is being used?

OK. I get the idea that there isn't a whole lot of logic.  

I had thought there might be a committee or a logic-tree or something that the developers would be forced to follow in order to get into a repository. 

Something like the logic in how I organize my toolbox in my garage, e.g.:

[LIST]
[*]Applications->Screwdrivers->{phillips, flathead, reed}
[*]Applications->Hammers->{ball peen, roofing, framing}
[*]Applications->Wrenches->{box,socket}->{metric,SAE}
[*]etc.
[/LIST]
I guess logic is not the case, based on all the comments (save the first).

> **satanselbow said:**
> When ever I fresh install I spend a fair bit of time editing .desktop categories to my liking...

I understand. But I failed.

Whenever I do a fresh install of Windoze, I bring along my own menu tree which fits all the tools that I need. Since Windoze programs have a habit of cluttering up the "Start Menu", I simply put my menu ABOVE (i.e., outside the main Start Menu hierarchy) - so that I CONTROL the menu (i.e., every program has a place and it goes in its place). 

Unfortunately, I tried long ago to create menus outside of "Applications", but I was defeated.
- [How to create a top-level menu (above the existing menus) in Ubuntu 10.04?]("http://ubuntuforums.org/showthread.php?t=1562680")             

> **lisati said:**
> It can depend on a number of things.

I have a pretty clear idea of where items 'should' go ... so ... I guess I'll try again to organize menus in a logical tree on Ubuntu.

If I can't create a logical menu outside of "Applications", I should at least be able to create it inside of "Applications", e.g.:

[LIST]
[*]Applications->Editors->Picture Editors->{pgm1, pgm2, pgm3, etc.}
[*]Applications->Editors->Video Editors->{pgm1, pgm2, pgm3, etc.}
[*]Applications->Editors->Text Editors->{pgm1, pgm2, pgm3, etc.}
[*]Applications->Editors->PDF Editors->{pgm1, pgm2, pgm3, etc.}
[*]etc. (note the need for at least two levels, preferably three)
[/LIST]
 > **satanselbow said:**
> Could be worse and go the windows route

I agree the (default) Windoze route is chaotic!
Most items are organized by brand name for heavens sake!
That's like organizing your toolbox by brand name instead of by what the tool does.

But, I feel I have total (logical) control over the Windows menus but not of the default menus on Ubuntu, unfortunately.

Here, by way of example, is my Windoze menu that I've been honing over the past decade for my use (refined each time I re-install the OS, which, for Windoze, is at least once a year).

This is the kind of menu tree I wish I could make on Ubuntu!

[LIST=1]
[*] [SIZE=1]Note 1: It is imperative to have more than two levels of menus!!![/SIZE]
[*][SIZE=1] Note 2: The only reason for the side menu is that, logically, vertical space is more precious (at least on my rather small laptop monitors) than is side space.[/SIZE]
[*][SIZE=1] Note 3: The only reason for being OUTSIDE of the main menu is to avoid having to undu the garbage that gets put in the "Start Menu" each time a program is installed. I leave the Start Menu alone so it's as chaotic as it wants to be.[/SIZE]
[*][SIZE=1] Note 4: Leaving the "Start Menu" alone allows a visitor to my PC to find stuff the way they always did without having to resort to 'my' menus. That's why I tried to create a menu on Ubuntu OUTSIDE of "Applications" (but I failed).[/SIZE]
[*][SIZE=1] Note 5: My particular logic in the menu tree below is not what's important - what's important is that 'a' particular logic can be outlined in the menu tree.[/SIZE]
[*][SIZE=1]Note 6: Names are shortened below (and never plural!) because of historic 8+3 restrictions which don't exist in Ubuntu.
[/SIZE]
[/LIST]
 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169583&stc=1&d=1284588772[/IMG]

---

### Post by mcduck on 2012-01-11
Gnome desktop actually has a pretty strict user interface guidelines, that are against the use of more than two levels in any menu. After that finding theings in menus becomes noticeably more confusing unless youa re the very person who arranged the menu oyurself.

Anyway, you don't need to edit the .desktop files by hand, just use the Alacarte menu editor (appears as "Main Menu" in Gnome's menus) and you can easily just drag & drop items between menu categories, create new ones and also add new submenus if you want deeper menu hierarchy.

(...and yes, Alacarte works for Unity, as well as any other XDG-compatible desktop environment / window manager)

---

### Post by grahammechanical on 2012-01-11
> I had thought there might be a committee or a logic-tree or something that the developers would be forced to follow in order to get into a repository. 

It is Linux that you are using and it is called Freedom. Ubuntu could not imposed this on developers. What can do is not make certain non-conforming applications available through the Ubuntu Software Centre. And Canonical is setting quality standards for applications to go in the Software Centre.

But that does not stop us installing an application through the terminal.

Regards.

Regards.

---

### Post by mcduck on 2012-01-11
> **grahammechanical said:**
> It is Linux that you are using and it is called Freedom. Ubuntu could not imposed this on developers. What can do is not make certain non-conforming applications available through the Ubuntu Software Centre. And Canonical is setting quality standards for applications to go in the Software Centre.

But that does not stop us installing an application through the terminal.

Regards.

Regards.

I'd say it's more of a question of many applications fitting just as well in many different categories, often depening on what the user is using the application for.

For example OpenOffice Draw would fit equally well under Graphics or Office categories. A CD burning tool wouldn't be wrongly placed under Accessories, but for somebody who uses it mostly with audio & movie discs "Sound & Video" would be a better category. And like Lisati said, tools related to disc images would fit easily under all Accessories, Sound & Video and System Tools-categories.

---

### Post by satanselbow on 2012-01-11
> **mcduck said:**
> 
Anyway, you don't need to edit the .desktop files by hand

Yeah I know - but where's the fun in that? :D

Menu's only get used when I'm feel too lazy to type the 1st couple of letters of an apps name these days anyhow ;)

---

### Post by mcduck on 2012-01-11
> **satanselbow said:**
> Yeah I know - but where's the fun in that? :D

Menu's only get used when I'm feel too lazy to type the 1st couple of letters of an apps name these days anyhow ;)

True, and of course if you *do* edit the .desktop files manually, you can at the same time add new options for the right-click menu in Unity's launcher...

---

### Post by rocksockdoc on 2012-01-11
> **mcduck said:**
> Gnome desktop...guidelines ... are against the use of more than two levels in any menu. 

But can more than two levels be created by the user? 

> **mcduck said:**
>  just use the Alacarte menu editor ...[to] create new ones and  also add new submenus if you want deeper menu hierarchy.

By that, I guess it can.

I guess my next job will be to figure out how to create sub->sub->menus! :)

> **mcduck said:**
> After that finding things in menus becomes noticeably more confusing unless you are the very person who arranged the menu 

I believe, on Windoze, I've solved that enigma. But I failed (miserably) on Ubuntu:
- [How to create a top-level menu (above the existing menus) in Ubuntu 10.04?]("http://ubuntuforums.org/showthread.php?t=1562680")             

To solve this problem in Windoze, I simply make a cascading "my applications" (or whatever named) menu for myself OUTSIDE the default Windoze "Start Menu".

That way, **I** get the menus **I** want ... while other users can either log into a different desktop for **their menus** ... or if they're stuck working with my desktop, they're welcome to the cluttered mess of the default "Start Menu".

It's the way menus should work.

Incidentally ... it's the way "applications" should work also!

Logically, I always try to put my programs and my menus in the SAME (but necessarily separate) logical tree.

For example, on Windoze, I shun "Program Files" (because it's a mess for the same reasons the "Start Menu" is a mess). 

[LIST]
[*]I create something like **C:\Applications** (the actual name is irrelevant; it could be c:\bin for all it matters but I've learned the moment I mention c:\bin to Windoze users, their eyes glaze over and they accuse me of trying to turn Windoze into UNIX. They misread logical intentions ... so I find they're infinitely happier if I call it something needlessly redundant like "C:My Programs".)
[*]Then under C:\Applications (or c:\bin or C:\My Programs) I have a logical tree.
[*]For example, here's a (simplified) snipped for my editing programs:
[LIST]
[*]C:\Applications\Editors\Picture Editors\{pgm1, pgm2, pgm3, etc.}
[*]C:\Applications\Editors\Video Editors\{pgm1, pgm2, pgm3, etc.}
[*]C:\Applications\Editors\Text Editors\{pgm1, pgm2, pgm3, etc.}
[*]C:\Applications\Editors\PDF Editors\{pgm1, pgm2, pgm3, etc.}
[*]etc. (A wily reader will note this is EXACTLY the same hierarchy as the menus listed previously!)
[/LIST]
 
[/LIST]
I would do the same thing under Ubuntu were I to better understand the installation process. 

This way, ALL programs are exactly where I expect them to be just like all menus are exactly where I expect them.

The genius of this is that both the  single instance of the program and the menu structure that mirrors that  installation tree use the SAME LOGIC!

I'd do this for Ubuntu ... but I'll leave organizing the /bin logical hierarchy the same as the menu logical hierarchy for a later date when I'm better at  understanding how Ubuntu works. For now, I'll just try to logically organize the menus.

> **mcduck said:**
> you don't need to edit the .desktop files by hand, just use the Alacarte menu editor

After having been defeated & demoralized, I'll try again to organize the menus to make better logical sense of them and post back the results. 

I realize not everyone has the same logic - so the best approach (I feel) would be a menu structure OUTSIDE (but right next to) the existing (admittedly confusing but not unusable) "Applications" menu. 

> **mcduck said:**
> I'd say it's more of a question of many applications fitting just as well in many different categories

Yes. But this is not a problem (for menus).

In my logical organization, there are times when an item fits into multiple categories. 

This is ok since a menu item is merely a link to an end result. 

Reflecting your apt example, you '**can**' have OpenOffice Draw under graphics editors and also under office applications. That's the beauty of menus!

It's (logically) OK to have the same program in two different menus if you feel that is your personal logic (personally I avoid duplication but I understand & agree with the concept).

> **mcduck said:**
> tools related to disc images would fit easily  under all Accessories, Sound & Video and System  Tools-categories.

And that's OK to fit under multiple categories (I avoid it - but I recognize the need at times).

What I find illogical is the extensive use of the common catchall of "Accessories" or "Utilities" ... which, by their very existence, are an implied admission of organizational laziness.

For the past two decades, I have NEVER used a category of  "Utilities" or "Accessories", as a matter of principle (everything can be considered a utility or an accessory). IMHO, things other people consider an accessory or utility 'do' have a logical place in my system.

Hint: If you ask me where I put anything on my Windoze computers, I can tell you ahead of time EXACTLY where they (logically) belong - without any need for a garbage-can "Accessory" or "Utilities" category!  :)

---

### Post by mcduck on 2012-01-11
Sure, the users can create as deep menu hierarchies as they want. At least I've never met any limit. And if duplicate menu entries is fine for you, you can of course do that as well. Alacarte should handle both easily. (they are just not considered as a good design for *default* desktop configuration)

I don't think there's any easy way to create a menu completely outside of the normal menu structure, but you could of course build a new one inside the existing one. Make it the first one and it should work pretty well for your purposes.

...actually one you've done that, you can even add that new menu as a icon of it's own to gnome-panel, if you want to. At least I remember being able to do that (it's been a while since I've used the Gnome2 desktop). You can do this for any existing menu category simply by dragging the menu entry to the panel, if I rember right, just like you can drag a launcher from menu to panel.

I actually find the "Accessories"-category pretty nice for all the simple, general-purpose tools like calculator, archive manager, basic text editor etc. (I don't have enough mathematics related apps to justify a Math category in menus so putting calculator into accessories seems like a better option.)

---

### Post by rocksockdoc on 2012-03-03
> **satanselbow said:**
> It can all be fixed to your own personal ordering by editing the relevant .desktop file - which will be found in /usr/share/applications...

For the record, the "Categories" in the .desktop files do not seem to be a one-to-one map to the actual menu entries.

[LIST]
[*]**[COLOR=DarkRed]Accessories[/COLOR]**->Furius ISO Mount===**[COLOR=DarkRed]Categories=Utility;DiscBurning;[/COLOR]**
[*]**[COLOR=DarkRed]Sound & Video[/COLOR]**->ISO Master===**[COLOR=DarkRed]Categories=AudioVideo;DiscBurning[/COLOR]**
[*]**[COLOR=DarkRed]System Tools[/COLOR]**->Gmount-iso===Categories doesn't even exist
[/LIST]
 For example, the desktop file for Applications->**[COLOR=DarkRed]Accessories[/COLOR]**->Furius ISO Mount is:
/usr/share/applications/furiusisomount.desktop
```
[Desktop Entry]
**[COLOR=DarkRed]Categories=Utility;DiscBurning;[/COLOR]**
Exec=furiusisomount
GenericName=Furius ISO Mount
Icon=furiusisomount
Name=Furius ISO Mount
Comment=Manage ISO, IMG, BIN, MDF and NRG images
Comment[it]=Gestire immagini ISO, IMG, BIN, MDF e NRG
Terminal=false
StartupNotify=true
Type=Application
X-AppInstall-Package=furiusisomount

```And for Applications->**[COLOR=DarkRed]Sound & Video[/COLOR]**->ISO Master is:
/usr/share/applications/isomaster.desktop
```
[Desktop Entry]
Name=ISO Master
GenericName=ISO File Editor
GenericName[ca]=Editor de fitxers ISO
GenericName[es]=Editor de ficheros ISO
Comment=Read, write and modify ISO images
Comment[ca]=Llegiu, escriviu i modifiqueu imatges ISO
Comment[es]=Leer, escribir i modificar imagenes ISO
Exec=isomaster
Terminal=false
StartupNotify=true
Type=Application
**[COLOR=DarkRed]Categories=AudioVideo;DiscBurning;[/COLOR]**
MimeType=application/x-iso;
Icon=/usr/share/icons/isomaster/isomaster.png
```And for Applications->**[COLOR=DarkRed]System Tools[/COLOR]**->Gmount-iso
 /usr/share/applications/gmount-iso.desktop
```
[Desktop Entry]
Type=Application
Name=Menu Editor
Icon=gnome-main-menu
Exec=gmenu-simple-editor
StartupNotify=true
NoDisplay=true
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-menus
X-GNOME-Bugzilla-Component=general
X-Ubuntu-Gettext-Domain=gnome-menus

```> **mcduck said:**
> you don't need to edit the .desktop files by hand, just use the Alacarte menu editor

I guess the Categories map to the following:

[LIST]
[*]**[COLOR=DarkRed]Accessories[/COLOR]** <== maps to ==>**[COLOR=DarkRed]Utility;DiscBurning;[/COLOR]**
[*]**[COLOR=DarkRed]Sound & Video[/COLOR]**<== maps to ==>**[COLOR=DarkRed]AudioVideo;DiscBurning[/COLOR]**
[*]**[COLOR=DarkRed]System Tools[/COLOR]** <== maps to ==> when Categories doesn't even exist
[/LIST]
I was expecting the "categories" to be "Accessories", "Sound & Video", & "System Tools" respectively above. 



  > **mcduck said:**
> Sure, the users can create as deep menu hierarchies as they want. At least I've never met any limit. And if duplicate menu entries is fine for you, you can of course do that as well. Alacarte should handle both easily. (they are just not considered as a good design for *default* desktop configuration)

Notice above that the Category "DiscBurning" is a duplicate menu entry for the first two items, yet, DiscBurning never shows up.

Why do they put duplicate Categories in the desktop files anyway?

> **mcduck said:**
> I don't think there's any easy way to create a menu completely outside of the normal menu structure, but you could of course build a new one inside the existing one. 

I'm trying to first figure out how they work! :)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213629&stc=1&d=1330789210[/IMG]

---

