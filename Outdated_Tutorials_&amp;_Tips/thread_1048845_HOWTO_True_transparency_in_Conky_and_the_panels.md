---
title: "HOWTO: True transparency in Conky and the panels"
date: 2009-01-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Yoshanuikabundi on 2009-01-23
[COLOR="Red"]EDIT:
 Apparently, Conky now supports true transparency - see [http://wiki.conky.be/index.php/1.8.0_tour]("http://wiki.conky.be/index.php/1.8.0_tour"). As far as I know, the panel's still don't have transparency, and since this can theoretically be applied to any program that allows you to set a background colour, it might still be useful for someone.[/COLOR]

Sorry I haven't been updating this, I pretty much forgot about it, and for some stupid reason apparently I didn't get the forums to email me when anyone responded. Apologies. Next time I boot into Ubuntu I'll run through it again and update it.

Hi guys

There are a couple of posts around with this problem - both conky and the panels in Gnome don't have true transparency. This usually creates problems with Compiz - having individual wallpapers on each desktop and semi/fully transparent cubes create glitches where the parts covered by these programs show are not transparent.

Well, I spent a while on the program, and I came up with a solution. It's pretty workaround-ish, and it could probably be improved on, but I'll post it here anyway. This is my first tutorial... ever, I think, so bare with me. :)

This should work with any program that you can change the background colour of. I'm using Intrepid (8.10), but this should work on anything with compiz. If you just want the panels transparent, or just conky transparent, skip the parts that tell about the other bits. Please keep in mind that this tutorial does make use of a compiz plugin that is still in development and could be unstable.

Ok, so the way we're going to do this is to use a plugin still in development to make certain colours transparent, and then colour the panels and conky's background that colour. Then we have to make the plugin initialise every boot. Here goes...

Step 1: Install everything we need.

1.a: That which is in the repo's: Lineakd, as well as a few programs needed to compile the Greenscreen plugin, and a settings manager for compiz. Open a terminal and enter:
```
sudo aptitude update
```
and then
```
sudo aptitude install lineakd compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev libcairo2-dev git-core compizconfig-settings-manager
```

1.b: Now we need to download and install the Greenscreen plugin, which is the core of everything...
Create a new folder to hold the sources in...
```
mkdir compizplugins
```
```
cd compizplugins
```
Now we'll download the source for the Greenscreen plugin...
```
git clone git://anongit.compiz-fusion.org/users/kristianerikson/cf-greenscreen
```
And then compile the plugin:
```
cd cf-greenscreen
```
```
make
```
```
sudo make install
```
If there were no errors, it's installed. To let compiz see it, you'll need to restart compiz - the easiest way to do this is to log out and then back in. Now to set everything up.

Step 2: Configure everything.

2.a: Configure the Greenscreen plugin.
Open CompizConfig Settings Manager (System -> Preferences -> CompizConfig Settings Manager)
Select the tick mark next to Greenscreen (under Accessibility), then click on the Greenscreen button to configure the plugin itself. Set the key combination for "Toggle screen filtering" to "<Shift><Control><Alt>d" (To do this, click the pen and paper icon the the right of the button and enter it into the box that appears). Set the Filtered colour to transparent (click it, drag the Opacity slider to the left). Change the value of Filtered Windows to "type=dock" and Exclude windows to "(any) & !(type=dock)".
Then we need to pick a colour that we want to make transparent. This is a bit tricky. We want a colour that won't appear very frequently, that contrasts well with the text and that will blend into the background easily. This is important because text in conky and the panels is anti-aliased - its edges will be outlined in a colour just off what we pick. I have white and light grey text everywhere, and a darkish background, so I picked #363B38. If you have a lighter background and darker text, try something like #EFFAF3. Make sure you pick a bizarre colour - make sure the blue, red and green values are slightly different. This will make it less likely that an icon will use the colour you pick.

2.b: Configure conky

Conky's configuration file, .conkyrc, can remain pretty much unchanged. You will need to make the following changes, though: 

own_window yes
own_window_type dock
own_window_transparent no
own_window_colour XXXXXX

Change XXXXXX to the colour you selected in step 2.a, without the #.

2.c: Configure the Panel

Right click on the panel you want to change and select Properties. In the background tab, select solid colour and change the colour to the one you selected earlier. Set the Opacity to 100% (full right).

3: Make it all work.

Press control+alt+shift+d. If everything worked, this will initialise the greenscreen plugin and the panel's and conky's backgrounds will become transparent. Now we need to make Ubuntu initialise the plugin on boot. To do this, we essentially just need to run the following command AFTER everything that should be transparent has opened:
```
xsendkeys "shift+control+alt+d"
```
I did this by creating a script that ran conky in the background, waited 5 seconds, and then sent the command. Here it is:
```
#!/bin/bash
conky &
sleep 5
xsendkeys "shift+control+alt+d"
```
Then I replaced Conky with this script in the sessions dialog (System -> Preferences -> Sessions).
If you don't use conky, you can probably just add that script without the "conky &" line to the dialog.

Thanks for reading! I hope this works for people, and that it wasn't too hard to follow. Please, if you have comments or (constructive) criticisms, post them. If you think you have a better way to do this, let us know!

