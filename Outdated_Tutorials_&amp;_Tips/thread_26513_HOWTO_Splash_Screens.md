---
title: "HOWTO: Splash Screens"
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by battletux on 2005-04-13
Being reletivly green when it comes to Linux i have spent ages trying to work out how to change the splash screen that is shown after you login to your system, but i have finally figured it out, and so to help everyone else wanting to do this here is how to do it:


First up you will need to find yourself a shiney new splash screen. Try [Gnome-art](http://art.gnome.org/themes/splash_screens/) for some new screens.

Once you have the screen of your choice it is time to place it somewhere on your system that it is not going to end up being moved/edited/renamed or anything else that could screw up the image being shown.
The file can be placed anywhere, personally i placed mine here:

```
/home/-my username-/.Splash
```

So that it was in it's own location and hidden so it reduces the chances of me accidentally messing with it. Wherever you place it make sure you remember the path and file name as we will need this for the next step.

Now the file is sorted we need to run the Gnome Config. tool, just go:

Applications --> System Tools --> Configuration Editor

Now in the config editor select:

```
/apps/gnome-session/options
```

By using the folder tree on the left of the window.

Now you will see a few options on the right one of which should be **splash_image**. Highlight this entry and right click and select **Edit Key**.
In the new pop-up under **Value** replace the existing text with the full path to your file. For me this is:

```
/home/-my username-/.Splash/Urban-Splash.png
```

Now all that you do is OK the change, exit the config editor, restart, Login and Roberts your farthers brother new splash screen.

---

### Post by orbit on 2005-05-08
Thanks for the HOWTO.  It was very useful in cutomizing my whole login experience.  I have one problem though, how do I change the brown background to better match my splash screen? 

Thanks,
orbit

---

### Post by dlpfmVfH on 2005-05-08
[QUOTE=orbit]Thanks for the HOWTO.  It was very useful in cutomizing my whole login experience.  I have one problem though, how do I change the brown background to better match my splash screen? 

Thanks,
orbit[/QUOTE]
 just figured that one out, you have to change the no wallpaper color in gnome-background settings...in the color you want.

---

### Post by orbit on 2005-05-08
[QUOTE=aboe]just figured that one out, you have to change the no wallpaper color in gnome-background settings...in the color you want.[/QUOTE]
 I've already done that, but when the splash screen is shown the background is still the default brown colour.  After the splash disappears the background colour changes to my theme's background colour.

orbit

---

### Post by dlpfmVfH on 2005-05-08
sorry thought that was the solution...
somewhere there is that brown colour defined, and I can't find it anywhere in gconf

---

### Post by bored2k on 2005-05-08
[QUOTE=orbit]I've already done that, but when the splash screen is shown the background is still the default brown colour.  After the splash disappears the background colour changes to my theme's background colour.

orbit[/QUOTE]
 Go to your gdmsetup [login screen setup] and change the background color to your liking.

---

### Post by orbit on 2005-05-08
[QUOTE=bored2k]Go to your gdmsetup [login screen setup] and change the background color to your liking.[/QUOTE]
 Thanks bored2k, that did the trick.  Seems very illogical to put that option in the standard greeter tab because I use the graphical greeter.

---

### Post by bored2k on 2005-05-08
[QUOTE=orbit]Thanks bored2k, that did the trick.  Seems very illogical to put that option in the standard greeter tab because I use the graphical greeter.[/QUOTE]
 Indeed. I've always tried to put a wallpaper there instead of a color, but its never displayed :\.

---

### Post by N'Jal on 2005-05-08
Expanding on the idea, how do you change the default sound? I have a nice tribal/celtic song that's only a min long i would rather hear than the ubuntu default noise

---

### Post by bored2k on 2005-05-08
[QUOTE=N'Jal]Expanding on the idea, how do you change the default sound? I have a nice tribal/celtic song that's only a min long i would rather hear than the ubuntu default noise[/QUOTE]
 Default sound of what ? start up [after login], the bump sound on the login screen, what ?

Go to system > preferences > sounds  to change some of them.

---

### Post by N'Jal on 2005-05-08
After login and, oh yeah, why didn't i think of that. *hit's head*

The system preferences and sound bit

Any way to get it to use mp3's instead of wav's?

---

### Post by mc_cgp on 2005-05-08
[QUOTE=orbit]Thanks bored2k, that did the trick.  Seems very illogical to put that option in the standard greeter tab because I use the graphical greeter.[/QUOTE]


Also change it on the Desktop Background
Bye

---

### Post by michaeltrainor on 2005-05-10
Thanks alot...clean, well spoken HOW TOs...gotta love em'

---

### Post by battletux on 2005-05-18
[QUOTE=michaeltrainor]Thanks alot...clean, well spoken HOW TOs...gotta love em'[/QUOTE]

Thanks. I just copied what i have seen in other HOWTO's.

---

### Post by Mikebgr on 2006-04-01
excelent input bored2k, answered exactly my questions too :).

Btw good how-to, i've seen it on the net tho, maybe you should give credit to the guy who wrote it?gj though :)


ps: ubuntu is anything but stylish, these little modifications go a long way with it's look and feel

---

### Post by Dwiman89 on 2007-07-26
Hay
   IM trying to change the song that plays when your prompted to login and the one that plays once u login and the splash screen comes up. I have found the place in the options to chang it. When i change them they dont play. The songs i want to chang them to are mp3. ive tried cutting them down shorter, and changing the format to wav(via audacity),but they wont play. im wondering if iis a location problem. ive tryed putting my song into the folder with the default sounds, but it wont let me. any ideas.

---

### Post by battletux on 2007-09-24
> **Mikebgr said:**
> Btw good how-to, i've seen it on the net tho, maybe you should give credit to the guy who wrote it?gj though :) 

I'm a bit green when It comes to linux and it was what I had stumbled through on my own to change the splash. The layout was copied from other howto's I've read as it is nice and clean and easy to read.

---

