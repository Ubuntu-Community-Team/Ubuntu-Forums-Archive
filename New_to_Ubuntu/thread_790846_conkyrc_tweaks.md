---
title: "conkyrc tweaks"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by armyben on 2008-05-11
Hi all I've been playing around with conkyrc and managed to get it all working to my satisfaction apart from one small thing; where I have my root and home disk usage listed, they are both the same size. I've had a look at other peoples conkyrc files but they seem to be the same as mine. Any ideas?



# Conky Ubuntu 7.10 configuration
#
# by XXXX
# 
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list of variables.

# set to yes if you want Conky to be forked in the background
background no

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

# Xft font when Xft is enabled
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
# own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 5 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

dexter_client no
dexter_server no
# config file for libdexter (default search path: $HOME/.dexterrc; /etc/libdexter/dexter.conf)
#dexter_config

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color slate grey}System: ${color}Daddy Cool
${color slate grey}Kernel: ${color }$kernel

${color slate grey}UpTime: ${color }$uptime

${color light blue}   CPU Load ${hr 1}

${color slategrey}Core 1: ${color lightgrey}${cpubar cpu1}  
${color slategrey}Core 2: ${color lightgrey}${cpubar cpu2}  

${color light blue}   System ${hr 1}

${color slate grey}Average Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes 
${color slate grey}Running: ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${color slate grey}MEM: ${color } $memperc% $mem/$memmax
${membar 3,165}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,165}

${color slate grey}ROOT  $color${fs_used /}  /${fs_size /} ${fs_bar /}
${color slate grey}HOME  $color${fs_used /home} /${fs_size /home} ${fs_bar /home}

${color slate grey}Disk I/O:  ${color}${diskio}B/s
${diskiograph 20,165}

${color light blue}   Network ${hr 1}

${color slate grey}Down: ${color}${totaldown eth0} @ ${downspeed eth0}k/s
${downspeedgraph eth0 20,165 191970 87cefa}
${color slate grey}Up: ${color}${totalup eth0} @ ${upspeed eth0}k/s
${upspeedgraph eth0 20,165 191970 87cefa}[ATTACH]69698[/ATTACH]

---

### Post by armyben on 2008-05-11
I would put a screenshot up but I can't get it to wotrk :( I'll have to play I'm still learning :)

---

### Post by simon_w on 2008-05-19
your '/home' folder is definitely a separate partition, right...?

---

### Post by kerry_s on 2008-05-20
> **armyben said:**
> I would put a screenshot up but I can't get it to wotrk :( I'll have to play I'm still learning :)

press> print
for screenshot
or
in terminal:
sudo apt-get install scrot

scrot %T.png

---

