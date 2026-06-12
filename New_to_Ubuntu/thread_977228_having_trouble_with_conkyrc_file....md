---
title: "having trouble with conkyrc file..."
date: 2008-11-10
forum: New to Ubuntu
---

### Post by ja660k on 2008-11-10
hey guys i got this conky theme, its pretty cool. but it doesnt work, ive tried a few different ones.

but i keep getting the same error..

the rcfile is called theme1(no extension)

```

background yes
use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
xftalpha 0.8
out_to_console no
update_interval 1.0
total_run_times 0
own_window no
double_buffer yes
minimum_size 280 5
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 4
border_width 1
default_color black
default_shade_color black
default_outline_color black
alignment bottom_left
gap_x 5
gap_y 5
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer no

TEXT
    $hr
    ${color black}$nodename - $sysname $kernel on $machine ${pre_exec uname -p | sed -e 's/(R)//g'} Uptime:${color blue} $uptime ${color black}- Load:${color blue} $loadavg CPU Usage:${color red} $cpu%  ${color black}RAM Usage:${color blue}$mem/$memmax - $memperc% ${color black}Swap Usage:${color blue} $swap/$swapmax - $swapperc% $color Disk Usage: ${color blue} ${fs_used /bin/bash}/${fs_size /bin/bash} - ${fs_free_perc /bin/bash}% Free


```

and the error i get is...
```

john@ja660k-LinUx:~$ conky
Conky: missing text block in configuration; exiting
john@ja660k-LinUx:~$ 


```

what is wrong with im doing?

---

### Post by ad_267 on 2008-11-10
Your configuration file should be called .conkyrc and should be in your home directory. If you want to call your configuration file something else you can call conky like this:
```
conky -c ~/theme1
```
That assumes your configuration file is called theme1 and is in your home directory.

---

### Post by ja660k on 2008-11-10
sorry i should of said that, it is in a folder called .conkyrc

```

john@ja660k-LinUx:~$ cd ~/.conkyrc
john@ja660k-LinUx:~/.conkyrc$ ls
theme1

```

---

### Post by ad_267 on 2008-11-10
Edit: Duplicate post

---

### Post by ad_267 on 2008-11-10
That won't work. It has to be a file called .conkyrc. I moved my .conkyrc to .conkyrc.bak, made a directory called .conkyrc and then copied my .conkyrc over and called it theme1. Guess what error I got:

```
$ conky &
Conky: missing text block in configuration; exiting
```

---

