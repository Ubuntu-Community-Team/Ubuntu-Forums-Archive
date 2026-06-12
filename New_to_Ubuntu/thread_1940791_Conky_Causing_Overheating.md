---
title: "Conky Causing Overheating?"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by wpwend42 on 2012-03-14
Anytime I load up Conky, the fan on my desktop computer goes crazy and will not shut off ever. If I turn off Conky, it slows and turns off pretty quickly. Normally, a program I would see in Conky would cause this problem, but it seems to be Conky itself. 

How can Conky being doing this? Is it the scripts running in combination with something else? I am willing to forgo running Conky, but I really like using it.

---

### Post by stinkeye on 2012-03-14
Comment out the lines calling scripts, one at a time and see which one if any is causing it.
Running conky in the terminal may give a hint.
```
conky -c /path/to_your/config
```


Try running conky with the default config as well
```
conky -c /etc/conky/conky.conf
```

---

### Post by wpwend42 on 2012-03-14
Okay, running the default is not causing any overheating. Does that mean it is one of the scripts?

---

### Post by stinkeye on 2012-03-14
> **wpwend42 said:**
> Okay, running the default is not causing any overheating. Does that mean it is one of the scripts?
Possibly.
What scripts are you running?

---

### Post by wpwend42 on 2012-03-14
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
# fiddle with window
use_spacer yes
use_xft yes
# Update interval in seconds
update_interval 0.5
# Minimum size of text area
minimum_size 180 0
# Draw shades?
draw_shades yes
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
# Stippled borders?
stippled_borders 8
# border margins
border_margin 4
# border width
border_width 1
# minimum size
minimum_size 0 780
# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white
own_window_colour brown
own_window_transparent yes
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
# Gap between borders of screen and text
gap_x 10
gap_y 10
override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8
short_units on
# stuff after 'TEXT' will be formatted on screen
TEXT
DATE ${hr 2}
${alignc 60}${font Arial Black:size=26}${time %H:%M:%S}${font}
${alignc}${time %A %d %B %Y}
DISKS ${hr 2}
HOME: ${fs_free /home}/${fs_size /home}${alignr}${fs_bar 10,120 /home}
NOW PLAYING ${hr 2}
${alignc}${exec conkyBanshee --datatype=AR}
${alignc}${exec conkyBanshee --datatype=TI}
${alignc}${exec conkyBanshee --datatype=AL} (${exec conkyBanshee --datatype=YR})
${alignc}${exec conkyBanshee --datatype=PT} / ${alignc}${exec conkyBanshee --datatype=LE}
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}q${font} Uptime: ${alignr}${uptime}
${font StyleBats:size=16}A${font} CPU1: ${freq_g cpu1} GHz ${cpu cpu1}% ${alignr}${cpugraph cpu1 20,120 000000 ff0000}
${font StyleBats:size=16}A${font} CPU2: ${freq_g cpu2} GHz ${cpu cpu2}% ${alignr}${cpugraph cpu2 20,120 000000 00ff00}
HIGHEST CPU ${hr 2}
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}
HIGHEST MEM ${hr 2}
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}

---

### Post by stinkeye on 2012-03-14
The only scripts I can see running are conkyBanshee.
You have a number of exec calls for conkyBanshee running every 0.5 seconds.
Try using a template file to generate output in one call.

See [**_[COLOR="DarkRed"]Conky Banshee Python Script[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1223883")



...and maybe change 
```
update_interval 0.5
```
to
```
update_interval 1
```

---

### Post by QIII on 2012-03-14
Did you try to run your conkyrc with the calls to conkyBanshee one at a time as stinkeye suggested?

If that is the conkyBanshee from the Conky Companions PPA, it doesn't seem likely to me that those could be the problem.

Some time ago I did a "How much conky is too much conky" conky and used some things from that PPA.  Even with a bunch of stuff and a lua that drew about 18 gauges, I got up to 2% CPU use by the time I added the kitchen sink.

---

### Post by wpwend42 on 2012-03-14
Whoa, changing the update interval seems to have done it!

---

### Post by wpwend42 on 2012-03-14
I can't remember where I got the banshee template...somewhere online (well, obviously). 

The problem seems to have corrected itself by changing the interval from .5 to 1

---

### Post by QIII on 2012-03-14
Good deal.  Stinkeye's suggestion was a home run.  I've never had a problem like that, but I use bash scripts I create.

It could be that the calls to conkyBanshee didn't complete during each cycle and started stacking up.

---

### Post by stinkeye on 2012-03-14
It seems you got it fixed.Good
I was playing around with your conkyconfig and instead of letting it go to waste I'll post it for you to have a look at.
I put conkyBanshee to the bottom and only shows when banshee is running.
It uses the sample template @ /usr/share/conkybanshee/example/conkyBanshee.template
Not sure if it works, I've been uninstalling Banshee and mono for years.
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
 # Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 # fiddle with window
use_spacer right
use_xft yes
 # Update interval in seconds
update_interval 1
 # Minimum size of text area
minimum_size 180 0
 # Draw shades?
draw_shades yes
 # Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 # Stippled borders?
stippled_borders 8
 # border margins
border_inner_margin 5
border_outer_margin 6
minimum_size 0 780
 # Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white
own_window_colour brown
own_window_transparent yes
 # Text alignment, other possible values are commented
 #alignment top_left
alignment top_right
 #alignment bottom_left
 #alignment bottom_right
 # Gap between borders of screen and text
gap_x 10
gap_y 10
override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8
short_units yes

color1 green 
color3 orange
 # stuff after 'TEXT' will be formatted on screen
TEXT
DATE ${hr 2}
${alignc 60}${font Arial Black:size=26}${time %H:%M:%S}${font}
${alignc}${time %A %d %B %Y}
DISKS ${hr 2}
    HOME: ${fs_free /home}/${fs_size /home}${alignr}${fs_bar 10,120 /home}
#${alignc}${exec conkyBanshee --datatype=TI}
#${alignc}${exec conkyBanshee --datatype=AL} (${exec conkyBanshee --datatype=YR})
#${alignc}${exec conkyBanshee --datatype=PT} / ${alignc}${exec conkyBanshee --datatype=LE}
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}q${font} Uptime: ${alignr}${uptime}
${font StyleBats:size=16}A${font} CPU1: ${freq_g cpu1} GHz ${cpu cpu1}% ${alignr}${cpugraph cpu1 20,120 000000 ff0000}
${font StyleBats:size=16}A${font} CPU2: ${freq_g cpu2} GHz ${cpu cpu2}% ${alignr}${cpugraph cpu2 20,120 000000 00ff00}
HIGHEST CPU ${hr 2}
${color ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}
HIGHEST MEM ${hr 2}
${color ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}
NOW PLAYING ${hr 2}
${if_running banshee}${execp conkyBanshee --template=/usr/share/conkybanshee/example/conkyBanshee.template}${font}${color}${else}${alignc}Play some Music${endif}
```

---

