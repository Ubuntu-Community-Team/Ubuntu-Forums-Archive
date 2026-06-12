---
title: "HOWTO: Change Font Color in Gnome Panels"
date: 2007-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by aktiwers on 2007-01-09
**[COLOR=Red]- THIS THREAD IS OUTDATED - It doesn't seam to work on newer versions of Ubuntu. [/COLOR]**

I have been looking around for a way to change the font color in the Gnome Panels. I found many ways, but non of them worked.

Finally I found a way it works for me in Edgy, so I will post a small howto do this below.

1)
In terminal write:
```
gedit .gtkrc-2.0
```2)
An empty Text document will open, and you need to copy/paste this into it:
> include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "[COLOR=Red]#FFFFFF[/COLOR]"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"
And save.


3)
Change the color code of: fg[NORMAL] = "#FFFFFF"
To whatever you like, and the text in gnome panels will become that color.
I made the part you need to change red.


4)   (optinal)
If you dont know the code for the color you want, you can use this little handy program.

In Terminal type:
```
sudo apt-get install gcolor2
```And when you are done, type:
```
gcolor2
```To open the program.

5)
Screenshots below, of my Gnome Panels with white text fonts. And one of the program gcolor2.

Good Luck!
Aktiwers

---

### Post by sv452 on 2007-01-09
i am happy to say i tried it in dapper and it worked great !!!!

thanx !!

---

### Post by DarkN00b on 2007-01-11
Your script works in Edgy as well. Here's the one I use personally, and it is also confirmed working in Edgy:

```
style "panel"
{
# fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000&#8243;
# fg[ACTIVE] = "#000000"
# fg[SELECTED] = "#000000&#8243;
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000&#8243;
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0&#8243;
# bg[SELECTED] = "#D8BB75&#8243;
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0&#8243;
# base[SELECTED] = "#DAB566&#8243;
# base[INSENSITIVE] = "#E8E8E8&#8243;
# text[NORMAL] = "#161616&#8243;
# text[PRELIGHT] = "#000000&#8243;
# text[ACTIVE] = "#000000&#8243;
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Just uncomment the line you want to change the color for and change the hex value. 

EDIT:
Actually I noticed that yours is the same as mine with the addition of the top few lines:

```
include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200
```

I added these lines and have the best of both! Thanks!

---

### Post by bernt on 2007-01-15
Hi!

I have tried both ways but nothing happens. The text stays black.

Changing the panelcolor works.

/Bernt

---

### Post by ScottFW on 2007-01-17
Thanks for posting this info, it's just what I was looking for! :cool:

---

### Post by towsonu2003 on 2007-03-01
> **DarkN00b said:**
> Your script works in Edgy as well. Here's the one I use personally, and it is also confirmed working in Edgy:

```
style "panel"
{
# fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000&#8243;
# fg[ACTIVE] = "#000000"
# fg[SELECTED] = "#000000&#8243;
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000&#8243;
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0&#8243;
# bg[SELECTED] = "#D8BB75&#8243;
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0&#8243;
# base[SELECTED] = "#DAB566&#8243;
# base[INSENSITIVE] = "#E8E8E8&#8243;
# text[NORMAL] = "#161616&#8243;
# text[PRELIGHT] = "#000000&#8243;
# text[ACTIVE] = "#000000&#8243;
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Just uncomment the line you want to change the color for and change the hex value. 

EDIT:
Actually I noticed that yours is the same as mine with the addition of the top few lines:

```
include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200
```

I added these lines and have the best of both! Thanks!

can't decypher it... what do all the stuff mean? any pointers? thanks :)

---

### Post by brt on 2007-03-05
yeehaaa !!

you are the greatest !

10000000 THANKS!

this is what i am waiting for since years :guitar: 


i already managed to change the color of the whole panel including the menu but what i needed was white font in the panel and black in the menu :) thanks to your howto i was able to manage it seperatly ! 

yeah !

---

### Post by notwen on 2007-03-29
Is there any way to change the menus coming down from my newly "white font-ed" gnome panel?  Kinda difficult to make out what my menus say w/ white font. =]

