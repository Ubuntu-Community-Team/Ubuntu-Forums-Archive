---
title: "Ultimate Mac OS X Pack!"
date: 2006-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by imrumpf on 2006-06-20
After scouring the internet, both these forums, gnome-look, and google, i have compiled the most complete MAC theme that I find to date. This is what it includes:

* Instructions for application bar
* usplash (Black and White) ** These are custom-made, took me foreverto do!
* cursors
* Firefox Theme
* gdm Login theme
* Login Splash
* Menubar (3 different colours in 2 resolutions: 1024 and 1280)
* Themes (Control, icons, and window)
* Wallpaper
* intructions for close/minimize/maximize buttons, mac logo, and more!

What I need to make perfect:

* Sounds
* Actual macintosh computer.


Hope everybody enjoys and let me know what you all think! Much thanks to Danny_Boy for hosting this file. Without him you would have to put up with Rapidshare for a long time. Thank you Danny Boy!
Screenshot of final product included.

[Download]("http://www.almostgeek.com/share/ultimateOSXPack.tar.bz2")

P.S. Personally, I need to keep the taskbar at the bottom (you can see I hid it for the screenshot on the right side), but you are free to do what you want!

EDIT:
*Screenshots added
*iFox Firefox theme added
*Bootsplash instructions rewritten
*Rapidshare link added.
*Rapidshare link removed, Danny Boy now hosting the file.

---

### Post by woifi on 2006-06-21
I'm not able to download the file, could you check it?

---

### Post by imrumpf on 2006-06-21
link tested. it works fine for me :confused:

---

### Post by bertd on 2006-06-21
Works fine for me too, wonderful idea by the way. With a few minor tweakers, OSX could look really nice. :)

---

### Post by imrumpf on 2006-06-21
could you inform me what needs to be tweaked? perhaps i can add these tweaks in and update the package :D

---

### Post by zluka on 2006-06-21
you could begin with screenshots of the result ;)

not everyone wants to download 8mb without knowing what it is

just a thought..

---

### Post by imrumpf on 2006-06-21
screenshots added, and here are the usplash options i have provided. The text is completly invisible and all you get is the apple icon and a progress bar underneath in the same colour. Personally I like the white much better, but it's your choice!

---

### Post by d0d0 on 2006-06-21
Nice one dude !

