---
title: "Odd display problem - maybe Nvidia-current at fault?"
date: 2011-08-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-08-10
Whe I start my OO system and the desktop arrives, the background appears then the screen blinks and the background moves down by about a quarter of an inch. I can see the picture move down, so that a small area at the bottom disappears.
When my conky display starts a few seconds later it uses the old desktop background - in its old height - so the conky's background and the desktop background don't now line up. See in the screenshot how conky's background is about a quarter of a inch higher than the actual background.
I would change the background to another so that it is clearer, however that option is not now working at all :confused: 
System settings doesn't start, nor does right-clicking on the desktop and selecting "change background".

Anybody noticing similar anomalies?

I'm using Nvidia 280.13

---

### Post by coffeecat on 2011-08-10
> **Quackers said:**
> Whe I start my OO system and the desktop arrives, the background appears then the screen blinks and the background moves down by about a quarter of an inch.

This is with gnome-shell? It's about half an inch for me, but I've got a bigger monitor! :p

From login screen, I see the wallpaper I've chosen, a brief flash of the default purple wallpaper, then the desktop with my chosen wallpaper again which then drops down a bit. I don't think it could be a nvidia driver problem because I'm using an ATI HD5450 card with the open source ati driver.

I can't test this in Unity 3d, because [it's broken at the moment](http://ubuntuforums.org/showthread.php?t=1822093) :(.

**EDIT**: I've tried logging in and out (of gnome-shell) a few times. I haven't seen the flash of the purple again, but something happens each time just before the wallpaper drops. A couple of times it did a sort of sideways wiggle - a bit like a timid belly-dancer - and once the display briefly broke up like a digital TV with a bad signal.

Also - try clicking on Activities top left. Does your wallpaper pop up again with the appearance of the gnome-shell launcher? If so, does the alignment of the wallpaper behind conky sort itself out (at least while the launcher is showing)?

---

### Post by Quackers on 2011-08-10
Aha! Thanks for that CC, so not nvidia-current then :-) Yes, gnome-shell in use (sorry, forgot to mention that).
It's an odd one isn't it?
Sadly, clicking on activities makes conky temporarily disappear (it always did) so no help there :-(

---

### Post by zoff_ita on 2011-08-10
with nvidia-current I can't even login to the desktop.

I can insert login credentials in gdm but no one desktop will be displaied after submit (no ubuntu, no ubuntu 2d, no gnome shell, no gnome classic, no one).

With nouveau I can login but since I use a NVIDIA GeForce GT425M I can't get 3d acceleration.

Any idea?

---

### Post by Quackers on 2011-08-10
Oh no! Things have got worse since tonight's updates, which include a conky-all update.

---

### Post by sparker256 on 2011-08-10
> **Quackers said:**
> Oh no! Things have got worse since tonight's updates, which include a conky-all update.

## Uncomment for Conky 1.8.1

this may help

Bill

---

### Post by Quackers on 2011-08-10
> **sparker256 said:**
> ## Uncomment for Conky 1.8.1

this may help

Bill

So that would be the conky-all update then :-) Am I on conky 1.8.1 now then?
To be honest, I have so many problems with both of my oneiric installations at the moment, I'm now back in Natty and staying there for a while :-)

But thanks anyway Bill, I seem to remember such a line in VinDSL's script :-)

---

### Post by sparker256 on 2011-08-10
> **Quackers said:**
> So that would be the conky-all update then :-) Am I on conky 1.8.1 now then?
To be honest, I have so many problems with both of my oneiric installations at the moment, I'm now back in Natty and staying there for a while :-)

But thanks anyway Bill, I seem to remember such a line in VinDSL's script :-)

conky -v

Bill

---

### Post by Quackers on 2011-08-10
Nocando, it's not booting reliably any more - neither is the alpha3 installation. Sometimes I get fallback, sometimes a black screen, sometimes gnome-shell loads fine but some basic system utilities don't work.
It's a mess. I'm resting for a while :-)
Thanks anyway sir :-)

---

### Post by Harry33 on 2011-08-10
> **Quackers said:**
> Nocando, it's not booting reliably any more - neither is the alpha3 installation. Sometimes I get fallback, sometimes a black screen, sometimes gnome-shell loads fine but some basic system utilities don't work.
It's a mess. I'm resting for a while :-)
Thanks anyway sir :-)

About booting problems.
You have reinstalled nvidia-current each time after any mesa update?
And there have been those lately.
It don't work if you don't.

---

### Post by Quackers on 2011-08-11
Yes, Harry33, I've got nvidia-current purge/re-install on speed dial :-)
Too much appears to be missing from my system, somehow.
System settings won't even start. I can't even change the desktop background any more. Booting to a desktop is a very hit and miss affair.
This includes a one day old alpha3 installation too.
One of the processors (and sometimes both) are pegged at 100% when I haven't used anything! I think that's gnome-settings daemon, or gdm, on occasions.
C'est la vie.

