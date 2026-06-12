---
title: "Move photo to desktop"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Jon Anderson on 2012-06-21
No matter what size I make a photo in Gimp ,Changing print size , canvas size or scale image size, when I move it to the desktop it is Icon size and Icons when enlarged loose all their definition
Any Ideas.

---

### Post by mike555 on 2012-06-21
are you trying to use picture as wallpaper?
 and what operating system?

---

### Post by Jon Anderson on 2012-06-21
> **mike555 said:**
> are you trying to use picture as wallpaper?
 and what operating system?
Ubuntu12:04, no I just want to move some picture about a quarter of my screen large.

---

### Post by philinux on 2012-06-21
> **Jon Anderson said:**
> Ubuntu12:04, no I just want to move some picture about a quarter of my screen large.

What does the image look like when you double click on the original from the file manager nautilus.

---

### Post by Jon Anderson on 2012-06-21
> **philinux said:**
> What does the image look like when you double click on the original from the file manager nautilus.
What is the file manager nautilus

---

### Post by Rodney9 on 2012-06-21
You will have to use viewer software to have it open at quarter size or some thing like risterrro or gpicview theres dozens of viewers in the Software Center.

For a desktop wallpaper it has to be the whole screen, or make a collage.

Nautilus is the file manager.
 

Rodney

---

### Post by d4m1r on 2012-06-21
What is the actual resolution of the image (pixel x pixel) and what is your desktop resolution?

---

### Post by sandraalvarez on 2012-06-21
Hey there, were you able to fix it? let u know your desktop resolution so we can figure out what to do.

---

### Post by Jon Anderson on 2012-06-22
> **sandraalvarez said:**
> Hey there, were you able to fix it? let u know your desktop resolution so we can figure out what to do.
1.4 MB (1,407,357 bytes) Thats the resolution of one of the photos that is icon size on the desktop . The desktop resolution  is 1152x864(4:3)

---

### Post by sandraalvarez on 2012-07-01
> **Jon Anderson said:**
> 1.4 MB (1,407,357 bytes) Thats the resolution of one of the photos that is icon size on the desktop . The desktop resolution  is 1152x864(4:3)

Thank you! Let me try that.

Thanks a lot!

---

### Post by stinkeye on 2012-07-02
Not too sure what you are trying to do?
If you want to display a picture on your desktop you could use conky.
```
sudo apt-get install conky-all
```

Save this as **deskimage.conkyrc**
```
background no
update_interval 30
total_run_times 0

use_xft yes
xftfont GE Inspira:bold:size=12
xftalpha 1.0
own_window yes
own_window_type override
own_window_transparent no
own_window_colour ECEEF4
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
#own_window_argb_visual yes
own_window_argb_value 180

double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10

alignment tl
gap_x 50
gap_y 40


default_shade_color grey
default_outline_color black
default_color 000000
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58

text_buffer_size 512
override_utf8_locale yes

minimum_size 400 400  # width height
maximum_width 400
#use_spacer left

max_specials 1024
max_user_text 4000


imlib_cache_size 0
border_inner_margin 0
border_outer_margin 0

TEXT
${image /home/glen/Pictures/frenchguard.gif -s 400x400}
```

Change the last line to the path to your image and desired size(-s XxY).


Change to match your required pic dimensions
```
minimum_size 400 400  # width height
maximum_width 400 
```



Change to match your screen start position
tl=top_left 
tr=top_right 
tm=top_middle
```
alignment tl
gap_x 50  
gap_y 40

```

Then to run use
```
conky -c [COLOR="Red"]/path/to/[/COLOR]deskimage.conkyrc
```

---

