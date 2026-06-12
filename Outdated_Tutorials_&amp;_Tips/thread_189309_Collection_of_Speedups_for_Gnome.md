---
title: "Collection of Speedups for Gnome"
date: 2006-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by balloons on 2006-06-05
Here's a collection of tips for making gnome and your Ubuntu experience better on slower machines (or those of us who are speed maniacs). Alot is gleaned from others (THANK YOU), and some is my own. I'd also like your tips, so we can centralize these tips into one place. I employ all of these on an Athlon 3200+, just for the speed :D 

1) install xubuntu to access xfce which is a lite desktop.
or install fluxbox, icewm as alt window managers

2) Do sudo gedit /etc/X11/xorg.conf on the terminal. Find DefaultDepth
and change it to 16 or 8 (but 8 is to extreme in most cases).
Then you have to restart X ( you can do that by doing ctrl-alt-backspace)
though you have less colors.

3) Disable animations
gconftool-2 --type bool --set /apps/panel/global/enable_animations false
gconftool-2 --type bool --set /apps/panel/global/tooltips_enabled false
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true

(Reduced resources also gives you black rectangles when you move windows, so
enable assistive technologies (System->Preferences->Assitive Technologies, it will remove the black boxes)

4) Shorten delays (I chose 100, you can do whatever you like)
gconftool-2 --type integer --set /apps/metacity/general/auto_raise_delay 100
gconftool-2 --type string --set /apps/panel/global/panel_animation_speed panel-speed-fast
gconftool-2 --type integer --set /apps/panel/global/panel_hide_delay 100
gconftool-2 --type integer --set /apps/panel/global/panel_show_delay 100

5) Go to System->Preferences->Theme and change the theme by going to
Theme Details. Choose something lite like Raleigh or Simple for
Controls and Atlanta or Esco for Window.

6) Go to Nautilus and Edit->Preferences->Preview and use Never for all.

7) Go to System->Preferences->Menus And Toolbars and unselect
Show icons in menu you can also change the Toolbar button label to only
Text.

8 ) Disable using Nautilus for the desktop (This will turn off all icons on desktop)
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

9) Turn off unessisary virtual terminals:
sudo gedit /etc/inittab and put # in front of
these lines:
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

10) Use different native GTK apps
OpenOffice Word = Abiword
OpenOffice Calc = Gnumeric
Firefox = Epiphany 
Evolution = Slypheed
Gedit = Leafpad

11) Reduce you number of workspaces to 1 or 2

12) Use the specific version of the kernel for you CPU
To update the kernel just follow the steps. 
Open Synaptic (or do it via apt) 
Search for linux-image packages 
Check you processor. 
If Pentium 4/Celeron or AMD Athlon, get the linux-image-686
If AMD, get linux-image-k7
If older pentium/celeron keep the linux-image-386 image
If you have multiple processor, like HT, get imagename-smp 

13) Follow these guides, or use BUM (Boot Up Manager) to speed up Boot and performance
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=82783&highlight=bum](http://ubuntuforums.org/showthread.php?t=82783&highlight=bum)

14) Follow this guide to tuning your hardrive for speed
[http://ubuntuforums.org/showthread.php?t=24416]](http://ubuntuforums.org/showthread.php?t=24416])

15) Follow this guide for a filesystem enhancement
[http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

16) Follow this guide to prelink your favorite applications
[http://ubuntuforums.org/showthread.php?t=74197](http://ubuntuforums.org/showthread.php?t=74197)

---

### Post by nowshining on 2007-10-14
thanks this may be at lest a year old but some things work great, also adding even with a non-ht p4 will speed up the system by adding acpi-ht and ht=on in the grub menu, i did and now it's superfast and got faster with ur links.. ;) oh and I did do some things before I saw this u already had lolz..

---