---

### Post by Harry33 on 2011-08-11
> **Quackers said:**
> Yes, Harry33, I've got nvidia-current purge/re-install on speed dial :-)
Too much appears to be missing from my system, somehow.
System settings won't even start. I can't even change the desktop background any more. Booting to a desktop is a very hit and miss affair.
This includes a one day old alpha3 installation too.
One of the processors (and sometimes both) are pegged at 100% when I haven't used anything! I think that's gnome-settings daemon, or gdm, on occasions.
C'est la vie.

Nvidia-current 280.13 should work well with the latest non gl cairo.
However, I have purged gdm, only using lightDM nowadays. Yesterdays updates of lightDM (0.9.3-0ubuntu2) and gnome-session (3.1.3-0ubuntu10) also work well.

I haven't found any difficulties with gnome-settings-daemon.

---

### Post by Quackers on 2011-08-11
I am running 280.13 and downgraded to the non-gl cairo, which did improve things for a while.

I think I'll leave it a few days and try again.

---

### Post by Harry33 on 2011-08-11
> **Quackers said:**
> I am running 280.13 and downgraded to the non-gl cairo, which did improve things for a while.

I think I'll leave it a few days and try again.

No need to downgrade cairo anymore.
The latest version (1.10.2-6ubuntu3) is a non gl version.

> Changelog
cairo (1.10.2-6ubuntu3) oneiric; urgency=low

  * Don't turn the gl backend on, it still creates issues for nvidia users
  * debian/control,
    debian/libcairo2.symbols,
    debian/rules:
    - updated for the non-gl build
 -- Sebastien Bacher <email address hidden>   Tue, 09 Aug 2011 22:47:20 +0200

---

### Post by Quackers on 2011-08-11
Yes, that's correct. Downgrading was the first step, to get things working again. I have the updated version installed now.

---

### Post by dino99 on 2011-08-11
works fine here on i386

what happen if you rename : .gnome2, .local & .gconf ?

---

### Post by Quackers on 2011-08-11
> **sparker256 said:**
> ## Uncomment for Conky 1.8.1

this may help

Bill

Tried that, Bill, but I still get the conky display taking up about two thirds of the width of the screen.

I've run today's updates and things are a little more stable, it seems.
On first reboot both processors were pegged at 100%, but at least this time the reboot function doesn't stall, as previously.
On reboot things speeded up a bit and the desktop arrived (with my extra-wide conky display) and things were ok.
System Settings won't open using any method. It just does nothing - not even a spinning wheel.
I've got no Additional Drivers icon in Applications and using the search for it comes up with nothing.
Sudo jockey-gtk reports
sudo: jockey-gtk: command not found
Is that the correct command? I thought I'd used that before.
It's a bit messy.

---

### Post by mc4man on 2011-08-11
> I've got no Additional Drivers icon in Applications and using the search for it comes up with nothing.
Even though jockey's value is slim to none if you wanted to see in GS's applications you'd likely need to make a small edit to it's .desktop

(there are some .desktops that may or may not show in GS and unity, can possibly vary from installs

It doesn't seem to like what's marked in blue in below line
```
Categories=GNOME;GTK;Settings;DesktopSettings;[COLOR="Blue"]X-GNOME-Settings-Panel[/COLOR];HardwareSettings
```

There are several .desktops that could use some cleaning up to either show or show in an appropriate Applications > sub category

Edit: the command though is jockey-gtk and doesn't need to be run w/ sudo

---

### Post by Quackers on 2011-08-11
Thanks mc4man, I've used your instructions previously to amend the Applications icons. However, as I've just discovered, that wouldn't have helped this time because for some reason jockey-gtk was not installed!
Oh my, I wonder what removed it - not me directly, that's for sure.

---

### Post by mc4man on 2011-08-11
What I have noticed here, where I pretty much always use synaptic, is that it doesn't always work as well as in the past
So I've gotten in the habit of always reloading the sources when I have synaptic open and if marking updates individually rather than in bulk to pay attention to what it may want to do

I've seen synaptic want to remove packages unnecessarily solely based on order picked and in terms of installing occasionally refuse to install, again based on order picked
So possibly synaptic removed your jockey or maybe it was something else..

---

### Post by Quackers on 2011-08-11
Yes, I mustn't have been paying attention on one of the recent updates. It's the only thing I can think of for these things to have gone missing.

An update.
Following Harry33's suggestion I have purged gdm and made lightdm the default desktop manager. 
I have purged and re-installed nvidia-current.
I must say that things have settled down considerably. No spurious cpu-pounding now.
Gnome-shell now loads normally at the first request :-) That's not happened for a while now.
Unity is fine as well.

