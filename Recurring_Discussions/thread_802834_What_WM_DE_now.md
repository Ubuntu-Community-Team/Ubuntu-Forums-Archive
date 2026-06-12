---
title: "What WM/ DE now"
date: 2008-05-21
forum: Recurring Discussions
---

### Post by -gabe-noob- on 2008-05-21
I've tried enlightenment Gnome KDE and XFCE 

What should I use now I'm bored...................

note i've tried all those on Ubuntu bases 

Enlightenment With OpenGEU 
and the other 3 with Ubuntu and the 2 varients

---

### Post by kevin11951 on 2008-05-21
**sits back and waits for LaRoza to post**

---

### Post by dizee on 2008-05-21
Openbox ;)

---

### Post by -gabe-noob- on 2008-05-21
How would I aquire this "openbox" Is it easy/hard to configure?

---

### Post by amingv on 2008-05-21
Fluxbox? That should entertain you for a while.

---

### Post by dizee on 2008-05-21
You can install it through the repos
```
sudo apt-get install openbox obconf openbox-themes obmenu pypanel
```
Not too hard to set up and pretty cool looking as well as very fast and minimal. You right click on the desktop for the menu, though you can run a panel as well if you want. Very useful guide here [http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

You *might* need to set up the menu yourself but when I tried it it was done automatically. Even if you do obmenu is really easy to use.

The beauty of openbox is its modularity, you can run a very minimal set up or run it with whatever docks, panels, file managers etc. you want.

---

### Post by p_quarles on 2008-05-21
Moved to Recurring Discussions.

---

### Post by -gabe-noob- on 2008-05-21
now if I installed it on my current kubuntu how would I remove KDE ?

---

### Post by -gabe-noob- on 2008-05-21
If I did this with an alternit install cd, then I could theroreticly just have openbox with no gnome and kde

If I use openbox with Gnome or KDE will it be as cpu intensive as the DE it's self?

---

### Post by NightwishFan on 2008-05-21
I believe if you just boot to a openbox/fluxbox session at login screen it will be that wm but you will have access to all your gnome/kde apps. Try Fluxbox, IceWM, and JWM. There are others as well, however I like those three.

---

### Post by dizee on 2008-05-21
You can run Openbox without Gnome or KDE easily, when you install it it gives you the option of an Openbox session, a Gnome with Openbox session, and a KDE with Openbox session.

If you use it with Gnome or KDE I would expect it to be a little lighter than regular Gnome/KDE sessions since it replaces Metacity or Kwin but the real performance boost is running it on its own.

---

### Post by RiceMonster on 2008-05-21
Openbox.

Or fluxbox for an "easier" *box, that already has a planel. Or maybe you're like me and you don't want any panels, so you just use stalonetray with Openbox for "tray apps" and conky for the time.

---

### Post by -gabe-noob- on 2008-05-21
cool, and I can install them all on a Ubuntu base for now (looking into arch, have been for about a month or so, I just wanna see if I'm up to it but I'm not gonna risk it till school is over cause I need the laptop till then...)

anyone know if openbox can recognise flashdrives?

---

### Post by NightwishFan on 2008-05-21
I believe it is up to the kernel. I like rox-filer file manager, and I think it can browse something like that.

---

### Post by -gabe-noob- on 2008-05-21
cool (flash drives supports kernals 2.4+ so I'm good on that)

---

### Post by RiceMonster on 2008-05-21
> **-gabe-noob- said:**
> cool, and I can install them all on a Ubuntu base for now (looking into arch, have been for about a month or so, I just wanna see if I'm up to it but I'm not gonna risk it till school is over cause I need the laptop till then...)

anyone know if openbox can recognise flashdrives?

Yep. You can use konqueror to view them too (you said you had kubuntu installed). The openbox default will launch konqueror if you hit windows-e. You can use any file manager you want though, and you can change the key binding to fit whichever one it is. You can add keybindings too.

Oh, and I noticed you asked if it's hard or easy to configure. By default, you configure it by editing text files (xml), but there's Obconf to make that easier. There's also Obmenu for editing the menu, but for some reason it won't start for me, so I just edit the root menu with vim, which works fine for me.

---

### Post by -gabe-noob- on 2008-05-21
> **RiceMonster said:**
>  windows-e

.
 


Ubunut-e you mean (yes I removed the windows key with a nail file and penciled in a ubuntu sign) 

Thanks for the help though, this looks like Openbox may keep my attention longer then some of the others... will compis work with it (the screenshots I've seen make it seem very minimalistic, which I like)


But will it take as long as kubuntu to go from me clicking the power button- to the login screen?

---

### Post by -gabe-noob- on 2008-05-21
WHOA I just relized that I'm better at installing with the terminal then with Synaptic :O I am now UBER PRO! (in my head)

---

### Post by -gabe-noob- on 2008-05-21
conky for the time... how would I do this?

---

### Post by dizee on 2008-05-21
My conky is set to display the day, date and time (24-hour, with seconds) only. Here is the .conkyrc file:
```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=10

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints below
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background 
colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 5

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects 
certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to 
localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 
or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 
or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${alignr}${time %a, %b %d}
${alignr}${time %H:%M:%S} 

```

Copy it to ~/.conkyrc to use it yourself. Add "conky &" to the ~/.config/openbox/autostart.sh if you like it :)

Edit -- need to have conky installed first of course, it's as simple as ```
sudo apt-get install conky
```

And of course try it first by running "conky &".

---

### Post by dizee on 2008-05-21
> **dizee said:**
>  Very useful guide here [http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

Just so you know some of this guide is a bit out of date. For example you just need to add programs to the autostart.sh file for them to start with openbox, there's no need to go messing around with the session files (skip the bit where it says "sudo gedit /usr/share/xsessions/openbox-autostart.desktop").

Also obmenu is in the repos so no need to compile it.

The rest of the guide seems spot on though :smile:

---

### Post by -gabe-noob- on 2008-05-21
uhm... 
I minimized a window... and I can't get it back...

---

### Post by -gabe-noob- on 2008-05-21
nvm I used a pypanel config that I found on the net... this openbox thing is ... AWESOME! I really Like it

---

### Post by dizee on 2008-05-21
> **-gabe-noob- said:**
> uhm... 
I minimized a window... and I can't get it back...
I don't even use a panel, I just Alt-tab to switch, it unminimizes (is that even a word?!) windows too.

---

### Post by jrusso2 on 2008-05-21
FVWM Crystal is lightweight and awesome looking.  I have also seen some customized fluxbox installs that were beautiful.

---

### Post by -gabe-noob- on 2008-05-21
is there anyway to take away kde and just work with openbox while still keping all the applications I have (will it effect the login? as my login screen is the defauld Kubuntu 1 also it will make time from when I click power to when I see the desktop shorter correct?

>

---

### Post by -gabe-noob- on 2008-05-21
instead of comming up on the desktop my conky comes up in a window and I think its supposed to come up on the desktop how can I fix this?

---

### Post by Dr Small on 2008-05-21
IceWM FTW!

---

### Post by eriqjaffe on 2008-05-21
> **-gabe-noob- said:**
> instead of comming up on the desktop my conky comes up in a window and I think its supposed to come up on the desktop how can I fix this?Technically, conky **is** a window.

Try adding the following to your .conkyrc:

```
own_window yes
own_window_type normal
own_window_transparent yes
```

...then just kill and restart conky.

You might need to change "own_window_type" to "desktop".

[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html) has all the conky documentation well laid-out.

BTW, if you haven't already, you might want to install gmrun (it's in the repos) and then bind it to a key in ~/.config/openbox/rc.xml:

```
<keybind key="A-F2">
  <action name="Execute">
    <execute>gmrun</execute>
  </action>
</keybind>
```

---

### Post by cardinals_fan on 2008-05-22
Openbox is a good WM.  I just {read: today} got hooked on Xmonad: it's **very** nice.

---

### Post by RiceMonster on 2008-05-22
> **-gabe-noob- said:**
> uhm... 
I minimized a window... and I can't get it back...

Use alt tab. Also, the default right-click menu gives you a "desktops" menu that shows you all the windows running in each desktop. Clicking on the one you want takes you there. Middle clicking should bring up a menu like this as well. 

I installed a bunch of different panels, but I realized I like the minimalism of having none, but I still needed a tray for apps like Emesene and Exaile. Alt-tab, a nicley setup root menu and keybindings to launch a few apps handles the rest of the panel uses for me :).

[quote=gabe-noob]Ubunut-e you mean (yes I removed the windows key with a nail file and penciled in a ubuntu sign) [/quote]
Haha, that's pretty cool actually. My laptop still has a windows vista sticker on it, but I'm too lazy to remove it :p.

---

### Post by urukrama on 2008-05-22
> **-gabe-noob- said:**
> this openbox thing is ... AWESOME! I really Like it

Have you seen my Openbox guide (link in signature)? It might make your venture into Openbox land smoother.

---

### Post by urukrama on 2008-05-22
> **-gabe-noob- said:**
> is there anyway to take away kde and just work with openbox while still keping all the applications I have (will it effect the login? as my login screen is the defauld Kubuntu 1 also it will make time from when I click power to when I see the desktop shorter correct?

>

I'm not sure I've fully understood what you are asking. 

If you are asking whether installing Openbox will mess with your KDE/Kubuntu installation: no. It just installs alongside it. In the "Sessions" menu of your login screen you should be able to select Openbox, KDE, and Openbox/KDE. The first will load Openbox, the second KDE, the third will load KDE with Openbox as the window manager (instead of Kwin).

If you are asking if you can use KDE applications in Openbox: yes. They should work fine (unless they depend on some key KDE part, but most apps don't). IF you want to speed up the loading of the first KDE app, you can add "kdeinit &" to your autostart file.

Having Openbox installed will not speed up the boot process (up to KDM, the login screen), but when you log into Openbox your desktop should appear faster than when you log into KDE (or Gnome).

---

### Post by -gabe-noob- on 2008-05-22
Thanks for the reply but I was asking if I could remove the whole kubuntu desktop while still keeping all the apps I have and replacing KDM with somthing else that would come up faster.

---

### Post by -gabe-noob- on 2008-05-22
> **cardinals_fan said:**
> Openbox is a good WM.  I just {read: today} got hooked on Xmonad: it's **very** nice.

uhm... wait how many times a week do you swich WM's? I think your worse them me... lol last I checked you were hooked on KDE mod arch...|

The guy in the arch forums was right, you went back to tiling managers

---

### Post by cardinals_fan on 2008-05-22
> **-gabe-noob- said:**
> uhm... wait how many times a week do you swich WM's? I think your worse them me... lol last I checked you were hooked on KDE mod arch...|

The guy in the arch forums was right, you went back to tiling managers
That's [chucky chuckaluck]("http://ubuntuforums.org/member.php?u=528483").  I switch often, but you'd never catch me using KDE ;)

---

### Post by -gabe-noob- on 2008-05-22
Oh yeah Chucky, I'm not kidding but I saw some one on warcraft 3 nammed Chuckaluck... I wonder if it was him :P

---

### Post by LaRoza on 2008-05-22
> **-gabe-noob- said:**
> Oh yeah Chucky, I'm not kidding but I saw some one on warcraft 3 nammed Chuckaluck... I wonder if it was him :P

Usually named "fuscia" I think.

---

### Post by zmjjmz on 2008-05-22
> **-gabe-noob- said:**
> Thanks for the reply but I was asking if I could remove the whole kubuntu desktop while still keeping all the apps I have and replacing KDM with somthing else that would come up faster.

I think SLiM would be a good login manager for you. I'm not too sure on removing KDM though, it's easy to do in Arch.

---

### Post by LaRoza on 2008-05-23
> **zmjjmz said:**
> I think SLiM would be a good login manager for you. I'm not too sure on removing KDM though, it's easy to do in Arch.

In Debian based systems:

```

sudo dpkg-reconfigure kdm

```

It will ask what you want to be the default.

For other package managers, find the utility that reconfigures packages and use it on KDM.

---

### Post by Inxsible on 2008-05-23
> **-gabe-noob- said:**
> Thanks for the reply but I was asking if I could remove the whole kubuntu desktop while still keeping all the apps I have and replacing KDM with somthing else that would come up faster.The fastest is to have no DM at all. All it does is let you login. So when you start up the computer, you will be presented with a console. You login and then issue```
startx
``` to start the GUI. This is very helpful in older resource lacking systems

---

### Post by -gabe-noob- on 2008-05-23
cool, theroreticly my system would boot faster too... (trying to get it to boot FAST!)

---

### Post by cardinals_fan on 2008-05-23
I'm really a traitor at heart.  I was having problems with my ghc version and Xmonad, and realized that I don't even like Haskell!  So now I'm on dwm and I'm very happy.

---

### Post by -gabe-noob- on 2008-05-23
Nice :P

I really like open box, when I use it I make it look kinda like a tilling WM, anyone know how to take a Screenshot?

---

### Post by cardinals_fan on 2008-05-23
> **-gabe-noob- said:**
> Nice :P

I really like open box, when I use it I make it look kinda like a tilling WM, anyone know how to take a Screenshot?
My way:

```
sudo apt-get install scrot
scrot -d 5
```
It'll stick a dated screenshot in your home directory after 5 seconds.

---

### Post by -gabe-noob- on 2008-05-23
thanks

---

### Post by eriqjaffe on 2008-05-24
You could also bind scrot to the Print Screen key:

```
<keybind key="Print">
  <action name="Execute">
    <execute>scrot 'scrot_%Y-%m-%d_%H:%M:%S.png' -e 'mv $f ~/Screenshots/'</execute>
  </action>
</keybind>
```

---

