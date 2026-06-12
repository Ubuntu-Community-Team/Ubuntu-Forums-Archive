---
title: "HOWTO: Better Autohide Gnome Panel"
date: 2006-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by jms830 on 2006-05-05
When I first came to Ubuntu from windows, I was used to having my panel autohide: in gnome, it just felt clunky.  I stumbled across this fix, but I doubt most new users would, so I made a howto.  I figured it was something that Windows converts (or anyone for that matter) might want to work smoother.


1. Go to [B][COLOR="Green"]Applications> System Tools> Configuration Editor
[/COLOR][/B] 

[COLOR="Red"]Note: I think this menu item was removed in dapper. You can either use alacarte menu editor to put it back or it can be opened simply with the command [/COLOR] [COLOR="Black"]**gconf-editor**[/COLOR][COLOR="Red"] in a terminal [/COLOR]

2. In the configuration editor, go to [COLOR="Green"]**apps/panel/top level**[/COLOR]

3. In this folder there will be a few folders called something like panel_0, panel_1, top_panel_screen0 or similar.  These folders are the options for your respective panels. Find the ones with **[COLOR="Green"]autohide[/COLOR]** checked: these are your panels that you have set to autohide (obviously).

4. Right click and "Edit Key..." on each of the fields listed below and set these values:
[B]
_Name _     =      _Value_[/B]

[COLOR="Green"][B]auto_hide_size        =         0
hide_delay          =           300
unhide_delay       =            0[/B][/COLOR]

That's it! You can of course change these values to whatever you prefer.

auto_hide_size is how much of the panel you want to show when it is hidden
hide_delay is how long until the panel hides itself after your cursor leaves the panel
unhide_delay is how long until the panel unhides when you put your cursor over it.

---

### Post by Irony on 2006-05-07
Useful - I was wondering how to do that after booting into Windows.

---

### Post by Fass on 2006-05-07
That little piece of the panel that was always visible was starting to annoy me. Great tip!

---

### Post by Iandefor on 2006-05-10
sweet! This was one of the things that I always hated about GNOME. You Rock!

This is one of those "doh!" moments for me.

---

### Post by oscar on 2006-05-11
Thanks, that is exactly what I was looking for. By default I found that with autohide on it looked...dirty, I could still see the bottom of the icons on my top panel when it was autohidden. I use your settings now but prefer having the hide_delay as 0, makes it faster and look smoother.

---

### Post by jms830 on 2006-05-12
Glad you like the tip, I'm happy to contribute to the community. It is interesting to me that the default settings aren't closer to this. I don't think many like the autohide to feel so clunky.

---

### Post by tweak on 2006-05-12
epic! you're a champ! :D

---

### Post by Knorhaen on 2006-05-13
Thanks mate, this has bugged me ever since I started using Gnome!

---

### Post by xyz on 2006-05-13
Thanks jms830...my laptop's screen is the smallest there is and any additional screen space is most welcome!Any way to achieve this at the bottom of the screen?

---

### Post by oscar on 2006-05-13
[QUOTE=xyz]Thanks jms830...my laptop's screen is the smallest there is and any additional screen space is most welcome!Any way to achieve this at the bottom of the screen?[/QUOTE]
same as with the top, but change bottom_panel_screen0 (or equivalent)

---

### Post by idarco on 2006-05-13
Ah, very nice. Was wondering about this myself.

---

### Post by Juippisi on 2006-05-14
After all it was so easy to do, hard to find. Thanks for guiding us to the right direction. This really makes my life easier :-).

Yea, I was wondering a long time how to make the hidden panel smaller and when I didn't find it, I gave up. I'm glad I read Ubuntuforums this night and found this thread.

---

### Post by tread on 2006-05-17
Cool! Never played around with the config editor much before .. this is useful. Thanks.

---

### Post by pillypoon on 2006-05-17
Thanks! Cant wait to give it a shot.:p

---

### Post by EdThaSlayer on 2006-05-20
THANKS! my screen looks so much bigger now!!

---

### Post by essetee on 2006-05-21
Icons on the desktop is a microsoft invention. Everyone now want it.
Under microsoft windows, those icons are useless, because you have only 1 desktop.
Under linux, we can switch between several virtual desktops, and so desktop icons becomes more interesting.

But here my trick under gnome.

I start with this dekstop :

