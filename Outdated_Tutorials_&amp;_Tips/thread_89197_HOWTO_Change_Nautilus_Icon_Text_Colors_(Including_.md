---
title: "HOWTO: Change Nautilus Icon Text Colors (Including Desktop Icons)"
date: 2005-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2005-11-12
In most desktop environments, colors, fonts and other visual properties of icons are individually modifiable. This is not the case with GNOME; icon text colors in GNOME are theme-dependent, which means the colors and decorations of the icon text are decided by the active GTK theme. No simple GUI tool is provided to override the active theme elements either, and the info you'll find in most places on the web on modifying (especially desktop) icon text is outdated and won't work for GNOME 2.12.x. At this point the .gtkrc-2.0 file and a few style tags to be specified in it come to rescue; whatever GTK theme properties you specify in this file will override your active theme properties.

The two most common complaints by users about GNOME desktop icon text are that it "remains white all the time" and that it has shadows which decrease readibility especially with small fonts. The dreaded white blends into light backgrounds and decreases legibility. 95% of all GTK themes out there do not modify the icon text color, so it seems to be fixed in white, whereas it can be easily tweaked. And with the method outlined below, you'll get rid of those ugly shadows forever. This may be a matter of personal preference, but I find the plain, unshaded icon text much more legible.

Here are the obligatory before / after screenshots:

[SIZE="4"]Before[/SIZE]
[IMG]http://i6.tinypic.com/6xuuk4n.png[/IMG]

[SIZE="4"]After[/SIZE]
[IMG]http://i10.tinypic.com/8ghkxkz.png[/IMG]

Ok, here are the steps:

[SIZE="4"]1)[/SIZE] Create a .gtkrc-2.0 file in your home folder if it does not exist.

[SIZE="4"]2)[/SIZE] Add the following lines to the file, substituting the variables appropriately:

```
style "desktop-icon"
{
 NautilusIconContainer::frame_text = [COLOR="Red"]X[/COLOR]
 text[NORMAL] = "#[COLOR="Blue"]YYYYYY[/COLOR]"
 NautilusIconContainer::normal_alpha = [COLOR="Lime"]Z[/COLOR] 
}
class "GtkWidget" style "desktop-icon" 

```

[COLOR="Red"]X[/COLOR] = Binary value; has to be set to 1 for this tweak to take effect. Setting it to 0 will bring back the shadows and reset the font color.

[COLOR="Blue"]YYYYYY[/COLOR] = HTML color value. Insert the value of the color you want for the icon text here.

[COLOR="Lime"]Z[/COLOR] = Background color transparency value. 0 is fully transparent (recommended), 255 is fully opaque (white; I have not yet figured out a way to set the framed bg color value)

To learn the HTML code of the color you'd like to have, launch GIMP, hit the foreground color box and choose the color you'll like; its code will appear in the "HTML Notation" box. 

Here's the code I used for the screenshot above:

```
style "desktop-icon"
{
 NautilusIconContainer::normal_alpha = 0
 text[NORMAL] = "#000000"
 NautilusIconContainer::frame_text = 1
}
class "GtkWidget" style "desktop-icon" 
```

[SIZE="4"]3)[/SIZE] Save the file and restart Nautilus with ```
killall nautilus
```.

---

### Post by LaSSarD on 2005-11-12
very nice, i've hated to use light wallpapers because of that but now i've got rid of this problem :)
thanks a lot ;D

---

### Post by 23meg on 2005-11-12
You're welcome; while the preset I gave above is very practical for light backgrounds, users who prefer dark backgrounds can also find use in this, since it lets you choose any color as your icon text, and I have yet to see a dark theme that sets icon font color to anything other than white. While experimenting I found bright green text on dark gray and black backgrounds to be quite pleasing.

---

### Post by endersshadow on 2005-11-13
I tried this with a new .gtkrc-2.0 file and an existing .gtkrc-1.2-gnome2 file...neither worked.  I don't know what info you need to tell me why...but I'm running Breezy and it's all up to date :confused:

---

### Post by 23meg on 2005-11-13
It's working fine for me in Breezy, and others have tested it successfully as well. What GTK theme are you using? Did you try it with different themes?

---