---

### Post by notwen on 2007-04-01
/bump

---

### Post by aktiwers on 2007-04-03
Im not sure, but if you look at the code it says:>                               include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "[COLOR=Red]#FFFFFF[/COLOR]"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"

See? "my_color" is in this example set to [COLOR=Red]#FFFFFF. [/COLOR]
Now all the widgets has been set to "my_color".

I think the one you are talking about is :
>  widget_class "*MenuItem*" style "my_color"

Now try to change the "my_color" part to whatever color you want.

Does this work?

---

### Post by dstanzler on 2007-04-06
To change the font color of the drop down menu using aktiwers' script:

Open terminal
Type: gedit .gtkrc-2.0
Delete the line: 

widget_class "*MenuItem*" style "my_color"

gl,
Dave

---

### Post by thenme on 2007-04-06
> **dstanzler said:**
> To change the font color of the drop down menu using aktiwers' script:

Open terminal
Type: gedit .gtkrc-2.0
Delete the line: 

widget_class "*MenuItem*" style "my_color"

gl,
Dave

You don't need to delete that line to change the color of the text for the menu item.
It can be any color all you have to do is create a new style tag. I'm not good at teaching so look at what I did. Its in [COLOR="Red"]red[/COLOR]
```
include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
[COLOR="Red"]style "black_text"
{
fg[NORMAL] = "#000000"
}[/COLOR]
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style [COLOR="Red"]"black_text"[/COLOR]
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"
```

I imagine this would work on any or all of those. 
hope that helps.

---

### Post by ChrisNiemy on 2007-04-06
Check the package **gnome-color-chooser**. Quite useful. But changing panel color does not work with it. But you can adjust several other settings, also very nice, that it's is possible to change the width of scrollbars etc.

---

### Post by aktiwers on 2007-04-07
> **thenme said:**
> You don't need to delete that line to change the color of the text for the menu item.
It can be any color all you have to do is create a new style tag. I'm not good at teaching so look at what I did. Its in [COLOR=Red]red[/COLOR]
```
include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
[COLOR=Red]style "black_text"
{
fg[NORMAL] = "#000000"
}[/COLOR]
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style [COLOR=Red]"black_text"[/COLOR]
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"
```I imagine this would work on any or all of those. 
hope that helps.

Yes this is the correct way to do it!
Thanks for clearing it out.

---

### Post by autocrosser on 2007-04-07
Hi aktiwers---

I'm glad you guys are using the stuff I wrote (I'm autocrosser):)

For more information about this & other fun mods, take a look at:
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)
The most updated reference on & about GTK inner workings & :
[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)
for some "hands on stuff"

You might also look at gnomelook.org for some of my "TestAlpha" stuff, & of course you can remod any of them:)

---

### Post by aktiwers on 2007-04-09
> **autocrosser said:**
> Hi aktiwers---

I'm glad you guys are using the stuff I wrote (I'm autocrosser):)

For more information about this & other fun mods, take a look at:
[http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html)
The most updated reference on & about GTK inner workings & :
[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)
for some "hands on stuff"

You might also look at gnomelook.org for some of my "TestAlpha" stuff, & of course you can remod any of them:)

Thanks for links! :)
Actually I found out how to do this in another (more stupid i guess) way.
I was googleing all kinds of howto's and Blogs and ended up with this solution.

Gonna have a look at the TestAlpha now. Thanks! :KS

---

### Post by gtratter on 2007-04-09
You are the HERO of the day! - thank you!

---

### Post by Billy McCann on 2007-04-11
One "weird" side affect is that now all menus related to the panels are now textless, at least, their text is white and their background is white.  This goes a little too far.

---

### Post by autocrosser on 2007-04-12
Change one of the "ffffff" lines to "000000" or some other html color description.

---

### Post by Tmi on 2007-04-15
> **Billy McCann said:**
> One "weird" side affect is that now all menus related to the panels are now textless, at least, their text is white and their background is white.  This goes a little too far.

