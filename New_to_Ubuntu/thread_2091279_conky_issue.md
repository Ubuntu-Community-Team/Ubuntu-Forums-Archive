---
title: "conky issue"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by rusty_jones on 2012-12-04
This is my conky_weather script that works. under the TEXT area I put a couple of lines that retrieve baseball standings when baseball is in season. That also works.

I'm also trying to do the standings for football.  the first line works. the second line is a copy of the baseball standings, so it should also work. I’ve changed the url to the football page, but it's not returning the standings.

 so here is the conky and the py files.

conky_weather

```

##############################################
#  Settings
##############################################
max_specials 10000
max_user_text 1500000
background no
use_xft yes
#xftfont Sans:size=12
#xftalpha 1
font Mono:size=8
total_run_times 0
own_window yes
own_window_argb_visual yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 600 680
maximum_width 700
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_left
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes
color1 86acad #darker blue
color2 b1c9c9 #lighter blue
text_buffer_size 100000
top_name_width 10
update_interval 1

lua_load ~/v9000/v9000.lua
lua_draw_hook_pre weather
lua_load ~/v9000/s11template.lua

TEXT

${voffset 550}${offset -06}${color  #EFEFEF}${font freemono:size=12} National Football League ${hr 1}
${voffset 10}${offset -24}${color   #EFEFEF}${font freemono:size=12}${exec home/rusty/.conky/football/standings_nfl.py}

#${voffset 530}${offset -06}${color  #CA1F2C}${font freemono:size=12} National League ${hr 1}
#${voffset 10}${offset -24}${color  #FFFFFF}${font freemono:size=12}${exec ~/.conky/baseball/standings_nl.py}

```

standings_nfl.py

```

#!/usr/bin/env python
import os
filename = "http://espn.go.com/nfl/standings | egrep -A20 'National Football League'"
cmd = os.popen("lynx -nonumbers -dump %s" % filename)
output = cmd.read()
cmd.close()
print output


```

---

