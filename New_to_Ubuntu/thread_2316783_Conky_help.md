---
title: "Conky help"
date: 2016-03-10
forum: New to Ubuntu
---

### Post by keenoheb2010 on 2016-03-10
[FONT=verdana]When I try to run conky [1.10] I get this error[/FONT]
```
conky: desktop window (1e0000a) is subwindow of root window (49b)
conky: window type - normal
conky: drawing to created window (0x2e00002)
```
[FONT=verdana]Any idea what it means or how to fix it? Here is my .conkyrc:[/FONT]
```
conky.config = {
use_xft = true,
font = '123:size=8',
xftalpha = 0.1,
update_interval = 1,

own_window = true,
own_window_type = 'normal',
own_window_transparent = false,
own_window_hints = 'undecorated,sticky,below,skip_taskbar,skip_pager',
own_window_argb_visual = true,
own_window_argb_value = 0,

--own_window = false,
--own_window_type = 'override',
--own_window_transparent = true,
--own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
double_buffer = false,

alignment = 'top_left',
gap_x = 60,
gap_y = 300,
minimum_width = 250,
minimum_height = 200,
maximum_width = 750,

draw_shades = false,
draw_outline = false,
draw_borders = false,

no_buffers = true,
cpu_avg_samples = 2,
net_avg_samples = 1,
override_utf8_locale = true,

color0 = 'EAEAEA',
color1 = 'FFA300',
};

conky.text = [[
    ${voffset 10}${color0}${font GE Inspira:pixelsize=120}${time                     %H:%M}${font}${voffset -84}${offset       10}${color1}${font GE Inspira:pixelsize=42}${time %d} ${voffset -15}${color0}${font GE Inspira:pixelsize=22}${time  %B} ${time      %Y}${font}${voffset 24}${font GE Inspira:pixelsize=58}${offset -148}${time %A}${font}
${voffset 1}${offset 12}${font Ubuntu:pixelsize=10}${color1}HD ${offset 9}$color${fs_free /} / ${fs_size /}${offset     30}${color1}RAM ${offset 9}$color$mem / $memmax${offset 30}${color1}CPU ${offset 9}$color${cpu cpu0}%
]];
```

---

### Post by vasa1 on 2016-03-10
> **keenoheb2010 said:**
> [FONT=verdana]When I try to run conky [1.10] I get this error[/FONT]
```
conky: desktop window (1e0000a) is subwindow of root window (49b)
conky: window type - normal
conky: drawing to created window (0x2e00002)
```
[FONT=verdana]Any idea what it means or how to fix it? Here is my .conkyrc:[/FONT]
```
conky.config = {
...
};

conky.text = [[...
]];
```

Some points probably unrelated to your real problem: 
with 1.10, conky can use *~/.config/conky/conky.conf* rather than *~/.conkyrc*
there's no need, I think for the ; after } in the configure section and ; after ]] in the text section.

---

### Post by deadflowr on 2016-03-11
What error?

---

