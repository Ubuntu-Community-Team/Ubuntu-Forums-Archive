---
title: "HOWTO: Transparent Eterm on Desktop"
date: 2006-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by NeoLithium on 2006-10-16
Hi All!
Well, after many hours of wanting, and searching through many different ways to do this; I have found a way that worked quite simple both from the configuration end of things; as well as the ease of setup.  Below, I have included a step by step process from star all the way to the end, and a screenshot of how you can get your own transparent Eterm to appear to be integrated into your desktop.  Please keep in mind the appear part; this doesn't in any way make it part, but puts a clear eterm overtop your wallpaper, and forces it to remain below the other windows.  It uses very few resources, and sometimes, to be honest, I forget I have it and still open my konsole window out of habit.

This is the first tutorial I've written for this; but have included everything so users reading this shouldn't need to switch between their forum window and google, or search around other boards to get it set up.  I should also point out that I have this set up for KDE; but since the commands to start Eterm with this setup universal between linux desktop environments as well as other window managers.  I cannot guarantee that you won't have a border around it for fluxbox or the others; but I'll explain that after you get the gist of how to set it up.

First off, you obviously will need Eterm installed, if you don't have it yet, you can download it from the repositories like so:
```
sudo apt-get install eterm
```

Once you have that installed, you will need to go into your login's KDE directory, and create a file that KDE will run when you actually log into it.  It's quite easy, but of course, you can use any writer you want, I just prefer Kate.  The commands below should be run one at a time in a terminal window. Keep in mind cleardeskterm is the name of the file, use whatever you want; I'm just using mine as an example.
```

cd ~/.kde/Autostart/

kate cleardeskterm
```

Now, you're inside the file that shall become your script.  Some boards around on other forums posted a generic terminal command that starts it up; but doesn't let you really customize or explain much.  To make it easier, I've written some explanations on the functions of the things that make up this script in the actual file; feel free to experiment as much as you want to make it appear just as you always may have wanted.  The code box below can ENTIRELY be copied and pasted into your editor window, once that is done; just save the file.
```

#!/bin/bash

kstart --skiptaskbar --skippager --alldesktops --onbottom Eterm -x -O --buttonbar no --scrollbar no \
--no-cursor  --geometry 75x54+0+0 -f white --font-fx none

#  ****ACTUAL CODE FOR THE COMMAND IS ABOVE THIS LINE. INFO IS BELOW****
#  Easy way to set up a transparent Eterm that appears integrated into your desktop's wallpaper.
#  Assembled by Neolithium for ease of use by new Ubuntu/Kubuntu users.

#Here is some infromation which hopefully help you to set up how you precicely want your eterm to appear. 
#Please keep in mind that the above example is what I actually use on my desktop with a resolution of 1024x768.  
#Mainly, aside from making it look as though you want, for your own desktop, read more on the --geometry setting 
#so you can place it exactly where you would like it on your own, as well as how big you want the window.  
#For more information or help, please see http://www.ubuntuforums.org


#  kstart Functions
#  --skiptaskbar      - This function prevents the program from appearing on your taskbars.
#  --skippager        - If you have multiple desktops, this Eterm window will not appear in the pager.
#  --alldesktops      -Again, multiple desktops, you'll have this window appear on each one.
#  --onbottom        -kstart will try to keep this window below all other windows.

#  Eterm functions
#  -x   -Forces Eterm to start without window borders.
#  -O  -(The capitalized letter) Transparency 
#  --buttonbar       -setting this to no (as in example) starts Eterm without the button bar..
#  --scrollbar         -Setting this to no (as in example) keeps the scrollbar from appearing. 
#                           HOWEVER, you still can scroll through the window with the mouse or 
#                           arrow keys.  Kinda handy without that annoying bar.
#  --no-cursor       -Deactivates the blinking cursor in the Eterm window. Looks good set.
#  --geometry       -Defines the size of the eterm window, as well as it's position on the grid.  
#                           Keep in mind the format goes W x H x XPos x YPos.  The width  
#                           and height are in characters, NOT pixels.  In my example, I have my 
#                           Eterm automatically open to 75 characters wide, and 54 characters 
#                           high (The 75x54 part). As well, it automatically starts in the desktop grid 
#                           at 0,0 - top left corner of the sreen.
#   -f                    -Set the color of the text you wish to use. (Example is white)
#  --font-fx           -Setting this to none (as in example), removes any of the funky shadows, or 
#                           other things that can make this look, well, ultimately hard to read.
```

Now that you have that pasted, and saved; we need to make this file executable; so KDE can actually run what you put inside, when you log into your desktop environment.  Simply type in this:
```
chmod +x cleardeskterm
```
It's DONE! WOO HOO!  Now if you're impatient, and want to see how it looks, you can just click on the file itself, or run it through another terminal window; it's up to you.  I personally ran that executable many many times until I got my settings just right.  Now to explain a bit more about what I was talking about before the tutorial started.  Kstart is what allow eterm specifically on the bottom, and keeps it from the taskbar and pager, etc.  I'm not sure what the specific equivalent is for GNOME or other window managers, so if anyone would like to add that, it would be very much appreciated! :)

The attached photo is how the script brings up Eterm on my desktop, and I just ran a simple apt-get update to show the fill length and dimensions of it. 

Hopefully you find this easier to set up than I did getting it all together. ENJOY!

---

### Post by taurus on 2006-10-16
I think this one should go into the Tips & Tricks section.  ;)

---

### Post by Haegin on 2006-10-16
I seem to remember seeing another method from over a year ago that was more complicated but covered more options and wasnt kde specific (which this one is as it uses kstart) but this is good for people using kde. 

