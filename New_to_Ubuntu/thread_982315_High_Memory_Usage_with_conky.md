---
title: "High Memory Usage with conky"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by josko88 on 2008-11-14
Hi there,
I am a veteran of Windows OS so I turned to Linux as a fresh start with PCs and to learn more about them. I got (ATM) Hardy Heron 8.04 Ubuntu with GNOME and before I even heard about this distribution I saw effects of Compiz(Fusion), Docks, conky!!! etc. And after a few days I installed probably all for now and I'm looking at the terminal, getting used to it (IMHO rocks, can DL, install, everything in 1 line! lazy mans way!)

I have a AMD Athlon +1400 (1245MHz) proc, 1 GIG RAM, ATI 9000 SERIES GPU. And conky says I am using 95% (minimal value was 85%) of my RAM! Before I used conky I think it was 245Mb / 1 Gig = about 26% in idle.And CPU is ok with 8-10% usage in idle.

3 Questions I would like to be answered (sorry if already mentioned, tried search and I didnt find it):

[LIST=1]
[*]Why it my RAM usage high? And can it be fixable w/o removing conky?
[*]What can I except to get out of Compiz/Fusion with my current bad PC?
[*]Does Ubuntu take full advantage of Multicored procs? (ie. quad-core)
[/LIST]

Thank you for reading! Please do answer.

conky: [[IMG]http://img128.imageshack.us/img128/8371/screenshotix0.th.jpg[/IMG]](http://img128.imageshack.us/my.php?image=screenshotix0.jpg)[[IMG]http://img128.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by taurus on 2008-11-14
Open a terminal and see which process "eats" up your memory.

Applications -> Accessories -> Terminal
```
top
```

---

### Post by markjensen on 2008-11-14
Not sure if conky is using the RAM, or if something else.

What are the results from **top**?   It defaults to CPU usage, to select the next column to the right, use the ">" key (shift + .).  What is reported at the top of top?

If you think it is conky, posting your .conkyrc file will help, especially if your file calls external scripts with execi or such.

---

### Post by josko88 on 2008-11-14
Well uses a script for Gmail (as far as I configured it).
```
background yes
    use_xft yes
    xftfont 123:size=8
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
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 1
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT
    
    ${font openlogos:size=20}Ma&#353;in ${font Arial:size=20}${color Tan1}${color Ivory}LINUX${font openlogos:size=20}

    ${voffset -90}
    ${color DimGray}
    ${font}
    ${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
    $font${color DimGray}$sysname $kernel $alignr $machine
    AMD Athlon 1400+$alignr${freq_g cpu0}Ghz
    Uptime $alignr${uptime}
    File System $alignr${fs_type}

    ${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
    $font${color DimGray}CPU  ${cpu cpu1}% ${cpubar cpu1}

    ${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
    $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar

    ${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
    $font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}
    /disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
    ${fs_bar /media/disk}

    ${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
    ${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
    $font${top_mem name 3}${alignr}${top mem 3} %
    $font${top_mem name 4}${alignr}${top mem 4} %
    $font${top_mem name 5}${alignr}${top mem 5} %

    ${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
    $font${color DimGray}Download speed: $alignr ${downspeed eth0} kb/s
    Upload speed: $alignr ${upspeed eth0} kb/s

    Downloaded: $alignr  ${totaldown eth0}
    Uploaded: $alignr  ${totalup eth0}

    ${font Arial:bold:size=10}${color Tan2}GMAIL ${color DarkSlateGray}${hr 2}
    ${font}${color Ivory}
    ${font Arial:bold:size=14}dr.velma@gmail.com${font}${color}
    ${font Arial:bold:size=11}You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).


    $endif
```

I copied it from somewhere, probably a guide and removed most of stuff but added Gmail support. Also here is the SS of "top" command.

[[IMG]http://img73.imageshack.us/img73/9489/screenshot1yq6.th.png[/IMG]](http://img73.imageshack.us/my.php?image=screenshot1yq6.png)[[IMG]http://img73.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

Doesnt look like 900Mb in total :/

---

### Post by Idefix82 on 2008-11-14
You screen shot of the output from 'top' wasn't very conclusive because there it appears that you are using at most 10% of your RAM.

I wouldn't activate any special effects in compiz if I were you, only when you want to show off Ubuntu and convert somebody. With your specs the difference in performance will be noticeable.

Ubuntu supports multiple cores better than most Windows versions. To make full use of them (once you have them), install the 64 bit version, it is said to distribute the tasks more cleverly between the cores (and of course it uses RAM more efficiently if it's more than 3GB).

Oh, and welcome aboard!:)

---

### Post by josko88 on 2008-11-14
Dont get me wrong, I know PCs well and I know the problems of 32-bit OS. But thanks for info!

And I was just experimenting: on None visual effects I use 650MB ram? with Xorg using most (32MB). Wierd... (Also I use dual-boot win XP SP3 but I didnt use it since I installed Ubuntu)

EDIT: System Monitor says only 245.1 Mb used but conky and "top" command (and free -m) say 650Mb used?

---

### Post by taurus on 2008-11-14
Do you have any swap partition and how large is it?

```
free
```

---

### Post by Idefix82 on 2008-11-14
I didn't want to insult your intelligence :) I don't think it lies in the nature of things that the 64 bit version has better algorithms for spreading tasks over multiple cores than the 32 bit version so I mentioned it.
650MB RAM really seems like a hell of a lot. I have the suspicion that most of it is not really used, it's just not freed because there is no need to. In principle, I think that processes which are sleeping remain in RAM until this memory is needed, at which point they are written into SWAP. So I think you should be fine like that.

As a check, I just ran top and it said that almost 1GB of RAM was being used. But when I add up the percentages of the running processes, I get at most 400MB.

---

### Post by josko88 on 2008-11-14
> **taurus said:**
> Do you have any swap partition and how large is it?

```
free
```


Yes, I do, I heard about your swap being at least 2xRAM so its 2.48 Gigz! Used only 38Mb.

---

### Post by archeryguru2000 on 2009-03-02
> **taurus said:**
> Do you have any swap partition and how large is it?

```
free
```

I have a response to that comment.  What would make the output from the aforementioned command look like the below results?
```

$: free -m                                                                                                                              </home/cfile>
             total       used       free     shared    buffers     cached
Mem:          2978        795       2183          0         11        386
-/+ buffers/cache:        396       2582
Swap:            0          0          0

```

It is as if Ubuntu cannot recognize my swap partition.  However...
```
$: sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafcaafca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5473    43960848+   7  HPFS/NTFS
/dev/sda2            5474        5597      996030   82  Linux swap / Solaris
/dev/sda3            5598       11334    46082452+  83  Linux
/dev/sda4           11335       14593    26177917+  83  Linux

```

... it's there!

Any suggestions?
~~archery~~

---

### Post by archeryguru2000 on 2009-03-06
Ah Ha!  I've got it.  I followed these EXTREMELY simple steps from **_[COLOR="Blue"][this thread]("http://ubuntuforums.org/showthread.php?t=691986")[/COLOR]_**.

Issue the commands:
```

#: blkid
#: cat /etc/fstab

```
If the line on fstab (referring to swap) does not match the line from the block-id command, fstab needs to be edited.  Mine did not match... but now they do.  Thanks very much to PmDematagoda and cdtech for their posts.  =D>  Swap is on and activates on each boot up.

Thanks,
~~archery~~

---