### Post by endersshadow on 2005-11-13
I'm using MilkMint GTK with Creme for my Metacity...and no, I haven't tried it with different themes...I'll play around with it some more, though.  If it just can't be done with MilkMint, that's fine, I can live with it.  Just thought this was a neat trick, and I'm always playing around way too much :)

Thanks!

---

### Post by 23meg on 2005-11-13
I've tried with MilkMint and some other non-Clearlooks themes and it's still working without problems here. Please  check that you've done everything right, and that you don't have another file linked as an "include" from your .gtkrc-2.0 file.

---

### Post by autocrosser on 2005-11-13
Hi 23meg--
Looked at you post with interest--hated just having white--Thanks for showing the option--I played with the icon alpha & got this ----

---

### Post by souled on 2005-11-13
Thanks for the tip. Is there a way to change the color of the font in the panels? I like to have fully transparent panels, and it's hard to read black on some wallpapers.

---

### Post by 23meg on 2005-11-13
autocrosser: Cool, I hadn't really considered semi-transparent text frames; seems they can work well with dark backgrounds.

souled: I'll investigate that; it most probably has its own style property in the gtkrc file.

---

### Post by autocrosser on 2005-11-14
Well--I did some digging & came up with this--  [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)
 certainly more that I want to go thru in one evening:-k---although I see several interesting paths I want to follow.............

---

### Post by 23meg on 2005-11-14
That one is the C reference to GTK, but you may at least get the names of those widgets to specify in gtkrc if you dig it. I'm still looking for a good documentation (actually, official specification) of GTK theme (gtkrc) files.

---

### Post by varunus on 2005-11-14
Maybe we should submit a bug report and have them put this in the Nautilus preferences?  Or somewhere, at least?

Also, it seems like this is just a gtkrc modification...theoretically, then, couldn't a theme adjust the nautilus text colors independently of everything else?  Interesting...I know one of the biggest complaints about gtk theming is the lack of specific color choices in different locations...

---

### Post by autocrosser on 2005-11-14
Yea--you can make a theme that includes the iconpackage changes--now that I know about the "way", I'll incorporate it in some of my new ones--Reading the GTK specs is like walking thru thick quicksand:???:  As soon as I come up with some ideas, I'll post them-----Still have not read what I want to know about----

---

### Post by 23meg on 2005-11-14
> **varunus]Maybe we should submit a bug report and have them put this in the Nautilus preferences?  Or somewhere, at least?
[/QUOTE]
Go ahead and do it, it's the logical thing to do said:**
> 
Also, it seems like this is just a gtkrc modification...theoretically, then, couldn't a theme adjust the nautilus text colors independently of everything else?  Interesting...I know one of the biggest complaints about gtk theming is the lack of specific color choices in different locations...
Sure, I speculated about that in my first post.

---

### Post by denisesballs on 2005-11-16
Very awesome! This has alluded me fore so long, great work! Someone has to be able to make a little app for this, I would if I could.

---

### Post by Biased turkey on 2005-11-16
Thanks a bunch for that customization 23meg.
My mother ( 83 years old ) uses Ubuntu on her PC and the default text icons is taking its toll on er eyes.
I'm sure she'll appreciate to have more readable text icons.

---

### Post by autocrosser on 2005-11-18
Well--I've played around with some parts of the .gtkrc-2.0 add file--Currently it looks like this for a Purple look (not everything obeys--Ideas anyone?)

style "desktop-icon"
{
 NautilusIconContainer::frame_text = 1
 text[NORMAL] = "#9203c1"
 NautilusIconContainer::normal_alpha = 70 
}
class "GtkWidget" style "desktop-icon" 

