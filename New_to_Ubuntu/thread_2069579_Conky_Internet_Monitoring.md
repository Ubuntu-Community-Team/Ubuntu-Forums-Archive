---
title: "Conky Internet Monitoring??"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by MoralAnarchy on 2012-10-11
So I'm looking to find out how I put my internet address into my conky script so it displays on my desktop. The script I have is not my own creation, just one I grabbed off the huge conkyrc thread on this site so don't get confused thinking my noob self had anything to do with this.  Anyway if somebody could take a look and let me know what I need to do to get my internet address put in there that would be great.  Thanks!

Btw here's the full script:

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 2.0

# Minimum size of text area
# minimum_size 260 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font ms sans
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
#default_outline_color CCCCCC

own_window_colour white
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 38

# stuff after 'TEXT' will be formatted on screen

TEXT
$sysname $kernel on $machine
CPU: ${freq}MHz Uptime: ${uptime}   
CPU: $cpu%  ${color lightblue}$cpubar
${color}${cpugraph ffffff 676f9d}$color

${color lightblue}NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}
${top name 6} ${top pid 6}   ${top cpu 6}    ${top mem 6}

${color}Processes: $processes  Running: $running_processes

RAM ($memmax):   $memperc%   ${color lightblue}${membar 6}$color
Swap ($swapmax): $swapperc%   ${color lightblue}${swapbar 6}$color

Ubuntu:  ${fs_used_perc /}%                 ${fs_free /}/${fs_size /}  
${color lightblue}${fs_bar 6 /}$color
Home:    ${fs_used_perc /home}%                 ${fs_free /home}/${fs_size /home} 
${color lightblue}${fs_bar 6 /home}$color 
Elendil: ${fs_used_perc /elendil}%                 ${fs_free /elendil}/${fs_size /elendil}  
${color lightblue}${fs_bar 6 /elendil}$color
Elrond:  ${fs_used_perc /elrond}%                 ${fs_free /elrond}/${fs_size /elrond} 
${color lightblue}${fs_bar 6 /elrond}$color
Gandalf: ${fs_used_perc /gandalf}%                 ${fs_free /gandalf}/${fs_size /gandalf}  
${color lightblue}${fs_bar 6 /gandalf}$color

Internet Status (${addr eth0}):
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
$color${downspeedgraph eth0 25,140 ffffff 676f9d}   ${upspeedgraph eth0 25,140 ffffff 676f9d}$color 
${color}Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

---

### Post by MoralAnarchy on 2012-10-11
Never mind guys I figured this one out on my own with some research.  If anybody needs to know how to do this though I will tell you that it's pretty easy and here it is.
When I first copied and pasted the configuration script into my conkyrc file it had been set up for a wired ethernet connection which I was not running.  Since I am using a wifi connection I needed to change that in the script.  Here is the codes for the various internet options.

1) eth0 - built in ethernet
2) eth1 - Gigabit PC card for work
3) eth2 - Gigabit PC card for home
4) ppp0 -- verizon wireless card
5) wlan0 -- wireless lan (wifi)

I just went down to the bottom of the configuration file and changed where it said 'eth0' to 'wlan0' (without the quotes obv).
Anyway I'm feeling pretty proud of myself for troubleshooting that myself.  I hope this may help somebody else out down the road!

---

