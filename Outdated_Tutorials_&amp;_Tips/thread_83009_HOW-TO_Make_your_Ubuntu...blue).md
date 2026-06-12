---
title: "HOW-TO: Make your Ubuntu...blue:)"
date: 2005-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by RubenGonc on 2005-10-27
Ok, this is just a short "how to" that explains what needs to be changed to make Ubuntu...blue:P

You may be wondering why I am writting this...well...because there are much people that don't likes the native brown look and feel...
Of course you may use whatever wallpapers, themes, etc you want...here I will just make sugestions...

My english may not be very good so sorry bout that:P

1-OK..so we will start..from the beginning..the boot splash: usplash.

How can we make it look blue?

There is an how to covering that already so you can take a look here:

[http://www.ubuntuforums.org/showthread.php?t=82835](http://www.ubuntuforums.org/showthread.php?t=82835)

2-And now...GDM

To make GDM look blue...you have to install a blue theme of course:P You can choice any theme you want...but I sugest:

BlueBuntu -  [http://www.gnome-look.org/content/show.php?content=28852](http://www.gnome-look.org/content/show.php?content=28852)

Human Blue - [http://www.gnome-look.org/content/show.php?content=29032](http://www.gnome-look.org/content/show.php?content=29032)

ubuntu / ximian gdm - [http://www.gnome-look.org/content/show.php?content=24143](http://www.gnome-look.org/content/show.php?content=24143)

Ubuntu-Smooth  - [http://www.gnome-look.org/content/show.php?content=22029](http://www.gnome-look.org/content/show.php?content=22029)

Ubuntu-Etiquette GDM - [http://www.gnome-look.org/content/show.php?content=18928](http://www.gnome-look.org/content/show.php?content=18928)

Ubluentu - Theme made by me (Based in ximian gdm). You can find it at the end of this post.

You may download more themes at gnome-look.org.

To install a GDM theme:

At a terminal, type:

> sudo gdmsetup

Choose the "Graphical greeter" tab and click 'Install New Theme'. Navigate to the location of the tarball.

Select the newly installed theme and close.

TIP: You may change GDM themes background unpacking the theme and then placing some image that you want in place of the default. Then pack the theme again (tar.gz it) and install it.

3-Next thing...change the backgroud color that appears while splash screen is shown:

At a terminal, type:

> sudo gdmsetup

Choose the "Standard greeter" tab and at the bottom choose the color that you want to use. I sugest you to use one that goes well with your wallpaper.

Close the GDM setup.

Now....right-click on your desktop and choose "Change wallpaper". At the color selector choose the same color you have choosed in the GDM setup (you may copy the values).

4-Now let's change the splash screen

Install gnome-splashscreen-manager:

At a terminal type:

> sudo apt-get install gnome-splashscreen-manager

Than download one theme.I sugest:

Ubuntu-Smooth-Splash (to go with Ubuntu-Smooth GDM theme) - [http://www.gnome-look.org/content/show.php?content=22030](http://www.gnome-look.org/content/show.php?content=22030)

HumanBlue (to go with Human Blue GDM theme) - [http://www.gnome-look.org/content/show.php?content=29030](http://www.gnome-look.org/content/show.php?content=29030)

bluebuntu splash (to go with Bluebuntu GDM theme) - [http://www.gnome-look.org/content/show.php?content=28887](http://www.gnome-look.org/content/show.php?content=28887)

Ubuntu Joy - [http://www.gnome-look.org/content/show.php?content=30020](http://www.gnome-look.org/content/show.php?content=30020)

Many others in gnome-look.org.

To install go to Computer->Prefs->Splash Screen

Click "Install" button Navigate to the location of the picture you want to use. Then "Activate" it.

5-Window Border (Metacity) theme:

Clearlooks default theme - "apt-get install gtk2-engines-clearlooks" and you may now install themes that use clearlooks engine

SystemG - [http://art.gnome.org/themes/metacity/778](http://art.gnome.org/themes/metacity/778)

Chiro - [http://art.gnome.org/themes/metacity/1026](http://art.gnome.org/themes/metacity/1026)

Clearbox - [http://www.gnome-look.org/content/show.php?content=25060](http://www.gnome-look.org/content/show.php?content=25060)

Red Hat Bluecurve:
[B]
khad post at ubuntuforums:[/B]

> The easiest way to get Bluecurve in my opinion is directly from the Fedora project Web site. You also get the latest version of it.

Download the "redhat-artwork" RPM from:

[http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/)

As of this writing, the current RPM is 0.120-1.2:

[http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.120-1.2.i386.rpm](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.120-1.2.i386.rpm)

In the directory you downloaded the RPM, run this command:

sudo alien -i redhat-artwork*

That's all there is to it. Run one command and a single file you download, and it is the latest version directly from the Fedora project.

Go to Computer->Desktop Preferences->Theme
To install a theme drop an down it to the window.
Choose any theme you want to use.

6-Wallpapers:

Basse-Ubuntu - [http://art.ubuntu.com/backgrounds/ubuntu/49](http://art.ubuntu.com/backgrounds/ubuntu/49)

Simple Ubuntu - [http://www.gnome-look.org/content/show.php?content=29323](http://www.gnome-look.org/content/show.php?content=29323)

CleanUbuntu - [http://www.gnome-look.org/content/show.php?content=28449](http://www.gnome-look.org/content/show.php?content=28449)

7-If you want a Grub splash screen:

[http://www.gnome-look.org/content/show.php?content=29962](http://www.gnome-look.org/content/show.php?content=29962)



Ok...that's it. Hope you enjoy it.

---

### Post by majikstreet on 2005-10-27
UBluetu rocks!

Thanks :)

---

### Post by Rinnan on 2005-10-27
I'm looking for the opposite -- how to make Kubuntu brown.

I've seen Human-Creamy or whatever it's called, but it looks awful, much worse than the normal Human theme in Ubuntu.  So seriously, is there some kind of plugin for KDE or QT that lets it use GTK+ themes?

---

### Post by RubenGonc on 2005-10-27
[QUOTE=Rinnan]I'm looking for the opposite -- how to make Kubuntu brown.

I've seen Human-Creamy or whatever it's called, but it looks awful, much worse than the normal Human theme in Ubuntu.  So seriously, is there some kind of plugin for KDE or QT that lets it use GTK+ themes?[/QUOTE]

Look at this:

[http://kde-look.org/content/show.php?content=25389](http://kde-look.org/content/show.php?content=25389)

Hope it helps ;)

---

### Post by RubenGonc on 2005-10-27
You can also try this one:

[http://kde-look.org/content/show.php?content=21720](http://kde-look.org/content/show.php?content=21720)

---

### Post by ewz on 2005-10-27
hey cool, clearlooks =Quicksilver Theme for me 
and Crystal for Gnome for my icons but the one thing I was missing A good looking GDM Theme Thanks Bro :cool:

---

### Post by gmc on 2005-10-28
This is a great HOWTO. I really like the blue themes much better than the standard brown. Although applying these changes are not quite as polished as the standard brown. I'm hoping that some of the Ubuntu artists and developers will get together and create a single application that can make all these changes and add a little spit'n'polish to a blue theme. The standard brown theme in Breezy really is spiffy, when you compare it to Hoary.

Great Job!

G.

---

### Post by ubuntu_demon on 2005-10-28
I moved this thread to the Gnome howto section.

---

### Post by jackmacokc on 2005-10-28
Man! awesome thread. Looks so much better!!! Thanks for all your work on those themes.

---

### Post by landotter on 2005-10-28
[quote=Rinnan]
I've seen Human-Creamy or whatever it's called[/quote]

Is Human-Creamy like Human-Crunchy?

:p

LOL

---

### Post by derrick1985 on 2005-10-28
This is a GREAT howto.

I love this. I get the look of KDE (which I like) in my Favourite Desktop Environment (Gnome)

Thanks!

---

### Post by dude2425 on 2005-10-28
Nice guide. This one and the usplash recolor inspired me to write one on my own. I've written a little readme and included a bunch of stuff with it in an archive. It's a nice olive color, although, what I did was recolor most of the default stuff and used it to replace the original stuff. Now everything is a neet-o olive green. Add that to the olive green usplash theme that SilentCacophony was kind enough to make upon request, and you've got yourself an greenbuntu or some other cornier play on the whole *buntu thing like majikstreet did for his ubluentu.

Mine will include a modified beep-media-player skin, and a modified distributer-logo.png. I enjoy green, and I hope others do too. I'm thinking of adding more color's to it, and then letting the user choose which color scheme he/she wants with a simple script that takes care of all the installation and permisions and stuff on its own. I'm uploading it now to rapidshare.de, so it might be quite a few minutes before I edit this post with what I've got so far. I still hadn't gotten to the credits, or version numbers, or anything real readme'ish like that, but it should be coming, if ofcourse, I can maintain it and not just forget all about it like everything else I do.

EDIT: Jeez, finaly. My upload to rapidshare.de is finaly finished, and now you can download green. I love green. And books. They smell good.  Good is good. It's like a book. They smell good. I've been waiting too long.

[http://rapidshare.de/files/6899329/Olive.tar.gz.html](http://rapidshare.de/files/6899329/Olive.tar.gz.html)

---

### Post by zencoder on 2005-10-29
Thanks! I've followed this and changed a lot, but I still can't get the Gnome spash screen to change.  I've changed the brown background color, but I can't get the splash image to change.  Any thoughts on where I should place the file?  I've got it in  /usr/share/gdm with world read permission.

---

### Post by RubenGonc on 2005-10-29
[QUOTE=zencoder]Thanks! I've followed this and changed a lot, but I still can't get the Gnome spash screen to change.  I've changed the brown background color, but I can't get the splash image to change.  Any thoughts on where I should place the file?  I've got it in  /usr/share/gdm with world read permission.[/QUOTE]

> 4-Now let's change the splash screen

Install gnome-splashscreen-manager:

At a terminal type:

Quote:
sudo apt-get install gnome-splashscreen-manager

Than download one theme.I sugest:

Ubuntu-Smooth-Splash (to go with Ubuntu-Smooth GDM theme) - [http://www.gnome-look.org/content/sh...?content=22030](http://www.gnome-look.org/content/sh...?content=22030)

HumanBlue (to go with Human Blue GDM theme) - [http://www.gnome-look.org/content/sh...?content=29030](http://www.gnome-look.org/content/sh...?content=29030)

bluebuntu splash (to go with Bluebuntu GDM theme) - [http://www.gnome-look.org/content/sh...?content=28887](http://www.gnome-look.org/content/sh...?content=28887)

Ubuntu Joy - [http://www.gnome-look.org/content/sh...?content=30020](http://www.gnome-look.org/content/sh...?content=30020)

Many others in gnome-look.org.

To install go to Computer->Prefs->Splash Screen

Click "Install" button Navigate to the location of the picture you want to use. Then "Activate" it.


I am working in a new GDM theme..I will upload this soon.

Thank you for like this How To. :)

---

### Post by RubenGonc on 2005-10-29
Here is my new theme (Ubuntu-Alphacube) based on Alphacube by CiccioBueo :)


Make sugestions and give me your opinions!

---

### Post by canadianwriterman on 2005-10-29
This was a great HOWTO and everything worked. The only problem is with the login window. The entry area for the username and password is only a tiny slit. I can type in it, but I can't see what I'm typing. Is there any way to expand the entry area? Thanks.

---

### Post by RubenGonc on 2005-10-29
[QUOTE=canadianwriterman]This was a great HOWTO and everything worked. The only problem is with the login window. The entry area for the username and password is only a tiny slit. I can type in it, but I can't see what I'm typing. Is there any way to expand the entry area? Thanks.[/QUOTE]


What theme are you using?

---

### Post by canadianwriterman on 2005-10-29
[QUOTE=RubenGonc]What theme are you using?[/QUOTE]

It's the Ubuntu Smooth greeter.

---

### Post by RubenGonc on 2005-10-30
[QUOTE=canadianwriterman]It's the Ubuntu Smooth greeter.[/QUOTE]

Report the bug in the gnome-look.org Ubuntu Smooth webpage.

---

### Post by JurB on 2005-11-02
Thanks great HowTo!
 Man, i love Linux :)

---

### Post by christooss on 2005-11-06
Any ideas how to make ubuntu olive greeen

Compatible with this usplash

---

### Post by dude2425 on 2005-11-06
[quote=christooss]Any ideas how to make ubuntu olive greeen

Compatible with this usplash[/quote]

Psst...
*points

[quote=dude2425][http://rapidshare.de/files/6899329/Olive.tar.gz.html]("http://rapidshare.de/files/6899329/Olive.tar.gz.html")[/quote]

That's what I've got on my box right now. Feel free to change anything you like in it, and all credits go to the owners of all the files I included with the archive. It's just a compilation of great pieces that make one larger greatness.

---

### Post by christooss on 2005-11-06
Hm silly question. How can I now install theme? And icons?

---

### Post by christooss on 2005-11-06
Forget my question. These theme is freakin great. THANK YOU

---

### Post by christooss on 2005-11-06
WIth your permission I will make a new how-to with some scripts included.

---

### Post by Zed on 2005-11-09
You can also make the Ubuntu icon in the gnome panel blue (as seen [here](http://ubuntuforums.org/showpost.php?p=25625&postcount=6).)

```

wget http://ubuntu.spymac.net/blugnome-logo-icon-tran.png
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.bak
sudo cp blugnome-logo-icon-tran.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

```

If you'd like the original back:

```

sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.bak /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
killall gnome-panel

```

(Thanks to [http://ubuntuforums.org/showthread.php?t=75034](http://ubuntuforums.org/showthread.php?t=75034) for reminding me how to do that.)

---

### Post by dude2425 on 2005-11-09
[quote=christooss]WIth your permission I will make a new how-to with some scripts included.[/quote]

Go right ahead, you're more than welcome to do what you wish for it, as long as no green slips of paper or shiny little flattened spheres of metal are involved in any way. The stuff in there isn't mine though, so try your best to give credit where true credit is due (or just say "credit goes to the respective owners of all the files in this how-to" or something. I am pretty sure that works. If not, waggle a chicken over your head and chant three times "Credit to the owners." I know for a fact that that will work flawlessly.)

---

### Post by phux on 2005-11-30
hmm i kind of messed up my boot screen...
doesnt display anything anymore... just a white cursor, not even blinking (frozen screen) till login-screen

any idea?
system: ubuntu 5.10 with gnome.
did everything as shown in "HOWTO: Change the default usplash colors"

---

### Post by Danielle on 2005-11-30
hi, i can't see the places you mention to go to after the **sudo gdmsetup** commands are they in the screenshot? sorry for being abit slow :(

---

### Post by exodus on 2006-03-26
bloody cool post m8!!! i love ubuntu..

---

### Post by yang_hui1986527 on 2006-04-01
i like it very much..

---

### Post by erik_boi on 2006-04-08
[QUOTE=phux]hmm i kind of messed up my boot screen...
doesnt display anything anymore... just a white cursor, not even blinking (frozen screen) till login-screen

any idea?
system: ubuntu 5.10 with gnome.
did everything as shown in "HOWTO: Change the default usplash colors"[/QUOTE]

I had the same problem after copying and pasting the commands. I thought I had done everything right. Anyhoo, to fix it I simply put the commands in again, rebooted, and it showed right up. 

I also managed to screw up grub when installing the grub splash. It tried to load failed, and rebooted over and over. I wasn't paying attention when I told it to load the image from the first partion which on my computer is widows. I managed to fix this with the live cd. 

I finally have everything working and it is great, thanks.

---

### Post by brentroos on 2006-08-08
,

---

### Post by loserboy on 2006-08-08
> I've seen Human-Creamy

lmao

---

### Post by brentroos on 2006-09-24
.

---

### Post by Ingla on 2007-01-19
Hi.

Any new blue images for the Dapper "3D look" boot screen and log-in?

---

