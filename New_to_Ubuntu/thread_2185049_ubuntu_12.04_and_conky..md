---
title: "ubuntu 12.04 and conky."
date: 2013-10-31
forum: New to Ubuntu
---

### Post by swipisnt on 2013-10-31
hey guys!
ok just did some configuration of conky and looks like working but not like should. ok problem is this - that thing is MOVING! (lol) in this case somehow icons from desktop disapiering in same time when that thing moving :). look at the forums but nothing helps, maybe i too big nuub dunno. any advice?

---

### Post by Frogs Hair on 2013-10-31
The conky window placement may be interfering with the icons and you can change the position in the configuration .  You would be looking for like something like the following. The 12 and 48 are the number of pixels and can be changed as well as top_right depending on the configuration. ```
 alignment top_right
gap_x 12
gap_y 48
```

---

### Post by deadflowr on 2013-10-31
Re-alignment might help.
Post the conky config you're working on, and we might be able to tell you why it's jumping.
Double buffer improperly set, maybe?

---

### Post by swipisnt on 2013-11-01
oh and processor type sometimg showing sometimes not. when i gen mouse over icons place, icons apears but conky disapears, aftes update conky apears inons disapears, now looks like not moving any more. here is code:
```

alignment top_right
own_window no
own_window_hints undecorated,below,skip_taskbar
background no
double_buffer yes
use_spacer yes
use_xft yes
update_interval 2.5
minimum_size 200 200
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
uppercase no
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
own_window_transparent yes
alignment top_right
gap_x 10
gap_y 100
override_utf8_locale no
xftfont Terminus:size=8
#xftalpha 0.8
# ${execi 60 cal -3 | cut -c23-64}



TEXT
${color #b0b0b0}${alignr}${time %d - %m - %Y}
${color gray}${font Arial Black:size=25}${alignr}${time %A}
    
${color }${font Arial Black:size=8}${alignr}Ubuntu 12.04 Precise
${alignr}${kernel}${machine}

${color #b0b0b0}Processor: ${color }${alignr}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'| uniq | cut -c 1-26}
${color lightgrey}${tab 20}Freqency: ${color }${freq_g cpu0}Ghz
${color lightgrey}${tab 20}Load: ${color #ddaa00}${cpu}% ${alignr }${color }${cpubar 6,175}
${color lightgrey}${tab 20}Processes Running: ${color }${running_processes}
${color lightgrey}${tab 20}Processes Sleeping: ${color }${processes}
   
${color #b0b0b0}Memory:
${color }${tab 20}Real: ${memmax} total / ${mem} in use
${color lightgrey}${tab 20}Used: ${color #ddaa00}${memperc}% ${alignr}${color }${membar 6,175}
${color }${tab 20}Swap: ${swapmax} total / ${swap} in use
${color lightgrey}${tab 20}Used: ${color #ddaa00}${swapperc}% ${alignr}${color }${swapbar 6,175}

${color #b0b0b0}Disk: ${color }/dev/sda6 Ubuntu (ext4)
${color lightgrey}${tab 20}Total: ${color }${fs_size}
${color lightgrey}${tab 20}Used: ${color }${fs_used}${color lightgrey}${alignr}Available: ${color }${fs_free}
${color lightgrey}${tab 20}Free: ${color #ddaa00}${fs_free_perc}% ${tab 45}${color }${alignr}${fs_bar 6,175}

${color #b0b0b0}Network:
${color lightgrey}${tab 20}IP: ${color }${addr eth0}
 
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,125 000000 ff0000}  ${alignr}${upspeedgraph eth0 
25,125 000000 00ff00}$color

Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

```

---

### Post by swipisnt on 2013-11-01
looks like just one problem left. why sometime processor insformatios is showing sometimes not? here its code line:
```

${color #b0b0b0}Processor: ${color }${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'| uniq | cut -c 1-26}

```

---

### Post by Frogs Hair on 2013-11-01
See the own window type option at the link there are more option listed at the beginning of that section. 

 [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by swipisnt on 2013-11-01
i did many times looking at these variables :). i think need some time to get cpu model, coz when conky is show up in model place showig '(null)' after while show info what i want to see. thanks

---