Did you get this fixed? Got the same problem.

EDIT: Oh never mind, the answer was a bit up on the page,

---

### Post by bimmerd00d on 2007-04-19
nice!!!!!!!!!!!!  Just what i've been looking for!

---

### Post by aztektum on 2007-04-20
for the next trick... turn my open menus transparent so it all blends together. :)

---

### Post by bryonak on 2007-04-21
Sorry for being slighty offtopic (since this thread is about the panel)...
 I'm trying to change the text-frame transparency for nautilus, especially for the desktop icons... and this just doesn't work for me :(
```

style "desktop-icon"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#000000"
  NautilusIconContainer::normal_alpha = 30
}
class "GtkWidget" style "desktop-icon"

```

Turning the text-frame on/off works, changing colors works, but changing the alpha value simply doesn't do anything ( I'm killing GNOME with ctrl+backspace in order to log back in -> all changes except transparency are applied)

I'm not using XGL or any other fancy stuff, my distro is Feisty upgraded (not a fresh install) from a quite unaltered Edgy.
I'm using the proprietary ATI fglrx driver for my Radeon 9800XTX... though I don't realize how this should interfere with the settings in .gtkrc

I've even tried using XFCE's **label_alpha = 30** instead of **normal_alpha = 30**... doesn't help either.

