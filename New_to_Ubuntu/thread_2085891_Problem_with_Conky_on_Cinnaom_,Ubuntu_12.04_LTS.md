---
title: "Problem with Conky on Cinnaom ,Ubuntu 12.04 LTS"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by jbaraibrahim on 2012-11-19
Conky: desktop window (e00029) is subwindow of root window (ae)
Conky: window type - override
Conky: drawing to created window (0x3600001)
Conky: drawing to double buffer

please need your help , whenever i open  terminal to run conky it gives me this message

---

### Post by SlugSlug on 2012-11-19
A snip of my conky.conf

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 200
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by jbaraibrahim on 2012-11-19
> **SlugSlug said:**
> A snip of my conky.conf

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 200
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
 how do i do to config that on the document  ?

---

### Post by SlugSlug on 2012-11-19
make backup
```
sudo cp /etc/conky/conky.conf /etc/conky/conky.conf.bak
```
then edit
```
gksudo gedit /etc/conky/conky.conf
```

Find the bit am referring to and compare 

it's normally

own_window_type normal  / own_window_type desktop

that needs changing

---

