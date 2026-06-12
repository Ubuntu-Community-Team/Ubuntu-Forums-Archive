---
title: "Help with changing font in Conky"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by weegeekus on 2008-09-01
Hey there,

First I want to say how pleased I am that this is the first time I've had to post on the forums as so far my Ubuntu install has gone very smoothly and I've been able to solve any problems I've had quite quickly (usually with the help of these here forums). 

Anyways, for the last couple of days, I've been fiddling with Conky and learning as I go. The one thing I can't get it to do however is use the font 'URW Gothic Book L' (which is what I use as my system font). It will change to certain other fonts but I imagine this is to do with the type of font. I keep hearing about xft and xfontsel but I'm a bit lost to be honest. Can anyone point me to a good resource for learning about this or suggest a solution?

I've posted my .conkyrc if anyone feels like taking a look (fixing the weather display is my next project ;p).

Thanks for your time :D

background yes
    use_xft yes
    xftfont URW Gothic L Book:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_left
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 1024

    TEXT

    ${color #3CB3D1} ${font :size=30}$alignc${time %H:%M:%S}
    ${voffset -30}${font :bold:size=10}$alignc${time %d %b %Y} ${font :bold:size=10}$alignc${time %A}
    $endif

    ${voffset -30}
    ${color DimGray}
    ${font}
    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}System ${color #3CB3D1} ${hr 2}
    $font${color DimGray}$sysname $kernel $alignr $machine
    Intel Pentium D $alignr${freq_g cpu0}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}Processor ${color #3CB3D1}${hr 2}
    $font${color DimGray}CPU  ${cpu cpu1}% ${cpubar cpu1}
    
    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}Memory ${color #3CB3D1}${hr 2}
    $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}HDD ${color #3CB3D1}${hr 2}
    $font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}

    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}Top Processes ${color #3CB3D1}${hr 2}
    ${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
    $font${top_mem name 3}${alignr}${top mem 3} %
    $font${top_mem name 4}${alignr}${top mem 4} %
    $font${top_mem name 5}${alignr}${top mem 5} %

    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}Network ${color #3CB3D1}${hr 2}
    $font${color DimGray}IP on eth1 $alignr ${addr eth1}

    Down $alignr ${downspeed eth1} kb/s
    Up $alignr ${upspeed eth1} kb/s

    Downloaded: $alignr  ${totaldown eth1}
    Uploaded: $alignr  ${totalup eth1}

    ${font URW Gothic L Book:bold:size=10}${color #3CB3D1}Weather ${color #3CB3D1}${hr 2}
    ${font}${color DimGray}

    ${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast &#8211;location=UKXX0001 &#8211;datatype=WF}
    ${alignc 22}${voffset -40}${font URW Gothic L Book:bold:size=10}${color DimGray}${execi 1800 conkyForecast &#8211;location=UKXX0001 &#8211;datatype=HT}

---

### Post by billgoldberg on 2008-09-01
Sorry I can't help, but it's a nice bump.

--

I had the same thing with Conky, it would be able to use some fonts, but never the ones I really liked :p

---

### Post by weegeekus on 2008-09-01
Cheers indeed :D

And thanks for your .conkyrc - if I can make the modifications I want I'll post it the [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