System settings still appears to be missing and my conky display is way too wide. I'll be trying to sort those out next.

Thanks all.

---

### Post by VinDSL on 2011-08-11
> **Quackers said:**
> Oh no! Things have got worse since tonight's updates, which include a conky-all update.
Hi Quackers,

I posted on this last night (linkage in sig)...  ;)

> 
**[color="darkorange"]_11-AUGUST-2011 UPDATE_[/color]**

conky-all 1.8.1-2 Oneiric (11.10) hit the repos today, and the Calendar Section definately wasn't happy about it.  :D

The 'fix' was easy -- simply remove the trailing ${font} tag, from a single line.

Here is the pertinent secion: 

```

##################################
##           CALENDAR           ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 16}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=18}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=18}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
${voffset -75}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e 's/\r//g' -e '1d' -e s/^/"\$\{offset 105"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}[S]**[COLOR="Red"]${font}[/COLOR]**[/S]
####
## Uncomment for Conky 1.8.1
# ${voffset -75}${offset 105}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e 's/\r//g' -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}[S]**[COLOR="Red"]${font}[/COLOR]**[/S]
${voffset -98}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}

```

For consistency, I dropped the tag from the Conky 1.8.0 version also, even though it wasn't necessary.


Give that a whirl...  ;)

---

### Post by Quackers on 2011-08-12
Thanks VinDSL but I tried that and it's still the same :-(

---

### Post by VinDSL on 2011-08-12
Hrm...

Well, just start commenting/uncommenting lines, until you find the offending code. 

Then, try to figure out why the code isn't working for your rig, and fix it.

Conky 1.8.1 (spacing) is a bish.  I'm the only guy that programs with 1.8.1, AFAIK.

Soooo, you aren't going to get help elsewhere.  The old-guard Conky types are troglodytes.

Let's figure it out together, and become Titans...  :D

---

### Post by sparker256 on 2011-08-12
> **VinDSL said:**
> Hrm...

Well, just start commenting/uncommenting lines, until you find the offending code. 

Then, try to figure out why the code isn't working for your rig, and fix it.

Conky 1.8.1 (spacing) is a bish.  I'm the only guy that programs with 1.8.1, AFAIK.

Soooo, you aren't going to get help elsewhere.  The old-guard Conky types are troglodytes.

Let's figure it out together, and become Titans...  :D
What you posted had 1.8.0 working and 1.8.1 commented out. I changed it to comment out 1.8.0 and have 1.8.1 working and my install is working as before the upgrade. As you stated in your post conky-all 1.8.1-2 is the upgrade and I would call it 1.8.1.

Bill

---

### Post by VinDSL on 2011-08-12
Glad it worked for you, Bill.

Heh!  That calendar has caused me no end of grief.

It's like reaching into a bowl and grabbing a handful of jello.  :D

Actually, I'm surprised that was the only problem that cropped up...

---

### Post by Quackers on 2011-08-12
Ha! It wasn't :-)
I've now got things working better, but not quite perfect.
First I tried the uncomment 1.8.0 and 1.8.1 lines as described in the .conyrc and by sparker256. No change at all.
Then from a suggestion by Sector11 in the conky thread (where I also posted) I changed the line ```
minimum_size 240 0
``` to ```
minimum_size 240 0
maximum_width 240
``` This put a narrower conky display in the middle of the screen, but with things missing on the right edge.
I then changed both values to somewhere between 240 and 500 and the display moved to the right of the screen where it should be, but was too narrow. Whatever value I put then made no change to the width.
I settled on 300 for each.

And thanks for all for the help :-)
I ran some updates and rebooted and conky was nearly normal.