#NautilusIconContainer::dark_info_color="#888888"
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "my_color"
{
fg[NORMAL] = "#9203c1"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
widget_class "*MenuItem*" style "my_color"
class "*MenuItem*" style "my_color"


Various apps like FireFox--etc will obey--I need to do more checking into how some of the notification boxes get font info:D

Have fun with this!!!

---

### Post by Biased turkey on 2005-11-18
Just tried it on my rig at work ( my boss is out for the day so I can boot Ubuntu )
It's a lot better, but there is that white rectangle around the text. Is it possible to get rid of that inconvenient ?

---

### Post by 23meg on 2005-11-18
[QUOTE=Biased turkey]Thanks a bunch for that customization 23meg.
My mother ( 83 years old ) uses Ubuntu on her PC and the default text icons is taking its toll on er eyes.
I'm sure she'll appreciate to have more readable text icons.[/QUOTE]
I'm very happy I was able to help about that. You can also consider using one of the Gnome high contrast themes to help with her reading.
> 
Just tried it on my rig at work ( my boss is out for the day so I can boot Ubuntu )
It's a lot better, but there is that white rectangle around the text. Is it possible to get rid of that inconvenient ?
Maybe you forgot to apply the normal_alpha parameter? That sets the transparency of the box; if you set it to zero it should disappear completely.

---

### Post by 23meg on 2005-11-18
[QUOTE=denisesballs]Very awesome! This has alluded me fore so long, great work! Someone has to be able to make a little app for this, I would if I could.[/QUOTE]
I had asked on a thread how to change desktop font colors months ago, and it seems you were one of those who seconded the question, yet noone came up with an answer.. Better late then never I guess. I will write a simple app, once I learn my way around Python. I found an app called Gnome Configurator that claims to do this, but it hasn't worked well for me and messed up my colors badly, and I've seen others reporting the same. I think it's outdated and doesn't work on recent GTK versions.
[QUOTE=autocrosser]Well--I've played around with some parts of the .gtkrc-2.0 add file[/QUOTE]Looks interesting; if you've found some guides or references for gtkrc tweaking, post them here and share the love :cool:

---

### Post by Biased turkey on 2005-11-18
I double checked my .gtkrc-2.0 file and it's exactly the same as the one you used:

style "desktop-icon"
{
 NautilusIconContainer::normal_alpha = 0
 text[NORMAL] = "#000000"
 NautilusIconContainer::frame_text = 1
}
class "GtkWidget" style "desktop-icon"

So , obviously the alpha is set to 0. But, the computer I have at work  has a crappy ATI Rage 128 video board ( so they are sure the employees wont play games lol  ) and maybe that's why I have some alpha problems.
I'll try to apply your procedure at home with an Nforce 6600 and 'll report.
Thanks again for your help 23meg
P.S. why 23meg , you only have 23 megabytes of ram on your motherboard ?

---

### Post by bolamix on 2005-11-18
Thanks a LOT for this tweak, makes things so much more readable on the desktop :)

---

### Post by 23meg on 2005-11-18
Biased Turkey: That's weird; I'm using a Nvidia chip too and am curious if the alpha value has anything to do directly with the video adapter. Keep us posted after you try at home. The answer to your nickname question is [here]("http://www.ubuntuforums.org/showthread.php?t=89897"); post yours on that thread too, I'm curious.

bolamix: glad it worked for you.

---

### Post by autocrosser on 2005-11-18
[quote=23meg]
Looks interesting; if you've found some guides or references for gtkrc tweaking, post them here and share the love :cool:[/quote]

Not a prob--I'll have time this weekend & next to "play"---I hope to have a way to change all the fonts by then;)--If anyone sees anything interesting---please post to help the "effort"!!!!!!!

---

### Post by autocrosser on 2005-11-21
Hey Guys (& Gals!)--there is another thread in Desktop that is covering some of the same ground as where this one is heading--thinking that the two should be merged & **Sticky**  Or one of us need to come up with a HowTo that covers font/menu/panel customization/recolorization---Ideas?????

---

### Post by 23meg on 2005-11-21
Which thread? Maybe it's enough to crosslink rather than merge.

---

