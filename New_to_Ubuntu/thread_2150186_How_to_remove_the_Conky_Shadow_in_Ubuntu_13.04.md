---
title: "How to remove the Conky Shadow in Ubuntu 13.04?"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by 3mutts on 2013-05-31
Ok, I have that annoying shadow around conky and Im wondering how to remove it. I tried many things but it wont seem to go away. Any help is welcomed

---

### Post by Frogs Hair on 2013-05-31
Could provide some information/link  about or post the .conkyrc ? Shadows, borders and window type are usually set up in the  conky syntax.  

Example: ```
 default_outline_color 000000 # Blackdefault_shade_color 000000	# Black
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 30
gap_y 80
max_specials 1024
max_user_text 10000
maximum_width 200
minimum_size 175
net_avg_samples 2
no_buffers yes
override_utf8_locale yes
own_window yes
own_window_colour 000000	# Black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal ## normal

```

---

### Post by stinkeye on 2013-05-31
Install ccsm
```
sudo apt-get install compizconfig-settings-manager
```

and in ccsm > Effects > Window decoration 
Change shadow windows to...
```
(any) & !(class=Conky)
```

---

### Post by 3mutts on 2013-05-31
^ I tried that before, however it won't launch for some reason (crashes on launch along with the fusion icon) Ill post the error later because I am posting from my IPad.

---

### Post by stinkeye on 2013-05-31
> **3mutts said:**
> ^ I tried that before, however it won't launch for some reason (crashes on launch along with the fusion icon) Ill post the error later because I am posting from my IPad.
If you enter ccsm into a terminal what errors do you get?
If you upgraded to 13.04 you may want to reset your compiz settings.
```
dconf reset -f /org/compiz/
```
log out/in

In your conky config you could also try changing
```
own_window_type **normal**
```
to
```
own_window_type **override**
```
override windows are not under control of the window manager, so won't be shadowed.

override widows can have their own problems though with transparency depending on your gfx driver.
Just see how it goes.

---

### Post by 3mutts on 2013-05-31
This is the error I get:

> compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
Segmentation fault (core dumped)


---

### Post by 3mutts on 2013-06-01
Fixed the Compiz error by removing this package through the Synaptic Package Manager.

> compizconfig-backend-kconfig

i will see if the thing mentioned above will fix the Conky shadow.

EDIT: Adding the rule to Compiz fixed it, thank you stinkeye! :KS

---

