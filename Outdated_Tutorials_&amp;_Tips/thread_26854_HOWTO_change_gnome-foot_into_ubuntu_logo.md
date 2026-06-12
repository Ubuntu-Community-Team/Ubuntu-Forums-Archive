---
title: "HOWTO change gnome-foot into ubuntu logo"
date: 2005-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu_demon on 2005-04-14
If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```

---

### Post by Heliode on 2005-04-14
It worked! Thanks!

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=Heliode]It worked! Thanks![/QUOTE]
 it's very easy but it looks very good :)

---

### Post by popdog on 2005-04-14
Looks great, nice tip thanks  :)

---

### Post by Jason-X on 2005-04-14
I just tried it. Works well and logo looks really good.

Thanks for this :smile: 

Jason

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=Jason-X]I just tried it. Works well and logo looks really good.

Thanks for this :smile: 

Jason[/QUOTE]
 np ... small things can make a person very happy :-D

---

### Post by ubuntu_demon on 2005-04-14
Does anyone know where the Main Menu icon is located ? (That's the one that incorporates places and system in it)

edit :
we can use this logo :
[http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9](http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9)
or the small logo we already used for the applications menu.

---

### Post by Cylanes on 2005-04-14
This is very cool, tnx

---

### Post by Pulka on 2005-04-14
Errr....it gives an error

~ $ sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak
:
~ $ sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png
cp: cannot stat `/usr/share/hwdb-client/ubuntu_logo.png': No such file or directory

---

### Post by ubuntu_demon on 2005-04-14
[QUOTE=Pulka]Errr....it gives an error

