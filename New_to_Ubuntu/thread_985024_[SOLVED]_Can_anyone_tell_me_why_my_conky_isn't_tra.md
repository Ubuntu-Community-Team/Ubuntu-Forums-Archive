---
title: "[SOLVED] Can anyone tell me why my conky isn't transparent?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-11-17
Conky still has a black background.

I'm using KDE 4.1.3, Intrepid, and Compiz.  Here's my .conkyrc:

> 
alignment top_left
background no
border_width 1
cpu_avg_samples 2
default_color cornflowerblue
default_outline_color white
default_shade_color white
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
gap_x 25
gap_y 15 
maximum_width 330
max_port_monitor_connections 64
max_specials 512
max_user_text 16384
minimum_size 330 10
net_avg_samples 2
no_buffers yes
out_to_console no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal
own_window yes
stippled_borders 2
update_interval 2
uppercase no
use_spacer right
use_xft yes
xftalpha 0.8
xftfont  Penguin Attack:size=11

TEXT
${color #0077ff}$nodename     ${alignc}$sysname $kernel ${alignr}$color${time %l:%M:%p}

${color #0077ff}Uptime:$color $uptime ${color #0077ff} Load:$color $loadavg
${color #0077ff}CPU:$color ${cpu}% ${color #0077ff}${cpubar 5,85}   ${color #0077ff}Disk I/O: $color${diskio}
${color #0077ff}${cpugraph 0 32,155 104E8B 0077ff} $alignr${color #0077ff}${diskiograph 32,155 104E8B 0077ff 750}
${color #0077ff}RAM Usage:$color $mem${color #0077ff}/${color}$memmax - $memperc% ${color #0077ff}$membar
${color #0077ff}Swap Usage:$color $swap${color #0077ff}/${color}$swapmax - $swapperc% ${color #0077ff}${swapbar}
${color #0077ff}Entropy: ${color}${entropy_avail}${color #0077ff}/${color}${entropy_poolsize} ${color #0077ff}${entropy_bar}
${color #0077ff}Net Down:$color ${downspeed eth0} k/s      ${color #0077ff}Net Up:$color ${upspeed eth0} k/s
${color #0077ff}${downspeedgraph eth0 32,155 104E8B 0077ff} $alignr${color #0077ff}${upspeedgraph eth0 32,155 104E8B 0077ff}
${color #0077ff}File systems:
 ${color #0077ff}/          $color${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
 ${color #0077ff}/home      $color${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
 ${color #0077ff}/2ndDr    $color${fs_used /media/secondDrive}/${fs_size /media/secondDrive}${alignr}${color #0077ff}${fs_bar 5,120 /media/secondDrive}

${color #0077ff}Top Processes:
${color #0077ff}Name              PID     CPU%   MEM%
$color ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
$color ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
$color ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #0077ff}Mem usage
$color ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
$color ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
$color ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #5b6dad}Local Weather:
${color #7f8ed3}${execi 1800 /home/tarahmarie/Documents/Scripts/weather/weather.sh}




Also, here's the konsole output when I start Conky:

Conky: desktop window (1a00058) is subwindow of root window (13b)
Conky: window type - normal
Conky: drawing to created window (0x2000001)
Conky: drawing to double buffer

---

### Post by I wanted to leave on 2008-11-17
I used your template and it seems to be working fine here...

The attached screenshot is your code unchanged.

Perhaps look at compiz for some answers

cheers

---

### Post by tarahmarie on 2008-11-18
What might I be doing in Compiz that screws it up?

---

### Post by epswinde on 2008-11-18
Here's what I got from running your code in kubuntu 8.10 with no modifications.  I would imagine that this is the same issue you're getting?

I can't say why, I havent run conky since kde 3.5.  It does sit on top of my plasmoids and everything though, annoying

---

### Post by tarahmarie on 2008-11-18
Actually, I'm getting a solid black background.

Argh!  I just want conky to be transparent!

---

### Post by tarahmarie on 2008-11-18
There's the screenshot.

---

### Post by I wanted to leave on 2008-11-18
> **tarahmarie said:**
> Conky still has a black background.

I'm using KDE 4.1.3, Intrepid, and Compiz.  Here's my .conkyrc:



Also, here's the konsole output when I start Conky:

Conky: desktop window (1a00058) is subwindow of root window (13b)
Conky: window type - [COLOR="DeepSkyBlue"][COLOR="Red"]override[/COLOR][/COLOR]
Conky: drawing to created window (0x2000001)
Conky: drawing to double buffer

Change the above in red and see if it helps. Perhaps even disable compiz though it might be a kde thing
Cheers

---

### Post by tarahmarie on 2008-11-18
Ok, here is the output when I tried setting window_type override in .conkyrc

~ : Yes, Supreme Empress? $ conky
Conky: desktop window (1800038) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  273
  Current serial number in output stream:  274

---

### Post by tarahmarie on 2008-11-18
Holy cow!  I switched it back to window_type normal, and it's working--almost.  See the attachment--it's still shadowed somehow.

---

### Post by tarahmarie on 2008-11-18
Argh.  On reboot, it went back to a black background.

---

### Post by tarahmarie on 2008-11-18
ookay--I'm marking this one as solved; not because it is, but because I gave up.  Instead, I used a combination of nifty plasmoids to get the information I wanted.  I'm attaching a screenshot so that anyone who wants can see what I did.  I used about seven of the CommandWatch plasmoids available on KDE-Look; if anyone wants to know the structure of the commands or the settings I used, PM me.

---

### Post by epswinde on 2008-11-18
Hey, what program are you using to get that nifty transparent terminal on your desktop?

---

### Post by whitethorn on 2008-11-18
This might be a little late, but conky has to start after compiz, otherwise it doesn't work properly.  One way of testing if it works, is to start conky after your desktop has loaded completely, if it's transparent then that was the problem.  :)

---

### Post by tarahmarie on 2008-11-19
> **epswinde said:**
> Hey, what program are you using to get that nifty transparent terminal on your desktop?

Hey, epswinde:

I'm using Tilda.  It's in the repos.  Start tilda, then right click on it.  Go to Preferences in the context menu.  In the General tab, enable Display on all Workspaces (if you want it to) and Do not show in taskbar.  Enable Antialiasing as well so you can get your custom font.  Click on the appearance tab.  Fiddle with the height, width, and X & Y settings to get Tilda where you want it on the desktop.  Enable transparency, then set the Level of Transparency to 100.  Make sure the Use Image for Background isn't checked.  Then, go to the Colors tab, and set the text color to one that's contrasted with your current desktop wallpaper color scheme so you can see it.  Go to the Scrolling tab, disable the scrollbar.  Set scrollback to 1000-2000 lines, whatever you want tilda to retain as scrollback history.  Enable only the Scroll Background option--that's so you can use a mouse wheel to scroll back in tilda instead of having an ugly scrollbar next to your pretty transparent Tilda window.

Other than that, my bash shell addresses me respectfully as Supreme Empress cuz I told my bash_profile to do so.

---

### Post by epswinde on 2008-11-19
> **tarahmarie said:**
> 
Other than that, my bash shell addresses me respectfully as Supreme Empress cuz I told my bash_profile to do so.

Mine adresses me as Sir, as in "What is your Command, Sir?"
Its one of those little things that makes me love linux just that much more...

---

### Post by ramaswamyps on 2008-11-19
thanks for introducing tilda to me:)tarahmarie
it works very nicely
conky also works with transparecy .
i find ubuntu-8.10 work better in my laptop than my desktop comp.

does the transparency work without kde-4 installed??

---

