---
title: "HOWTO: install new icon-themes?"
date: 2004-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by wulle on 2004-11-09
hello,
how can I install new iconthemes I downloaded from [www.gnome-look.org?](www.gnome-look.org?)

thx
wulle

---

### Post by ubuntu-geek on 2004-11-09
To install a new icon theme:
   
  >   Download the Icon theme tarball..
 cp tarball.tar.gz /home/username/.icons
   cd /home/username/.icons
   tar xfz tarball.tar.gz
   Goto **Computer > Desktop Preferences > Themes** to change to the new Icon theme.  If you do not have a .icons directory you can create one:
   > mkdir -p /home/username/.icons

---

### Post by wulle on 2004-11-09
to ubuntugeek,

thank's a lot for your quick answer.
kind regards
wulle

---

### Post by mattyh on 2004-11-12
For some odd reason, I have tried twice now to install new icon themes, and yet when I get to the point of trying to add them in through the themes manager, I click ok, and they never show up.  This is very odd.

---

### Post by kamstrup on 2004-11-12
> ... trying to add them in through the themes manager ... The point was that you can't /add/ them through the themes manager (this is very odd indeed), but you have to extract the icon-theme into ~/.icons, and then select it (not install) from the theme manager (click the Details button or what it is called...).

Hope you get it to work. Cheers.

---

### Post by TravisNewman on 2004-11-12
[QUOTE=kamstrup]The point was that you can't /add/ them through the themes manager (this is very odd indeed), but you have to extract the icon-theme into ~/.icons, and then select it (not install) from the theme manager (click the Details button or what it is called...).

Hope you get it to work. Cheers.[/QUOTE]
 Yes, I've often wondered what the add dialog actually does, since you have to extract them manually. Is it if you extracted it somewhere else besides .icons?

---

### Post by mattyh on 2004-11-12
For some reason, after untarring them into .icons, they don't show up in the dialog... very odd

---

### Post by umarmung on 2004-11-12
[QUOTE=panickedthumb]Yes, I've often wondered what the add dialog actually does, since you have to extract them manually. Is it if you extracted it somewhere else besides .icons?[/QUOTE]

Indeed. All archives are extracted to .themes. The theme-dialog doesn't check if the package contains an icon, gtk or metacity theme. 
 #-o

---

### Post by TravisNewman on 2004-11-12
Excellent, that's what I needed to know :)

---

### Post by wallijonn on 2004-11-19
[SIZE=1]I usually don't even bother untar'ing / extract'ing them. I just drop the whole file into the "Show details" theme window. Icons themselves are a different matter if you want to manually select them. Just right click an icon, change icon, to see where the icons are stored. [/SIZE]

[Edit][SIZE=3]
Download the Icon file, double click it to extract the files.
[COLOR=Blue]Computer -> Home-> View -> Show Hidden Files[/COLOR]
Copy or move the extracted icon folder to the [COLOR=Red].icons[/COLOR] folder
[COLOR=Blue]Computer -> Desktop Preferences -> Theme -> Theme Details ->[/COLOR] Icon Tab -> Select the Icon package just installed. 
[/SIZE]

---

### Post by gabbman on 2004-12-11
> ndeed. All archives are extracted to .themes. The theme-dialog doesn't check if the package contains an icon, gtk or metacity theme.

So if I have it installed in ~.themes and ~.icons and I don't see the iconset in the themes managers, then something is wrong?

I am used to the kde way of seeing what I am selecting, so I may need a lesson in how to on this one.

---

### Post by bslgw on 2004-12-14
I have copy same icon-theme  to ".cion" but can not find anything into the theme manage .Who can tell me WHY???? 

thx

---

### Post by a.stefanou on 2004-12-28
click > computer> home then click file menu "View">show hidden files

........
now you can see your normal folders + hidden folders...
........
Folder:

.themes > there is all your custome themes that you create... or drag and drop your newst...

.icons > there is all your install icons... or again  :D  drag and drop your newst...

.xmms/skins> put your skins for your xmms music player... 
...........


 =D>  that's it...

---

### Post by amendron220 on 2007-05-15
> **a.stefanou said:**
> click &gt; computer&gt; home then click file menu &quot;View&quot;&gt;show hidden files

