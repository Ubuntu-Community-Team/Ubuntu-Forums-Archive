---
title: "Conky Problem"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by jmittleider723 on 2013-12-12
So I just got my computer up and running with Ubuntu 12.04. I'm completely new to Ubuntu and Linux in general so I've just been messing around and
installing stuff to see how it all works. I'm trying to get conky to work but I get this message when I try to run it...

jesse@Jesse-Ubuntu:~$ conky
Conky: invalid configuration file '/home/jesse/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
jesse@Jesse-Ubuntu:~$ 

This is the code that is in /home/jesse/.conkyrc - conky.conf

Any ideas what's going wrong? When I first installed it, it worked without even creating a .conkyrc
directory. Then when I tried to make one and put a copy of conky.conf in it so I could mess with customizing
I got this error. So next I just went online and copied someone else's code to see if it works
instead. Still getting the same error. I'm stumped.


#####################################################################################################################
# Conky Configuration
# Compatible with Gnome2 and OpenBox
# Much of this config file was originally created by the folks at Dream Linux, I believe.
# I've modified this to suit my own needs.
# HilltopYodeler | [http://www.hilltopyodeler.com/blog](http://www.hilltopyodeler.com/blog) | [email]hilltopyodeler@gmail.com[/email]
#
# Conky Resources:
#  - Documentation: [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)
#  - FAQ: [http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)
#  - Formatting/Config Settings: [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)
#  - Variables/Arguments: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)
#  - ManPage: [http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)
#####################################################################################################################
#
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color black
default_outline_color black
default_color FFFFFF
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
minimum_size 160
maximum_width 160
# Gap between borders of screen and text
gap_x 14
gap_y 38


TEXT
 ${color FFFFFF}${font Helvetica:size=10}${time %A %b %d %Y}
${color FFFFFF}${font Helvetica:size=24}${time %H:%M} 
${color BDDBF6}${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth0} Kb/s 
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth0} Kb/s 

${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth0}
${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth0}

${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}
#
# ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

${font StyleBats:size=18}P${font}  Uptime:  ${uptime_short}


# ${color #F4C8E3}${font StyleBats:size=16}F${font}${font Helvetica:size=10}  Rhythmbox
# ${color white}${font Verdana:size=8}${execi 10 conkyRhythmbox --datatype=TI}
# ${execi 10 conkyRhythmbox --datatype=AR}
# ${execi 10 conkyRhythmbox --datatype=AL}
# ${execi 10 conkyRhythmbox --datatype=PT} / ${execi 1800 conkyRhythmbox --datatype=LE}

---

### Post by jmittleider723 on 2013-12-12
Ok,
Well I tried removing it and reinstalling again. This time deleting the .conkyrc directory I created earlier. Now it will run in stock form. As soon as I create a .conkyrc directory and copy over conky.conf it stops working. Made no modifications to the .conf file

---

### Post by stinkeye on 2013-12-12
Conky will use the config @ **~/.conkryrc**  ....a hidden text file in your home directory.
Installing conky does not install a config to your home folder. You must either create or download a config.
If **~/.conkryrc** doesn't exist, conky will use the sample config @  **/etc/conky/conky.conf**

If your config is at the correct location you should be able to view it with the terminal command....
```
gedit ~/.conkyrc
```
 

Alternatively when running conky, you can specify a config using the "**-c**" option.
eg (terminal command)
```
conky -c [COLOR="#696969"]/path/to/config[/COLOR]
```

When using "-c" your config can be named and located whatever and wherever you like.
eg I keep all my configs in **/home/glen/conky/configs** and name them for easy recognition....
```
conky -c /home/glen/conky/configs/gmail.conkyrc
```


For the config from your first post, make sure you have the fonts
[LIST]
[*]StyleBats
[*]PizzaDude Bullets
[/LIST]
Most fonts can be downloaded from [**_[COLOR="#B22222"]Dafont[/COLOR]_**]("http://www.dafont.com")

---