Note - for gnome users look into devilspie for getting it off the taskbar and pining it to the desktop etc.

---

### Post by NeoLithium on 2006-10-16
Once I get the final release of Edgy; I'll have both KDE and GNOME for desktop environments, and will tinker around a bit to keep one as up to date and such; I've just been using KDE for a while for really no apparent reason for me; they're both good DE's.

The GNOME tutorial I found at around 5am yesterday was good and in-depth; but I didn't really find one that worked quickly for KDE; so I thought I might as well :)  Plus the 4 pots of coffee throughout my normal linux tinkering day made me bored easily; which is how half my posts come about  ;)

---

### Post by hikaricore on 2006-10-16
Before I venture into this to replace my gnome-terminal / devilspie setup, do you know if this resolves the conflict with the show desktop button in gnome where upon clicking it the terminal is minimized as well?  Thanks for any info. :)

---

### Post by NeoLithium on 2006-10-16
This specific setup is for KDE; I haven't done any investigating yet for the GNOME setup; although I'm hoping to see if that's doable sometime soon; depending on my time.

---

### Post by hikaricore on 2006-10-16
Well it can't hurt to try, i'll set out on this mission now, got a good 23 hours before my movie finishes downloading anyway :P

---

### Post by NeoLithium on 2006-10-16
I know what you mean; except I ditched my movies for a w**** wack of linux/unix ebooks that will be about 6 gigs worth :)

If I can help out; send me an MSN or ICQ message sometime; I'm almost always around.

---

### Post by bodhi.zazen on 2006-10-16
[img]http://img213.imageshack.us/img213/9572/25226vw1.gif[/img][color=navy]bodhi.[/color][color=gray]zazen[/color]

First, nice how-to. Just book marked it....

But ...

If you are not stuck on eterm this is easy to do with the xfce terminal. Just install and configure from pull-down menu's. Takes less then 1 minute.

[Screen Shot](http://img179.imageshack.us/img179/2416/200609272336471600x1200scrotht5.pn)

---

### Post by hikaricore on 2006-10-16
Well i set it up and worked perfectly.  The show desktop issue still exists, but it's a hell of alot faster than running a cloaked gnome terminal in the middle of my desktop.  lol

(here's my overkill at the moment) ------------------------- (and the work in progress running pico)
[[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/tScreenshot-9.png[/IMG]]("http://img.photobucket.com/albums/v414/hikari_corgan/Screenshot-9.jpg")  [[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/tScreenshot-10.jpg[/IMG]]("http://img.photobucket.com/albums/v414/hikari_corgan/Screenshot-10.jpg")
(gnome-term easier to see in full size shot)

With a bit of visual tweaking it may just replace my everbloated desktop terminal.  This will be enough to keep me busy for a bit lol.  Thanks for the good howto. :)

---

### Post by qcicada on 2006-10-16
O, wow, the result is so cool. 
 But I am a beginner for linux. I still stuck in the first step.
 when I typed in the install command, it responded that it can't find the package. What did I do wrong?  :-| 
 
 the message appear:
 $ sudo apt-get install eterm
 Reading package lists... Done
 Building dependency tree... Done
 E: Couldn't find package eterm

---

### Post by hikaricore on 2006-10-16
Eterm is in [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe

make sure there is a line in your sources.list

```
sudo gedit /etc/apt/sources.list
```

that says:

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

^ i think

and make sure there is not a # character before it :)

after you've added/edited this line (and saved your sources.list)

you need to run

```
sudo apt-get update
```

and try again

---

### Post by NeoLithium on 2006-10-16
> **qcicada said:**
> O, wow, the result is so cool. 
 But I am a beginner for linux. I still stuck in the first step.
 when I typed in the install command, it responded that it can't find the package. What did I do wrong?  :-| 
 
 the message appear:
 $ sudo apt-get install eterm
 Reading package lists... Done
 Building dependency tree... Done
 E: Couldn't find package eterm

[This page]("https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html") should be able to help you enable the extra repositories that you need. :)

---

### Post by moore.bryan on 2006-10-16
*nice tutorial... this should go in the tips and trix... one question, though... why not just use aterm and specify transparency in .Xdefaults?*

---

### Post by NeoLithium on 2006-10-16
Soft spot in my heart for Eterm, I guess. :)  I just tinkered around for a while to find something I liked; of course there probably are tons of better ways; but this was easy to set up, and get running.

---

### Post by qcicada on 2006-10-16
Wow, thanks your help. It's working cool right now. 

You make me love Linux more.:-D

---

### Post by NeoLithium on 2006-10-16
No problem, glad the forum helped you out :)

---

### Post by moore.bryan on 2006-10-17
> **NeoLithium said:**
> Soft spot in my heart for Eterm, I guess. :)  I just tinkered around for a while to find something I liked; of course there probably are tons of better ways; but this was easy to set up, and get running.
*no problems... we all have soft-spots for certain programs (ah, pornview over gthumb...)*

---

### Post by Old Pink on 2006-10-17
Nice! :) 

I'll try this when I get on my primary system tonight.

---

### Post by happy-and-lost on 2006-10-29
I notice that script is for kstart...

How would a n00b translate that into GNOMEspeak?

---

### Post by NeoLithium on 2006-10-29
I think that [this was the thread]("http://www.ubuntuforums.org/showthread.php?t=36811&highlight=devilspie") for GNOME users, although I haven't tried it yet, I'm just installing Edgy with GNOME on another computer right now, so I'm going to give that a try as soon as I'm all set up and running.

---

### Post by lovo on 2010-04-09
that a great tuto!
however when I press Show desktop, the Eterm disapear. Is there any option to disable minimize ?

---