~ $ sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak
:
~ $ sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png
cp: cannot stat `/usr/share/hwdb-client/ubuntu_logo.png': No such file or directory[/QUOTE]
 that logo should be there if you have installed ubuntu-desktop
But otherwise try this logo : [http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9](http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9)

---

### Post by Pulka on 2005-04-14
ok, it worked. I hadn't the ubuntu-desktop installed.

Now i have another question that doesn't relate with this topic.

Now i have something called "ubuntu update manager" and i have synaptic. Let me see if i understand. The update manager is just for the updates the system needs, and synaptic to install software. Is this right?

---

### Post by bnutting on 2005-04-14
You are correct.

---

### Post by Gandalf on 2005-04-14
thanks man, nice trick

---

### Post by Draaku on 2005-04-14
w00t! works! thanks for this simple but effective "update"

---

### Post by jerome bettis on 2005-04-14
yeah that foot is stupid isn't it?  i have a penguin there instead

---

### Post by HungSquirrel on 2005-04-14
If Mark Shuttleworth pays attention to the critique of the Ubuntu/GNOME user interface, this hack should become default.

---

### Post by Topper on 2005-04-14
Nice. However, the 'About Gnome' entry in 'Systems' now got the Ubuntu logo too  ;-)

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=HungSquirrel]If Mark Shuttleworth pays attention to the critique of the Ubuntu/GNOME user interface, this hack should become default.[/QUOTE]


I think its not the default because Ubuntu doesn't want to piss off the Gnome devs.

---

### Post by clparker on 2005-04-15
Cool Trick, Very Cool Trick!

---

### Post by jerome bettis on 2005-04-15
[QUOTE=poofyhairguy]I think its not the default because Ubuntu doesn't want to piss off the Gnome devs.[/QUOTE]
 i hear ya.  

but for real what's with the foot .. seriously i mean come on it's a foot!!  i don't want that on my screen!!!

---

### Post by artnay on 2005-04-15
Think about usability. Every distro having its own icon as a Main menu icon, that's a terrible idea. The foot stands for GNOME and Menus, let it be that way by default. People using many distributions only get confused if every distribution has its own "action icon". Maybe a distro-specific icon as a symbol for home directory, but that would need some extra job done.

Seriously, replacing the foot in default install wouldn't be that good idea. GNOME isn't Ubuntu, and vice versa.

---

### Post by jerome bettis on 2005-04-15
right

well it would be a smart move for gnome to change their logo.  i wonder if they thought about what users would think before they chose to use a foot.  i should start a poll:  do you like the gnome foot?  i bet 90-95% would say hell no.

whenever i showed ubuntu to 3 friends, each one said "what's the deal with the foot?  i'm not going to use an os that has a foot for a logo."  :razz:

---

### Post by ubuntu_demon on 2005-04-15
[QUOTE=artnay]Think about usability. Every distro having its own icon as a Main menu icon, that's a terrible idea. The foot stands for GNOME and Menus, let it be that way by default. People using many distributions only get confused if every distribution has its own "action icon". Maybe a distro-specific icon as a symbol for home directory, but that would need some extra job done.

Seriously, replacing the foot in default install wouldn't be that good idea. GNOME isn't Ubuntu, and vice versa.[/QUOTE]
 Well Kubuntu has their own logo. So if Kubuntu would do the same with their logo people won't get confused. I don't like having a foot as "start" button.

But is there anyone who knows how to change the Main Menu logo ?

---

### Post by ba5e on 2005-04-15
Nice one!! now this is really ubuntu! not a silly smeely foot! (not that I do not like Gnome!) :)  :)

---

### Post by parktownprawn on 2005-04-18
> But is there anyone who knows how to change the Main Menu logo ?

To change the main menu icon try

```
sudo cp /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png.bak  
sudo cp your_custom_icon.png  /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png 
killall gnome-panel
```

worked for me

---

### Post by ubuntu_demon on 2005-04-18
[QUOTE=parktownprawn]To change the main menu icon try

```
sudo cp /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png.bak  
sudo cp your_custom_icon.png  /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png 
killall gnome-panel
```

worked for me[/QUOTE]
 cool thnx I'll try it when I get home!

Like I said earlier in this post there's a nice Ubuntu logo we can use for this :

[http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9](http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9)

---

### Post by ubuntu_demon on 2005-04-19
okay I created a png for this. I just converted the svg to png .. it's probably way too big but maybe you can use it for something else too :)

---

### Post by ubuntu_demon on 2005-04-19
here it is (it's transparant)

---

### Post by N'Jal on 2005-04-19
This hack isnt working :( I really like the ubuntu logo. I dont have a problem with the foot. But id personally prefer the ubuntu logo and as for the whole Dont have it as the default arguement what about Redhat and Mandriva (formally mandrake). Last i checked they have their own GNOME "start" button. I dont really care if it is default or not coz if it isnt there are ways around it and i'd simply do that.

But back to my point if anyone could tell me why it might not be working id be appriciative, i have ubuntu-desktop installed and am runng hoary.

---

### Post by ubuntu_demon on 2005-04-20
[QUOTE=N'Jal]This hack isnt working :( I really like the ubuntu logo. I dont have a problem with the foot. But id personally prefer the ubuntu logo and as for the whole Dont have it as the default arguement what about Redhat and Mandriva (formally mandrake). Last i checked they have their own GNOME "start" button. I dont really care if it is default or not coz if it isnt there are ways around it and i'd simply do that.

But back to my point if anyone could tell me why it might not be working id be appriciative, i have ubuntu-desktop installed and am runng hoary.[/QUOTE]

did you do $killall gnome-panel ?

---

### Post by ubuntu_demon on 2005-04-20
here's another very nice logo :

---

### Post by globalspace on 2005-04-20
i use this one found in gnome-look.org  :) 

i like it very much  ;-)

ps. it's transparent

---

### Post by ubuntu_demon on 2005-04-20
[QUOTE=globalspace]i use this one found in gnome-look.org  :) 

i like it very much  ;-)

ps. it's transparent[/QUOTE]
 funny ! 
it's some kind of blue monster right ? :)

---

### Post by globalspace on 2005-04-20
[QUOTE=demon666_nl]funny ! 
it's some kind of blue monster right ? :)[/QUOTE]

 :razz:  hiihih i love to customize my Gnome  :smile:

---

### Post by N'Jal on 2005-04-20
Yes a follewed the instructions to the letter. I know that all the icons are in the folders, i checked everything is where it should be execute killall gnome-panel gnome panel is killed and when it comes back nothing has changed. One thing that does change though is that i have to log out to restart GDesklets

---

### Post by thoms on 2005-04-20
[QUOTE=demon666_nl]If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```[/QUOTE]
 Awesome tip, simple and effective.

---

### Post by ubuntu_demon on 2005-04-20
thnx :)

---