It now has just a couple of items missing (the three-quarter circle around the HT/LT on the right and the grey square thing round the current date - but that's no biggie).
There are also now squares at the start of each line of the calender dates.
Also the "step" in the background (conky's background is a quarter of an inch high) is still persisting. See the "edge" visible and the slight difference in height of the background where conky display starts.

Current .conkyrc ```
##################################
## VinDSL | rev. 11-06-01 00:27 ##
##################################
##        May 2011 Series       ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (currently)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME2)
#  Ubuntu 11.10 'Oneiric Ocelot'   (UNITY)
#  Screen Resolution: 1280x1024    (DELL)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1
#  conkyForecast 2.16 or newer 
#  Weather.com XML Data Feed (XOAP)
#  UTF-8 Compatible Text Editor

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  ConkyWindNESW (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  Moon Phases (Curtis Clark)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva)
#  Weather (Jonathan Macagba)
# 
## Tips from Mr. Peachy, djyoung4, and 42dorian:
## Download ALL of the necessary fonts listed above.
## Unzip fonts to your font folder. Example: /home/username/.fonts
## Run this command in a terminal (rebuilds cache): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 384

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window instead of using desktop?
#
own_window yes
#own_window_class Conky
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar

####
## Force images to redraw when they change.
#
imlib_cache_size 0

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment top_right

####
## Minimum size of text area.
#
minimum_size 300 0
maximum_width 300

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 32  ## Top / Bottom

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 4

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 white #Ivory		#FFFFF0
color2 white #Ivory2		#EEEEE0
color3 white #Ivory3		#CDCDC1
color4 orange		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Black		#000000

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
#lua_load ~/.conky/draw_bg.lua
#lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/.conky/bargraph_small.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
${color white}${offset 5}${voffset -40}${font OpenLogos:size=120}v${font}$alignr ${voffset -90}${goto 210}${color4}${font UbuntuTitleBold:style=bold:size=22}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
##################################
##            SYSTEM            ##
##################################
${voffset 25}${font DroidSans:bold:size=12}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${offset -2}${font OpenLogos:size=14}${color2}Z${voffset -4}${font DroidSans:size=12}${color3}${offset 4}${sysname}${offset 5}${kernel}${alignr}${font DroidSans:size=12}${machine}${font}
${voffset 2}${font StyleBats:size=14}${color2}q${voffset -1}${font DroidSans:size=12}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=12}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font StyleBats:size=12}${color2}k${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=12}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=12}${color2}k${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=12}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 5}${font StyleBats:size=12}${color2}l${voffset -2}${font DroidSansFallback:size=12}${color3}${offset 3}RAM${goto 110}${font DroidSans:size=12}${mem}${goto 150}/${offset 5}${memmax}${alignr}${memperc}%${font}

##################################
##             HDD              ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=12}${color2}x${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 4}ROOT${goto 110}${font DroidSans:size=12}${fs_used /}${goto 150}/${offset 5}${fs_size /}${alignr}${fs_used_perc /}%${font}

${voffset 15}${font StyleBats:size=12}${color2}x${voffset -4}${font DroidSansFallback:size=12}${color3}${offset 4}HOME${goto 110}${font DroidSans:size=12}${fs_used /home}${goto 150}/${offset 5}${fs_size /home}${alignr}${fs_used_perc /home}%${font}

##################################
##           BATTERY            ##
##################################
${voffset 10}${font DroidSans:bold:size=12}${color4}BATTERY${offset 8}${color8}${voffset -2}${hr 2}
${voffset -6}${font DroidSansFallback:size=12}${color1}${alignc}${battery BAT0}
##################################
##         TOP PROCESSES        ##
##################################

${voffset 4}${font DroidSans:bold:size=12}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=12}${color1}h${voffset -3}${font DroidSans:size=12}${color3}${offset 5}${top_mem name 1}${goto 150}${font DroidSans:size=12}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=12}${color1}h${voffset -3}${font DroidSans:size=12}${color3}${offset 5}${top_mem name 2}${goto 150}${font DroidSans:size=12}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=12}${color1}h${voffset -3}${font DroidSans:size=12}${color3}${offset 5}${top_mem name 3}${goto 150}${font DroidSans:size=12}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font PizzaDudeBullets:size=11}${color2}T${font DroidSans:size=12}${color3}${offset 5}${voffset -2}Down${alignr}${font DroidSans:size=12}${downspeed wlan0}${font}
${voffset 2}${font PizzaDudeBullets:size=11}${color2}N${font DroidSans:size=11}${color3}${offset 5}${voffset -2}Up${alignr}${font DroidSans:size=12}${upspeed wlan0}${font}
${voffset 4}${font PizzaDudeBullets:size=11}${color2}T${font DroidSans:size=11}${color3}${offset 5}${voffset -2}Downloaded${alignr}${font DroidSans:size=12}${totaldown wlan0}${font}
${voffset 2}${font PizzaDudeBullets:size=11}${color2}N${font DroidSans:size=11}${color3}${offset 5}${voffset -2}Uploaded${alignr}${font DroidSans:size=12}${totalup wlan0}${font}
##################################
##      WEATHER (Imperial)      ##
##################################
#${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 2}${goto 38}${font Weather:size=43.5}${color2}y${font}
#${voffset -50}${font RadioSpace:size=32}${color3}${alignc}${execi 1800 conkyForecast -d HT -i}${font}
#${voffset -33}${goto 199}${font DroidSansFallback:bold:size=7.55}${color6}H:${offset 1}${execpi 1800 conkyForecast -d HT -s 0 -ui | sed -e 's/N\/A'/'\$\{color7}TBA\$\{color6}/g'}${voffset 15}${goto 200}L:${offset 2}${execi 1800 conkyForecast -d LT -s 0 -ui}${font}
#${voffset -40}${font KRARound:size=36}${color7}${goto 185}I${font}
#${voffset 4}${font Ubuntu:size=23}${color4}${alignc}${execpi 1800 conkyForecast -d CT}${font}
#${voffset 12}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -d MF}${font}
#${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS -i | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 3}mph/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -ui}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
#${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
#${voffset 2}${goto 25}${font ConkyWeather:size=32}${color3}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
#${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 1 -ui}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -ui}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -ui}${goto 187}${execi 1800 conkyForecast -d HT -s 4 -ui}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -ui}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}

${voffset -2}${goto 20}${font Weather:size=43.5}${color2}y${font}
${voffset -62}${font RadioSpace:size=40}${color3}${alignc}${execi 1800 conkyForecast --location=UKXX0092 -d HT}${font}
${voffset -33}${goto 265}${font DroidSansFallback:bold:size=7.55}${color2}H:${offset 1}${execi 1800 conkyForecast --location=UKXX0092 -d HT}${voffset 15}${goto 265}L:${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT}${font}
${voffset -45}${font KRARound:size=43}${color2}${goto 250}I${font}
${voffset 6}${font Ubuntu:size=20}${color4}${alignc}${execi 1800 conkyForecast --location=UKXX0092 -d CT}${font}
${voffset 12}${goto 5}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast --location=UKXX0092 -d BS}${font}${voffset -38}${goto 130}${font ConkyWeather:size=45}${execi 1800 conkyForecast --location=UKXX0092 -d WF}${font}${voffset -40}${goto 260}${font MoonPhases:size=32}${execi 1800 conkyForecast --location=UKXX0092 -d MF}${font}
${voffset 6}${goto 12}${font DroidSansFallback:bold:size=11}${color4}${execpi 1800 conkyForecast --location=UKXX0092 -d WS -i}${execpi 1800 conkyForecast --location=UKXX0092 -d MP | sed -e 's/First.*'/'\$\{goto 252}First Qtr/g' -e 's/Last.*'/'\$\{goto 252}Last Qtr/g' -e 's/New.*'/'\$\{goto 252}New/g' -e 's/Full.*'/'\$\{goto 252}Full/g' -e 's/Waning.*'/'\$\{goto 252}Waning/g' -e 's/Waxing.*'/'\$\{goto 252}Waxing/g'}${font}
${voffset 9}${goto 15}${font DroidSansMono:bold:size=12}${color3}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 1 -w}${goto 92}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 2 -w}${goto 169}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 3 -w}${goto 246}${execi 1800 conkyForecast --location=UKXX0092 -d DW -s 4 -w}${font}
${voffset 2}${goto 10}${font ConkyWeather:size=45}${color3}${execi 1800 conkyForecast --location=UKXX0092 -d WF -s 1 -e 4 -S 1}${font}
${voffset 0}${goto 13}${font DroidSans:bold:size=11}${color4}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 1 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 1 -u}${goto 90}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 2 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 2 -u}${goto 165}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 3 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 3 -u}${goto 240}${execi 1800 conkyForecast --location=UKXX0092 -d HT -s 4 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast --location=UKXX0092 -d LT -s 4 -u}${font}
##################################
##             TIME             ##
##################################
${voffset 6}${font DroidSans:bold:size=12}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=45}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M %p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M %p}${endif}${endif}${font}
${voffset 3}${font DroidSansFallback:bold:size=12}${color4}${alignc 2}Sunrise${offset 1}${execi 1800 conkyForecast -d SR}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${execi 1800 conkyForecast -d SS}${font}

##################################
##           CALENDAR           ##
##################################
${voffset 4}${font DroidSans:bold:size=12}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${offset 12}${voffset 20}${font DroidSansMono:size=10}${color3}${time %A}${font}
${offset 25}${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=28}${color5}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=28}${color5}${time %e}${endif}${endif}${font}
${offset 30}${voffset 0}${font DroidSansMono:size=10}${color3}${time %B}${font}
${offset 30}${voffset 0}${font DroidSansMono:size=10}${color3}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
#${voffset -85}${font DroidSansMono:size=10}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 130"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1
${voffset -85}${font DroidSansMono:size=10}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 130"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
#${voffset -130}${font CutOutsFor3DFX:size=85}${color8}2${font}
##################################
##          RHYTHMBOX           ##
##################################
#${if_running rhythmbox}${voffset 21}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${endif}${font}
#${if_running rhythmbox}${voffset 10}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${endif}${endif}${font}
##################################
##    BANSHEE (Experimental)    ##
##################################
#${if_running banshee}${voffset -5}${font DroidSans:bold:size=7.75}${color4}BANSHEE${offset 8}${color8}${voffset -2}${hr 2}${voffset 31}${endif}${font}
#${if_running banshee}${voffset -28}${font DroidSans:size=8.25}${color3}${if_match "${execpi 16 expr length "`/usr/bin/banshee --query-title --no-present | cut -f1- -d " "`"}" >= "48"}${alignr}${scroll 38 4* ${execi 2 banshee --query-title --no-present | cut -f2- -d " "}}${font}${else}${alignc}${execi 2 banshee --query-title --no-present | cut -f2- -d " "}${endif}${endif}${font}
```

---

### Post by Quackers on 2011-08-12
An update
I've now changed the lines above to 360 and my circle round the HT/LT has returned and all is normal now except for the boxes at the start of the calendar date lines and the background thing (but that could be oneiric, not conky).

---

### Post by VinDSL on 2011-08-12
Looking good, Quackers!

I used to put a maximum_width setting in the pretext, but...

From time-to-time, this-or-that Conky feature will bug out, due to updates, changes to Python, and so forth, and so on.

When this happens, a resultant error message will be displayed (Banshee comes to mind) which often causes Conky to expand halfway across the display.

When you confine Conky output to a tightly defined dimension, these error dialogs will become a jumbled, unreadable, mess.

So, if your Conky display ever becomes a mishmash of indecipherable characters, liberate the output by commenting the maximum_width setting.  Then, uncomment it after you've corrected the problem.  ;)

---

### Post by Quackers on 2011-08-12
Ok, will do, thanks.
Have you any idea about the boxes at the start of the calendar dates? I'm not able to fathom out the code. How do you know all that stuff?

---

### Post by sparker256 on 2011-08-12
> **Quackers said:**
> Ok, will do, thanks.
Have you any idea about the boxes at the start of the calendar dates? I'm not able to fathom out the code. How do you know all that stuff?
```

## Uncomment for Conky 1.8.1
${voffset -75}${offset 100}${font DroidSansMono:size=7.55}${color0}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color0}/'}
${voffset -99}${font CutOutsFor3DFX:size=67}${color8}${alignc 130}2${font}

```

This is what I am using and have a box around where yours is missing.

---

### Post by Quackers on 2011-08-12
Here's mine ```
## Uncomment for Conky 1.8.1
${voffset -85}${font DroidSansMono:size=10}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e '1d' -e s/^/"\$\{offset 110"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
#${voffset -130}${font CutOutsFor3DFX:size=85}${color8}2${font}
``` but I've commented out the grey box for the moment.
I also have the calendar starting at pixel 110.
If you notice you'll see that calendar entries for the 12th and 13th of the month are missing!
No idea why that's the case :-)

---

### Post by sparker256 on 2011-08-14
> **VinDSL said:**
> Glad it worked for you, Bill.

Heh!  That calendar has caused me no end of grief.

It's like reaching into a bowl and grabbing a handful of jello.  :D

Actually, I'm surprised that was the only problem that cropped up...
I thought I had it working but today not looking so good. Here is the relevant part of .conkyrc and a screen shot of the issue. I looked at the code but did not see a clear picture and to what the issue is. I had to add the ${offset 30} to the last line to get the grey box to move in position.

```

##################################
##             TIME             ##
##################################
${voffset 6}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
${voffset 0}${font DroidSansFallback:bold:size=6.85}${color4}${alignc 2}Sunrise${offset 1}${execi 1800 conkyForecast -d SR}${color3}${offset 2}|${offset 2}${color4}Sunset${offset 1}${execi 1800 conkyForecast -d SS}${font}
##################################
##           CALENDAR           ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 16}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${if_match ${time %e}<=9}${font DroidSansFallback:bold:size=18}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${font DroidSansFallback:bold:size=18}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
####
## Uncomment for Conky 1.8.0
#${voffset -75}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e 's/\r//g' -e '1d' -e s/^/"\$\{offset 105"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1
${voffset -75}${offset 120}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_8=`date +%-d`; cal -h | sed -e 's/\r//g' -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
${voffset -98}${offset 30}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}

```
Thanks Bill

---

### Post by VinDSL on 2011-08-14
> **sparker256 said:**
> I thought I had it working but today not looking so good.
Heh!  Welcome to my nightmare, Bill!

Conky 1.8.1 doesn't like semicolons.

This only happens when you're highlighting Sundays with double-digit dates.  :D

The "ghetto fix" is to simply put parenthesis around the object:

```

${voffset -75}${offset 120}${font DroidSansMono:size=7.55}${color3}${execpi 60 **[COLOR="Red"]([/COLOR]**[COLOR="Blue"]VinDSL_Cal_8=`date +%-d`; cal -h[/COLOR]**[COLOR="Red"])[/COLOR]** | sed -e 's/\r//g' -e '1d' -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}

```

Then, remove the parenthesis on Monday. LoL!

This temporarily kills the date highlighting, but restores the proper spacing.

If you come up with a better idea, let me know.

In the meantime, I'll keep working on a permanent solution.  ;)

---

### Post by Quackers on 2011-08-15
I've been having fun with this too :-)
I can't get the grey box to appear at all in gnome-shell, so for the moment I have commented that line out.
The currently highlighted date is missing from the main calendar display and sometimes every other date on the same line as well! That could be a spacing problem, as sometimes a single digit of the missing date(s) appears at the far right edge.
I cannot get rid of the boxes at the start of each calendar date line at all!
However, Vin's new brackets have brought all the dates back again :-)

My latest efforts ```
## Uncomment for Conky 1.8.1
${voffset -85}${font DroidSansMono:size=10}${color3}${execpi 60 (VinDSL_Cal_8=`date +%-d`; cal -h) | sed -e '1d' -e s/^/"\$\{offset 110"\}/ -e 's/\<'"$VinDSL_Cal_8"'\>/${color4}&${color3}/'}
#${voffset -130}${font CutOutsFor3DFX:size=85}${color8}2
```

---

### Post by VinDSL on 2011-08-15
To quote myself...  LoL!

> **VinDSL said:**
> Heh!  That calendar has caused me no end of grief.

It's like reaching into a bowl and grabbing a handful of jello.  :D


I'll get ahold of it, one of these Sundays.  :)

---

### Post by Quackers on 2011-08-15
It's all good fun :-)
It might be more fun if I knew what the bits of code meant :-)
But guessing and adjusting is fun too!

---

### Post by VinDSL on 2011-08-21
Another Sunday, and...  I *think* I have the "Odd display problem" nailed (for now).

Heh!  I wish I had a dollar for every time I've said that...  :D

I was playing around with the nested "if_" calls this week, and discovered that Conky 1.8.1 didn't like the closing tag order in the "Top Processes" section.  And, these tags were affecting sections, further down in the script.

The following code made my Conky script run a lot smoother!

```

