---
title: "lsb_release -c output usage"
date: 2011-01-14
forum: Programming Talk
---

### Post by Cypher2 on 2011-01-14
Hello everyone,

I have very rudimentary knowledge on using command output as a variable.

I'm trying to use lsb_release -c output to generalize the writing of apt sources that require the codename parameter in a script I made.

unfortunately, the way I have been using it writes the whole output as "Codename:  maverick" instead of just "maverick".

here is the piece of script:

--------------------------------
#! /bin/bash

RELEASE=$(lsb_release -c)

cd /etc/apt

echo "" >> sources.list
echo "# Dropbox #" >> sources.list
echo "" >> sources.list
echo "deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) $RELEASE main" >> sources.list

sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E

--------------------------------------------------------

how can I force only the use of the codename itself and not the whole command output to the $RELEASE variable in the source?

Thanks for any help you can provide :)

---

### Post by sisco311 on 2011-01-14
Use the --short option:
```
lsb_release -cs
```

and instead of echoing each line separately use a here-document:
```
cat << EOF >> /etc/apt/sources.list.d/dropbox.list
line 1
next line
and so on...
EOF
```

EDIT:
Oh, and don't edit the sources.list file. Create a new one in /etc/apt/sources.list.d/

---

### Post by Cypher2 on 2011-01-14
thank you very much.

please explain the "EOF"

---

### Post by Cypher2 on 2011-01-14
thank you very much.

please explain the "EOF"

---

### Post by sisco311 on 2011-01-14
See:
[http://mywiki.wooledge.org/BashGuide/InputAndOutput#Heredocs_And_Herestrings](http://mywiki.wooledge.org/BashGuide/InputAndOutput#Heredocs_And_Herestrings)
and of course the man page:
```
man bash | less +/"Here Documents"
```

---

### Post by Cypher2 on 2011-01-19
I've read the wiki and man but the output stream does not redirect to a file when i test it...

example:


#!/bin/bash
cd /home/nathael
touch .conkyrc
cat << EOF >> /home/nathanel/.conkyrc
background yes
update_interval 1
cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius
double_buffer yes
no_buffers yes
text_buffer_size 2048
gap_x 10
gap_y 30
minimum_size 190 450
maximum_width 190
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment tr
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no
default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 EF5A29
lua_load ~/.conky.lua
lua_draw_hook_post main
#${voffset 35}
#${goto 95}${color3}${font ubuntu:size=32}${time %e}${color1}${voffset 0}${offset -60}${font ubuntu:size=10}${time %A}
#${goto 85}${color2}${voffset -2}${font ubuntu:size=9}${time %b}${voffset -2} ${color3}${font ubuntu:size=12}${time %Y}${font}
#
#${voffset 70}
TEXT
${voffset 35}
${goto 95}${color4}${font ubuntu:size=22}${time %e}${color1}${offset -50}${font ubuntu:size=10}${time %A}
${goto 85}${color2}${voffset -2}${font ubuntu:size=9}${time %b}${voffset -2} ${color3}${font ubuntu:size=12}${time %Y}${font}
${voffset 80}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}CPU
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${top name 1}${alignr}${top cpu 1}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color2}${top name 2}${alignr}${top cpu 2}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color3}${top name 3}${alignr}${top cpu 3}%
${goto 90}${cpugraph 10,100 666666 666666}
${goto 90}${voffset -10}${font Ubuntu:size=7,weight:normal}${color}${threads} process 
${voffset 20}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}MEM
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${top_mem name 1}${alignr}${top_mem mem 1}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color2}${top_mem name 2}${alignr}${top_mem mem 2}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color3}${top_mem name 3}${alignr}${top_mem mem 3}%
${voffset 15}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}HDD
${goto 90}${diskiograph 30,100 666666 666666}${voffset -30}
${goto 90}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /home} /home
${goto 90}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /} /
${voffset 10}
${goto 70}${font Ubuntu:size=20,weight:bold}${color3}NET${alignr}${color2}${font Ubuntu:size=7,weight:bold}${color1}${if_up eth0}eth ${addr eth0} ${endif}${if_up wlan0}wifi ${addr wlan0}${endif}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}open ports: ${alignr}${color2}${tcp_portmon 1 65535 count}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}${offset 10}IP${alignr}DPORT
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  0}${alignr 1}${tcp_portmon 1 65535 rport  0}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  1}${alignr 1}${tcp_portmon 1 65535 rport  1}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  2}${alignr 1}${tcp_portmon 1 65535 rport  2}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  3}${alignr 1}${tcp_portmon 1 65535 rport  3}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  4}${alignr 1}${tcp_portmon 1 65535 rport  4}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  5}${alignr 1}${tcp_portmon 1 65535 rport  5}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  6}${alignr 1}${tcp_portmon 1 65535 rport  6}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  7}${alignr 1}${tcp_portmon 1 65535 rport  7}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  8}${alignr 1}${tcp_portmon 1 65535 rport  8}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip  9}${alignr 1}${tcp_portmon 1 65535 rport  9}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 10}${alignr 1}${tcp_portmon 1 65535 rport 10}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 11}${alignr 1}${tcp_portmon 1 65535 rport 11}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 12}${alignr 1}${tcp_portmon 1 65535 rport 12}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 13}${alignr 1}${tcp_portmon 1 65535 rport 13}
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${tcp_portmon 1 65535 rip 14}${alignr 1}${tcp_portmon 1 65535 rport 14}
EOF

Am I doing it wrong?

Edit:

FILE=/path/to/file

cat > $FILE <<EOF
blablabla
EOF

---

### Post by Cypher2 on 2011-01-19
actually the output system works but it does not write anything to file..

how can I manage to make bash understand all the command lines as absolute instead of interpreting them?

Thanks for any help you can provide...

---