### Post by autocrosser on 2005-11-21
Take a look at Customizing Gnome Panel-- [http://www.ubuntuforums.org/showthread.php?t=81016](http://www.ubuntuforums.org/showthread.php?t=81016)
 I think we should all put our heads together & make a customizing/tweek HowTo--What do you think---

[quote=23meg]Which thread? Maybe it's enough to crosslink rather than merge.[/quote]

---

### Post by 23meg on 2005-11-21
I think individual guides are a better idea; one big guide that includes everything is likely to look too complicated and will be difficult to scan through for users who will be looking for particular tweaks. That said, a gtkrc modification howto that explains all available options would be cool.

---

### Post by autocrosser on 2005-11-22
Good point--I am working on several different ideas at this time & it would be several pages to incorporate them into one HowTo--I've got one idea more-or-less finished............I have about 95% of fonts using one color--I re-edited one of my themes to include your NautilusIcon info & the semi-transparent text boxes for the desktop icons--Feel free to edit the gtkrc files to the colors you (or anyone else) wants--I've started to find a way to make transparent menus (had some AMAZING failures so far!!), so gtk-2.0 has some .png's for currently no good reason:???:  

Anyway--its all purple & I freely allow modification for all within the tarball---just post interesting stuff:smile:

---

### Post by 23meg on 2005-11-22
Cool - so this changes the Gnome panel font color too; first theme I've seen that changes the panel font actually. Lovers of purple will adore it, but still nothing tops Gperfection2 for me.

I think you should post your ideas as separate guides and then we can bring them all together under a "theme tweaking" page on the Document Storage and/or the official wiki maybe. I'll go on with tweaking themes when I get some free time.

---

### Post by autocrosser on 2005-11-22
So grab it & open your fav html color picker--easy enough to make it blue-red-etc----It will change "almost" everything:cool:

---

### Post by 23meg on 2005-11-22
[This app]("http://gcolor2.sourceforge.net/") seems like a handy one for doing that.

---

### Post by autocrosser on 2005-11-23
Found another App on Freshmeat that works hand-n-hand with the one you found--http://freshmeat.net/projects/colorscheme/ It works a "group" of colors around the "picked" one!!!:smile:

Edit--just satified all the depends on Colorscheme--Give it a try--WORKS GREAT!!!!:smile:

---

### Post by bvc on 2005-11-25
[QUOTE=23meg]Cool - so this changes the Gnome panel font color too; first theme I've seen that changes the panel font actually.[/QUOTE]
you can control more panel color aspects with something like```
style "clearlooks-panel"
{
	fg[NORMAL] 			= "#ffffff"
	fg[PRELIGHT] 			= "#ffffff"
	fg[ACTIVE] 			= "#000000"
	fg[SELECTED] 			= "#000000"
  	bg[NORMAL] 		= "#5881B6"
	bg[PRELIGHT]      	= "#6089BE"
	bg[ACTIVE]       	 = "#d0c8c1"
}
class "*Panel*" style "clearlooks-panel"
widget_class "*Panel*GtkToggleButton" style "clearlooks-panel"
widget_class "*Panel*GtkButton" style "clearlooks-panel"
widget_class "*.Panel*Button*GtkLabel" style "clearlooks-panel"
widget_class "*.Panel*GtkLabel" style "clearlooks-panel"
```

---

### Post by Biased turkey on 2005-11-26
[QUOTE=Biased turkey]I double checked my .gtkrc-2.0 file and it's exactly the same as the one you used:

style "desktop-icon"
{
 NautilusIconContainer::normal_alpha = 0
 text[NORMAL] = "#000000"
 NautilusIconContainer::frame_text = 1
}
class "GtkWidget" style "desktop-icon"

So , obviously the alpha is set to 0. But, the computer I have at work  has a crappy ATI Rage 128 video board ( so they are sure the employees wont play games lol  ) and maybe that's why I have some alpha problems.
I'll try to apply your procedure at home with an Nforce 6600 and 'll report.
Thanks again for your help 23meg
P.S. why 23meg , you only have 23 megabytes of ram on your motherboard ?[/QUOTE]

OK I said I would report, so here it is:
I had no problem at home to change the icon text colors on both rigs at home, one has an ATI Radeon 9600 and the other an Nvidia geForce 6600.
So I give 23meg's howto the **Approved** stamp :)

---

### Post by bvc on 2005-11-26
So if you set the desktop icon text to a light color, you get that same light color in the nautilus browser, which is useless. How do you change the text in the browser? There should be a way to do it because the default is white text on the desktop and black in the browser.

---

### Post by jhnphm on 2005-12-20
[http://mail.gnome.org/archives/gnome-list/2000-September/msg00275.html](http://mail.gnome.org/archives/gnome-list/2000-September/msg00275.html)

I got this in my gtkrc:
```

style "desktop-icon" {
     NautilusIconContainer::frame_text = 1
      text[NORMAL] = "#FFFFFF"
     NautilusIconContainer::normal_alpha = 44
}
#class "GtkWidget" style "desktop-icon"
widget_class "*DesktopIcon*" style "desktop-icon"

```
which just affects desktop icon color but not nautilus folders or anything else.

---

### Post by gmc on 2005-12-20
[QUOTE=jhnphm]
```

style "desktop-icon" {
     NautilusIconContainer::frame_text = 1
      text[NORMAL] = "#FFFFFF"
     NautilusIconContainer::normal_alpha = 44
}
#class "GtkWidget" style "desktop-icon"
widget_class "*DesktopIcon*" style "desktop-icon"

```
[/QUOTE]

This is great. Now I may have missed it in this thread, but does anyone know how to change the text colour on the panel(s)? I like to have a dark wallpaper but all the panel applets that display text are black and disappear. I know I could change the panel background to opaque but I like to use transparent.

G.

Additional: I found the answer [HERE]("http://ubuntuforums.org/showthread.php?t=47776"). Thanks to agapito.

---

### Post by kanem on 2005-12-27
> **23meg]
```
style "desktop-icon"
{
 NautilusIconContainer::frame_text = [COLOR="Red"]X[/COLOR]
 text[NORMAL] = "#[COLOR="Blue"]YYYYYY[/COLOR]"
 NautilusIconContainer::normal_alpha = [COLOR="Lime"]Z[/COLOR] 
}
class "GtkWidget" style "desktop-icon" 

```

[COLOR="Red"]X[/COLOR] = Binary value said:**
> YYYYYY[/COLOR] = HTML color value. Insert the value of the color you want for the icon text here.

[COLOR="Lime"]Z[/COLOR] = Background color transparency value. 0 is fully transparent (recommended), 255 is fully opaque (white; **I have not yet figured out a way to set the framed bg color value**)

Have you (or anyone else) figured out how to set this background color yet? I've been looking but haven't found the answer.

Edit: Fount it. Underneath the line starting with "text[NORMAL]" put the line:
base[NORMAL]="#ff0000"
or whatever you want the colour to be.

---

### Post by joselin on 2005-12-27
Is what i want lots of times.

Thanks.

---

### Post by amohanty on 2005-12-29
Some links to 'documentation' :)