##################################
##         TOP PROCESSES        ##
##################################
${voffset 16}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${if_running rhythmbox}${voffset -14}${else}${if_running banshee}${voffset -14}${else}${voffset -14}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
${voffset -14}${endif}${endif}

```

Then, Sunday arrived.

After some fiddling with the calendar code, I finally hit the right combination.

```

## Uncomment for Conky 1.8.1
${voffset -75}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}${font}

```


Highlighted date is working now.  Here's the result...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-21 02:44:01(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-21 02:44:01.png")[/INDENT]


Anyway, you might want to give it a try, before the day is done.  ;)

**EDIT**

BTW, speaking of order...

If you decide to try this, I would strongly suggest killing Conky BEFORE making the changes, then starting it again after saving .conkyrc

That way bash won't booger you up (since I changed a variable name).

You can kill the shell scripts manually, but it's easier to let "killall conky" do it for you.

---

### Post by Quackers on 2011-08-21
Dude! Now no calendar dates show at all (other than the current date which is highlighted and on the left side) and these messages in the terminal :-(
I've checked everything I've typed in .conkyrc
```
ocelot2@ocelot2-VGN-AR51SU:~$ killall conky
ocelot2@ocelot2-VGN-AR51SU:~$ conky
Conky: forked to background, pid is 7034
ocelot2@ocelot2-VGN-AR51SU:~$ 
Conky: desktop window (180001c) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x2200001)
Conky: drawing to double buffer
sh: Syntax error: end of file unexpected (expecting ")")
sh: Syntax error: end of file unexpected (expecting ")")
sh: Syntax error: end of file unexpected (expecting ")")
sh: Syntax error: end of file unexpected (expecting ")")
sh: Syntax error: end of file unexpected (expecting ")")
Conky: '/home/ocelot2/.conkyrc' modified, reloading...
Conky: desktop window (180001c) is subwindow of root window (15a)
Conky: window type - normal
Conky: drawing to created window (0x2200001)
Conky: drawing to double buffer
sh: Syntax error: end of file unexpected (expecting ")")
sh: Syntax error: end of file unexpected (expecting ")")

