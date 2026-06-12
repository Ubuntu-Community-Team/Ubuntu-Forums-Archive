---
title: "WiFi signal strength display please ?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by Innernet on 2013-06-20
Hi.
What application should I chose to display the signal strenght of the wifi on my laptop running 12.04 ?
The wifi internet connection comes in via a USB port; from a Ralink 802.11n WLAN like this:
[http://www.crucialwifi.co.uk/Alfa_Network_AWUS036NH_BGN_WIRELESS_NETWORK_USB_2000mw_33_dBmRALINK_RT3070_CHIPSET/p740998_6834595.aspx](http://www.crucialwifi.co.uk/Alfa_Network_AWUS036NH_BGN_WIRELESS_NETWORK_USB_2000mw_33_dBmRALINK_RT3070_CHIPSET/p740998_6834595.aspx)

During summer, time of the day, temperature and vegetation growth diminishes the link capability in my remote forest location and would like to monitor variations.  I know there is a few options but do not have the knowledge to choose which would work for 12.04 and via the USB port, if that matters.
Thanks

---

### Post by Kopkins on 2013-06-21
You can use conky. You can install it via command line with sudo apt-get install conky or through the software center. 

Here's a copy of my conky config which will display the wifi quality near the bottom. Start messing around with stuff until you have something you like. you can find information on the various conky objects here [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) 

copy and paste this into a file and save it as .conkyrc in your home folder. 

```

background no
font ubuntumono:size=10
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color green}${font style=bold}SYSTEM${font} ${hr 1}${color}
$sysname $kernel $alignr $machine
Host: $alignr$nodename
Uptime: $alignr$uptime

${font style=bold}Ram${font} ${alignr}$mem / $memmax ($memperc%)
${membar 4}

${color green}${font style=bold}Processors ${font}${hr 1}${color}
CPU 1: ${cpu cpu1}% 
${freq_g 1} Ghz$
${cpubar cpu1 10,107}
${cpugraph cpu1 10,107}

${goto 40}${top name 1} ${goto 120}${top cpu 1}${alignr }${top mem 1}
TOP${goto 40}${top name 2} ${goto 120}${top cpu 2}${alignr }${top mem 2}
${goto 40}${top name 3} ${goto 120}${top cpu 3}${alignr }${top mem 3}

${color green}${font style=bold}Filesystem${font} ${hr 1}${color}
Root: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_used /home} / ${fs_size /home}
${fs_bar 4 /home}

${color green}${font style=bold}NETWORK${font} ${hr 1}${color}
IP local: $alignr ${addr wlan0}
IP public: $alignr ${execi 600 curl ifconfig.me}
wifi quality: ${wireless_link_qual_perc wlan0}%${alignr}${wireless_link_qual wlan0} / ${wireless_link_qual_max wlan0}

Down ${downspeed wlan0} / s ${alignr}Up ${upspeed wlan0} / s
${downspeedgraph wlan0 10,107} ${alignr}${upspeedgraph wlan0 10,107}
```

good luck!

Kopkins

---

### Post by mastablasta on 2013-06-21
you can also try wicd: [http://wicd.sourceforge.net/screenshot.php](http://wicd.sourceforge.net/screenshot.php)

how do you need the strength displayed? 

conky is for sure another way of displaying the info you need on desktop.

---

### Post by Zill on 2013-06-21
> **Innernet said:**
> What application should I chose to display the signal strenght of the wifi on my laptop running 12.04 ?...
If you are using the default "network-manager" then simply hovering over the applet should show the current signal strength.

To graph signal strength historically and/or to see other access points (including different channels) I recommend [iwScanner]("http://kuthulu.com/iwscanner/").

---

### Post by kurt18947 on 2013-06-21
Another option is wavemon, found in the repositories.  It runs in a terminal and seems very light. When run with sudo privileges will scan for networks and tell what encryption (if any) is being used.

---

### Post by BrunoLotse on 2013-06-21
Yet another option is nm-tool, iwconfig, bmon and another, and another... Cheers,Bruno

---

### Post by Innernet on 2013-06-21
Thanks to all.
For my poor skills level, decided to install linSSID 2.0; seems to work fine and does what I was after.

---

### Post by Rebelli0us on 2013-06-21
Install hardinfo, run gui and go to Network > Interfaces, wlan has live info on signal strength.

---