Personally, for the firefox theme, I prefer the "ifox" smooth theme [https://addons.mozilla.org/firefox/1830/]("https://addons.mozilla.org/firefox/1830/")

By the way, how do you get the upsplash to work ?

---

### Post by bertd on 2006-06-21
[QUOTE=imrumpf]could you inform me what needs to be tweaked? perhaps i can add these tweaks in and update the package :D[/QUOTE]

Haha no, I didn't mean that, the version you uploaded looked pretty accurate! 

I meant that OSX itself could look very nice with a few tweaks, I'm not a great fan of some of the default fonts and the striped white bars... :) Also, it's a bit too colourful at times for my taste.

But let's not turn this into a OSX-GUI discussion. ;)

---

### Post by imrumpf on 2006-06-21
[quote=d0d0]Nice one dude !

Personally, for the firefox theme, I prefer the "ifox" smooth theme [https://addons.mozilla.org/firefox/1830/]("https://addons.mozilla.org/firefox/1830/")

By the way, how do you get the upsplash to work ?[/quote] 
sorry I forgot a few commands, here is the instructions for it. ifox theme and these instructions have been added to the pack! Hope the instructions help!

---------------------------

Copy whichever bootsplash you want (White or black) to your home folder. Open up the terminal (Applications -> Accessories -> Terminal) and copy and paste the commands one by one, hitting enter to execute the command after each one.

1. sudo apt-get install libbogl-dev gcc
2. pngtobogl usplash-artwork.png > usplash-artwork.c
3. gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
4. gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o yourimage-splash.so 
3. sudo mkdir -p /usr/local/lib/usplash/
4. sudo cp yourimage-splash.so /usr/local/lib/usplash/yourimage-splash.so
5. sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourimage-splash.so 55
6. sudo update-alternatives --config usplash-artwork.so
7. sudo dpkg-reconfigure linux-image-$(uname -r

---

### Post by maubp on 2006-06-21
[QUOTE=imrumpf]screenshots added, and here are the usplash options i have provided. The text is completly invisible and all you get is the apple icon and a progress bar underneath in the same colour. Personally I like the white much better, but it's your choice![/QUOTE]
Wouldn't it be more useful to have the startup/shutdown text visible (but not very strong) just in case there are errors?

---

### Post by rado_london on 2006-06-21
[QUOTE=maubp]Wouldn't it be more useful to have the startup/shutdown text visible (but not very strong) just in case there are errors?[/QUOTE]
No because Mac does things in the easy way which doesnt have error messages. By the way it looks OK, and I must say you did loads of work to put all these things together. But I dont think copying OS X interface is good thing. I use both linux/mac os x (osx86) and I must say that both have their + and -.

---

### Post by imrumpf on 2006-06-21
While I agree about the fact that since it is not a mac, don't make it look like a mac, as each have their + and -, there are tons of people out there who love to tweak the hell out of their system. I like to make it look like something else because people look and say "wow is that a mac? how much did it cost?" and I can reply "no it's linux, it's free and if you want I can put that on your computer too!" The power of linux is not only in it's kernel, but the ammount of customizing available. With the source code open, one is free to make it do anything they want. If they (or I) want it to look like a mac, might as well.

Just my opinion.

Anyways i hope everybody likes this pack and to keep a look-out, I am trying out something which will be amazing (I hope haha)

---

### Post by d0d0 on 2006-06-22
Just a little question for mac users :

I've noticed on mac screenshots that there isn't a visible window task-bar (the one at the bottom which lets you switch windows). So the question is, how do you navigate between windows (especially when you minimize them) ?

---

### Post by imrumpf on 2006-06-22
if you look in the screenshot in the top right-ish area, there is something called a window selector. When there are multiple windows open, this window selector changes icons to reflect the current open window. their main source is ALT + TAB just like in windows, except it works in a differently. Instead of switching between different windows, it actually switches between applications. Here is an example:

You have MSN open with 3 conversations. You have two firefox windows open. You want to view your MSN so you hit alt + tab and boom, ALL of your MSN windows pop up. now you switch back to firefox, but you only see one window, because you have to minimize, move, or hide the one firefox window to see the other one, or evoke an alt+shift+tab to switch between open windows. 

Oh and clicking the close button doesnt actually close the program, so if your computer is working slow, you go to the window selector, choose the program you THOUGHT you closed, and then to go file -> Quit. Quite a few annoyances which i hope not to ever replicate in this pack :p But what i have talked about is from OS 9, it may have changed in OSX.

---

### Post by haani on 2006-06-22
the link is not working properly it stops downloadin half way through

---

### Post by imrumpf on 2006-06-22
just tried it, works fine for me :confused:

---

### Post by oskvaz on 2006-06-22
Hi, your link doesn't work. This is the error message:


bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: EOF inesperado en el archivo
tar: El error no es recuperable: salida ahora

Have you got another location for the file?

Bye

---

### Post by Xzallion on 2006-06-22
This is awesome.  I wish someone would do this but make it look like the XP desktop though.

---

### Post by rado_london on 2006-06-22
[QUOTE=Xzallion]This is awesome.  I wish someone would do this but make it look like the XP desktop though.[/QUOTE]
I would love that parody!

---

### Post by imrumpf on 2006-06-22
Perhaps XP could be my next project ;) As far as the errors people are getting, I have the file on my googlepages website. I have added a rapidshare link as backup, so now there are two links for you to choose from: if one doesnt work try the other one! And thanks for the positive feedback, that makes me really happy :)

---

### Post by haani on 2006-06-22
how do to you add menubars??

**EDIT:** Nevermind figured it out pretty easy drag and drop lol!

---

### Post by oskvaz on 2006-06-23
Man, your rapidshare link works.
The Mac OS X Pack is amazing. Congratulations
I have attached a screenshot of my desk to show you how it looks.

---

### Post by J.J Morrison on 2006-06-23
I have a big white border around the starter bar anybody know how to fix this?

---

### Post by manicka on 2006-06-23
nice effort guy :)

I'm not sure why you'd want to make your Linux desktop look like something it's not, but hey, to each their own.

enjoy :)

---

### Post by kpkeerthi on 2006-06-23
[QUOTE=manicka]
I'm not sure why you'd want to make your Linux desktop look like something it's not, but hey, to each their own.
[/QUOTE]

Yeah... not to flame... but its about individuality. Personally, I have Kubuntu but with only GNOME. Everyone said KDE is probably easier for someone moving from windows like me. After I got fairly comfortable with Linux I removed KDE and switched over to GNOME completely 'cause I feel GNOME gives my linux the unique 'linuxy' look that stands out. KDE is more microsoftish. Some like the look  & feel of OS X. Ofcourse its their personal taste.

Great work btw

---

### Post by imrumpf on 2006-06-23
:D[quote=J.J Morrison]I have a big white border around the starter bar anybody know how to fix this?[/quote] 
not 100% sure, because this has never happened to me before. there are a few things you can try tho:

