---
title: "Three minor questions/problems with GNOME Shell in Oneric"
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bash on 2011-07-26
So I finally decided to make to jump over to Oneric today, now that it looks like most of the bigger hick-ups of the GNOME 3 transition are worked out. Install and updating went smooth and got my Unity set up the way I like it rather quickly. Like the new touches in themes, like that dark toolbars are now the default (sadly still a 1px border, altough easily removed). Compiz model dialog seem to be a nice idea, but still need some work. 

After all the basics were set it was time to start playing around with GS. Followed the development of it and actually tried to through jhbuild quite a few times, but since it was properly released never found the time to try out the final version. So finally spent a bit of time now with it. After having a few crashes with the repo version, updated to the ricotz testing one and now got it mostly set up the way I want it. Except I ran into a couple of minor troubles that are stil big enough for me to quite bug me:

[list=1][*](**Solved**) Is there a an Ambiance window decorator (border) theme that works with the shell. The GTK+ part of the theme works normally but the window borders get replaced with some ugly fallback theme when I try to use them in GS. Am I doing something wrong? Or is there an extra theme yet?
[*] I must be doing something wrong but for some strange reason I can't manage to get the dock extension to work. Installed the extensions package provided by ricotz testing and other extensions work just. But I can install the dock extension all I want, turn it on and off in the tweak tool all I want - no dock shows up.
[*] (**Solved**) For some reason Alt+F2 isn't working in the Shell. Since Alt+F2 in Unity is handled through the Unity Compiz plugin, I figured the default gnome run program just isn't installed. Except haven't been able to figure out the package name. Solution will probably be quite obvious, but a pointer would be nice[/list]

Anyone got an idea how to resolve these troubles? Help would be appreciated.

---

### Post by mc4man on 2011-07-26
> For some reason Alt+F2 isn't working in the Shell. 
Go system settings > keyboard > shortcuts >  system and enable if disabled

---

### Post by bash on 2011-07-26
Thanks that worked greated. 1 down, two to go :D

---

### Post by bash on 2011-07-26
Took my quite a bit of tinkering, searching and comparing, but I finally figured out what broke the Ambiance metaticy (window border) theme under GNOME Shell. So I finally got the full Ambiance themer running under the Shell. Only thing to figure out now is how to get that dock working. Anyone got similiar problems?

Btw if someone wants the Ambiance version that works under GNOME Shell, I can upload it here.

---

### Post by G0B1!N on 2011-07-28
> **bash said:**
> Btw if someone wants the Ambiance version that works under GNOME Shell, I can upload it here.
 
Yes Please ^^ I can't figure out how to get rid of these ugly borders. :icon_frown:

---

### Post by 23dornot23d on 2011-07-28
To get the dock working you need to alter the metadata.json file

/home/.local/share/gnome-shell/extensions/ (inside the dock folder)

Then check using **Gnome Tweak Tool** ...... to make sure it is turned on ...

[[COLOR=Blue]_***Screenshot***_[/COLOR]]("http://img194.imageshack.us/img194/431/screenshotat20110729022.jpg")

similar with the Ambiance theme
[URL="http://img64.imageshack.us/img64/4592/screenshotat20110729023.jpg"][COLOR=Blue][U][I][B]
Screenshot[/B][/I][/U][/COLOR][/URL]

same with a menu extension added too

[_***Screenshot***_]("http://img40.imageshack.us/img40/184/snapshot31i.jpg")

---

### Post by bash on 2011-07-29
> **23dornot23d said:**
> To get the dock working you need to alter the metadata.json file

/home/.local/share/gnome-shell/extensions/ (inside the dock folder)

Then check using **Gnome Tweak Tool** ...... to make sure it is turned on ...

[[COLOR=Blue]_***Screenshot***_[/COLOR]]("http://img194.imageshack.us/img194/431/screenshotat20110729022.jpg")

As I wrote in my original post, I did all that, yet it still does not work for some reason. Instead it even breaks my shell when I activate it.

> similar with the Ambiance theme
[URL="http://img64.imageshack.us/img64/4592/screenshotat20110729023.jpg"][COLOR=Blue][U][I][B]
Screenshot[/B][/I][/U][/COLOR][/URL]

What I was talking about, wasn't the Gtk+ part of the theme that defines how the inside of the window looks like, but the Metacity part that defines how the window borders are drawn. Found a solution for that though after quite a bit of playing around and now got the complete Ambiance theme running in the shell.

