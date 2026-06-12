---
title: "How do people get all those 3D effects and such in Ubuntu?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-09-06
the 3d flip, i saw it on youtube

---

### Post by cwsnyder on 2008-09-06
Go into the menu: Applications >> Add/Remove and search for compiz.  Install the compiz-fusion packages with their dependencies, then search for emerald and install that package (a theme for compiz-fusion) and its dependents.

After that, go into System >> Preferences >> Appearance and select the Visual Effects tab.  Now select the E_x_tra radio button and select the Apply button if there is one, or simply select the _C_lose button.

---

### Post by hubie on 2008-09-06
I don't know what you saw on YouTube, but my guess is that you saw [Beryl]("http://www.beryl-project.org/").

---

### Post by cwsnyder on 2008-09-06
Last I was informed, Beryl had been combined with Compiz to make up the package Compiz-Fusion.

---

### Post by RequinB4 on 2008-09-06
Beryl is now compizfusion -- to use it, go to system - administration - system package manager and install the package "simple-ccsm" OR the package "compizconfig-settings-manager" (the first if you don't want a high level of customization.

You can now go into the appropriate new menu in system - preferences (either "advanced desktop effects settings" or "simple compizconfig settings manager") and have fun

---

### Post by lovinglinux on 2008-09-06
Read this FAQ [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

It has everything you need to know to get started.

---

### Post by thebigfatgeek on 2008-09-06
I suggest you also go across to the Conky thread at [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)[/COLOR] which is another way to get a really cool desktop without the hardware requirements of Compiz.

It is really easy to install and configure, and you can get hundreds of scripts from other users on the thread above. I have come across Conky only last night, and have taken a bog standard desktop to what you can see in my attached screenshot in less than 24h. 

```
sudo apt-get install conky
```and afterwards create a text file on your desktop with a simple script. 

Call the file whatever you like initially, until you have it properly setup and you want to make it part of your normal desktop, after which you can read on the above thread more about autostarting Conky etc. Here is a script from the abovementioned thread (thank you fusion.fake), not mine (mine requires a special font for the clock), which does not seem to require anything special to run.

```
 #    .conkyrc configuration
#    basics by Tristam Green, 11-21-2007
#     edited by fusion.fake

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want tormo to be forked in the background
#background yes

use_xft yes

# Xft font when Xft is enabled
xftfont Vera-8
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border widt5
border_width 6

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

#    *** RHYTHMBOX FORMAT SETTINGS ***

#    ${rhythmbox-client --print-playing}
#              Print the title and artist of the playing song

#    ${rhythmbox-client --print-playing-format}
#              Print formatted details of the song

#    *** PARAMETERS ***

#       %at    Album title
#       %aT    Album title in lowercase
#       %aa    Album artist
#       %aA    Album artist in lowercase
#       %ay    Release year of album
#       %an    Album disc number
#       %aN    Album disc number with leading zero
#       %ag    Album genre
#       %aG    Album genre in lowercase
#       %tt    Track title
#       %tT    Track title in lowercase
#       %ta    Track artist
#       %tA    Track artist in lowercase
#       %tn    Track number
#       %tN    Track number with leading zero
#       %td    Track duration
#       %te    Elapsed time of track

#       Variables can be combined using quotes. For example "%tn %aa %tt", will
#       print the track number followed by the artist  and  the  title  of  the
#       track.


# stuff after 'TEXT' will be formatted on screen

TEXT

${color white}${font OpenLogos:size=14}danY Linux ${font}${font Vera:size=8}$alignr ${time %a } ${time %e %B %G} | ${time %I:%M %P}${font}
${color #5da5d3}User ${hr 1}
  ${color #e5e5e5}${execi 30 whoami} @ $nodename $alignr $sysname $machine $kernel
  ${color #e5e5e5}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color #CCCCCC}$alignr${freq_g} GHz
  ${color #e5e5e5}uptime $alignr $uptime_short

${color #5da5d3}System ${hr 1} 
  ${color #e5e5e5}cpu usage $color $alignr $cpu%
  ${color #e5e5e5}load $alignr $loadavg
  
${color #5da5d3}Processes ${hr 1}
  ${color #e5e5e5}total $alignr $processes
  ${color #e5e5e5}running $alignr $running_processes

${color #5da5d3}Memory ${hr 1}
  ${color #e5e5e5}total $alignr ${memmax}
  ${color #e5e5e5}used $alignr $memperc%  $mem

${color #5da5d3}Wired (${color #ff9900}${addr eth0}${color #5da5d3}) ${hr 1}
  ${color e5e5e5}down ${color #ff9900}${downspeedf eth0} ${color e5e5e5}k/s ${alignr}${color e5e5e5}up ${color #0000ff}${upspeedf eth0} ${color e5e5e5}k/s
  ${color e5e5e5}total down: ${totaldown eth0} $alignr total up: ${totalup eth0}

${color #5da5d3}File Systems ${hr 1}
  ${color #e5e5e5}fusion linux ${color white}${fs_free /} (${fs_free_perc /}%) ${color #e5e5e5}free of ${fs_size /}
       ${fs_bar /}
  ${color #e5e5e5}fusion XP ${color white}${fs_free /media/sda1} (${fs_free_perc /media/sda1}%) ${color #e5e5e5}free of ${fs_size /media/sda1}
       ${fs_bar /media/sda1}
  ${color #e5e5e5}fusion 320gb ${color white}${fs_free /media/sda5} (${fs_free_perc /media/sda5}%) ${color #e5e5e5}free of ${fs_size /media/sda5}
       ${fs_bar /media/sda5}
  ${color #e5e5e5}fusion 250gb ${color white}${fs_free /media/sdb5} (${fs_free_perc /media/sdb5}%) ${color #e5e5e5}free of ${fs_size /media/sdb5}
       ${fs_bar /media/sdb5}

${if_running rhythmbox}  ${color #e5e5e5}status $alignr active
  ${color #e5e5e5}title      ${execi 1 rhythmbox-client --print-playing-format "%aA -  %tT"}
  ${color #e5e5e5}album   ${execi 1 rhythmbox-client --print-playing-format "%aT (%ay)"} $alignr track ${exec rhythmbox-client --print-playing-format "%tn"}
  ${color #e5e5e5}time     ${exec rhythmbox-client --print-playing-format "%te / %td"}${else}  ${color #e5e5e5}status $alignr inactive
  ${color #e5e5e5}title      Not playing
  ${color #e5e5e5}album   Not playing $alignr track Not playing
  ${color #e5e5e5}time     Not playing${endif}

${execi 30 wmctrl -a conky}
```You can just cut and paste the above into a file on your desktop (for starters) and run the script with Conky after you installed it with the following 

```
conky -c ~/Desktop/filename.ext
```Just replace the filename.ext with whatever you have saved your file. I attach the script also as a file called FirstConkyScript.txt, and you can just download it to your desktop and run it with Conky:

```
conky -c ~/Desktop/FirstConkyScript.txt
```and hopefully the bug will bite you too!!

Just remember Linux is case sensitive, so FirstConkyScript.txt is not the same as firstconkyscript.txt
[B]
IT IS REALLY AWESOME!!

[/B]PS: I must admit that the transparent terminal windows on the left do require Compiz to function, but that is part of Screenlets, and not Conky.

```
sudo apt-get install screenlets
```

---

### Post by knix on 2008-09-06
Compiz fusion is installed by default. you need to install compizconfig-settings-manager.
then, go to system >> preferences >> advanced desktop effects. enable shift switcher, then click on it, change switcher mode to Flip.

You'll need to enable effects as seen in above posts, as well as enabling the 3d drivers.

Edit: simple-ccsm will work, but basically gives you preconfigured profiles that may not have everything you want.

you may need to install compiz-fusion-plugins-unsupported.

you may want to enable dodge, rotate cube, expo, and anomations plus.

---