Edit: Gnome-Color-Chooser lets me set the alpha value and writes it correctly to .gtkrc-2.0-gnome-color-chooser (and there's an include in .gtkrc-2.0), but still no effect visible.

Thanks for any hints!

---

### Post by autocrosser on 2007-04-21
Did you goto the links I posted earlier in the thread? If not, goto the GTK info page--I think it might have the info you need.

Also, look thru: [http://developer.gnome.org/doc/](http://developer.gnome.org/doc/)

And for more weight that you might want: [http://developer.gnome.org/projects/gup/hig/2.0/index.html](http://developer.gnome.org/projects/gup/hig/2.0/index.html)

---

### Post by alanh on 2007-04-24
> **bryonak said:**
> Sorry for being slighty offtopic (since this thread is about the panel)...
 I'm trying to change the text-frame transparency for nautilus, especially for the desktop icons... and this just doesn't work for me :(
```

style "desktop-icon"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#000000"
  NautilusIconContainer::normal_alpha = 30
}
class "GtkWidget" style "desktop-icon"

```

Turning the text-frame on/off works, changing colors works, but changing the alpha value simply doesn't do anything ( I'm killing GNOME with ctrl+backspace in order to log back in -> all changes except transparency are applied)

I'm not using XGL or any other fancy stuff, my distro is Feisty upgraded (not a fresh install) from a quite unaltered Edgy.
I'm using the proprietary ATI fglrx driver for my Radeon 9800XTX... though I don't realize how this should interfere with the settings in .gtkrc

I've even tried using XFCE's **label_alpha = 30** instead of **normal_alpha = 30**... doesn't help either.

Edit: Gnome-Color-Chooser lets me set the alpha value and writes it correctly to .gtkrc-2.0-gnome-color-chooser (and there's an include in .gtkrc-2.0), but still no effect visible.

Thanks for any hints!

I'm having the same problem with Feisty, see my post #50 here.  

[http://ubuntuforums.org/showthread.php?t=89197&page=5](http://ubuntuforums.org/showthread.php?t=89197&page=5)

 The code I'm using worked perfectly well with both Dapper and Edgy.

---

### Post by forrestcupp on 2007-04-25
> **notwen said:**
> Is there any way to change the menus coming down from my newly "white font-ed" gnome panel?  Kinda difficult to make out what my menus say w/ white font. =]

I made the my_color style black: "#000000"  Then I made a different style for only the panel:
```
style "panel_color"
{
fg[NORMAL] = "#whatever color you want"
}
```

Then I just changed the style of PanelWidget and PanelApplet from "my_color" to "panel_color"

This way you have all of your normal black menus, but the panel is whatever you want it to be.

---

### Post by bryonak on 2007-04-26
@ autocrosser
Thanks for the links... though they made me toy around with gtk+2 and write some basic applications, I haven't made any prgress concerning my (and [alanh's](http://ubuntuforums.org/showthread.php?p=2529104))  transparency problem ;)
I think it might be related to my online-upgrading from Edgy, but I've no idea where to start searching.

---

### Post by gotmonkey on 2007-05-16
> **autocrosser said:**
> Did you goto the links I posted earlier in the thread? If not, goto the GTK info page--I think it might have the info you need.

Also, look thru: [http://developer.gnome.org/doc/](http://developer.gnome.org/doc/)

And for more weight that you might want: [http://developer.gnome.org/projects/gup/hig/2.0/index.html](http://developer.gnome.org/projects/gup/hig/2.0/index.html)

Great Thread! Thanks

Now I just need to see if I can figure out (RTFM) changing the desktop icons text to another color and dumping the box around the text

---

### Post by aktiwers on 2007-05-16
> **gotmonkey said:**
> Great Thread! Thanks

Now I just need to see if I can figure out (RTFM) changing the desktop icons text to another color and dumping the box around the text

[http://ubuntuforums.org/showthread.php?t=89197](http://ubuntuforums.org/showthread.php?t=89197)

---

### Post by gotmonkey on 2007-05-16
> **aktiwers said:**
> [http://ubuntuforums.org/showthread.php?t=89197](http://ubuntuforums.org/showthread.php?t=89197)

Thank you, that link did the trick

---

### Post by alanh on 2007-05-23
Some resolution to the Gnome  desktop font issue here:

[http://ubuntuforums.org/showthread.php?p=2706033#post2706033](http://ubuntuforums.org/showthread.php?p=2706033#post2706033)

Also, a link to a neat utility to allow the Gnome desktop to be customised through a GUI.

---

### Post by Danyl on 2007-05-29
Should this script work in Feisty? I've tried it but it doesn't seem to be working for me.

Edit: Nevermind. It does work. Don't know what I was doing wrong!

---

### Post by juniah on 2007-11-03
Im trying to change the font colour in Gutsy Gibbon and Its not working for me... any ideas?

Edit:  Works now!  However you need to use this piece of code to reload the panels: killall gnome-panel

---

### Post by aaaantoine on 2007-11-06
Good stuff.  Building on this, is there a way to get the same white-bold-on-black behavior that the Window Titlebar text has?

---

### Post by aktiwers on 2007-11-06
> **aaaantoine said:**
> Good stuff.  Building on this, is there a way to get the same white-bold-on-black behavior that the Window Titlebar text has?

Can you show this in a screenshot? Then we might work out how to do it :)

Im not sure what you want to do..

---

### Post by aaaantoine on 2007-11-06
The attached image should show what I'm talking about.

I'd like the same Bold + Shadow effect to also be on the panel.  It might end up being too much, but I'd still like to try.

---

### Post by LouisChappell on 2008-01-06
I'm using gutsy, I can change the colour of the top panel's writing but it changes the _F_ile _E_dit _V_iew bar also. I've tried to change one of the lines rather than my_color and it didn't work and gave me this;
> louis@ubuntu:~$ gedit .gtkrc-2.0
/home/louis/.gtkrc-2.0:20: error: invalid string constant "#FFFFFF", expected valid string constant
 Am I doing something drastically wrong?

---

### Post by aktiwers on 2008-01-07
> **LouisChappell said:**
> I'm using gutsy, I can change the colour of the top panel's writing but it changes the _F_ile _E_dit _V_iew bar also. I've tried to change one of the lines rather than my_color and it didn't work and gave me this;
 Am I doing something drastically wrong?

Scroll a little up and see. It has been discussed: 

> 
include "/home/autocrosser/.gnome2/panel-fontrc"style "desktop-icon"

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
[COLOR=Red]style "black_text"
{
fg[NORMAL] = "#000000"
}[/COLOR]
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style [COLOR=Red]"black_text"[/COLOR]
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"

Then change the "black_text" color code to whatever you like.

---

### Post by LouisChappell on 2008-01-08
thanks for that, couldn't see the wood for the trees :)

---

### Post by BandD on 2008-01-18
Is there a way to make this script apply to only the top panel?  

My top panel is transapent so a lighter color font is preferable.  And I have the User Switcher and the defualt Date and Time applets in that panel.

My bottom panel is still the defualt white color.  

The problem I'm having is that when I change the font color with this script to white the text in the bottom panel within the window boxes (can't think of the right term at the moment, i.e. if I have Firefox open, there is a little box in the bottom panel that says the title of the page I'm viewing, if I have the terminal open, is says the text trom the terminal, both have little icons and the control the window--minimize etc. ) fades into the white background.  I tried the black_text fix thus ```
widget "*PanelApplet*" style "black_text"
```  This fixed the text in the window boxes, but it also change the User Switcher and the Date and Time text in the top panel to black.

So I was wondering if there is a way to specify which panel the code would be applied to.  Or, alternatively, which widgets to apply the code to.

Thanks,

Dustin

---

### Post by uberlube on 2008-03-04
Worked great. Thanks! :)

---

### Post by bobbo85 on 2008-03-23
I'm sure this works and all, but where is the GUI version of these options?  I feel like there has to be a "properties" button for a panel that should allow you to pick the font size/color as well as the background size/color, and their transparencies or background settings etc.

I mean it's good to know that I have the ability to customize most anything in Ubuntu, but you shouldn't have to reinvent the wheel and use color codes, modifying text files by hand to do anything

---

### Post by eAi-T0ky0 on 2008-05-21
how can i change font tybe for Gnome Panels?! like Arial or Whatever!?

---

### Post by aktiwers on 2008-05-21
> **eAi-T0ky0 said:**
> how can i change font tybe for Gnome Panels?! like Arial or Whatever!?

Hey there,

I have no idea, but I will look into this when I have more time. Or someone else can point us in the right direction.

---

### Post by eAi-T0ky0 on 2008-05-22
i hope so aktiwers ... my question again is any one know how to [COLOR="DarkOrange"]change font "type" for gnome panels[/COLOR]?! :-s

---

### Post by PinkBullets9 on 2008-06-24
If you go to appearence in the system menu there is a tab for fonts and you can change it there. Does this font color change still work in hardy heron?

---

### Post by MarcusCarabas on 2008-07-07
This sounds really wrong.... but when I type

[B]gedit .gtkrc-2.0
[/B]
in the terminal window, gedit opens up with a new (blank) file titled ".gtkrc-2.0"

I did a search on my system for ".gtkrc-2.0" and it seems I don't have this file...

I'm sure I'm screwing something up.. any ideas as to what it might be

---

### Post by aktiwers on 2008-07-08
That is perfectly normal. Just follow the rest of the guide and you will be fine :)
Normally that file is not on Ubuntu, that is why we create it.

---

### Post by aktiwers on 2008-07-08
> **eAi-T0ky0 said:**
> i hope so aktiwers ... my question again is any one know how to [COLOR=DarkOrange]change font "type" for gnome panels[/COLOR]?! :-s

I have looked for this but still not found a solution ..  I will let you know if I do.

---

### Post by MarcusCarabas on 2008-07-08
> **aktiwers said:**
> That is perfectly normal. Just follow the rest of the guide and you will be fine :)
Normally that file is not on Ubuntu, that is why we create it.
thanks :)

---

### Post by boombada on 2009-01-08
i want a white font, so #ffffff is the code for the color....
so,i tried both codes, neither of them work. 
sigh~ 	](*,)
anyway, i am using gnome 2.24.1 ubuntu 8.10
does the codes above could work with my current gnome version?

this is the screenshot,any idea where is the wrong part?

---

### Post by boombada on 2009-01-08
o ya i also did the killall gnome command to refresh the gnome panel, but still no effect....

---

### Post by ashsmith on 2009-01-08
This is very helpful! I like changing my font colors so this is a great guide.. Thank you..

---

### Post by boob11 on 2009-01-17
thnx

---

### Post by Islington on 2009-01-23
> **boombada said:**
> i want a white font, so #ffffff is the code for the color....
so,i tried both codes, neither of them work. 
sigh~ 	](*,)
anyway, i am using gnome 2.24.1 ubuntu 8.10
does the codes above could work with my current gnome version?

this is the screenshot,any idea where is the wrong part?
/home/autocrosser needs to be edited to home/*whatever your home dir is*

---

### Post by aktiwers on 2009-01-23
> **Islington said:**
> /home/autocrosser needs to be edited to home/*whatever your home dir is*

That should not make any difference.. atleast it did not back when I wrote this Howto :)
Sorry have no idea about the problems, maybe this does not work in newer versions of Ubuntu? Well let us know if you get it fixed.

---

### Post by autocrosser on 2009-01-23
I'll take a look into it in the next couple of days---been very busy with Jaunty......

---

### Post by aktiwers on 2009-01-24
Cool, looking forward to hear from you :)

---

### Post by autocrosser on 2009-01-24
OK--

First problem---it's gtkrc-2.0, not gtkcr-2.0

You can delete the "include" line--not needed

I'm not sure that it's working--I'd need to reboot in Intrepid & test for a bit to be sure, but try this:

File name: .gtkrc-2.0

gtk-menu-popup-delay = 2

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color" 


The "popup" delay shortens the normal menu delay--makes the menus a bit quicker---again, change the "FFFFFF" colour to what you want.....

I'll keep track of this thread for a couple of days to see if it is working...


Cheers!!!
autocrosser

---

### Post by monguin61 on 2009-01-24
This worked pretty well for me, I changed the colors of the main menu, the taskbar button items (not sure what those are called in linux) and the clock. However my username in the switch user tool is still black. It seems to be affected by the MenuItem style - is there no way to control this color separately?

---

### Post by aktiwers on 2009-01-25
I will update the main thread with this soon..  thanks Autocrosser!

---

### Post by autocrosser on 2009-01-25
> **monguin61 said:**
> This worked pretty well for me, I changed the colors of the main menu, the taskbar button items (not sure what those are called in linux) and the clock. However my username in the switch user tool is still black. It seems to be affected by the MenuItem style - is there no way to control this color separately?


Hmmm--That is a new addition to the panels and might be coded differently....I'll look into it. What is the menu popup speed like?

---

### Post by autocrosser on 2009-01-25
Ok--The fast-user-switch-applet uses GTK Dialogs, so I added the comment lines at the bottom of the gtkrc-2.0

Post back to see if that worked for you.


gtk-menu-popup-delay = 2

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"
widget_class "*GtkDialog*" style "my_color"
widget_class "*GtkLabel*" style "my_color"
widget_class "*GtkRadioButton*" style "my_color"
widget_class "*GtkCheckButton*" style "my_color"
widget_class "*GtkLabel*" style "my_color"

---

### Post by Arrgoss on 2009-01-28
I feel lost...
I have followed the instructions of the first post, line by line, and nothing changed with my fonts... I've been reading the thread, but didn't find anyonw with the same problem. Am I missing something? How could I do it to check what is, or to give you some more info?
:(

[EDIT] forget about my question, I saw the answer two posts above... shame on me

---

### Post by Arrgoss on 2009-01-28
It's me again... I could not fix the problem. I've tried with the first line, without the first line, with the delay... and I can't change the font color. This is my last trial
```
gtk-menu-popup-delay = 2

{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 70
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#FFFFFF"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
widget_class "*ToolItem*" style "my_color"
widget_class "*SeparatorMenuitem*" style "my_color"
widget_class "*SeparatorToolitem*" style "my_color"
widget_class "*ImageMenuitem*" style "my_color"
widget_class "*RadioMenuitem*" style "my_color"
widget_class "*CheckMenuitem*" style "my_color"
widget_class "*TearoffMenuitem*" style "my_color"
widget_class "*GtkDialog*" style "my_color"
widget_class "*GtkLabel*" style "my_color"
widget_class "*GtkRadioButton*" style "my_color"
widget_class "*GtkCheckButton*" style "my_color"
widget_class "*GtkLabel*" style "my_color" 
```
Can you hint me what am I doing wrong, please?

By the way, when I do
```
gedit .gtkrc-2.0
```
I get the following warning
```
/home/izeddin/.gtkrc-2.0:3: error: unexpected character `{', expected keyword - e.g. `style'
```

---

### Post by Prium on 2009-02-10
> **aktiwers said:**
> I have been looking around for a way to change the font color in the Gnome Panels. I found many ways, but non of them worked.

Finally I found a way it works for me in Edgy, so I will post a small howto do this below.

1)
In terminal write:
```
gedit .gtkrc-2.0
```

2)
An empty Text document will open, and you need to copy/paste this into it:


And save.


3)
Change the color code of: fg[NORMAL] = "#FFFFFF"
To whatever you like, and the text in gnome panels will become that color.
I made the part you need to change red.


4)   (optinal)
If you dont know the code for the color you want, you can use this little handy program.

In Terminal type:
```
sudo apt-get install gcolor2
```

And when you are done, type:
```
gcolor2
```
To open the program.

5)
Screenshots below, of my Gnome Panels with white text fonts. And one of the program gcolor2.

Good Luck!
Aktiwers



I found this thread after Googling, and it is exactly what I need! 

One thing though - how do you get it to work???

I followed your instructions exactly as they are here. I mean I literally copied and pasted this text into gedit .gtkrc-2.0. All that happened was that menu text in active windows appeared white - as did the context menu text. I thought this was supposed to change the Gnome Panel text.....

---

### Post by forelelyon on 2009-03-16
is this for Ibex? it didnt work for me...

---

### Post by aktiwers on 2009-03-16
I think this thread is outdated.. I wrote it in  			January 9th, 2007.

I will update the main thread

---

### Post by t0mmy9 on 2009-05-01
Sorry for bumping an old thread, but i can confirm that the first post on this topic works for me for the new ubuntu (9.04 jaunty jackalope)

I was searching for a way to do this for a while, this was really helpful.

---

### Post by aktiwers on 2009-05-02
Glad it worked, if more people test it in 9.04 and report back I might update the first thread :)

---

### Post by fooman on 2009-05-03
> **aktiwers said:**
> Glad it worked, if more people test it in 9.04 and report back I might update the first thread :)

seems to work fine on my jaunty 64 installation. :)

well,  except for "applications - places - system" ....the drop down menus from those are the colors that i have chosen,  but the words "applications - places - system" in the panel are still the default white.

anyway to get those to match the new colors as well??

thanks

---

### Post by wamukota on 2009-05-10
Can confirm it works on JJ/64 bit :P

---

### Post by Zweih on 2009-05-14
Confirming this works in Debian lenny. One question though, while the panel itself is black (with white text for apps, places, system), how do i change the menu color (ie when you click apps and it shows the list with "Accessories", etc.) to black on white? which lines need be edited?

---

### Post by CylnZ on 2009-05-27
I only read a few pages of this thread because I'm looking for a fix related to this, but cant you do most of these changes these days in Gnome Color Chooser?

---

### Post by anthonypace on 2010-03-08
Hi. I was screwing around with themes and one of the ones that I installed seemed to change some of my backgrounds black and left my text black. I don't mind black backgrounds but I need to change the color of the text so that I can read it without having to highlight it. Any help would be greatly appreciated. Most of the text is in nautilus, pidgin, gedit, etc... if that makes a difference.

---

### Post by deboga on 2010-11-30
Great post !!!!
It has worked fine for my computer.
Thank you very much !

---

### Post by nzjethro on 2011-06-10
> Your script works in Edgy as well. Here's the one I use personally, and it is also confirmed working in Edgy:

Good-oh, worked for me from here in the future with Maverick!

---

