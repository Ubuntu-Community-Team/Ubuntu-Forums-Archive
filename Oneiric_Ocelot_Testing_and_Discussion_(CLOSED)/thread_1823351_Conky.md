---
title: "Conky"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-08-11
I can't seem to get conky running in gnome-shell.  It runs fine in unity.  I get no errors when I launch it.  Maybe I'm missing something?  Thanks

```
Conky: forked to background, pid is 1901
matthew@ocelot:~$ 
Conky: desktop window (1600019) is subwindow of root window (1ad)
Conky: window type - override
Conky: drawing to created window (0x2c00001)
Conky: drawing to double buffer

```

---

### Post by Quackers on 2011-08-12
A couple of the own_window entries need changing iirc for gnome-shell.
Post the contents of your .conkyrc, or at least the entries before the TEXT line.

---

### Post by mdhollis on 2011-08-12
Here it is:

```
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
color4 666666

lua_load ~/.conky/conky_grey.lua
lua_draw_hook_post main

```

---

### Post by Quackers on 2011-08-12
The only difference between my conkyrc and yours in respect of the own_window fileds is that one of your is set to
own_window_type override
and for gnome-shell mine is
own_window_type normal

Try that first then save the file.

---

### Post by mdhollis on 2011-08-12
Thanks Quackers, that did the trick.

---

### Post by Quackers on 2011-08-12
Aha! Nice one :-)
Please mark the thread as solved using Thread Tools near the top of the page.

---