```

---

### Post by Quackers on 2011-08-21
DOH! Please ignore previous ramblings. I left in one of the brackets of your last set of amendments :-)
It is displaying now but due to my screen resolution I need to put in a ${offset 130} or similar somewhere. 
I'll have a play!!


EDIT done now :-)
Once again, many thanks for all your hours of work VinDSL :-)

---

### Post by sparker256 on 2011-08-21
> **VinDSL said:**
> Another Sunday, and...  I *think* I have the "Odd display problem" nailed (for now).

Heh!  I wish I had a dollar for every time I've said that...  :D

I was playing around with the nested "if_" calls this week, and discovered that Conky 1.8.1 didn't like the closing tag order in the "Top Processes" section.  And, these tags were affecting sections, further down in the script.

The following code made my Conky script run a lot smoother!

```

##################################
##         TOP PROCESSES        ##
##################################
${voffset 16}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
${if_running rhythmbox}${voffset -14}${else}${if_running banshee}${voffset -14}${else}${voffset -14}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font DroidSans:size=8.75}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
${voffset -14}${endif}${endif}

```

Then, Sunday arrived.

After some fiddling with the calendar code, I finally hit the right combination.

```

## Uncomment for Conky 1.8.1
${voffset -75}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}${font}

```


Highlighted date is working now.  Here's the result...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-21 02:44:01(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-21 02:44:01.png")[/INDENT]


Anyway, you might want to give it a try, before the day is done.  ;)

**EDIT**

BTW, speaking of order...

If you decide to try this, I would strongly suggest killing Conky BEFORE making the changes, then starting it again after saving .conkyrc

That way bash won't booger you up (since I changed a variable name).

You can kill the shell scripts manually, but it's easier to let "killall conky" do it for you.

Followed your instructions and all is well again. I have a small ongoing alignment issue with the Calendar and the High Low display but adjusting the offset corrects it. I think it is a width issue from looking at your screen shot.

Thanks Bill

---

### Post by Xgen on 2011-08-21
The highlighted date correction works fine with no changes to my voffset/offset settings BUT only if I remove the trailing ${font} from the calendar string. If I don't, the width of the conky panel increases and the voffset/offset setting changes.

---

### Post by Quackers on 2011-08-21
That was happening to mine too a week or so ago. I think it was due to the new conky-all package. I'm not absolutely sure what fixed it now. I think there may be something about that in the earlier posts.
At one thime though, it was definitely necessary to remove the trailing ${font}

---

### Post by VinDSL on 2011-08-21
> **sparker256 said:**
> I have a small ongoing alignment issue with the Calendar and the High Low display but adjusting the offset corrects it.

> **Xgen said:**
> The highlighted date correction works fine with no changes to my voffset/offset settings BUT only if I remove the trailing ${font} from the calendar string.

> **Quackers said:**
> That was happening to mine too a week or so ago. I think it was due to the new conky-all package. I'm not absolutely sure what fixed it now.[...]

At one thime though, it was definitely necessary to remove the trailing ${font}
Aye!  I broke one of my cardinal rules.  Sorry!

As a rule, I don't run a "maximum_width" tag.  It's a crutch IMO, but...

I was playing around with it last week, and forgot to comment it during testing.

```
####
## Minimum size of text area.
#
minimum_size 240 0