### Post by ubuntu_demon on 2005-04-20
[QUOTE=N'Jal]Yes a follewed the instructions to the letter. I know that all the icons are in the folders, i checked everything is where it should be execute killall gnome-panel gnome panel is killed and when it comes back nothing has changed. One thing that does change though is that i have to log out to restart GDesklets[/QUOTE]
 strange .. I have no idea why this doesn't work at your pc. did you try restarting gnome ? (ctrl-alt-backspace)

---

### Post by mattack on 2005-04-20
[QUOTE=N'Jal]Yes a follewed the instructions to the letter. I know that all the icons are in the folders, i checked everything is where it should be execute killall gnome-panel gnome panel is killed and when it comes back nothing has changed. One thing that does change though is that i have to log out to restart GDesklets[/QUOTE]

I have this problem with certain icon themes (most notably Lila). Try switching icon themes and see if it works. I'm still trying to get it to work with the Lila theme...
I've tried renaming every icon that looks like the foot in the theme and it still wants to have that foot for the Application menu...

I didn figure out a fix for the new icon for "About GNOME" in the system menu.
edit /usr/share/applications/gnome-about.desktop
in the file there's a path for the icon, change it to point to the correct foot icon.

---

### Post by N'Jal on 2005-04-21
Yes that has made it work execept for the gartoon theme (the one i was using at the time), i assume switching themes then running through the process will fix this. If not i will post that it dont

---

### Post by Jade Robbins on 2005-04-21
[QUOTE=demon666_nl]If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```[/QUOTE]
 Wow what a great idea, i like the idea of seeing ubuntu rather than gnome any day! Thanks for the tip!

---

### Post by bored2k on 2005-04-21
For some unknown reason, I still like the ol' Red Hat > [http://img135.echo.cx/my.php?image=flow27ki.png](http://img135.echo.cx/my.php?image=flow27ki.png) :-|

---

### Post by N'Jal on 2005-04-21
I have yet to get this working with the gartoon icon set

Strange

---

### Post by randomidiot on 2005-04-21
> Well Kubuntu has their own logo. 
The icon for applicationsmenu is the standard logo for kde 3.4 ....

Anyway, is there a way to avoid an icon at all in gnome-menu?

---

### Post by Spudgun on 2005-04-21
[QUOTE=N'Jal]I have yet to get this working with the gartoon icon set

Strange[/QUOTE]

You have to replace the Gnome icon in /usr/share/icons/gartoon

---

### Post by zaxer on 2005-04-22
Isnt working for me =( All commands went well but when I kill the panel the old gnome foot appears..

---

### Post by ubuntu_demon on 2005-04-22
[QUOTE=zaxer]Isnt working for me =( All commands went well but when I kill the panel the old gnome foot appears..[/QUOTE]
 try switching your theme to human. If this solves the problem you should go hunt for the icon file of your theme.

---

### Post by hypersonic5 on 2005-04-22
Is there any way I can do this method, but instead of using the default ubuntu logo, use a blue one instead?

---

### Post by N'Jal on 2005-04-22
I have discovered the problem, for me anyway, it might be the same for others. Gartoon (and goodness knows how many other themes) use SVG. So unless someone can create this as a SVG i dont think i can use it. Please dont ask me to do it, coz i dont know how.

---

### Post by ubuntu_demon on 2005-04-23
[QUOTE=N'Jal]I have discovered the problem, for me anyway, it might be the same for others. Gartoon (and goodness knows how many other themes) use SVG. So unless someone can create this as a SVG i dont think i can use it. Please dont ask me to do it, coz i dont know how.[/QUOTE]
 well just replace the svg with an ubuntu svg then :)

---

### Post by greenwom on 2005-04-23
Well just finished installing Hoary... Still in my first month in the Linux realm.

About dang time... 

Anyway as a newbee I'm a fan of Ubuntu and it's Logo !!! 

To change this images (color) all you should have to do is edit the png image and stay with the size restrictions of the original image right?  Sounds right to me...

---

### Post by ubuntu_demon on 2005-04-23
[QUOTE=greenwom]Well just finished installing Hoary... Still in my first month in the Linux realm.

About dang time... 

Anyway as a newbee I'm a fan of Ubuntu and it's Logo !!! 

To change this images (color) all you should have to do is edit the png image and stay with the size restrictions of the original image right?  Sounds right to me...[/QUOTE]
 yeah
and it doesn't matter much how big/small the end-result is because it will be scaled. But it's nice to make it aproximately half as big as your avatar :)

---

### Post by IceEyz on 2005-04-23
Worked a bit, had to relocate the icon to /home/user/.icons/gartoon/scalable/apps because of the Gartoon-icon set.

Also, somehow the icon did not want to scale to a big enough size, it stayed crappy small. With Inkscape SVG I was able to resize it though and it definately looks nice :)

And well... yup, first post :)

---

### Post by N'Jal on 2005-04-24
^
|
|

Same solution. Oh well its a dirty way to do it but it works

---

### Post by Gezzer on 2005-05-03
[QUOTE=N'Jal]^
|
|

Same solution. Oh well its a dirty way to do it but it works[/QUOTE]
 just updated the Gnome logo to the Ubuntu one, looks great
now just have to install the Gnome menu editor ...

---

### Post by Psquared on 2005-05-04
[QUOTE=demon666_nl]If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```[/QUOTE]


Sweet!!!!

---

### Post by JGJones on 2005-05-15
[QUOTE=poofyhairguy]I think its not the default because Ubuntu doesn't want to piss off the Gnome devs.[/QUOTE]

I use this - [http://www.gnome-look.org/content/show.php?content=22413](http://www.gnome-look.org/content/show.php?content=22413)

Incorpate the Gnome foot and the Ubuntu icon into one...look good and Gnome devs should be happy that their foot's there while Ubuntu get their icon too :D

---

### Post by Nu-Buntu on 2005-05-15
Beeyooteeful!

---

### Post by gabbman on 2005-05-15
I would like to see this built in on subsequent releases.

---

### Post by ddocta on 2005-05-16
Nice Trick

---

### Post by byen on 2005-05-17
Tried it on gnome? pretty darn kool..... but is there anyway I can do this on KDE? Im really inclined towards KDE since I kinda need the graphic front...i tried renaming the icons as someone suggested but it just doesnt allow me to do anything.....
can someone please help me?
Byen!

---

### Post by Xian on 2005-05-17
[QUOTE=byen]Tried it on gnome? pretty darn kool..... but is there anyway I can do this on KDE? [/QUOTE]
You mean change the main menu icon? 
You just need to replace the "kmenu.png" image.

This is showing the 32x32 image but I think the menu uses 16x16.

[img]http://img.photobucket.com/albums/v469/camplear/forums/kdemenu.png[/img]

---

### Post by bored2k on 2005-05-17
[QUOTE=Xian]You mean change the main menu icon? 
You just need to replace the "kmenu.png" image.

This is showing the 32x32 image but I think the menu uses 16x16.

[img]http://img.photobucket.com/albums/v469/camplear/forums/kdemenu.png[/img][/QUOTE]
 I'm sorry but that is the ugliest nautilus screenshot I have ever seen (and I like Kubuntu !).

---

### Post by Xian on 2005-05-17
[QUOTE=bored2k]I'm sorry but that is the ugliest nautilus screenshot I have ever seen (and I like Kubuntu !).[/QUOTE]
Oh, you want Nautilus? Okay.... :)

[img]http://img.photobucket.com/albums/v469/camplear/forums/kdemenu2.png[/img]

---

### Post by klutzini on 2005-05-17
[QUOTE=demon666_nl]If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```[/QUOTE]
 wow... never though of doing that....

Works brilliantly..

Thankyou...

---

### Post by byen on 2005-05-17
thanks for your reply guys. Infact what you suggested was my first try but it says "access denied!" mysay be it would work if I logged in as root but there is no root account in Ubuntu is there?

(sorry if my Q? sound dumb.... but hope tha shows how new I am to linux)

thank you guys.

---

### Post by Xian on 2005-05-17
[QUOTE=byen]Infact what you suggested was my first try but it says "access denied!" mysay be it would work if I logged in as root but there is no root account in Ubuntu is there?[/QUOTE]
KDE Menu Icon > Run Command > kdesu konqueror
Navigate to the desired images and rename/replace.

---

### Post by byen on 2005-05-18
man...i tried it before and it did not work...and now it seemed so simple....that reading my own post pissed me off....wow that was silly. I guess i better try a lil more before posting. thank you anyways.

---

### Post by SamH on 2005-05-18
Finally got around to trying this.  Wow! It worked great.

---

### Post by Kyral on 2005-05-19
[QUOTE=hypersonic5]Is there any way I can do this method, but instead of using the default ubuntu logo, use a blue one instead?[/QUOTE]

Nice trick, but I second this one, it would fit in better with my theme. Perhaps the Kubuntu logo?

---

### Post by sebgate20 on 2005-05-20
[QUOTE=Kyral]Nice trick, but I second this one, it would fit in better with my theme. Perhaps the Kubuntu logo?[/QUOTE]
 Does anyone have a link (or can they attach) the blue Ubuntu Logo? I found it somewhere on the forums but I can't remember where!

I prefer the blue version to the orange as this fits in better with my desktop theme!

Thanks

Seb

---

### Post by Kyral on 2005-05-20
I think I found it. It was one of the Super Moderator's Avatars. Hope they let us use it :D

---

### Post by Jormundgand on 2005-05-21
Having followed the instructions in this Howto I found the resulting Ubuntu icon too small for my needs, so I made a good 48x48 from the official logo available on the wiki. I'm attaching it here.

The Howto is sound, it's just the image is too small. This should look nicer.

---

### Post by Poul on 2005-05-21
simple and effective

---

### Post by RastaMahata on 2005-05-22
[QUOTE=sebgate20]Does anyone have a link (or can they attach) the blue Ubuntu Logo? I found it somewhere on the forums but I can't remember where!

I prefer the blue version to the orange as this fits in better with my desktop theme!

Thanks

Seb[/QUOTE]
 [Why not take the logo from the Kubuntu Wiki?](http://www.ubuntulinux.org/wiki/KubuntuArtwork)

---

### Post by Jormundgand on 2005-05-22
[QUOTE=sebgate20]Does anyone have a link (or can they attach) the blue Ubuntu Logo? I found it somewhere on the forums but I can't remember where!

I prefer the blue version to the orange as this fits in better with my desktop theme![/QUOTE]

You might try looking at [this watermark](http://www.gnome-look.org/content/show.php?content=16278).

---

### Post by hanzj on 2005-05-23
I have a problem:
I'm running the "Main Menu" (the one with Applications, Places, and System all integrated) . I'm not running the Menu Bar (the default bar Ubuntu puts on the panel, with Applications, System, etc spread out).

Here's what I did:

First, I followed the advice in [post #1]("http://ubuntuforums.org/showpost.php?p=131629&postcount=1"), the one about changing the logo for those using the Menu Bar. 

[QUOTE=demon666_nl]If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :
 
 ```

 sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak
 
 sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png
 
 killall gnome-panel
 
```[/QUOTE]
----------

Then I realized that I wasn't using the Menu Bar, I'm using the Main Menu (the one with Applications, Places, and System all integrated). So then, I took the advice of [post #25]("http://ubuntuforums.org/showpost.php?p=137703&postcount=25").

[QUOTE=parktoprawn]To change the main menu icon try
 
```
sudo cp /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png.bak 
 sudo cp your_custom_icon.png  /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png 
 killall gnome-panel
```
 [/QUOTE]


But the icon for the main menu is still a Gnome Foot. What do I do? I think my error was trying to do both changes. 
Can anyone help?

---

### Post by Curing@ on 2005-05-26
Very nice! ;-)

---

### Post by parktownprawn on 2005-05-26
In reply to hanzj:
[post #77](http://www.ubuntuforums.org/showpost.php?p=183333&postcount=77) 

whether the trick works or not may depend on what icon theme you are using.

which icon theme are you using? 

i presume you  tried something like:
```
sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png
```

---

### Post by ganatronic on 2005-05-26
I'm getting this error (with the fix being to get ubuntu-desktop):

~ $ sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png
cp: cannot stat `/usr/share/hwdb-client/ubuntu_logo.png': No such file or directory


Yeah, I can't believe I never realized that I should have this program. **However**, installing ubuntu-desktop results in this error:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/r/readahead/readahead_1.0.1-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/readahead/readahead_1.0.1-2ubuntu1_i386.deb)
  404 Not Found

So I can't get readahead, and so I can't finished the ubuntu-desktop install. This seems to be a recent issue, as per [this mailing list thread](http://ubuntuforums.org/showthread.php?t=36615&highlight=failed+fetch+readahead). Any one have an idea when this will be fixed? or how to fix it right now?

---

### Post by ganatronic on 2005-05-26
Figured it out. The archives are having a little problem right now. So I went on irc and a super nice fellow gave me readahead_1.0.1-2ubuntu1_i386.deb, I then copied it to the synaptic cache - /var/cache/apt/archives - and then successfully installed the ubuntu desktop through synaptic.

Awesome!

The footprint is dead. Long live the footprint!

---

### Post by Orunitia on 2005-05-26
Right, this pretty much broke my system. First it killed my gnome-panel and wouldn't let me restart it, so I restarted my system, and this is what error pops up when I try to start gnome. It won't let me start KDE, xfce, or fvwm either.

** (gnome-session:8323): WARNING **: unable to read ICE authority file /home/ben/.ICEauthority

Any help on getting this fixed is appreciated.


EDIT: I fixed my problem by deleting the file "ICEauthority"

EDIT 2: Now that it's actually working, this looks a lot nicer than the gnome foot, thanks.  :)

---

### Post by misterx on 2005-06-19
A nice, non-destructive way to do the same thing (set the Application menu icon) :

1.    open **Configuration Editor** -> apps -> panel -> objects -> find the object  with object type "menu-object", for me it was "object_2"
2.    check the "use_custom_icon" check box
3.    next to "custom_icon", enter the path to the icon in the value field (/usr/share/hwdb-client/ubuntu_logo.png) 

That should leave all the other places where the gnome icon is used unchanged.

I tried doing this using Smeg, and it didn't work--it lets you choose the icon with a file browser, however when commiting the changes, nothing happens to the icon.

---

### Post by spockrock on 2005-06-19
thanks for the cool how to................

---

### Post by FrzzMan on 2005-06-25
This icon is theme dependant...

You have to copy the .svg file (don't know if .png file will work or not) to your-icons-directory/scalable/apps/gnome-logo-icon-transparent.svg

your-icons-directory should be in your ~/.icons or /usr/share/icons (if it's a system wide icons package)

---

### Post by manicka on 2005-06-25
Nice howto :D I've gone back to the little foot though. Just didn't suit my theme

---

### Post by vladuz976 on 2005-07-08
[QUOTE=demon666_nl]If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```[/QUOTE]
 hi i followed the how to and the ubuntu icon now shows, only thing is that my notification area is gone now.  i added it again. but it doesn't show up. really inconvenient.  
any ideas how to get it back?

---

### Post by ubuntu_demon on 2005-07-08
[QUOTE=vladuz976]hi i followed the how to and the ubuntu icon now shows, only thing is that my notification area is gone now.  i added it again. but it doesn't show up. really inconvenient.  
any ideas how to get it back?[/QUOTE]
 You are probably using a different theme. If you switch to human you should be able to have the desired effect.

But to change it back :
```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak /usr/share/pixmaps/gnome-logo-icon-transparent.png
killall gnome-panel

```

---

### Post by djSeverin on 2005-07-11
[QUOTE=misterx]A nice, non-destructive way to do the same thing (set the Application menu icon) :

1.    open **Configuration Editor** -> apps -> panel -> objects -> find the object  with object type "menu-object", for me it was "object_2"
2.    check the "use_custom_icon" check box
3.    next to "custom_icon", enter the path to the icon in the value field (/usr/share/hwdb-client/ubuntu_logo.png) 

That should leave all the other places where the gnome icon is used unchanged.
[/QUOTE]
This's EXACTLY what I was looking for **misterx**! Thanks heaps!  :grin: 

Figured I'd contribute in my own little way, so I've built/nailed together a slightly improved Ubuntu menu PNG logo image. I've also attached the associated Gimp project.

---

### Post by ubuntu_demon on 2005-07-12
[QUOTE=djSeverin]This's EXACTLY what I was looking for **misterx**! Thanks heaps!  :grin: 

Figured I'd contribute in my own little way, so I've built/nailed together a slightly improved Ubuntu menu PNG logo image. I've also attached the associated Gimp project.[/QUOTE]
 nice !
but my method is also non destructive because you can copy it back.

I like the icon :)

---

### Post by maxsideburn on 2005-07-12
Here you go guys, I really like the idea of having an Ubuntu icon, that's one of the reasons I like Ubuntu in the first place. It's like Windows or MacOS, very integrated. Well the one thing that I didn't think matched up very well was having a bright orange icon up there, so I created a simple flat black one to take it's place. I think it integrates very nicely.

---

### Post by ubuntu_demon on 2005-07-12
[QUOTE=maxsideburn]Here you go guys, I really like the idea of having an Ubuntu icon, that's one of the reasons I like Ubuntu in the first place. It's like Windows or MacOS, very integrated. Well the one thing that I didn't think matched up very well was having a bright orange icon up there, so I created a simple flat black one to take it's place. I think it integrates very nicely.[/QUOTE]
 you are right. After a while I went crazy with the orange icon so I changed it back to the gnome foot. But I think I'm gonna try yours :)

---

### Post by ArBaDaCarBa on 2005-07-12
Very cool trick, but if I may, if would be much better to replace the first "cp" with a dpkg-divert:

$ sudo dpkg-divert --rename /usr/share/pixmaps/gnome-logo-icon-transparent.png

This way, the customization will stay effective even if you upgrade the gnome-desktop-data package.

[More info on dpkg-divert](http://www.debian-administration.org/?article=118).

---

### Post by ubuntu_demon on 2005-07-12
[QUOTE=ArBaDaCarBa]Very cool trick, but if I may, if would be much better to replace the first "cp" with a dpkg-divert:

$ sudo dpkg-divert --rename /usr/share/pixmaps/gnome-logo-icon-transparent.png

This way, the customization will stay effective even if you upgrade the gnome-desktop-data package.

[More info on dpkg-divert](http://www.debian-administration.org/?article=118).[/QUOTE]
 But then you won't see it if they would have changed it :-P

But there are always different ways to do stuff in linux :)

---

### Post by cdk on 2005-07-13
good post. i had done this but a month ago and reformated.  This sparked me to do it again!

cheers,

---

### Post by magalas_79 on 2005-07-13
[QUOTE=N'Jal]This hack isnt working :( I really like the ubuntu logo. I dont have a problem with the foot. But id personally prefer the ubuntu logo and as for the whole Dont have it as the default arguement what about Redhat and Mandriva (formally mandrake). Last i checked they have their own GNOME "start" button. I dont really care if it is default or not coz if it isnt there are ways around it and i'd simply do that.

But back to my point if anyone could tell me why it might not be working id be appriciative, i have ubuntu-desktop installed and am runng hoary.[/QUOTE]

I discovered why this trick didn't work for you. This trick replace the foot icon of Menu Bar. It's a different bar from Main Menu. Probably in your applet you are visualizing Main Menu not Menu Bar, I haven't yet found a solution for Main Menu, but i'm seeking...

Bye

---

### Post by SpEcIeS on 2005-07-14
It is looking more like home. :)

---

### Post by traherom on 2005-07-14
It, uh, made the lower left corner of my screen redish... hope it fixes with a restart...

 :?

--EDIT--
A degause fixed it. Don't know why the gnome-panel kill did that, but... Yeah! Very pretty.

---

### Post by arnieboy on 2005-07-14
[QUOTE=parktownprawn]To change the main menu icon try

```
sudo cp /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png.bak  
sudo cp your_custom_icon.png  /usr/share/icons/hicolor/48x48/apps/gnome-main-menu.png 
killall gnome-panel
```

worked for me[/QUOTE]

sure did work for me too.. thanks!

---

### Post by ubuntu_demon on 2005-07-15
[QUOTE=magalas_79]I discovered why this trick didn't work for you. This trick replace the foot icon of Menu Bar. It's a different bar from Main Menu. Probably in your applet you are visualizing Main Menu not Menu Bar, I haven't yet found a solution for Main Menu, but i'm seeking...

Bye[/QUOTE]
 see this post : [http://www.ubuntuforums.org/showpost.php?p=137703&postcount=25](http://www.ubuntuforums.org/showpost.php?p=137703&postcount=25) :)

---

### Post by charlieg on 2005-07-15
Nice hack.  Still, it's a hack.  Would be cool if this were properly done by Ubuntu - it's logo is so much brighter than that boring black foot!

---

### Post by sebgate20 on 2005-07-17
Here is a copy of the Ubuntu logo in Blue. It has taken me months to find it :-) I found it through the Art Gallery.

Seb

---

### Post by black hole sun on 2005-07-17
Guess I'm in the minority of those who LIKE the foot.  :)

---

### Post by poptones on 2005-07-17
I like the foot, but it's black and kinda boring. I also did not like the BRIGHT ORANGE DOT being stuck up there, it was annoying, So I tried the black ubuntu dot and didn't like that for the same reason I was bored with the foot. So I made yet ANOTHER version, this time something in between. I find it juuuust right.

---

### Post by charlieg on 2005-07-24
Ah, found the **proper** way to do this.  (I'm not sure if this is mentioned earlier in the thread, but I don't have time to read the previous 10 pages, sorry!)

Rather than copying over the original foot logo, as suggested in the howto, simply save the image somewhere of your choosing and in GConf set 'use_custom_logo' and point 'custom_icon' to the image you want!  Those two settings can be found under '/apps/panel/default_setup/objects/menu_bar' - just search for 'menu'.

Much nicer and much less hackier!!!

Edit: eek, I posted before I'd properly tried it!  I spoke too soon!  Changing that particular setting in GConf doesn't seem to do the trick, unless I'm doing something very wrong.

Edit: btw, I discovered this (as if it isn't obvious) here:
[http://www.ubuntuforums.org/showthread.php?t=51640](http://www.ubuntuforums.org/showthread.php?t=51640)

---

### Post by SYD2005 on 2005-07-25
ubuntu_demon -- thanks for the tip. 

Great stuff.

---

### Post by JoeyrS on 2005-07-25
Looks very nice, thanks for the tip :)

---

### Post by JimmyBEng on 2005-09-04
along to lines of charlieg 's post.  Is there a way to do this so that instead of overwriting the gnome-foot icon that we can just tell the system to use an icon of a different name? It seems like there should be a file somewhere where the name just needs to be changed.  I've looked but haven't been able to find it yet, but then again I'm not real familar with the internals of gnome.

---

### Post by pinguimtux on 2005-09-06
[QUOTE=black hole sun]Guess I'm in the minority of those who LIKE the foot.  :)[/QUOTE]

I like the foot too.

---

### Post by Monkey-Dude on 2005-09-08
Is it possible to have a rectangular start button instead of a square one...?

---

### Post by CMIVXX on 2005-09-10
Awesome stuff.  So simple yet, adds so much.  Thanks for the tip.

---

### Post by alinux on 2005-09-10
really cool thanks! :) It must be default rof the future! :) I think.

---

### Post by urbandryad on 2005-09-20
[QUOTE=ubuntu_demon]that logo should be there if you have installed ubuntu-desktop
But otherwise try this logo : [http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9](http://www.ubuntuforums.org/showpost.php?p=116892&postcount=9)[/QUOTE]
 I think the foot is kind of cute, actually. :3 I can't wait to have linux all set up on my own laptop

---

### Post by axlpxl on 2005-09-28
Should'nt this be standard in breezy?

---

### Post by vvlist on 2005-09-28
For anyone who's wondering, this works in Breezy too.

---

### Post by strawberry on 2005-10-05
I have breezy. I also made this trick.
I've just recognized that on 3.October an update changed back gnome-logo-icon-transparent.png to original one but on the left corner of the upper panel I still see the ubuntu logo. I think the ubuntu logo on the panel will be the default in breezy. ;)

---

### Post by LaSSarD on 2005-10-05
[QUOTE=strawberry]I have breezy. I also made this trick.
I've just recognized that on 3.October an update changed back gnome-logo-icon-transparent.png to original one but on the left corner of the upper panel I still see the ubuntu logo. I think the ubuntu logo on the panel will be the default in breezy. ;)[/QUOTE]
yes, it will. i was very happy with my gnome foot logo then I updated the system and now there's an ubuntu logo... it is nice, but not on my system, because it doesn't fit at all with my icons theme &#172;&#172;

---

### Post by vr6stress on 2005-10-05
I keep forgetting where it resides - this default ubuntu logo - but i'd like to change it back.

it's not in the same location it used to be in...and i can't seem to find it anywhere...

---

### Post by vr6stress on 2005-10-05
NM - found it  /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.

---

### Post by manicka on 2005-10-06
[QUOTE=LaSSarD]yes, it will. i was very happy with my gnome foot logo then I updated the system and now there's an ubuntu logo... it is nice, but not on my system, because it doesn't fit at all with my icons theme ¬¬[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=70652](http://www.ubuntuforums.org/showthread.php?t=70652)

---

### Post by niigatapeter on 2005-12-02
[QUOTE=Monkey-Dude]Is it possible to have a rectangular start button instead of a square one...?[/QUOTE]

I was wondering the same thing? I'm trying to set up an installation of Ubuntu for my old mother, who would get confused if the "start button" isn't similarly shaped as the windows one.

---

### Post by christhemonkey on 2006-01-11
very nice little trick:)

---

### Post by pienose on 2007-10-15
I can't get this to work, I run the code, and the killall bit, and the panels re-start. But nothing hapens. I am using ubuntu studio if that makes a difference. Help would be apreaceated.

---

### Post by tehgam3r on 2008-11-16
I know this is off the subject but how do I change the ubuntu logo to the apple icon logo on the panel. because  I just cant after following the procedures the right way for mac osx logo

---

### Post by LonelySEason on 2009-02-25
> **ubuntu_demon said:**
> If you want to change the gnome-foot logo next from the Applications menu into the ubuntu logo this is all you have to do :

```

sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png.bak

sudo cp /usr/share/hwdb-client/ubuntu_logo.png /usr/share/pixmaps/gnome-logo-icon-transparent.png

killall gnome-panel

```

cp: cannot stat `/usr/share/hwdb-client/ubuntu_logo.png`: No such file or directory
I've tried to search on /usr/share but I didn't see the hwdb-client folder, anything wrong with my Ubuntu???

---

### Post by nebileix on 2009-05-26
A little script to do it for u.

Btw, it required root permission in order to change the logo.

---

### Post by Gamfrek on 2009-07-10
):P Hi everybody! This is my first post!!!!!

Anyway, I just got Ubuntu this morning and I don't think I understand what you are saying... Where would I put that code? And where can I make icons so I can set my own Icon?

---