[http://developer.gnome.org/doc/API/2.2/gtk/gtk-Resource-Files.html](http://developer.gnome.org/doc/API/2.2/gtk/gtk-Resource-Files.html)
[http://www.gtk.org/~otaylor/gtk/2.0/theme-engines.html](http://www.gtk.org/~otaylor/gtk/2.0/theme-engines.html)

I was trying to figure out how to make my own theme and kind of stumbled upon it. Its the closest I have been able to find to anything like documentation for resource files and applicable stuff.

AM

---

### Post by tagra123 on 2006-08-28
I've caught one problem with this. I really dont understand why either.

I have crossover office installed on Dapper.

A VB app reports a memory error when using this change. Renaming or deleting the edited file and the one Dapper autocreates with -gnome2 as part of the filename makes the memory error go away.


Wierd. Can anyone explain?

---

### Post by mjpoetic on 2006-08-29
I know this probably doesn't help much...but I also have CX office installed and that hasn't been a problem for me.  When you say VB...I assume you mean Visual Basic.  I don't have that program installed (yet), but I know I have it lying around here somewhere and will try and take a look at it if possible.  I am about to get hit by a hurricane here, so I should probably have some time.  ;)

p.s.
As an alternative you may want to ask this question with CX Office support or the forums they have.

---

### Post by tagra123 on 2006-09-29
The Crossover problem only appeared for one app. Most likely it was the application and not Crossover or Gnome

---

### Post by mjpoetic on 2006-09-29
Good to know...sorry for not getting back to you, but life caught up with me a little bit.  ;)  CX office has a new beta 6 out...you may want to check it out.

---

### Post by abelthorne on 2006-11-03
As said in the Murrine engine thread, I have a problem with one theme (MurrinaNeo from Gnome-look.org).

My problem is that when I set this theme, the icons on the desktop get a black text with no shadow, which is unusable with dark backgrounds.
In the theme file, there is no desktop-icon entry so I guess it uses the default text color.

I've tried to change the .gtkrc-2.0 as explained at the beginning of this thread, but it changes all text color, not only the desktop icons one : if I set the texte to white, it gets white on white background in Nautilus filebrowser, text editors and such.

What can I do to change only the desktop icons text colors and nothing else ?

---

### Post by adds2one on 2007-01-11
> **abelthorne said:**
> 
What can I do to change only the desktop icons text colors and nothing else ?

I would like to know the same thing. 

Anyone?

---

### Post by x7xstring on 2007-04-06
> **adds2one said:**
> I would like to know the same thing. 

Anyone?

I would like to know as well!

---

### Post by alanh on 2007-04-24
I've been using 23meg's original solution for modifying desktop icon text for some time now.  It has worked just fine for me on Dapper and Edgy but something seems to have changed with Feisty.  The original code as given by 23meg still gives black text but the normal_alpha setting no longer seems to determine the transparency.  I now have a white text box background irrespective of any value I set for normal_alpha.  I have this on 2 different installations of Feisty. I've also tried a number of different themes and all give the same result.   Anyone having the same problem and does anyone know of a solution?

Cheers.

---

### Post by bryonak on 2007-04-26
> **alanh said:**
> I've been using 23meg's original solution for modifying desktop icon text for some time now.  It has worked just fine for me on Dapper and Edgy but something seems to have changed with Feisty.  The original code as given by 23meg still gives black text but the normal_alpha setting no longer seems to determine the transparency.  I now have a white text box background irrespective of any value I set for normal_alpha.  I have this on 2 different installations of Feisty. I've also tried a number of different themes and all give the same result.   Anyone having the same problem and does anyone know of a solution?

Cheers.

As you already pointed out in [this thread](http://ubuntuforums.org/showthread.php?p=2500171#post2500171), we've got the same problem. Still in search for a solution...
Have you upgraded Edgy to Feisty on your machines? I have, and since it's working on a friend's box who did a fresh install,  it might be broken by upgrading. Then again, maybe not ;)

---

### Post by alanh on 2007-04-26
I have a clean install of Feisty.   I've also kept my Edgy installation, so I can boot into either.   The code as given originally by 23meg works fine in Edgy, the problem is in Feisty.  

I've also posted on the Nautilus developer/user forum, to see if there have been any changes to Nautilus:

[http://www.nabble.com/Changes-to-nautilus-desktop-icon-display-tf3636166.html](http://www.nabble.com/Changes-to-nautilus-desktop-icon-display-tf3636166.html)

I'd really like to fix this, as I like to use very neutral colours for my desktop and the default white icon text doesn't display very clearly.

Cheers

---

### Post by diskotek on 2007-04-28
this is very nice howto for those who use light-colored wallpapers..simple & cool... thanks

---

### Post by mechanic on 2007-05-04
This current problem with gtk...rc can be fixed quite easily by installing xfce window manager and removing gnome. This xfdesktop is better looking than gnome, and more customisable (you can roll up windows into the title bar which I never could do with gnome). See this for details of what to put in the gtk-2.0rc file:
[http://svn.xfce.org/svn/xfce/xfdesktop/branches/xfce_4_4/README](http://svn.xfce.org/svn/xfce/xfdesktop/branches/xfce_4_4/README)

Regds, m.

---

### Post by andrek on 2007-05-17
Doesn't work for me..
Look at the pic : [http://i3.tinypic.com/521d28n.png](http://i3.tinypic.com/521d28n.png)
I've still got those ugly borders..
Any suggestions?

---

### Post by mechanic on 2007-05-17
Nice clock! What is it?

Regds, m.

---

### Post by andrek on 2007-05-18
Oh that's not the answer I was expecting.. 
It's MacSlow's Cairo-Clock

---

### Post by mechanic on 2007-05-18
Well I've got Cairo-clock on my desktop, but I have a black square frame around the circular clock - how did you get rid of that?

Regds, m.

---

### Post by andrek on 2007-05-18
It works properly ( as my does ) only with beryl / compiz enabled.

---

### Post by alanh on 2007-05-23
Returning this thread to its original topic.  I have some resolution for the "normal_alpha" issue, from some good folks at the Nautilus developers forum.  

[http://www.nabble.com/Changes-to-nautilus-desktop-icon-display-tf3636166.html](http://www.nabble.com/Changes-to-nautilus-desktop-icon-display-tf3636166.html)

It seems there had been some changes that made Nautilus ignore the "normal_alpha" setting in the .gtkrc file.  Apparently this will be corrected in Gnome release 2.18.3.

In the meantime, I have a workaround by setting the icon background colour to the same value as my desktop (I don't use wallpaper).

BTW, the guy who fixed this problem is also responsible for a neat utility to customise the Gnome desktop, found here:

[http://www.punk-***-bitch.org/gnome-color-chooser/](http://www.punk-***-bitch.org/gnome-color-chooser/)

(sorry about the name)

It saves a lot of messing around with configuration files.

---

### Post by corefile on 2007-06-11
> **alanh said:**
> 
In the meantime, I have a workaround by setting the icon background colour to the same value as my desktop (I don't use wallpaper).



How do you set the Icon background color?

---

### Post by alanh on 2007-07-10
[http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349)

---

### Post by linuxhelp on 2007-10-11
Hello 

is there a possibility to disable the icon font shadow?

for clean fonts under icons?

Thx Tom

---

### Post by Niniel on 2007-11-11
Found the color chooser!
(original website has been removed)

[http://ppa.launchpad.net/misery/ubuntu/pool/main/g/gnome-color-chooser/]("http://ppa.launchpad.net/misery/ubuntu/pool/main/g/gnome-color-chooser/")

---

### Post by linuxhelp on 2007-11-12
1000X Thanks to you

i make it, and my LCD-Laptop-Desktop is now readable...

Thx Tom

[www.linuxonlinehelp.de](www.linuxonlinehelp.de)

---

### Post by ubuntu_amatuer on 2007-12-02
I tried the .gtkrc edit and did the killall for nautilus and I still have the shadow for the desktop icons. 

Any one have any ideas as to why it didn't take effect. I have Gutsy running.

---

### Post by 23meg on 2007-12-03
Please post the contents of the file.

---

### Post by ubuntu_amatuer on 2007-12-03
style "desktop-icon"
{
 NautilusIconContainer::normal_alpha = 0
 text[NORMAL] = "#000000"
 NautilusIconContainer::frame_text = 1
}
class "GtkWidget" style "desktop-icon"


That is the content and it saved as .gtkrc-2.0 under my /home directory.

---

### Post by 23meg on 2007-12-04
I have no idea why it shouldn't work under Gutsy. I have the same file, and it's working fine. What GTK theme are you using?

---

### Post by ubuntu_amatuer on 2007-12-04
I am using the theme named Black. 

Just want to make some thing clear,

I make that file and save it in my /home folder - Do I have to save it in a specific folder in the /home directory or directly in the home directory ?

And then all I have to do is do a killall for nautilus ?

---

### Post by 23meg on 2007-12-05
Do you know what theme engine it uses? A link would be useful.

You have to save the file in your /home/*username* folder, not your /home folder. What's referred to as "your home folder" is /home/*username*, not /home, where you shouldn't save anything. ~/ also points to /home/username.

What does ```
cd ~/ && ls .gtkrc-2.0
```return?

---

### Post by ubuntu_amatuer on 2007-12-05
I guess I just made my first of many amateur mistakes. Once I transferred the file to the home/<usrname> folder the effect took place.

Thanks for the time and help.

---

### Post by 23meg on 2007-12-06
You're welcome.

[I](Note: I've fixed the missing image in the first post by going to March 2006 with the [Wayback Machine]("http://www.archive.org/web/web.php"), which it seems has cached it. Here's how this thread and the forums looked back then: [http://web.archive.org/web/20060303070920/http://ubuntuforums.org/showthread.php?t=89197](http://web.archive.org/web/20060303070920/http://ubuntuforums.org/showthread.php?t=89197))
[/I]

---

### Post by the_blur on 2007-12-16
Awesome! Worked for me!

---

### Post by Sugz on 2008-01-06
Nope, didnt work here :(

---

### Post by janfsd on 2008-04-28
Thanks for this. It works on Hardy.

---

### Post by Psyphre on 2008-05-24
The title says nautilus icon texts (including dekstop icons), does this mean it can work for text other than on the desktop? For example the nautilus browser window. It only uses black (on light backgrounds) or white (on dark backgrounds), but I want it to use a gray colour.

Is that possible?

---