........
now you can see your normal folders + hidden folders...
........
Folder:

.themes &gt; there is all your custome themes that you create... or drag and drop your newst...

.icons &gt; there is all your install icons... or again  :D  drag and drop your newst...

.xmms/skins&gt; put your skins for your xmms music player... 
...........


 =D&gt;  that's it...


[Bankruptcy generator Mortgages Equity Line Credit physics](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

### Post by xjgnsdof on 2007-11-09
I installed my icon themes in Gutsy without using the shell. In System -> Preferences -> Appearance, select "Install..." in the Themes tab. Select the .tar file containing the icon theme and select Apply if you're so inclined.

---

### Post by smartboyathome on 2007-11-09
> **elgilicious said:**
> I installed my icon themes in Gutsy without using the shell. In System -> Preferences -> Appearance, select "Install..." in the Themes tab. Select the .tar file containing the icon theme and select Apply if you're so inclined.

This thread was done back in 2004, when this functionality wasn't available. :(

---

### Post by stnsgeneral on 2007-12-02
I tried following the first directions, but could not find the Computer -> Desktop Preferences place, so I kept reading and using an adaptation of elgilicious's post, I managed to get them working.  I used, System -> Preferences -> Appearance, then selecting the theme that I wanted to use.  Then I hit "Customize -> Icons" and presto, there was the icons that I had wanted.  Hopefully this helps someone.

---

### Post by yomeh on 2007-12-09
cheers this worked for me

---

### Post by Skillachi on 2008-07-11
this doesnt work for me in hardy...

edit: it does work... it seems whoever did this damn icon pack needs to be shot

---

### Post by minhaaj on 2008-07-14
> **wallijonn said:**
> [SIZE=1]I usually don't even bother untar'ing / extract'ing them. I just drop the whole file into the "Show details" theme window. Icons themselves are a different matter if you want to manually select them. Just right click an icon, change icon, to see where the icons are stored. [/SIZE]

[Edit][SIZE=3]
Download the Icon file, double click it to extract the files.
[COLOR=Blue]Computer -> Home-> View -> Show Hidden Files[/COLOR]
Copy or move the extracted icon folder to the [COLOR=Red].icons[/COLOR] folder
[COLOR=Blue]Computer -> Desktop Preferences -> Theme -> Theme Details ->[/COLOR] Icon Tab -> Select the Icon package just installed. 
[/SIZE]
I dont get it. under my .icons i got to apps and all icons are there but ubuntu won't use it. how do i use them. do i have to extract the folder and paste it as it is under .icons? and then go to theme and customize and go to icons and choose that folder ? thats confusing

---

### Post by Salvagluque on 2009-08-26
in ubuntu intrepid ibex 8.10 you must copy your icons to /usr/share/icons
maybe that's why in the very first post made back in 2004 they couldn't use them.

sudo nautilus from a terminal. So you can paste your icons in the folder.

greetings

---

### Post by SPARTAN-118 on 2009-09-19
It's weird, but, for some *STRANGE* reason, many of my icon packs only apply some of the icons.

For example, my nuoveXT-aero (or whatever it's called) icon pack only makes the .tar.gz icons vista-folder-like, not the actual folder icons themselves.

Any ideas as to why it's not working?

---

### Post by rs_man on 2009-10-04
Great! I was trying to add my icons to the ~/share/icons folder. Banging my head against the wall I set out to find out why I could not access that folder: coming across this I remembered that you typically dont want to work under root (potential user created problems). Thanks to the OP and ubuntu-geek. 
 
> **SPARTAN-118 said:**
> It's weird, but, for some *STRANGE* reason, many of my icon packs only apply some of the icons.

For example, my nuoveXT-aero (or whatever it's called) icon pack only makes the .tar.gz icons vista-folder-like, not the actual folder icons themselves.

Any ideas as to why it's not working?

You may want to make sure there are icons for all the items: my $0.02.

---

### Post by motio on 2009-10-04
Download the Icon theme tarball..
extract to /home/username/.icons
open termilnal 
cd to /home/username/.icons
chmod +x Install
./Install
after Goto Syestem >  Preferences > apearance > Themes>customize>icons to change to the new Icon theme.

---

### Post by fela on 2009-10-04
Can you please not label a support question with HOWTO. This gives the impression that it's a howto.

Just my £0.02

---

### Post by SPARTAN-118 on 2009-10-04
> **fela said:**
> Can you please not label a support question with HOWTO. This gives the impression that it's a howto.

Just my £0.02

Two cents, two euros.... what's the difference?

Oh, and BTW, I just downloaded the "Linux Broken Vista" icon pack, and everything works fine.

I guess it's because the author put all the "scalable" icons in "extras," so I would have had to re-organize everything. 

*Not* worth my $0.02.

---

### Post by wombatvvv on 2010-06-01
I've been struggling with this a bit myself, but have finally got it figured out now, thanks to this thread.

I find it a bit silly that the Theme Manager doesn't correctly install the icons. If I choose to install the icons, through the Theme Manager, they do appear in the icons list, but they don't change anything once selected. However, if I install manually (as above), then they work fine (and look great!).

The other thing is that most of the icon sets that ship with Ubuntu 1.0.4 seem not to work. They all just appear as orange folders in the icons tab and don't change anything when selected.

---

### Post by lanetherif on 2010-06-03
Hi,
sort of the same problem in here...

I am not able to use the newly installed icon packs, at least not wholly. 
I've downloaded a few icon packs from package manager and two manually. I am trying to use G-Flat SVG icon pack. It seems to work fine with navigation buttons both in Gnome and in programs such as Firefox. Yet, folder icons somehow fall back to default Gnome icon theme. 
I've read a post in a blog which tells adding another folder in icon's directory named /places and editing index.theme respectively has solved the problem. I did it, it didn't worked. I copied the icon theme directory to /usr/share/icons, it was a desperate attempt and as I expected it also didn't work.
This is the index.theme file the icon theme uses:
```
# The Flat icon theme for GNOME
# Flat icons that are the work of Danny Allen (danny@dannyallen.co.uk) have been used with permission from the author.
# Original Flat icon conversion by Exdaix
# Stock gnome icons, emblems, misc applications, and gnome specific enhancements added 12/05 by poptones
# Versioning for this GNOME port does not explicitly follow the versioning of the original KDE icon set 
# as this set has become more completely gnome-centric and so does not include most kde applications.

[Icon Theme]
Name=G-Flat SVG 0.99

inherits=gnome
Directories=scalable/apps,scalable/mimetypes,scalable/emblems,scalable/devices,scalable/stock,scalable/stock/media,scalable/stock/net,24x24/stock,24x24/stock/media,24x24/stock/net,scalable/places
Example=gnome-theme-preview.svg

[scalable/actions]
MinSize=1
Size=48
MaxSize=256
Context=Actions
Type=scalable

[scalable/apps]
MinSize=1
Size=48
MaxSize=256
Context=Applications
Type=scalable

[scalable/devices]
MinSize=1
Size=48
MaxSize=256
Context=Devices
Type=scalable

[scalable/emblems]
Size=72
Context=Emblems
Type=Scalable

[scalable/places]
MinSize=1
Size=48
Maxsize=128
Context=Places
Type=Scalable

[scalable/mimetypes]
MinSize=1
Size=48
MaxSize=128
Context=MimeTypes
Type=Scalable

[scalable/stock]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable

[scalable/stock/net]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable

[scalable/stock/media]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable

[scalable/stock/navigation]
MinSize=1
Size=48
MaxSize=128
Context=Stock
Type=scalable


[24x24/stock]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

[24x24/stock/net]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

[24x24/stock/media]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24

[24x24/stock/navigation]
MinSize=1
Size=128
MaxSize=24
Context=Stock
Type=24x24
```Any idea will be appreciated.

edit: I just figured out, the index.theme is missing scalable/filetypes and the entry about it. I included them in the file on my computer. The existence or omission of it doesn't change the situation -though it may corrupting some other thing.

---

### Post by lanetherif on 2010-06-13
Any ideas?

---

### Post by Topazgb on 2010-10-10
Select the theme and 'Customise', then select the icons tab.  Choose the icon theme then save the theme that you have created.

---

### Post by jeffersonthought on 2011-07-21
Thanks guys had similar problems but the help got me through it all. Love me some themes!:D

---