[B][COLOR="Blue"]####
## Maximum width of text area.
## Comment during code testing.
## Uncomment for normal operation.
# maximum_width 240[/COLOR][/B]
```

With the "maximum_width" *crutch* uncommented (enabled), everything was fine.

With "maximum_width" commented (disabled), the trailing ${font} tag is indeed messing with the alignment (again).

The pertinent line should read:

```
####
## Uncomment for Conky 1.8.1
${voffset -75}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}[S]**[COLOR="Red"]${font}[/COLOR]**[/S]
```


Lesson learned!  I'll correct it in my next data dump.  

I just need to make sure the 'fix' sticks, when the calendar rolls over to Monday at midnight.  ;)

---

### Post by Quackers on 2011-08-22
Thanks for the clarification VinDSL.
The calendar is fine today, here :-)

---

### Post by VinDSL on 2011-08-22
Thanks, all.

It struck midnight here, and everything looks fine.

I'll button things up and do a data dump, in a little while. ;)

---

### Post by VinDSL on 2011-08-22
LoL!  Works, in Unity 2D too!  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/Screenshot at 2011-08-22 00:12:06(650x520).png[/IMG]]("http://vindsl.com/images/Screenshot at 2011-08-22 00:12:06.png")[/INDENT]


How's that for a temp, at midnight?!?!?

---

### Post by Quackers on 2011-08-22
VinDSL I was going to ask if you live in a desert with those temps!
But I see that you do :-)

---

### Post by Quackers on 2011-09-16
An update.
The mis-alignment in the desktop background at the start of the conky display in gnome-shell is now fixed (obviously by VinDSL - not me!)
The addition of another own window line and an addition to the own window hints line has done the job for me in Ubuntu (though strangely these don't seem to be required in Fedora15 with gnome-shell).

My own_window entries now look like this ```
own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
Hail VinDSL ! :-)

---