1. Restart the applet (right-click, restart desklet)
2. Configure the desklet (right-click again) 
3. As last resort, uninstall gdesklets and gdesklets-data (either apt or synaptic) and then reinstall.

Hope that solves the problem.

[quote=kpkeerthi]Yeah... not to flame... but its about individuality. Personally, I have Kubuntu but with only GNOME. Everyone said KDE is probably easier for someone moving from windows like me. After I got fairly comfortable with Linux I removed KDE and switched over to GNOME completely 'cause I feel GNOME gives my linux the unique 'linuxy' look that stands out. KDE is more microsoftish. Some like the look & feel of OS X. Ofcourse its their personal taste.

Great work btw[/quote] 
Thanks a lot, the praise is really all i need from people. I think i am finally catching this "open source" bug, and finally realizing that many people do work for others just to get a "thanks d00d" or "awesome job!". it's awesome. Also to back you up on the subject of individuality, take a look at post # 23, oskvaz's screenshot. Now look at my post, #1. The freedom of open source cannot be shown any better: same pack, 2 people, and two individual looks, each tailored to the person's own taste. Rock on!:D

---

### Post by kpkeerthi on 2006-06-23
[QUOTE=imrumpf]Also to back you up on the subject of individuality, take a look at post # 23, oskvaz's screenshot. Now look at my post, #1. The freedom of open source cannot be shown any better: same pack, 2 people, and two individual looks, each tailored to the person's own taste. Rock on!:D[/QUOTE]
Yeah that. And thats why linux is fun. :)

---

### Post by fingal12 on 2006-06-25
Hi, sorry about my stupid question but how do i install this?

---

### Post by Harold P on 2006-06-25
fingal, extract the main .tar.bz2 and read the install.txt's

Anyways, what about fonts?

---

### Post by hereonyourown on 2006-07-31
> **Harold P said:**
> Anyways, what about fonts?

you mean this one? [http://www.osx-e.com/downloads/misc/macfonts.html](http://www.osx-e.com/downloads/misc/macfonts.html)

Edit: also for mac sounds, i only could find the alert bits: [http://www.osx-e.com/downloads/misc/tiger_alert_sound.html](http://www.osx-e.com/downloads/misc/tiger_alert_sound.html)

---

### Post by gorilla_king on 2006-08-08
this looks totally awesome.
i'm downloading it now, to see what it looks like after i install.
brb.

EDIT: i'm back and it's completly awesoem, nice work! now all i could hope for is an install script or maybe putting all those installs into one files instead of so many. I personally didn't like that at all. But hey, it was worth it.

---

### Post by imrumpf on 2006-08-08
The thought about a script came up, but was quickly disregarded for the following reasons:

1) I have no idea how to program
2) I have noticed some people only like to take certain elements of this pack and use them. For example on one person's computer they were sick of the brown theme so i changed the background and the icons, and changed the theme to the blue clearlooks. This gave it a nice blue theme without being too "mac-ish". I think in breaking it up, i give the person a little bit more control over what they want installed.

If somebody knew some scripting language and would be willing to help me out, i'd gladly make one for you.

---

### Post by gorilla_king on 2006-08-09
> **imrumpf said:**
> The thought about a script came up, but was quickly disregarded for the following reasons:

1) I have no idea how to program
2) I have noticed some people only like to take certain elements of this pack and use them. For example on one person's computer they were sick of the brown theme so i changed the background and the icons, and changed the theme to the blue clearlooks. This gave it a nice blue theme without being too "mac-ish". I think in breaking it up, i give the person a little bit more control over what they want installed.

If somebody knew some scripting language and would be willing to help me out, i'd gladly make one for you.

i have no idea how to code anything like that either, i'm all about php, and it's a little different. But still, awesoem job putting all this together!

---

### Post by Kingsley on 2006-08-09
awesome guide, thanks (y). i followed all the instructions and got everything to fit to my liking. a small question though; how do i place the trash icon on my desktop?

---

### Post by gorilla_king on 2006-08-09
> **Kingsley said:**
> awesome guide, thanks (y). i followed all the instructions and got everything to fit to my liking. a small question though; how do i place the trash icon on my desktop?
lol, i came back to ask the same question.

---

### Post by kurup on 2006-08-09
Go to

System Tools > Configuration Editor

apps > nautilus > desktop

Check the value field for 'trash_icon_visible'

You should see the trash icon on the desktop.

---

### Post by richstad on 2006-08-09
I don't see a Configuration Editor under under system tools - how do i get it?

---

### Post by dmitry_roslyakov on 2006-08-09
> **richstad said:**
> I don't see a Configuration Editor under under system tools - how do i get it?