[http://www.essetee.be/downloads/schermafdruk1.png]("http://www.essetee.be/downloads/schermafdruk1.png")

Then I make a new panel and put it on the right side of my screen.

I use the tips found here to make it autohide.

As soon I move the mouse pointer to the right side of the screen, I have this :

[http://www.essetee.be/downloads/schermafdruk2.png]("http://www.essetee.be/downloads/schermafdruk2.png")

So, even when applications covers the icons, I still have mines by the hand.

---

### Post by overmetal61 on 2006-07-26
I am attempting to follow these directions:

I open gconf-editor and I don't have an toppanels option.

All I have is default_setup

Attached is a screenshot.

Can someone help me?

---

### Post by Iandefor on 2006-07-26
> **overmetal61 said:**
> I am attempting to follow these directions:

I open gconf-editor and I don't have an toppanels option.

All I have is default_setup

Attached is a screenshot.

Can someone help me? Try toplevels/top_panel from where you are in that screenshot.

---

### Post by overmetal61 on 2006-07-26
I tried in default_setup/toplevels and it doesn't seem to do anything... I asked in #ubuntu on freenode and someone else said they have the /apps/panel/toplevel there... I don't understand why mine is not there?

---

### Post by Iandefor on 2006-07-26
> **overmetal61 said:**
> I tried in default_setup/toplevels and it doesn't seem to do anything... I asked in #ubuntu on freenode and someone else said they have the /apps/panel/toplevel there... I don't understand why mine is not there? Did you check in default_setup/top_panel?

---

### Post by overmetal61 on 2006-07-26
Yeah checked everywhere!

After investigating this further I believe it a corrupt profile of some form.

I logged onto my box as another user and the folders where there.

Weird!  I guess I will attempt at recreating my profile from scratch.

I think it will work. Thanks!

---

### Post by ScottFW on 2006-07-27
Great tip! I'm just getting started with Ubuntu and am trying to customize the little details like these. Thanks for the info.

---

### Post by staura on 2006-09-24
Do NOT run gconf-editor as root, it will not find your users properties...

---

### Post by jpyanowski on 2006-09-25
Thanks for helping me reclaim more of my desktop.\\:D/

---

### Post by Lil' Kempo on 2006-09-26
Thanks for the great tip! I've been wondering how to get rid of the tiny part that get left on show for ages ](*,)

---

### Post by StarkD on 2007-01-30
Excellent! You can never get too much working space :smile:

---

### Post by satya_461 on 2007-06-11
Great Article..
I am looking exactly for this..
THanks..

---

### Post by Lunks on 2007-07-05
After I set auto_hide_size to 0, I can't make it appear again =~

---

### Post by Frostsongr on 2008-10-31
Works great in Ubuntu 8.10

---

### Post by yugrotavele on 2008-10-31
Awesome tip! That little bit of panel showing on autohide always annoyed me. Thanks!

---

### Post by Sand Lee on 2008-12-05
Thank you very much!
Here's the [Bug Report]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/218982") if anyone is interested. ):P

---

### Post by rlhawk1 on 2009-02-01
> **overmetal61 said:**
> I tried in default_setup/toplevels and it doesn't seem to do anything... I asked in #ubuntu on freenode and someone else said they have the /apps/panel/toplevel there... I don't understand why mine is not there?

That one only changes the default for new panels.  To change your current panels, go to apps/panel/toplevels/ and edit the panels under there.

---

### Post by amiga_os on 2009-02-13
Great tip...

anyone have any ideas on how to speed up the animation of the panel?  That would make it feel even more crisp.  I found an option in panel-global->panel-animation-speed, but it says it's deprecated.

Why doesn't gconf tell me what it's deprecated by?  Anyway, any help would be appreciated.

---

### Post by ´silas on 2009-02-13
Great tip man. The only reason why I not using autohide, was because of the way it would only be partially hidden. Thanks a lot :)

---

### Post by m4lte on 2009-02-14
> **amiga_os said:**
> 
anyone have any ideas on how to speed up the animation of the panel?  That would make it feel even more crisp.  I found an option in panel-global->panel-animation-speed, but it says it's deprecated.

Why doesn't gconf tell me what it's deprecated by?  Anyway, any help would be appreciated.

For each panel (e.g. '/apps/panel/toplevels/panel_4/') there's a key 'animation_speed', which you can set to 'fast', 'medium', or 'slow'!



Another question: **Is it possible to hide a panel completely?** Using the **auto_hide_size** key I can only get the panel down to a size of 1 pixel. (I can of course change the key to other values, but the panel always appears at least 1 pixel in size)

---

### Post by ´silas on 2009-02-20
> **m4lte said:**
> For each panel (e.g. '/apps/panel/toplevels/panel_4/') there's a key 'animation_speed', which you can set to 'fast', 'medium', or 'slow'!



Another question: **Is it possible to hide a panel completely?** Using the **auto_hide_size** key I can only get the panel down to a size of 1 pixel. (I can of course change the key to other values, but the panel always appears at least 1 pixel in size)

I have successfully set mine to 0 just like that. What kind of error do you get when you try and set the auto_hide_key to 0?

---

### Post by l3ftm1n0r on 2009-02-21
Hey there for this nice info.
Some questions:

I have currently only two panels; one on the top and the one on the bottom. But under toplevels it shows four of them with the names:
panel_0
panel_1
panel_2
top_panel_screen0

Now i have found which ones are the ones i need to make changes to but the other two have left orientation and they aren't really present. Why's that?

Second question is that the top_panel_screen0 is the one containing the menus does not have a animation speed parameter so i cannot make the animation faster cause medium animation is rather slow.

Please help out. Thanks.

---

### Post by phiphi on 2009-02-27
This trick is so very helpful!

**activate "auto_hide" and disable "enable_animation"** and set the "auto_hide_size" to 0. and you have a very well working menu.
The animation was too slow even with animation_speed fast.

---

### Post by m4lte on 2009-02-27
> **´silas said:**
> I have successfully set mine to 0 just like that. What kind of error do you get when you try and set the auto_hide_key to 0?

I don't get any error, when I set the auto_hide_key to 0, but I still looks as if the key was 1. Setting it to higher values works, but I can't make the panel completely disappear. There's always a "thin line" on the edge of the screen.

---

### Post by Linux_Shishya on 2009-04-14
Guess what I did? Created a new panel, dumped the ugly notification applet on it and set it to autohide! 

My desktop :[IMG]http://img21.imageshack.us/img21/4527/screenshotyig.png[/IMG]

Notice the thin line beneath the clock applet on bottom panel?

---

### Post by SirSlipALot on 2009-04-26
Hi all,

I'm using Ubuntu 9.04 and i had to disable the key
/apps/panel/toplevels/top_panel_screen0/enable_animations

Now the panel pops up instantly! Great! :)

