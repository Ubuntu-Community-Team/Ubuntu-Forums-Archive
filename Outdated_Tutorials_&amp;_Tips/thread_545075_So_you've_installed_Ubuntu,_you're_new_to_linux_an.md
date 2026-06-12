---
title: "So you've installed Ubuntu, you're new to linux and you HATE BROWN... READ ME FIRST!"
date: 2007-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by LT1Caprice57L on 2007-09-07
Don't go crazy.  Take a deep breath, sit back, relax & grab a coffee.  While the developers have a perfectly logical explanation for the default brown theme (and if you read it, it makes perfect sense!), it seems there are a great plenty of people who, plain and simple, HATE brown.  I'm not a fan of it myself, so here's a one-stop-shop on how to get rid of it entirely:

Ubuntu offers several default themes, available under System > Preferences > Theme.  You'll be presented with a list of default themes.  Pick the one you like.

Same with the login screen theme.  Go to System > Administration > Login Window.  Enter your password, then go to the Local tab.  You can change the initial background color here, too.

Don't see anything that strikes you in these lists? Notice how there aren't many pre-installed wallpaper options?  No biggie, the internet offers practically unlimited options.

For various themes, [http://www.GNOME-look.org](http://www.GNOME-look.org) is pretty much a one-stop shop.  Literally hundreds of thousands of different themes, splash screens and wallpapers are available here.

For wallpapers, [http://www.interfacelift.com](http://www.interfacelift.com) is hard to beat.  Around 150 pages worth of wallpapers, available in practically every screen resolution known to man.

"OK, so I looked on GNOME-look.org, WHAT THE HECK DO THE DIFFERENT TYPES OF THEMES MEAN!?"

GTK themes are the controls: buttons, checkboxes, scroolbars, etc.  Metacity themes are the window borders, pretty much.  GDM themes affect the login screen.  If  you've never used Linux, much less Ubuntu before, you probably won't be ready to mess with Compiz and Beryl just yet (and besides, these programs are still in the beta stages, so it would ideally be best to leave these alone until a stable version of each is released), so just ignore those ones for now.  Icon themes are self-explanatory: they're the icons.

Now that you know, get searching and downloading! Save everything to your home folder or desktop for easy locating in a few minutes when we go to install them.  All themes will come packaged in **.tar.gz** files. These are the Linux equivalent of Windows **.zip** files.  Wallpapers will be **.jpg** files, and splash screens will be **.png** files.

Ubuntu makes it easy to install themes of all types: you just have to know where to go to install them.  You don't even have to extract a thing from the .tar.gz files, Ubuntu does it all for you.

For GDM themes: System > Administration > Login Window.  Enter your password if prompted. Go to the 'local' tab.  You'll see a list of themes here.  To the right of this list is a button that says 'install'.  Click it, and locate where you put the theme you just downloaded.  Remember that it's a .tar.gz file.  When you click it and click 'open' the theme will be automatically installed.  Yes, folks, it really was that easy, you didn't imagine anything.

The proccess is identical for GTK, Metacity and Icon themes.  You'll install both of these under System > Preferences > Theme.  Click the Customize button on the right.  For GTK themes, you want the Controls tab, for Metacity themes, you want the Window Border tab and for Icon themes you want the Icons tab. The Install buttons on these pages work exactly the same way as they do when customizing the login screen.

Changing your wallpaper is pretty straightforward, but if you're new to computers entirely or need a refresher:  Right click on a blank space in the desktop, and select "Change desktop background" Below the list of available wallpapers, there will be an "Add wallpaper" button.  Click it, select the wallpapers you want, and click Open.  You can select a group of image files in a row by clicking the first one you want, holding down the SHIFT key, and clicking the last one you want.  Kabam!  Everything in between is automatically selected.  Saves a lot of effort, doesn't it?  As an alternative method, if you don't want to save wallpapers to your HD, you can set them straight from Firefox: Right click the image you'd like to use for your wallpaper and click "Set as desktop wallpaper".

Now, if you're using Feisty or earlier, you've reached the last annoying hurdle: that damn brown splash screen. Note that if you have Gutsy or Hardy, splash screens are no longer enabled by default, so this is not an issue.

Without gnome-splashscreen-manager, you won't easily be able to rid yourself completely of brown, so we'll install that now.

Go to System > Administration > Synaptic Package manager.  Enter your password if prompted.

Once it's finished loading everything, click on the Search button in the toolbar, and enter: ```
gnome-splashscreen-manager
```

When it comes up in the list box, click on the checkbox next to it.  A menu will appear, select "Mark for installation" (NOTE: If the checkbox appears dark/green, you already have this tool installed.  Skip this and the next step and see below.)

Click the Apply button in the toolbar, and OK any boxes that come up after that.  A series of files will download and install automatically.  After that, you're done!

Alternatively, if you wish to use the command line, you can fire up a terminal and enter the following: ```
sudo apt-get install gnome-splashscreen-manager
``` and enter your password when prompted.  This approach is actually *simpler*, so don't be afraid to try it.

You can now go to System > Preferences > Splash Screen and add/change your splash screen just like you would your desktop wallpaper, with the only difference being you need to click the "Activate" button. for the one you want to use.  Highlighting a splash screen will not automatically apply it here like it does in the desktop wallpaper box.

If everything has gone well, you will be brown-free by this point. :guitar:

Any questions? Suggestions? PM me, I'll do the best I can to help.

Oh, and last not least, wanna see the current iteration of my Ubuntu desktop?  Here ya go:

Click for full-size:
[[IMG]http://i141.photobucket.com/albums/r60/mr740ti/th_Screenshot-10-1.png[/IMG]]("http://i141.photobucket.com/albums/r60/mr740ti/Screenshot-10-1.png")

I actually got this theme from [http://ubuntustudio.org](http://ubuntustudio.org) - it's their Feisty theme, available under "fun stuff" on the downloads page.  I can't exactly remember where I got the wallpaper, but I have it and others that are identical in different colors in a tar archive.  Just send me a PM with your E-mail address and I'd be happy to send it to you.

Enjoy your Ubuntu, guys!

---

### Post by AlexenderReez on 2007-09-07
..if you hate brown to much how about use other distro...?hahha...just a joke...btwn...i think most of users know about gnome-look.org...

---

### Post by LT1Caprice57L on 2007-09-07
> **AlexenderReez said:**
> ..if you hate brown to much how about use other distro...?hahha...just a joke...btwn...i think most of users know about gnome-look.org...

LOL.  I did try LinuxMint and Freespire, neither one worked terribly well on my laptop.  I like Ubuntu anyway.

Most do know about G-L.org, but I intended this post for absolute newcomers who know little to nothing about Linux/Gnome/Ubuntu.  After all, this is the Absolute Beginner Talk forum ;)

---

### Post by loell on 2007-09-07
suggestion? i think this is qualified for a blog post, not just forum post. not that forums are less attractive or anything, but i think its more fitting, thats just me though.

---

### Post by wladston on 2007-10-26
Imho, I think Ubuntu should provide at least a basic set of non-brown backgrounds, and a set of WELL MADE non-brown themes.

And I think the user should be given a chance to try and choose one of these themes at install time.

[http://ubuntuforums.org/showthread.php?t=591257](http://ubuntuforums.org/showthread.php?t=591257)

---

### Post by TidusBlade on 2007-10-26
Nice guide, althought I kind of hate the Mac OS X theme, Ill try out the other things :) I dont mind Brown, but it's gets annoying if you use it for like 2 months :p

---

### Post by the badger on 2008-01-25
hey! this was actually lovely and helpful! not that i didn't already figure out how to manage the splash screen and themes (minus glitches b/w themes + OO), but damn if the title of this post didn't make me smile!
:)

---

### Post by Black Tooth Grin on 2008-01-25
I fixed all my own problems but i'm sure this will still help people.

---

### Post by oldb0y on 2008-01-25
Why don't you put this in Tutorials&Tips?

---

### Post by jpeddicord on 2008-01-25
>  		Why don't you put this in Tutorials&Tips? Done. :)

---

### Post by studiesinsound on 2008-01-25
ah wonderful.
been trying to figure out how to get rid of that brown splash screen.
nice one.

listening to "a pound for a brown on the bus" by zappa while nixing my brown splashscreen.

:)

---

### Post by LT1Caprice57L on 2008-05-23
Bump, made a couple version-specific updates!

---

### Post by Abu_Dayya on 2008-05-24
Very helpful. 
Good work

Now I have a question:
I Use Gutsy and I don't see a splash screen after logging with GDM, but I see a brown colored page for about ten sconds untill gnome loads. Will enabling splash screen and using one from gmone-look change that brown page?
Thanks in advance





And btw, the theme looks orange to me not brown.. lol

---

### Post by psyke83 on 2008-05-28
Thanks for the guide. Just a little note, the UbuntuStudio theme is a part of the official repositories (since Gutsy, or perhaps before), so it's better to install the actual package:

```
sudo apt-get install ubuntustudio-theme
```

Alternatively, to grab the UbuntuStudio theme, wallpapers, icons, gdm theme and sounds:
```
sudo apt-get install ubuntustudio-look
```

Also, a warning. Installing themes using System/Preferences/Appearances -> Install can cause trouble with applications that require administrator access (e.g. Synaptic, any application that prompts for your password). You will notice an ugly Windows95-esque theme for such applications, because the theme gets installed in /home/yourusername/.themes/, but applications that need administrator access cannot access that folder, so it does not apply a theme to the application at all.

The solution to this problem is to move all the themes you have custom-installed to /usr/share/themes, as this can be read by all users on the system:

```
sudo mv ~/.themes/* /usr/share/themes
```

---

### Post by NTolerance on 2008-05-29
I'd like to add that you can simply drag and drop Metacity/GTK/icon themes directly to the Appearance window to install them provided that the theme creator packaged them in the usual way.  Most themes are like this with some exceptions.

---

