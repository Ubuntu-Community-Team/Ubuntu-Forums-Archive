---
title: "conkey icon problem"
date: 2009-02-17
forum: Philippine Team
---

### Post by detorresrc on 2009-02-17
Bakit kaya hindi icon yung lumabas dun sa conky ko, help naman. Eto nga pala yung .conkyrc ko.

# Use Xft?                                                           
use_xft yes                                                          
xftfont DejaVu Sans:size=8                                           
xftalpha 0.8                                                         
text_buffer_size 2048                                                

# Update interval in seconds
update_interval 1           

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.                                   
total_run_times 0                                               

# Create own window instead of using desktop (required in nautilus)
own_window yes                                                     
own_window_transparent yes                                         
own_window_type override                                           
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager 

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes                                                  

# Minimum size of text area
minimum_size 180 0         
#maximum_width 200         

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no 

# Draw borders around text
draw_borders no           

# Stippled borders?                                                                                                                                                                                        
stippled_borders 0                                                                                                                                                                                         
                                                                                                                                                                                                           
# border margins                                                                                                                                                                                           
border_margin 5                                                                                                                                                                                            

# border width                                                                                                                                                                                           
border_width 1                                                                                                                                                                                           

# Default colors and also border colors
default_color white                    
#default_shade_color black             
#default_outline_color white           
own_window_colour white                

# Text alignment, other possible values are commented
#alignment top_left                                  
alignment top_right                                  
#alignment bottom_left                               
#alignment bottom_right                              

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35                                  
gap_y 50                                  

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
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU0: ${cpu cpu0}% ${alignr}${cpubar 8,60 cpu0}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar 8,60 cpu1}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}

${font Pie charts for maps:size=14}7${font}   ${voffset -5}WINDOW_C:
${voffset 4}${fs_free /mnt/WINDOWS_C}/${fs_size /mnt/WINDOWS_C} ${alignr}${fs_bar 8,60 /mnt/WINDOWS_C}

${font Pie charts for maps:size=14}7${font}   ${voffset -5}WINDOW_D:
${voffset 4}${fs_free /mnt/WINDOWS_D}/${fs_size /mnt/WINDOWS_D} ${alignr}${fs_bar 8,60 /mnt/WINDOWS_D}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan1} kb/s ${alignr}${upspeedgraph wlan1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan1} kb/s ${alignr}${downspeedgraph wlan1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan1}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan1}% ${alignr}${wireless_link_bar 8,60 wlan1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan1}
${voffset -8}${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 600 conkyEmail --servertype=IMAP --servername=imap.gmail.com --username=detorresrc --password=xxxxxxxx --ssl}${font} New email(s)
${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

WEATHER ${hr 2}
${if_existing /proc/net/route wlan1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=RPXX0017 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=RPXX0017 --datatype=HT}${font}

${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=RPXX0017 --datatype=HM}
${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}

---

### Post by killer_d76 on 2009-02-17
go to this link bossing and download the file.. ;)

[http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328](http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328)

---

### Post by detorresrc on 2009-02-17
yehey ok n, killer_d76 salamat ha. :p

---

