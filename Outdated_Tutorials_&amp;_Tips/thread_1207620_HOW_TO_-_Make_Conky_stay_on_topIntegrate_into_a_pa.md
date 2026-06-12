---
title: "HOW TO - Make Conky stay on top/Integrate into a panel"
date: 2009-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by kpkeerthi on 2009-07-08
Ever wondered how to make conky stay on top, so even maximized windows do not cover it up? Here is a neat trick.

**_Summary:_**
1. Position conky at the top, horizontally aligned to center.
2. Overlay fbpanel on top of conky.
3. Use compiz to adjust fbpanel's transparency so it lets you see through making conky visible.

fbpanel is, well, a panel and therefore maximized windows do not cover it up. The transparent panel protects conky from being hidden by other application windows including the maximized ones.

I chose fbpanel as I find it to be the lightest among the lightweight panels - implemented in C/GTK. 

1. Install required packages:
```

sudo apt-get update
sudo apt-get install fbpanel compizconfig-settings-manager

```

2. Create a blank fbpanel profile.
```

gedit ~/.fbpanel/default

```
Copy paste the below contents, Save & Exit gedit.
```

Global {
    edge = top
    allign = center
    margin = 0
    widthtype = percent
    width = 70
    heighttype = pixel
    height = 22
    roundcorners = false 
    transparent = false
    tintcolor = #ffffff
    alpha = 75
}

```

3. I use the following conkyrc file, so that it appears at the top, spread out horizontally, as shown in the screenshot below. (As you can see, a terminal window covers it partially, which we will fix in a moment)
[INDENT][[img]http://xs541.xs.to/xs541/09283/before770.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs541&d=09283&f=before770.png)[/INDENT]
```

background yes
use_xft yes
xftfont denmark:size=7
xftalpha 0.8
out_to_console no
update_interval 3.0
total_run_times 0
draw_shades no


own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

minimum_size 1250
maximum_width 1250

double_buffer yes
default_color 482C16
color1 DDBBAA

alignment top_middle
gap_y 5
no_buffers yes

TEXT
${color}KERNEL: ${color1}$kernel     ${color}UPTIME: ${color1}$uptime     ${color}CPU: ${color1}${cpu cpu0}% - ${freq}MHz - ${acpitemp} deg.  ${color}RAM: ${color1}${mem} - $memperc%     ${color}SWAP: ${color1}${swap} - $swapperc% ${color}     DISK: /home ${color1}${fs_free /home} free   ${color}/ ${color1}${fs_free /} free     ${color}NETWORK: ${color1} ${wireless_essid eth1}  (${wireless_link_qual_perc eth1}%) - ${downspeed eth1} kb/s down - ${totaldown eth1} total / ${color1}${upspeed eth1} kb/s up - ${totalup eth1} total

```

4. Open a terminal window and enter **fbpanel**. This will launch fbpanel and position it at the top.It would completely hide conky behind, as in the screenshot below. Notice the terminal window pushed down a bit!
[INDENT][[img]http://xs541.xs.to/xs541/09283/opaque-fbpanel572.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs541&d=09283&f=opaque-fbpanel572.png)[/INDENT]

5. Now open CCSM (System -> Preferences -> CompizConfig Settings Manager). Enable the **Opacity, Brightness and Saturation** plugin. Select the plugin, under **Opacity** tab, **Window Specific settings**, click **New**. Enter **fbpanel** for 'Windows' and **0** for 'values'. 

Watch conky emerging from behind and standing out and on top of all windows as shown in the screenshots below.
[INDENT][[img]http://xs541.xs.to/xs541/09283/after-1991.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs541&d=09283&f=after-1991.png) [[img]http://xs541.xs.to/xs541/09283/after-2-maximized434.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs541&d=09283&f=after-2-maximized434.png)[/INDENT]

6. If everything turns out well, add **conky** and **fbpanel** to System -> Preferences -> Startup Applications. I use the the following script for this:
```

#! /bin/bash

sleep 15 && /usr/bin/conky && sleep 2 && /usr/bin/fbpanel

```
**NOTE:** The above startup order is important. If fbpanel starts up first, conky will get pushed down below.

7. If you do not want compiz to draw shadows for conky, you may turn it off from CCSM -> Window Decoration. Under Shadow window, enter:
```

(any) & !class=Conky 

```

Have fun.
- Keerthi

---

### Post by jpeddicord on 2009-07-11
Approved. I might have to try this one out soon, been meaning to take a look at Conky. Thank you for your Tutorials & Tips contribution!

---

### Post by Phobiac on 2009-09-19
I'm having trouble getting this to work. Despite the two options to make it a dock and keep maximized windows below it being on, everything maximizes past it anyway. Anyone have a clue why?

Edit: Never mind, it turns out I had own_window_type set to panel in my conky config. Setting it to desktop made this work. Thank you!

---

### Post by Quick Silver on 2009-10-01
You can also do this with lxpanel if you are using lxde or if you would like to use the panel. Simply create new panel for the top align it to the left or the right and go to /home/user/.config/lxpanel/LXDE/panels/top and edit 

Global {
    edge=bottom
    allign=left
    margin=0
    [COLOR=Red]widthtype=percent[/COLOR]
    [COLOR=Red]width=100[/COLOR]
    height=31
    [COLOR=Red]transparent=255[/COLOR]
    tintcolor=#000000
    alpha=255
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=0
    fontcolor=#000000
    background=0
    iconsize=25
}

[COLOR=Red]To[/COLOR]

Global {
    edge=bottom
    allign=left
    margin=0
    [COLOR=Red]widthtype=pixel[/COLOR]
   [COLOR=Red] width=1[/COLOR]
    height=31
   [COLOR=Red] transparent=0[/COLOR]
    tintcolor=#000000
    alpha=255
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=0
    fontcolor=#000000
    background=0
    iconsize=25
}

Then of course change the height of the panel to the hight of conky.

---

### Post by GaaraOfDSand on 2010-01-13
Thanks, all the google pages told you how to make conky at the bottom, it was hard to find, and I was only missing this line:

own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

Thanks a lot. =)

---

### Post by VCoolio on 2010-01-13
If you want conky on top of a non-transparant (gnome-)panel, you'll notice that despite the conky own_window_hints above setting gnome-panel will be stubborn and on top of anything (at least this was the case in jaunty). If you're struggling with this you can use devilspie to place conky on top.

(if 
  (is (application_name) "conky") 
  (above)
)

---

### Post by GaaraOfDSand on 2010-01-13
Thanks for the reply, but I'm happy with the outcome now.. =)

It even integrates with the wallpaper so it has a transparent background.

---