[[IMG]http://img684.imageshack.us/img684/9833/ambianceshell.th.png[/IMG]](http://imageshack.us/photo/my-images/684/ambianceshell.png/)

> **G0B1!N said:**
> Yes Please ^^ I can't figure out how to get rid of these ugly borders. :icon_frown:

If you just want the borders gone, you need to edit the file **/usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml** and change a the following lines to look like this (replace value="1" with "0"):

```
<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="false" rounded_bottom_right="false">
 	<distance name="left_width" value="0"/>
	<distance name="right_width" value="0"/>
	<distance name="bottom_height" value="0"/>
```

---

### Post by 23dornot23d on 2011-07-29
Try this extension for the dock ..... its the one I use ..... see if it does the same ..... [[COLOR=Blue]_***Download ***_[/COLOR]]("https://sites.google.com/site/000menu/home/gnome---3/filestouse/dock%40gnome-shell-extensions.gnome.org.tar.gz?attredirects=0&d=1")

it goes in

(your home directory)/.local/share/gnome-shell/extensions/(unpack/extract here)

also do

**gnome-shell --version**

just to make sure we are working from the same version

keithg@keith-Aspire-7730ZG:~$ gnome-shell --version
GNOME Shell 3.1.3


Search for [COLOR=Blue]_***[other things related to the dock]("http://www.google.com/search?client=ubuntu&channel=fs&q=dock+extension&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=ANm&channel=fs&source=hp&q=gnome+dock+extension&pbx=1&oq=gnome+dock+extension&aq=f&aqi=&aql=&gs_sm=e&gs_upl=5006l7034l0l7222l6l5l0l0l0l3l863l2680l3-1.0.1.2l4l0&bav=on.2,or.r_gc.r_pw.&fp=26e57aa7900464a7&biw=1077&bih=552")***_[/COLOR] if it still does not work

---

### Post by bash on 2011-07-29
> **23dornot23d said:**
> Try this extension for the dock ..... its the one I use ..... see if it does the same ..... [[COLOR=Blue]_***Download ***_[/COLOR]]("https://sites.google.com/site/000menu/home/gnome---3/filestouse/dock%40gnome-shell-extensions.gnome.org.tar.gz?attredirects=0&d=1")

it goes in

(your home directory)/.local/share/gnome-shell/extensions/(unpack/extract here)

also do

**gnome-shell --version**

just to make sure we are working from the same version

keithg@keith-Aspire-7730ZG:~$ gnome-shell --version
GNOME Shell 3.1.3


Search for [COLOR=Blue]_***[other things related to the dock]("http://www.google.com/search?client=ubuntu&channel=fs&q=dock+extension&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=ANm&channel=fs&source=hp&q=gnome+dock+extension&pbx=1&oq=gnome+dock+extension&aq=f&aqi=&aql=&gs_sm=e&gs_upl=5006l7034l0l7222l6l5l0l0l0l3l863l2680l3-1.0.1.2l4l0&bav=on.2,or.r_gc.r_pw.&fp=26e57aa7900464a7&biw=1077&bih=552")***_[/COLOR] if it still does not work

If I use that version of the dock extensions, the dock at least gets displayed. But in the top left corner of the screen, even blocking the "Activities" button. Also the shell still crashes if I try to enter into the overlay/activities view. But at least a small step in the right direction.

---

### Post by 23dornot23d on 2011-07-29
Ok well there is some more work going on ..... with the dock they are setting autohiding for it

( I noticed in it too is a Position Const ....... thats set up in the  new file - that is not in the other ,,,, so I am hoping that they are  making it moveable ) also in[***_ xml file_***]("http://git.gnome.org/browse/gnome-shell-extensions/plain/extensions/dock/org.gnome.shell.extensions.dock.gschema.xml.in?id=bbc00e5c3dab574fbd83c28abf9e9e0b5dc3e528")

<_description>Sets the position of the dock in the screen. 
Allowed values are 'right' or 'left'</_description>

Will put a[COLOR=Blue]*_[** link here to the latest**]("http://git.gnome.org/browse/gnome-shell-extensions/plain/extensions/dock/extension.js?id=bbc00e5c3dab574fbd83c28abf9e9e0b5dc3e528")_*[/COLOR] I found in the GIT repository  will then see if I can use it and then let you know .... as I am in another system at the moment so cannot test it out ..... 

[COLOR=Red]**well I can but its a older version I am in 3.0.1 .... ( ok [_*screenshot*_]("http://img233.imageshack.us/img233/7526/screenshotgng.jpg") )**[/COLOR]

I use the 11.10 - 64 bit system by the way ..... ( will post a screenshot here .... once I swap over to it )

Yes you are right in that it goes to the top left ..... ( [[COLOR=Blue]_***Screenshot***_[/COLOR]]("http://img263.imageshack.us/img263/2845/screenshotat20110729161.jpg") )  only difference is 3.1.3

but the system still runs fine for me .... wonder what needs changing to move it back again ... then .....

sorry that it did not solve the problem .... will update if I find anything new
__________________________________________________________________

Will now try the autohide file see if that works .... seems it autohides for good using that ..... maybe its not complete ......
if anybody else has it working ..... can you zip the extension up and post it please for download .... quite like it if it will autohide - I would also like to position where I want it though ,,,,,,

Ok will keep watching here too for updates [COLOR=Blue][_***LINK***_]("http://git.gnome.org/browse/gnome-shell-extensions/")

Some information on whats happening with  [Gnome]("http://news.gnome.org/")  and the [U][I][B][Schedule]("https://live.gnome.org/ThreePointOne")

I have a feeling from that schedule - by the end of August it should all  be pretty good ......
[/B][/I][/U] [/COLOR]

---