[SIZE="4"]Show the Computer, Home, and Trash desktop icons in GNOME[/SIZE]
[LIST=1]
[*]Open the Configuration Editor, by running the program gconf-editor (see the section called “Start a Program Manually”). 
[*]Choose apps->nautilus->desktop.
[*]Tick the box beside computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.
[/LIST]

[https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html](https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html)

---

### Post by James_N on 2006-08-09
I just get a 404 error when trying to download the pack?

can anyone email it to me? [email]james@jnolan.co.uk[/email]

Cheers :)

---

### Post by imrumpf on 2006-08-09
try the rapidshare link, that should work. If it still doesnt i will e-mail you it, but be warned that it is about 9 MB.

---

### Post by James_N on 2006-08-09
all i get with rapidshare is that "you have exceeded your download allowance" but i never use rapidshare :(

---

### Post by Danny Boy on 2006-08-11
Imrumpf,

I just sent you a PM. I'd be happy to host the file, RapidShare is PITA. 

Dan

---

### Post by GavinX on 2006-08-11
This is great! A grand effort..... Congrats from Antigua

---

### Post by MakubeX on 2006-08-16
Anyone here who has the opening/login sound of Mac OS X?

---

### Post by Xelinis on 2006-08-16
How well does this theme work with XGL?

---

### Post by Danny Boy on 2006-08-20
The "[Tiger Mail]("https://addons.mozilla.org/thunderbird/1713/")" thunderbird theme may be worth including for those who use TB..

---

### Post by op_iyean on 2006-08-20
From the Pictures this looks like a very nice looking set up (i like how chrisp everything looks)
only problum for me is that i cant install any of it so far (i'm a beginner and dont really know what to do with the file. i've opened it up but i still do not understand what i do with all of the peices )
i only wish ubuntu would make it easyer for people who would like to install a file of this type (i sometimes wonder about linux in all...i dont know about every linux system, but a system that makes you have to type in word commands to download and install , is one that might keep people like me out who dont understand the system and would rather not be apart of academics at all.  i would not say no to pictures to click apon though, and would be very happy to find a system that made things useable for everyone, and free aswell)
anyway, thanks alot for your time and effort in making a ubuntu look like a mac, i have wanted to know what a mac looks like and liked what people created for it, and now people without macintoshes get a chance to have a mac in there computer as well. cheers!

---

### Post by Danny Boy on 2006-08-20
> **op_iyean said:**
> From the Pictures this looks like a very nice looking set up (i like how chrisp everything looks)
only problum for me is that i cant install any of it so far (i'm a beginner and dont really know what to do with the file. i've opened it up but i still do not understand what i do with all of the peices )
i only wish ubuntu would make it easyer for people who would like to install a file of this type (i sometimes wonder about linux in all...i dont know about every linux system, but a system that makes you have to type in word commands to download and install , is one that might keep people like me out who dont understand the system and would rather not be apart of academics at all.  i would not say no to pictures to click apon though, and would be very happy to find a system that made things useable for everyone, and free aswell)
anyway, thanks alot for your time and effort in making a ubuntu look like a mac, i have wanted to know what a mac looks like and liked what people created for it, and now people without macintoshes get a chance to have a mac in there computer as well. cheers!

Drop me an IM.. My instant messengers are in my profile, I'll walk you through everything. 

Screen shots:
[http://www.almostgeek.com/wp-content/uploads/2006/08/osxdesktop.png](http://www.almostgeek.com/wp-content/uploads/2006/08/osxdesktop.png)
[http://www.almostgeek.com/wp-content/uploads/2006/08/osxopen.png](http://www.almostgeek.com/wp-content/uploads/2006/08/osxopen.png)

---

### Post by op_iyean on 2006-08-20
> **Danny Boy said:**
> Drop me an IM.. My instant messengers are in my profile, I'll walk you through everything. 

Screen shots:
[http://www.almostgeek.com/wp-content/uploads/2006/08/osxdesktop.png](http://www.almostgeek.com/wp-content/uploads/2006/08/osxdesktop.png)
[http://www.almostgeek.com/wp-content/uploads/2006/08/osxopen.png](http://www.almostgeek.com/wp-content/uploads/2006/08/osxopen.png)

Thats really nice of you, thanks! i'm not really someone who knows how to use IM, but thats a really nice gesture.   i'm going to try my hand at installing this again , and get back to you all with how it went . thanks again!

---

### Post by MakubeX on 2006-08-20
Here's mine (without implementing the panels on the pack):

[http://nightfox.wordpress.com/2006/07/16/mac-os-x-theme-for-ubuntu-version-2/](http://nightfox.wordpress.com/2006/07/16/mac-os-x-theme-for-ubuntu-version-2/)

---

### Post by op_iyean on 2006-08-21
Hola,
i looked into all of thefolders, and most of them had install files that told me how to install most of the parts! this has made my computer look very sleek and bright, thank you very much!

---

### Post by andlinux21 on 2006-08-24
I can't wait to get home and try this on my laptop I tried another howto on my Breezy desktop to get nice bar at the bottom and loved it!!

---

### Post by fstab on 2006-08-25
This is really cool.  Thanks!

:)

---

### Post by neo_reloaded on 2006-08-25
Sorry, But I must say 3 things
[LIST=1]
[*]There is no good OS X theme for GNOME (Look at those scrollbars and tabs on screenshots - it is ..well, yucky, for me) When you are running a pale theme, with almost flat appearance on  edges, you need shadow around it to notice the active(focussed) window. ( The shadow is not available in basic GNOME).I think there used to exist one, but that is no longer available any where -mostly, due to art work copyright issues.

[*]What makes OS X different from other platforms are the applications(ichat, photobooth, iLife, iCal etc) and eye candy effect that it has. May be compiz xgl and cgwd will some day mature and give a good eyecandy UI - but I dont see that happening in near future (Even in edgy)

[*]Font rendering - unless you do the "cleartype" patch, font rendering is horrible in X11 + Gnome - and with out a doubt, it takes away a lot of aesthetics.
[/LIST]Now, if you are really an OS X fan, and want a clean Mac Look and feel, may I suggest Milk theme ? It is really perfect and easy on eyes.
[http://www.maxthemes.com/themes/?theme=Milk](http://www.maxthemes.com/themes/?theme=Milk) 
(There is  linux port at this link)
Use OSX Icons theme
[http://www.gnome-look.org/content/show.php?content=31618](http://www.gnome-look.org/content/show.php?content=31618)
The aqua blue wall paper matches the theme

If you are a Java programmer, look up the quaqua Look and feel for Java apps - that is one ultimate LnF theme that gives a OS X look ( but only for Java apps, ofcourse with a little bit of hacks)

---

### Post by mexicancupcak3 on 2006-08-28
r u supposta drag and drop this into the theme preferences file or how do u get this mac osx look im a n00b so dont be to mean thanks if possible step by step instructions for doin this please

---

### Post by Matrixy on 2006-08-29
Hi,
i have trouble installing the icons.
when i drop it into the icons in themes it says installation failed.
wht can i do??
i have amd 64bit ubuntu

---

### Post by dlpfmVfH on 2006-08-29
made a compiz theme, based on your theme package:

look here::KS

[http://ubuntuforums.org/gallery/showphoto.php?photo=3398&cat=2](http://ubuntuforums.org/gallery/showphoto.php?photo=3398&cat=2)

thanks, for your theme package, love the way my computer looks right now.:D

---

### Post by turkenator on 2006-11-14
any luck of u making a kde version? i tried baghira but that just renders most gtk applications useless and if i disable the gtk theming then all the gtk apps look very very ugly and incosistent

---

### Post by buu700 on 2007-02-18
The link doesn't work for me. By the way good job on the theme; it's the only good OS X theme I've seen for GNOME.

---

### Post by vikasrawal on 2007-08-17
You link at almostgeek.com is not working!! In fact it seems the whole site has been removed.

---

### Post by infra_red_dude on 2007-08-17
been working on it for quite sometime now. here's mac os leopard for free! :D

clean:
[[IMG]http://img401.imageshack.us/img401/2193/screenshotum1tg7.th.jpg[/IMG]](http://img401.imageshack.us/my.php?image=screenshotum1tg7.jpg)

dirty:
[[IMG]http://img524.imageshack.us/img524/7193/screenshot1uj9uz0.th.png[/IMG]](http://img524.imageshack.us/my.php?image=screenshot1uj9uz0.png)

wallpaper: leopard
composite manager: beryl
emerald theme: leopard self modded
gtk theme: leopard-gtk self modded
cursors: jaguar os x
icon set: OsX_Mod self modded
dock: avant window navigator-bzr
custom distro logo, custom top gnome panel background
clock: cairo clock
tray icons: lotsa hard work! :D
apps running: pidgin 2.1.0, exaile 0.2.11svn, nautilus, terminal

---

### Post by spupy on 2007-08-17
Nice things you got posted here guys! ;) The time I tried to skin my linux like osx got past and i lost interest in the matter. So i decided to share with you a mac theme for GNOME, i put it together from various other themes (for beryl, gnome, firefox :P). Its not finished, its not perfect, but i hope someone from you may find it interesting and continue the work. You can see some screenshots [here]("http://www.stud.uni-karlsruhe.de/~uibxn/Screenshots/screens2/"). 

I attached the theme to the post. In the tarball there ar 4 themes altogether - two themes for gtk - color and graphite, and 4 for metacity - 2 color and 2 graphite. The themes work really good with the mac style menubar hack posted on this forum. (There is an annoying bug in the themes that some buttons which have only icons and no text are not visible until mouseover. I told you its not finished).

Good luck in your quest anyway! ;P

---

### Post by infra_red_dude on 2007-08-18
hey those are really nice themes :) and the icon set you use are sweet :)

---

### Post by Quillz on 2007-08-18
It's a good start, although still not very close to Tiger. But nonetheless, it does look good.

---

### Post by spupy on 2007-08-18
The icon set for Gnome is called OSX, but the other icons are from the Ekisho pack - they are not strictly OSX but i like them very much. 
I know "my" themes weren't close, i never wanted them to be - i just wanted to get the non-techies to ask "Uuu, is that a mac?" It worked twice :O

---

### Post by Resilient on 2007-08-28
> **infra_red_dude said:**
> been working on it for quite sometime now. here's mac os leopard for free! :D

clean:
[[IMG]http://img401.imageshack.us/img401/2193/screenshotum1tg7.th.jpg[/IMG]](http://img401.imageshack.us/my.php?image=screenshotum1tg7.jpg)

dirty:
[[IMG]http://img524.imageshack.us/img524/7193/screenshot1uj9uz0.th.png[/IMG]](http://img524.imageshack.us/my.php?image=screenshot1uj9uz0.png)

wallpaper: leopard
composite manager: beryl
emerald theme: leopard self modded
gtk theme: leopard-gtk self modded
cursors: jaguar os x
icon set: OsX_Mod self modded
dock: avant window navigator-bzr
custom distro logo, custom top gnome panel background
clock: cairo clock
tray icons: lotsa hard work! :D
apps running: pidgin 2.1.0, exaile 0.2.11svn, nautilus, terminal

What are your settings for AWN? What I'm referring to are things like height, angle, icon offset, glass colors, etc. Many thanks in advance. :)

---

### Post by hibernatus on 2007-08-29
Hi,

when i try to download from the link you provided it's not working (almostgeek.com)

(see attached image)

Can you provided a new link please 

Thanks

---

### Post by nebriv on 2007-08-29
I get that also, please repost another link

---

### Post by shaamone on 2007-08-30
What a shame the download page is dead, does anyone have a copy they could mail to me? I'll stick it on my google webspace :)

---

### Post by illbashu on 2007-08-30
when ever i click the link i get this... and whenever i right click on it and save the file wont open and it says its a plane text doc... :( :-?

---

### Post by DrumScum on 2007-08-31
Mhh, I had my Gnome look like OSX much better, but I can't quite remember which themes I used. They were all on gnome-look.org though. On vital component was kiba-dock, which I got from the trevino repository.

---

### Post by darkhacker902 on 2007-09-02
[http://www.youtube.com/watch?v=HTY7H_YKJZU](http://www.youtube.com/watch?v=HTY7H_YKJZU)

MY Leopard theme.

---

### Post by infra_red_dude on 2007-09-04
Mac4Lin Project hosted on Sourceforge.net

My Mac4Lin project is on Sourceforge.net! Keep visiting the page and my blog (URL in my siggy) for updates. The project has been conceived on Ubuntu and GNOME. But it'll soon be tested on other distros and Unix-like OS which employ GTK+. Its in alpha version as of now. People who would like to test may please drop me a mail. Please leave your comments and suggestions regarding the project here, on my blog or on the project website. Feature requests and Bug tracking welcomed

head here: [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)

screenshots on the project page.

edit: update coming up..

changelog:

leopard folder icons - generic and specific
new ichat icon
new system prefs like config icon

firefox skin with safari like progress bar support in the skin + the addon (courtesy vishal)
safari like buttons
safari like tabs
safari like search bar and menus

screenshots for the updated pack:

[http://img368.imageshack.us/my.php?image=2screenshotbc9.jpg](http://img368.imageshack.us/my.php?image=2screenshotbc9.jpg)

[http://img517.imageshack.us/my.php?image=3screenshotpb2.jpg](http://img517.imageshack.us/my.php?image=3screenshotpb2.jpg)

---

### Post by dustman on 2007-09-04
> **illbashu said:**
> when ever i click the link i get this... and whenever i right click on it and save the file wont open and it says its a plane text doc... :( :-?

yeah, i'm getting the same thing here....any solutions?

P.S. infra_red_dude, i downloaded mac4lin, but i'm kinda new to this stuff, so could you tell me what to do with that archive? :D

---

### Post by hackxxcrack on 2007-09-04
it looks nice but how do i install it?

---

### Post by infra_red_dude on 2007-09-05
jus untar the packages onto a temporary folder.

to install gtk theme goto, system> prefs>theme>install theme. select the gtk theme .tar.gz file. then select it to apply.

to install cursors goto system>prefs>theme>customize>icons and install. select the jaguar cursor theme .tar.gz file. then to apply it goto system>prefs>mouse>points and select the jaguarx

to install the icons goto system>prefs>thems>customise>icons and install. select the icon pack .tar.gz file and after install select it to use it.

to install emerald theme (for beryl/compiz) goto system>prefs>emerald theme manager> click on import... select the emeral theme .tar.gz file then select it to apply.

the avant window manager dock installation instructions are given in the package. read and sintall. its very easy.

you need to install the 'gtweakui' package from the repos to easily change the splash screens. 

to install gdm theme, goto system>admin>login window>local. click add... and select the gdm .tar.gz theme and select it form the list to enable that.

i guess other things are commonly installed stuff (like xmms/bmp/firefox skins etc.)

---

### Post by hackxxcrack on 2007-09-05
i think the link is down! is not working for me...

---

### Post by gohanssjn on 2007-09-06
Whwnever I try to use this, Emerald says the Emerald file is not valid (not in .Emerald format).  Simply changing the name does not help either.  Any ideas?

---

### Post by infra_red_dude on 2007-09-06
@hackxxcrack

link is not down. there haf been a lot of downloads. hence u mebbe facing that problem. try now.

@gohanssjn
i'll look into the matter right away :)

---

### Post by dotweb on 2007-09-06
I get to an other page than a download page - if thats right where on the "geek" page can I download the file?

Cant wait to get some osx look to my desktop

---

### Post by infra_red_dude on 2007-09-06
this is the direct download page link: [https://sourceforge.net/project/platformdownload.php?group_id=204373](https://sourceforge.net/project/platformdownload.php?group_id=204373)

clicking on individual files will start the download. i just tested it and its fine.

regarding installtion of emerald theme. i'm sorry its not in .emerald format. but it can be installed easliy. simply untar the contents to ~/.emerald/themes. so the folder structure should now be ~/.emerald/themes/leopard/<all the theme files: .pngs, .ini etc.>. then the theme will show up in emerald theme manager.

thanks for pointing it out :) plz give ur valueable feedback. i'm soon gonna post an update for the icon theme and a new more safari like firefox theme and extension. working on them now.

---

### Post by vassalle on 2007-09-06
Regarding the emerald theme, can you release a version where the min, max, close buttons are on the right?

THanks.

---

### Post by gohanssjn on 2007-09-06
Thanks a lot, I love how this all looks :)

---

### Post by infra_red_dude on 2007-09-06
@vassalle
if the one from my pack is working for you then you don't need a new theme. simply goto system>prefs>emerald theme manage. now select the leopard theme (that is downloaded and installed from my pack) and got 'edit themes' tab. now select the 'title bar' sub tab. here on the right side u can see 'title bar object layout'. click on the down arrow to make the drop down menu visible. from the options click on 'it:hnxc normal layout' and you'll haf everything onto the right :) simple :)

@gohanssjn
is everything working fine? plz give ur valueable feedback :)

---

### Post by gohanssjn on 2007-09-06
Ok, emerald installed!

---

### Post by gohanssjn on 2007-09-06
One thing, I don't see any icon packs...is there one in here?

---

### Post by infra_red_dude on 2007-09-07
yes, the tarball Leopard_Pack_2.tar.gz is the icon pack. its mentioned on the download page. i'll be updating this pack soon wid new leopard folder icons.

---

### Post by cyneuron on 2007-09-13
how to use font.conf.

i think it is to be save in /home/user folder.

and how to change grub slash. i have changd gtk splash by gtweak.

---

### Post by depi on 2007-09-13
I've got an error when I'm unpacking files - there are missing some files in the archives.

---

### Post by infra_red_dude on 2007-09-13
some users haf reported that the included font config hasnt worked for them. anyways u may try it. just make a backup of /etc/fonts.conf and copy the fontconfig included in the pack to that location. restart X.

@depi
which files? lemme know. i jus checked and its fine.

---

### Post by Belinrahs on 2007-09-13
To OP:

I have a Mac running OS X 10.3.9.

I can help you in any way you want, just send me a PM :D

---

### Post by sophtpaw on 2007-09-15
the download link takes me to [www.almostgeek.com](www.almostgeek.com) ???

how is one supposed to follow this how-to?

--
sophtpaw

---

### Post by infra_red_dude on 2007-09-17
mac4lin version 0.2 has been releaed!!! download the newest and the greatest version! i've submitted a thread in the tutorials section. it is subject to moderation. once that is approved, we can continue the discussion there. meanwhile head to the SF.net project site and download the latest ver0.2!

---

### Post by infra_red_dude on 2007-09-17
Mac4Lin version 0.2 Released!

17th September 2007

I am happy to announce the version 0.2 release of the Mac4Lin Project. Version 0.1 alpha has received an overwhelming response. People have used and liked it and the downloads (as on this day) have touched about 6GB!!! Lots of comments/suggestions/bugs were received and I have tried to iron out all the bugs known till this day. This update also brings a whole lot of new things. See the changelog for changes.

Special thanks to Victor of vsdigital for provding the Firefox Safari Skin and thanks to everyone who tested the version 0.1 alpha. Because of all this I'm giving version 0.2 stable to this release. Keep visiting the project website for more updates.

Apply it, flaunt it, enjoy it!

Anirudh (a.k.a ANi, infra_red_dude)

For any suggestions/comments/complaints/feedback/bug tracking please drop by my blog or send a mail:

My Blog: [http://phoenix-ani.blogspot.com/](http://phoenix-ani.blogspot.com/)
My E-Mail id: infra_red_dude<AT>users<DOT>sourceforge<DOT>net
Project Website: [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin)
Screenshots: [http://sourceforge.net/project/screenshots...group_id=204373](http://sourceforge.net/project/screenshots...group_id=204373)

Folks, got my GRE on 8th October. I gotta prep for it and also go thru all the universities' websites. Will be a bit busy. So, I may not be regular at the forums for the next one month. You may post your feedback either on my blog/project website/this thread or mail it to me. I'll look into it as soon as possible.

changelog:
Mac4Lin version 0.2, 17/09/2007

Icon updates
New firefox skin by Victor of vsdigital
Mac OS System Sounds
New Grub Screens
More Leopardish Emerald theme
Simdock source tarball included
Leopard Dock AWN theme updated
OS X Fonts and font enhancing guide
More Leopardish GTK Metacity theme
One GTK Splash screen added
Updated Pidgin OSX Theme
Four new wallpapers added
Documentation (README) added for every component
GTK Mac Menu is not included in this pack as some users have reported some issues. If anybody wants to install this, it can be Downloaded from the ver.0.1alpha pack. The GTK Mac Menu package remains unchanged.

---

### Post by infra_red_dude on 2007-09-20
folks, yester the SF.net servers hosting the Mac4Lin project were excessively bombarded wid download requests! 19th Sept. 2007 witnessed the highest ever number of downloads on a single day - 386 and the total data served on a single day was 4GB!!!!! it has broken all records!

i've been observing an average of almost 1GB download per day. happy to see ppl making use of this project combined downloads haf been about 1600 and a total of 13.2GB of data has been served till date. makes me really happy :)

---

### Post by cyneuron on 2007-09-20
buddy you have done awesome job.......

themes & icons are really great.....

font configuration you gave is the perfect i have seen as yet ever....


can you make minimise, maximise & close button on left side as in real Mac ? that wil be  real great....

---

### Post by infra_red_dude on 2007-09-20
plz continue all mac4lin discussions here: [http://ubuntuforums.org/showthread.php?t=555373](http://ubuntuforums.org/showthread.php?t=555373)

if you apply the emerald theme the min,max,close button automatically go to the left side. if you do not use emerald or any composite manager but only metacity then here is the procedure to bring these buttons to the left:

type alt+f2 to bring up the run dialog box. type 'gconf-editor' press enter. in the gconf-editor window goto 'apps > metacity > general' here make a note of original 'button layout' key on the right hand side (in case u need the original thing back again)

now right click on the 'button layout key' and select 'edit key' option. in place of the orignal (after noting it down) type 'close,minimize,maximize:menu'.

you'll get mac like left hand side buttons :)

---

### Post by April Rustianto on 2007-12-09
unable to get the packet!!!!!!!!!!

---

### Post by kyren on 2007-12-11
I downloaded it, but i cant find the installation instructions
a little help here?

---

### Post by Flare183 on 2007-12-12
The link is broken

---

### Post by D_invictus on 2007-12-22
I absolutely love it. Where can I find a good cairo clock theme?
I also need someone to babystep me through updating my ATI driver which hates linux. =/

---

### Post by in-sanity on 2008-02-21
The link doesn't work for me either. Could you upload it to rapidshare.com or someplace else, pls? Thanks.

---

### Post by sirlancelot on 2008-02-22
Link is broken, leads to stupid Verizon landing page.

Please don't upload to **C**rapidshare, I will mirror it if you email it to me.

---

