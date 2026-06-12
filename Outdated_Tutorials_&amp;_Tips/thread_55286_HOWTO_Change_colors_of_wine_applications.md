---
title: "HOWTO: Change colors of wine applications"
date: 2005-08-08
forum: Outdated Tutorials &amp; Tips
---

### Post by minio on 2005-08-08
Because i've found default colors of wine applications too dark, i tried to found if it's possible to change it to something brighter or better to change colors to match colors of GTK theme. And i succeded :). So if you want to change look of your wine then open ~/.wine/user.reg in text editor : ```
gedit ~/.wine/user.reg
``` and replace line```
[Control Panel\\Colors] some numbers
``` with ```
[Control Panel\\Colors] 1122940464
"ActiveBorder"="154 154 154"
"ActiveTitle"="0 0 0"
"AppWorkSpace"="154 154 154"
"Background"="246 246 246"
"ButtonAlternativeFace"="200 0 0"
"ButtonDkShadow"="154 154 154"
"ButtonFace"="246 246 246"
"ButtonHilight"="238 238 238"
"ButtonLight"="246 246 246"
"ButtonShadow"="238 238 238"
"ButtonText"="0 0 0"
"GradientActiveTitle"="213 166 55"
"GradientInactiveTitle"="213 166 55"
"GrayText"="128 128 128"
"Hilight"="100 132 164"
"HilightText"="255 255 255"
"InactiveBorder"="246 246 246"
"InactiveTitle"="193 197 171"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="246 246 246"
"Menu"="246 246 246"
"MenuBar"="0 0 0"
"MenuHilight"="100 132 164"
"MenuText"="0 0 0"
"Scrollbar"="246 246 246"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="154 154 154"
"WindowText"="0 0 0"
``` 


These colors match Industrial theme, but you can change them as you wish to make them match your theme colours. Values are in "R G B" format.
And sorry for my english :)
Now if you start your windows application it should look something like this:

---

### Post by chazm on 2005-08-08
[QUOTE=minio]Because i've found default colors of wine applications too dark, i tried to found if it's possible to change it to something brighter or better to change colors to match colors of GTK theme. And i succeded :). So if you want to change look of your wine then open ~/.wine/user.reg in text editor : ```
gedit ~/.wine/user.reg
``` and replace line```
[Control Panel\\Colors] some numbers
``` with

.......

These colors match Industrial theme, but you can change them as you wish to make them match your theme colours. Values are in "R G B" format.
And sorry for my english :)
Now if you start your windows application it should look something like this:[/QUOTE]
 Looks nice, I'll have to try it :)

---

### Post by kiddyfurby on 2005-08-09
wt abt crossover office?

i have user.reg in /opt/cxoffice/somewhere

but modifying it like u doesn't help :(

---

### Post by phi6 on 2005-08-11
My god, jesus bloody christ (forgive my blasphemy... but....) I've been searching for a way to do this for ages.

Finally, my Wine windows no longer look like default Win98 colour schemes (ugly!) and now look like my linux.

Brilliant.

Seamless integration with wine.

!!!

---

### Post by benplaut on 2005-09-19
okey dokey... figured this out in Crossover Office, plus rethemed a bit. Here's mine, based off of Whiteplate theme:

~/.cxoffice/dotwine/user.reg

```
[Control Panel\\Colors] 1105779303
"ActiveBorder"="240 240 240"
"ActiveTitle"="240 240 240"
"AppWorkSpace"="198 198 191"
"Background"="93 77 52"
"ButtonAlternativeFace"="216 216 216"
"ButtonDkShadow"="85 85 82"
"ButtonFace"="240 240 240"
"ButtonHilight"="255 255 255"
"ButtonLight"="255 255 255"
"ButtonShadow"="198 198 191"
"ButtonText"="0 0 0"
"GradientActiveTitle"="240 240 240"
"GradientInactiveTitle"="240 240 240"
"GrayText"="198 198 191"
"Hilight"="119 153 221"
"HilightText"="0 0 0"
"InactiveBorder"="240 240 240"
"InactiveTitle"="240 240 240"
"InactiveTitleText"="255 255 255"
"InfoText"="0 0 0"
"InfoWindow"="216 216 216"
"Menu"="240 240 240"
"MenuBar"="0 0 0"
"MenuHilight"="179 145 105"
"MenuText"="0 0 0"
"Scrollbar"="240 240 240"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"
``` 