---

### Post by vickoxy on 2009-04-27
Hi, if i set up auto hide size to 0 and uncheck expand (want it more macOs)  and i open open office/firefox, i still have 1 pixel on display to see (there where the panel actually is). Can you  confirm this?

---

### Post by Cresho on 2009-04-28
I still have a pixle ontop.  I wish it could be set to 0

---

### Post by vickoxy on 2009-04-28
So for everyone who can not stand that  1 Pixel, and want some kind of quick app launcher in Gnome:

Sorry for putting these post on several threads, but maybe others will find it usable.

I succeeded to make KoolDock working just fine in Dell´s Ubuntu 8.04 (lpia).
First: from synaptic you can download only KoolDock 0.3-no good...it won´t work.

1) Find then on line KoolDock 0.4.6. and download it
2) install KDEbase (it will install 34 Packages with more than 70 MB... i didn´t notice any change in my system-hope just that this downloads are not fatal)
[http://lists.kde.org/?l=kde-announce...3945506482&w=2](http://lists.kde.org/?l=kde-announce...3945506482&w=2)
3) Doobleclick on your KoolDock (you can previously install from synaptic 0.3 if you want....) and installation will go automatically

So, that was it. Panel and KoolDock are fastest Launchers for Metacity LPIA Ubuntu 8.04-you don´t have to activate compositing metacity. There are some issues-fonts looks ugly-so better do not show them. But the panel is quick, installation of new apps is easy (just drag and drop), and transparency works fine (sometimes there are some glitches...but nothing serious).

P.S. I didn´t figure how to add folders and documents on KoolDock, so if anyone find solution...

---

### Post by trash on 2009-05-07
On both my panels i set a BG solid color through the properties dialog however with one of my panels that auto-hides(window list) I can't see any of the buttons. If i open properties and change the size the buttons appear but disappear upon closing the dialog... On the other panel(no auto-hide) all icons and notification areas are visible all the time... anybody got any ideas?

EDIT: Buttons appear and stay visible only if panel is at least 35 pixils!

---

### Post by Makum on 2009-07-14
Does anyone know were is the option to the same with the autohide in the main menu???

---

### Post by Baneblade on 2009-07-14
Thanks for that tip.. just used autohide yesterday to allow me to work on a remote desktop with a higher resolution than mine. I thought it was a bit off when i used it. This "feels" much better now! Cheers!

---