Enjoy
 - Josh

---

### Post by wesgentry on 2009-07-04
Hey Josh, Im new to this and I was wondering how you wrote that script. I went into preferences and there was no sessions option. Im running 9.04. I used the greenscreen for the background in my file browser and set the opacity to about .50 so it dose a cool glass pain effect but when i close the window, like the terminal window when you enable transperancy. I have to hit the hotkey combo every time I open a file browser to get the filter back. I dont know how to write that script to have it open with the filter on and was wondering if you would help me.

---

### Post by DougEdey on 2009-07-20
Hi there, I followed the instructions to the letter but the only response I get when using the shortcuts is to get a flicker on whatever window I'm currently using, there's no changet to either conky or the gnome-panel!

---

### Post by DougEdey on 2009-08-04
> **DougEdey said:**
> Hi there, I followed the instructions to the letter but the only response I get when using the shortcuts is to get a flicker on whatever window I'm currently using, there's no changet to either conky or the gnome-panel!

Fixed now, I recompiled and rebooted and it worked. Very odd.

---

### Post by bobpaul on 2010-05-08
> **Yoshanuikabundi said:**
> 
2.b: Configure conky

Conky's configuration file, .conkyrc, can remain pretty much unchanged. You will need to make the following changes, though: 

own_window yes
own_window_type dock
own_window_transparent no
own_window_colour XXXXXX

Change XXXXXX to the colour you selected in step 2.a, without the #.

When I set the type to dock, conky goes to the top of the screen and won't come down, even though my alignment is bottom_middle. If I set the window type to override, it doesn't look like greenscreen can control it. Any suggestions?

**Edit** I got it working with window type normal, but I can't get rid of the title bar. If I turn off window decorations with own_window_hints, then the background turns black and it doesn't work with greenscreen anymore.

---

### Post by Chame_Wizard on 2010-05-09
Nice one .:guitar:

---

### Post by capleton on 2010-05-18
Hey, I was about to do this workaround and then I discovered this:  [http://wiki.conky.be/index.php/1.8.0_tour]("http://wiki.conky.be/index.php/1.8.0_tour") --as of version 1.8, conky ***does*** do 'true' transparency (provided a compositing wm).  Spread the news!  (also if you're like me, and need a sample config, just google "conky own_window_argb_visual" and you should be all set)

---

### Post by Yoshanuikabundi on 2010-05-18
Sorry I haven't been updating this, I pretty much forgot about it, and for some stupid reason apparently I didn't get the forums to email me when anyone responded. Apologies. Next time I boot into Ubuntu I'll run through it again and update it.

> **wesgentry said:**
> Hey Josh, Im new to this and I was wondering how you wrote that script. I went into preferences and there was no sessions option. Im running 9.04. I used the greenscreen for the background in my file browser and set the opacity to about .50 so it dose a cool glass pain effect but when i close the window, like the terminal window when you enable transperancy. I have to hit the hotkey combo every time I open a file browser to get the filter back. I dont know how to write that script to have it open with the filter on and was wondering if you would help me.

OK, the way I would do that would be to write a script that opens the file manager and then sends the key combo. Something like this:
```
#!/bin/bash
nautilus $1 &
sleep 2
xsendkeys "shift+control+alt+d"
```

I think... Assuming you use Nautilus. You might want to fiddle with the sleep command to minimise the time between opening Nautilus and sending the combo. Then just set the script as your default file manager. I haven't tested that - on Windows at the moment - but I will at some point, if you're interested.

Basically what this script does is open nautilus as a background task (So that the script can continue without waiting for nautilus to close), then sleep for a few seconds to give it time to load (this may or may not be necessary depending on how quick your computer is), and then sends the key combination.

---

### Post by lusguz on 2010-09-29
OK, I'm following your instructions and everything seems to be going along fine till I enter "Make", whereupon I get the reply: make: *** No targets specified and no makefile found.  Stop.

So I move along to "make install" and get the reply:
make: *** No rule to make target `install'.  Stop.

Since I'm am absolute Newbie I presume there's something obvious I'm overlooking.  If you'd like to just email me what it is I'm "lusguz@yahoo.com"

                                 Thanx

---

### Post by bobpaul on 2010-09-29
> **lusguz said:**
> OK, I'm following your instructions and everything seems to be going along fine till I enter "Make", whereupon I get the reply: make: *** No targets specified and no makefile found.  Stop.


It's failing when you run make. You need to run make in the same folder as the file "Makefile". I went back and it looks like cf-greenscreen no longer has a Makefile but has a CMakeList.txt instead. This means they're using cmake instead of make.

But you don't want cf-greenscreen anyway. You want conky version 1.8 as [stated by capleton]("http://ubuntuforums.org/showpost.php?p=9318179&postcount=7"). Conky v1.8 is in Universe in Ubuntu 10.04 Lucid Labradoodle. 

So you need to:
1. Upgrade to 10.04
2. Enable Universe
3. sudo aptitude install conky
4. Enable visual effects (this turns on compositing window manager). System->Appearance->Normal or Extra
5. Google "conky own_window_argb_visual", look at the conky man page, or the conky wiki or post your config file and maybe someone will edit it to enable transparency.

---