If anyone has the time, see if you can figure out how to get fonts working from this page: [http://justlinux.com/forum/showthread.php?t=141123](http://justlinux.com/forum/showthread.php?t=141123)

i can't quite figure out what he's trying to do...

Here are the important bits, for making your own (it's in simple R G B):

Everything that says 240, that's the base color of your theme... the bcakground behind everything.

The "Hilight" is the color of mouse-overs... right now, it's a nice light blue. Be careful with "HilightText", it's actually the color of selected entries when opening and closing a file. "InfoWindow" is for tooltips. Those are all i've messed with, and, i must say, it looks pretty darn swell! Pics attached... someone please figure out somethign with the fonts :/

---

### Post by Draku on 2007-02-28
Maybe a litle late (2 years since last post :P) but why not use the Windows XP Royale Theme :P download from here : [http://www.softpedia.com/get/Desktop-Enhancements/Themes/Royale-Theme-for-WinXP.shtml](http://www.softpedia.com/get/Desktop-Enhancements/Themes/Royale-Theme-for-WinXP.shtml)
Fire UP the exe inside the archive with Wine and after installation go to your winecfg Desktop tab and select the theme. Work like a charm :popcorn:

---

### Post by pt123 on 2007-05-06
Thanks is it possible to put a image on the wine desktop as the background?

---

### Post by Super Jamie on 2007-08-09
many months too late, but this page has good google rating

here are wine xp settings, which i lifted from [http://www.winehq.org/pipermail/wine-bugs/2004-August/010161.html](http://www.winehq.org/pipermail/wine-bugs/2004-August/010161.html)

> These are the colors from a Windows XP Professional installation, they do an
amazing job of making the WINE user experience quite a bit more enjoyable
without any changes to the source!

~/.wine/user.reg:

[Control Panel\\Colors] 1085191500
"ActiveBorder"="212 208 200"
"ActiveTitle"="10 36 106"
"AppWorkSpace"="128 128 128"
"Background"="58 110 165"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="64 64 64"
"ButtonFace"="212 208 200"
"ButtonHilight"="255 255 255"
"ButtonLight"="212 208 200"
"ButtonShadow"="128 128 128"
"ButtonText"="0 0 0"
"GradientActiveTitle"="166 202 240"
"GradientInactiveTitle"="192 192 192"
"GrayText"="128 128 128"
"Hilight"="10 36 106"
"HilightText"="255 255 255"
"HotTrackingColor"="0 0 128"
"InactiveBorder"="212 208 200"
"InactiveTitle"="128 128 128"
"InactiveTitleText"="212 208 200"
"InfoText"="0 0 0"
"InfoWindow"="255 255 225"
"Menu"="212 208 200"
"MenuBar"="212 208 200"
"MenuHilight"="0 0 0"
"MenuText"="0 0 0"
"Scrollbar"="212 208 200"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"

---

### Post by tomauty on 2007-09-02
> **Draku said:**
> Maybe a litle late (2 years since last post :P) but why not use the Windows XP Royale Theme :P download from here : [http://www.softpedia.com/get/Desktop-Enhancements/Themes/Royale-Theme-for-WinXP.shtml](http://www.softpedia.com/get/Desktop-Enhancements/Themes/Royale-Theme-for-WinXP.shtml)
Fire UP the exe inside the archive with Wine and after installation go to your winecfg Desktop tab and select the theme. Work like a charm :popcorn:

Oh god thank you. I've been trying to fix the colors to look like that for a while.

---

### Post by ubuntios on 2007-10-26
Very good job minio,
Really  nice!!!

---

### Post by zora123 on 2007-10-26
i really thank you, minio.
i've been trying to find a way to change the color.
:)

---

### Post by Can+~ on 2007-10-27
AWESOME! I was looking forward to this.

Thank you, now I can really use fireworks without that "**** this is an fugly app" feeling. :guitar:

Here's how it looks: [http://img.photobucket.com/albums/v517/CanXp/fireawesome.jpg](http://img.photobucket.com/albums/v517/CanXp/fireawesome.jpg)

---

### Post by mdpalow on 2007-10-28
Can someone pls help me on this. I've done exactly (I believe) what is required here and nothing looks any different for me.

I opened the /home/mynameishere/.wine/user.reg file and replaced with this:

[Control Panel\\Colors] 1085191500
"ActiveBorder"="212 208 200"
"ActiveTitle"="10 36 106"
"AppWorkSpace"="128 128 128"
"Background"="58 110 165"
"ButtonAlternateFace"="181 181 181"
"ButtonDkShadow"="64 64 64"
"ButtonFace"="212 208 200"
"ButtonHilight"="255 255 255"
"ButtonLight"="212 208 200"
"ButtonShadow"="128 128 128"
"ButtonText"="0 0 0"
"GradientActiveTitle"="166 202 240"
"GradientInactiveTitle"="192 192 192"
"GrayText"="128 128 128"
"Hilight"="10 36 106"
"HilightText"="255 255 255"
"HotTrackingColor"="0 0 128"
"InactiveBorder"="212 208 200"
"InactiveTitle"="128 128 128"
"InactiveTitleText"="212 208 200"
"InfoText"="0 0 0"
"InfoWindow"="255 255 225"
"Menu"="212 208 200"
"MenuBar"="212 208 200"
"MenuHilight"="0 0 0"
"MenuText"="0 0 0"
"Scrollbar"="212 208 200"
"TitleText"="255 255 255"
"Window"="255 255 255"
"WindowFrame"="0 0 0"
"WindowText"="0 0 0"

I started Photoshop 7 and NOTHING looks different. What am I missing?

Thanks very much in advance to anyone who'll take a minute to explain...

P.S. I also used this number as specified in the previous posts:

1085191500   (this number is at the top next to control panel colors)

EDIT:

Ultimately found Wine to be less than I hoped for, so I installed VMware and loaded Win XP into a virtual server and loaded Photoshop and Dreamweaver. Now they work perfectly.

---

### Post by ice60 on 2007-10-28
i'm using Luna Element themes 8)
[http://tornado5.deviantart.com/art/Luna-Element-v5-1-Blue-47567543](http://tornado5.deviantart.com/art/Luna-Element-v5-1-Blue-47567543)
[http://gelosea.deviantart.com/art/Luna-Element-v5-1-Black-57571128](http://gelosea.deviantart.com/art/Luna-Element-v5-1-Black-57571128)

here's the blue one.

---

### Post by ice60 on 2007-10-28
here's the ubuntu theme :lolflag:
[http://fioressj.deviantart.com/art/Human-for-Windows-37743373](http://fioressj.deviantart.com/art/Human-for-Windows-37743373)

---

### Post by Andrej Danilov on 2007-10-28
This is an great Tutorial nice done m8

---

### Post by ice60 on 2007-10-28
here's a black one -
[http://lassekongo83.deviantart.com/art/Lakrits-Visual-Style-59440359](http://lassekongo83.deviantart.com/art/Lakrits-Visual-Style-59440359)

EDIT here's some more -
MurrinaFancyClearlooks
[http://wingnome-xp.deviantart.com/art/MurrinaFancyClearlooks-65562925](http://wingnome-xp.deviantart.com/art/MurrinaFancyClearlooks-65562925)

SmoothGnome for Windows XP
[http://schmoove.deviantart.com/art/SmoothGnome-for-Windows-XP-14772543](http://schmoove.deviantart.com/art/SmoothGnome-for-Windows-XP-14772543)

Murrina 'Dark' Chocolate
[http://wingnome-xp.deviantart.com/art/Murrina-Dark-Chocolate-65990170](http://wingnome-xp.deviantart.com/art/Murrina-Dark-Chocolate-65990170)

i know this is OT but here's an xmms/bmp skin :D TangoFancyClearlooks
[http://wingnome-xp.deviantart.com/art/TangoFancyClearlooks-67587428](http://wingnome-xp.deviantart.com/art/TangoFancyClearlooks-67587428)

---

### Post by mdpalow on 2007-10-28
Ok, so no one wanted to help me with my question, but instead I got a few themes to download and try. :) 

That's OK though 'cause I took the HUMAN theme and appreciate it very much.

However, there's one problem with the HUMAN theme and two others I found on the Internet:

->  It causes my Window$ applications to run slower. 

I see the HUMAN theme for instance is loading more colors to the Wine/Window$ app. as opposed to the one that runs faster.

Is anyone else running a theme and finds their app. running a little slower? How can I fix this?

I'm running:

AMD 64 Athelon 3500
Nvidia FX 5200 w/ 128 megs of RAM
1 Gig of DDR Mem
3 Gig Swap Drive

I can only imagine it is the Video Card, but even that seems suspect. I would think the theme would allow the app. to still run as quickly as another one that I'm using that doesn't color-up the app. as much.

Pls help with thoughts.

Thanks...

P.S. As long as I'm asking questions, I might as well throw this other one out there as well....

Whenever I run Firefox or any app. for that matter in Ubuntu or Wine - the top bar (where the title of the app. is located) seems to gray out and the minimize, maximize, and close buttons on the top, far right kind disappear. If I move my mouse over the buttons in the top, far right corner - they come back. Any thoughts?

---

### Post by ice60 on 2007-10-28
i didn't notice my wine program running slower, it does go crazy when i switch themes, resize the window, startup etc, when it's being drawn i suppose, but no longer then a second then it goes back to normal.

does compiz use emerald? maybe compiz-emerald?? that might be the problem with the buttons part of the windows.

---

### Post by KillerKiwi on 2007-10-28
I've started this... it grabs the color scheme from GTK and produces a wine user.cfg  at least it will

```
#!/usr/bin/env python
import pygtk
pygtk.require("2.0")
import gtk


def format_color_string( Color ):
	return "%s %s %s" % (Color.red /256, Color.green/256,  Color.blue/256)
	
def format_color_key( key, Color):
	return "\"%s\"=\"%s\"\n" % (key, format_color_string( Color ))
	
style = gtk.Style()

user_reg = """WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\\\Colors]
"""

# REF - http://www.moeraki.com/pygtkreference/pygtk2reference/class-gtkstyle.html
user_reg += format_color_key('ButtonHilight', style.bg[gtk.STATE_ACTIVE] )
user_reg += format_color_key('ButtonLight', style.bg[gtk.STATE_NORMAL] )
user_reg += format_color_key('ButtonShadow', style.dark[gtk.STATE_NORMAL] )
user_reg += format_color_key('ButtonText', style.text[gtk.STATE_NORMAL] )
user_reg += format_color_key('ButtonFace', style.bg[gtk.STATE_PRELIGHT])

print user_reg 
```

It should just be a matter of finding the correct mappings from here.....

---

### Post by mdpalow on 2007-10-29
do I copy this into a file and then run it? Can you pls explain this a little more detailed for the novice. :)

Thanks in advance...

---

### Post by MemoryDump on 2007-10-29
> **KillerKiwi said:**
> I've started this... it grabs the color scheme from GTK and produces a wine user.cfg  at least it will

```
#!/usr/bin/env python
import pygtk
pygtk.require("2.0")
import gtk


def format_color_string( Color ):
	return "%s %s %s" % (Color.red /256, Color.green/256,  Color.blue/256)
	
def format_color_key( key, Color):
	return "\"%s\"=\"%s\"\n" % (key, format_color_string( Color ))
	
style = gtk.Style()

user_reg = """WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\\\Colors]
"""

# REF - http://www.moeraki.com/pygtkreference/pygtk2reference/class-gtkstyle.html
user_reg += format_color_key('ButtonHilight', style.bg[gtk.STATE_ACTIVE] )
user_reg += format_color_key('ButtonLight', style.bg[gtk.STATE_NORMAL] )
user_reg += format_color_key('ButtonShadow', style.dark[gtk.STATE_NORMAL] )
user_reg += format_color_key('ButtonText', style.text[gtk.STATE_NORMAL] )
user_reg += format_color_key('ButtonFace', style.bg[gtk.STATE_PRELIGHT])

print user_reg 
```

It should just be a matter of finding the correct mappings from here.....

omg this worked like a charm!! thxs

> **mdpalow said:**
> do I copy this into a file and then run it? Can you pls explain this a little more detailed for the novice. :)

Thanks in advance...
to answer mdpalow's question..
copy and paste the code provided in a new document.. like getcolors.py for example.
then in a shell simply type: python getcolors.py
it'll spit out the colors you can copy and paste in your user.reg file as described in the first post. Good luck! :D

---

### Post by KillerKiwi on 2007-10-29
A bit more tweaking.... the mappings still arnt correct but its closer

```
#!/usr/bin/env python
import pygtk
import gtk


def format_color_string( Color ):
	return "%s %s %s" % (Color.red /256, Color.green/256,  Color.blue/256)
	
def format_color_key( key, Color):
	return "\"%s\"=\"%s\"\n" % (key, format_color_string( Color ))
	

invisible1 = gtk.Invisible()
style1 = invisible1.style

button1 = gtk.Button()
buttonstyle = button1.style

scroll1 =  gtk.VScrollbar()
scrollbarstyle = scroll1.style

menu1 = gtk.Menu()
menuitem1 = gtk.MenuItem()
menu1.add(menuitem1)
menustyle = menuitem1.style

user_reg = """WINE REGISTRY Version 2
;; All keys relative to \\User\\S-1-5-4

[Control Panel\\\\Colors]
"""

# http://www.moeraki.com/pygtkreference/pygtk2reference/class-gtkstyle.html
# http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html

user_reg += format_color_key('Scrollbar', scrollbarstyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Background', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ActiveTitle', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('InactiveTitle', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('Menu', menustyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Window', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('WindowFrame', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('MenuText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('WindowText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('TitleText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ActiveBorder', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('InactiveBorder', menustyle.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('AppWorkSpace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('Hilight', menustyle.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('HilightText', style1.bg[gtk.STATE_PRELIGHT])
user_reg += format_color_key('ButtonFace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonShadow', style1.bg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('GrayText', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('ButtonText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InactiveTitleText', style1.fg[gtk.STATE_INSENSITIVE])
user_reg += format_color_key('ButtonHilight', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonShadow', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonLight', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InfoText', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('InfoWindow', style1.fg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonAlternateFace', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('ButtonHilight', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('GradientActiveTitle', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('GradientInactiveTitle', style1.bg[gtk.STATE_NORMAL])
user_reg += format_color_key('MenuHilight', menustyle.bg[gtk.STATE_NORMAL])

print user_reg 


```

---

### Post by dnns123 on 2007-11-09
Thanks! But I think its too bright :P

---

### Post by mscir on 2008-03-01
Thanks, that looks a lot better. 

My menu text (Ubuntu 7.10) is still grey instead of black, is there any way to fix that?

---

### Post by bg1256 on 2008-04-25
[http://tombuntu.com/index.php/2008/01/04/stop-wine-from-beating-your-windows-apps-with-the-ugly-stick/](http://tombuntu.com/index.php/2008/01/04/stop-wine-from-beating-your-windows-apps-with-the-ugly-stick/)

---

### Post by LeeU on 2008-06-18
> **Super Jamie said:**
> many months too late, but this page has good google rating

here are wine xp settings, which i lifted from [http://www.winehq.org/pipermail/wine-bugs/2004-August/010161.html](http://www.winehq.org/pipermail/wine-bugs/2004-August/010161.html)

Sweet! Thanks!

---

### Post by WillemToerien on 2008-06-18
> **ice60 said:**
> here's the ubuntu theme :lolflag:
[http://fioressj.deviantart.com/art/Human-for-Windows-37743373](http://fioressj.deviantart.com/art/Human-for-Windows-37743373)

I've installed the theme in wine, and it looks great.

...however... its way slower and eats a ton of your cpu usuage just by for example selecting another tab.

---

### Post by Endolith on 2008-08-01
> **KillerKiwi said:**
> A bit more tweaking.... the mappings still arnt correct but its closer

I decided to take a stab at fulfilling my own request in [Bug 111061]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/111061").  While researching, I found that you had already done much of the work for me.  :)

I fixed some mappings and got it working so that it does everything automatically now; reads the color codes from various places, creates a .reg file, and then imports that into the Wine registry.  So you just run the script once after changing themes and it updates.  Although some of your choices looked better than nothing, and work pretty well on some themes, they don't work on all, so I've disabled them for now so we can find the real settings.  It's a lot harder than I expected to get the correct colors that the system is currently using:
[LIST]
[*]'ActiveBorder' = Active window border
[*]'ActiveTitle' = Left end of active title bar
[*]'GradientActiveTitle' = Right end of active title bar
[*]'GradientInactiveTitle' = Right end of inactive title bar
[*]'InactiveBorder' = Inactive window border
[*]'InactiveTitle' = Left end of inactive title bar
[*]'InactiveTitleText' = Inactive title bar text
[*]'TitleText' = Active title bar text
[/LIST]
Aren't all of these defined by the window manager; not GTK?  How do we access those settings?  There's a metacity module for python, but I can't find any documentation.

[LIST]
[*]'AppWorkSpace' = Background color of multiple-document interface
[/LIST]
Seems like Gnome has pretty much abandoned MDIs, and I don't know where to read this color from.  Seems like a GTK setting, though.

[LIST]
[*]'Background' = Gnome desktop color
[/LIST]
I scraped this from gconf, but there might be a better way.

[LIST]
[*]'HotTrackingColor' = Single-click navigation hover color
[/LIST]
Is there an equivalent of this in Gnome?  It's used in Windows Explorer and Internet Explorer as the hover color for single-click navigation.

[LIST]
[*]'InfoText' = ToolTip text
[*]'InfoWindow' = ToolTip background
[/LIST]
I think this is in GTK, but I don't know where to look.   

tooltips1 = gtk.Tooltips() ?

'gtk.Tooltips' object has no attribute 'style'

[LIST]
[*]'Menu' = Background for menus, also background for menu bars in 3D mode
[*]'MenuBar' = Background for menu bars - rarely seen with 3D menus
[*]'MenuHilight' = Highlight for flat menus - in 3D mode, Hilight is used instead
[*]'MenuText' = Menu text
[/LIST]
The menustyle.bg thing returns values for these, but they don't usually match with the theme.  For instance, menustyle.bg[gtk.STATE_SELECTED] gives me a blue in the Human theme, when the selected menu background is actually yellow.  I don't get it.  (Note that these really only work in Wine when you [enable flat menus]("http://blogs.msdn.com/tonyschr/archive/2004/05/10/129412.aspx").)

[LIST]
[*]'Scrollbar' = Background color of scrollbar, but only in some apps.
[/LIST]
I don't think scrollbarstyle.bg[gtk.STATE_NORMAL] matches the real color, either.

If anyone can help with this, it would be very appreciated.

Also, it took me a while (and tweaking in actual Windows) to figure out what all the Wine registry values do.  Some are obvious, but others are not.  I still don't know what ButtonAlternateFace does.  (As far as I can tell, "ButtonAlternativeFace" is just a typo of "ButtonAlternateFace".)  I wish there were more documentation for this, but I'll post what I've found somewhere so that others don't have to reverse-engineer it again like I did.

I also want to look into importing font faces, sizes, and widget sizes as well.  I'm sure some of these would be a further improvement, while others would just make Wine look stupid.

Attached is the script [s]as well as a spreadsheet of all the registry values and the mappings I've found[/s].  This is my first Python script; be nice. :)

Edit: Latest version is on Launchpad: [http://bazaar.launchpad.net/~endolith/%2Bjunk/wine-color-scraper/files](http://bazaar.launchpad.net/~endolith/%2Bjunk/wine-color-scraper/files)

---

### Post by Endolith on 2008-08-03
The spreadsheet of Wine color names is too big to upload here, but I created a page explaining them all anyway:

[http://www.endolith.com/wordpress/2008/08/03/wine-colors/](http://www.endolith.com/wordpress/2008/08/03/wine-colors/)

---

### Post by KillerKiwi on 2008-08-05
> **Endolith said:**
> The spreadsheet of Wine color names is too big to upload here, but I created a page explaining them all anyway:

[http://www.endolith.com/wordpress/2008/08/03/wine-colors/](http://www.endolith.com/wordpress/2008/08/03/wine-colors/)

Nice work... I just looked at the code that mono "was" using for its winforms code (they have since changed there method) as it mimics the gtk theme fairly accurately 

[http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html](http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html)

---

### Post by Endolith on 2008-08-05
> **KillerKiwi said:**
> Nice work... I just looked at the code that mono "was" using for its winforms code (they have since changed there method) as it mimics the gtk theme fairly accurately 

[http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html](http://lists.ximian.com/pipermail/mono-winforms-list/2003-August/000469.html)

Ah, thanks!

I'm not sure they're correct in using style1.Foreground(Gtk.StateType.Normal) for both COLOR_3DDKSHADOW and COLOR_3DLIGHT, for instance.

Do you know of any screenshots of the Wine theme and regular theme side-by-side?  Maybe their method looks good the way it is.

---

### Post by KillerKiwi on 2008-08-05
> **Endolith said:**
> Ah, thanks!

I'm not sure they're correct in using    style1.Foreground(Gtk.StateType.Normal) for both COLOR_3DDKSHADOW and COLOR_3DLIGHT.  I'll have to look through it carefully later.

Do you know of any screenshots of the Wine theme and regular theme side-by-side?  Maybe their method looks good the way it is.

No sorry... it may be worth looking at the new mono winform code to see what its doing... I'm pretty sure its reading gtk styles directly but it should be readable still.. 

[http://anonsvn.mono-project.com/source/trunk/winforms/](http://anonsvn.mono-project.com/source/trunk/winforms/)
it some where in there... I cant find it exactly I know there's themes though so it might be under a theme....

[http://anonsvn.mono-project.com/source/trunk/winforms/ls-styles/ls-styles.cs](http://anonsvn.mono-project.com/source/trunk/winforms/ls-styles/ls-styles.cs)
[http://anonsvn.mono-project.com/source/trunk/winforms/visualstyles20/VisualStyleTest.cs](http://anonsvn.mono-project.com/source/trunk/winforms/visualstyles20/VisualStyleTest.cs)
[http://anonsvn.mono-project.com/source/trunk/gtk-sharp/gtk/Style.custom](http://anonsvn.mono-project.com/source/trunk/gtk-sharp/gtk/Style.custom)

---

### Post by Endolith on 2008-08-05
> **KillerKiwi said:**
> [http://anonsvn.mono-project.com/source/trunk/winforms/](http://anonsvn.mono-project.com/source/trunk/winforms/)
it some where in there... I cant find it exactly I know there's themes though so it might be under a theme....

[http://anonsvn.mono-project.com/source/trunk/winforms/ls-styles/ls-styles.cs](http://anonsvn.mono-project.com/source/trunk/winforms/ls-styles/ls-styles.cs)
[http://anonsvn.mono-project.com/source/trunk/winforms/visualstyles20/VisualStyleTest.cs](http://anonsvn.mono-project.com/source/trunk/winforms/visualstyles20/VisualStyleTest.cs)
[http://anonsvn.mono-project.com/source/trunk/gtk-sharp/gtk/Style.custom](http://anonsvn.mono-project.com/source/trunk/gtk-sharp/gtk/Style.custom)

There are themes in here:

[http://anonsvn.mono-project.com/viewcvs/trunk/mcs/class/Managed.Windows.Forms/System.Windows.Forms/](http://anonsvn.mono-project.com/viewcvs/trunk/mcs/class/Managed.Windows.Forms/System.Windows.Forms/)

Theme.cs 	 
ThemeClearlooks.cs
ThemeEngine.cs 	
ThemeGtk.cs 	
ThemeNice.cs 	
ThemeVisualStyles.cs 	
ThemeWin32Classic.cs

Is that it?

There is also a note though: 

> 2008-07-11  Jonathan Pobst  <monkey@jpobst.com>

	* System.Windows.Forms.dll.sources: Remove the clearlooks, nice,
	and old gtk themes.  They are bit-rotted and have always been listed
	as "unsupported".


---

### Post by Endolith on 2008-08-12
Liferea also gets colors from GTK

[http://liferea.blogspot.com/2006/12/gtk-theme-colors-support.html](http://liferea.blogspot.com/2006/12/gtk-theme-colors-support.html)

[http://liferea.svn.sourceforge.net/viewvc/liferea/trunk/liferea/src/render.c?view=markup](http://liferea.svn.sourceforge.net/viewvc/liferea/trunk/liferea/src/render.c?view=markup)

also, does Compiz read the colors for use in the gtk-window-decorator.c?

---

### Post by Endolith on 2008-08-22
I figured out some of my problems.  The menu selection color was wrong when menuitem.style is "gtk.Style object", but if I add it to a real gtk.Window instead of gtk.Invisible, and then do window.show_all(), menuitem.style changes to "__main__.ClearlooksStyle object" (or whatever engine I am using) and the color is now correct.  I'm sure there's a better way to do this, but I found that by trial and error.  (I wish the pygtk reference had examples for each item, but maybe it's easy enough for others to decipher as is.)

I still can't figure out:

[LIST]
[*]How to add a Tooltip to my window and scrape its colors
[*]I don't think there's any such thing as an MDI in GTK, so I don't have a color to scrape for the MDI background
[*]I still don't know how to get title bar/border colors, since those aren't provided by GTK.  Or are they?  They change when I change the GTK engine.  I really don't understand the relationship between Clearlooks, Metacity, GTK, and window decorations.  Who sets the title bar colors?
[*]Some of the color mappings seem different from one engine to the next.  I'm reverse engineering these by color-picking from the screen and matching the value up with "object.style.attr[gtk.STATE]", for every combination of "STATE" and "attr".  Surely there's documentation for these mappings somewhere?
[/LIST]


Script so far:

[http://bazaar.launchpad.net/~endolith/%2Bjunk/wine-color-scraper/files](http://bazaar.launchpad.net/~endolith/%2Bjunk/wine-color-scraper/files)

---

### Post by KillerKiwi on 2008-09-07
Just used your updated script for my little sisters machine complete with pink theme... wine now looks great nice work

---

### Post by shafin on 2008-10-12
Great work! many thanks to you:)

---

### Post by craftomaniac on 2008-10-13
Wow. Your theme looks great. =)

Just to add another point, you could download MS visual styles from deviantArt or some other place and apply them in winecfg > Desktop Integration. That also works, at least on my system. =)

---

