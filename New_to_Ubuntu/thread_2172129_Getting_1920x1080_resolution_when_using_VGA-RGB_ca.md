---
title: "Getting 1920x1080 resolution when using VGA-RGB cabel"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by alonbr on 2013-09-03
Hello there,

Bought a new TV.
Have a Percise running computer connected.
Was a bit cheap and bougth low end hardware (see [lshw]("https://docs.google.com/file/d/0B5H5wnDHRk84cnNMb3prX3ZrQkk/edit?usp=sharing"))
Connecting the TV using VGA-RGB cable (if only there was an HDMI connection onboard... I am really OK with not seeing real full HD)
Acording to TV manual Component only accepts 1080p\1080i (Samsung UA32EH5000 LED - good price and low power consumption... Old TV a little dodgy lately).
Ubuntu is too stuburn to allow 1920x1080 resolution via VGA.

What to do? What to do? :confused:

---

### Post by sandyd on 2013-09-03
> **alonbr said:**
> Hello there,

Bought a new TV.
Have a Percise running computer connected.
Was a bit cheap and bougth low end hardware (see [lshw]("https://docs.google.com/file/d/0B5H5wnDHRk84cnNMb3prX3ZrQkk/edit?usp=sharing"))
Connecting the TV using VGA-RGB cable (if only there was an HDMI connection onboard... I am really OK with not seeing real full HD)
Acording to TV manual Component only accepts 1080p\1080i (Samsung UA32EH5000 LED - good price and low power consumption... Old TV a little dodgy lately).
Ubuntu is too stuburn to allow 1920x1080 resolution via VGA.

What to do? What to do? :confused:

Lets check the resolutions that xorg indicates it can support.
Run
```

xrandr
```
and post the output

---

### Post by alonbr on 2013-09-03
```

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  


```
tried:
```

  xrandr --newmode "1080p"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync


```
and then

```

xrandr --addmode VGA-0 "1080p"


```

But it didn't work out...
[only error masseges on start up]("https://docs.google.com/file/d/0B5H5wnDHRk84S1lnNEczV2RrOXc/edit?usp=sharing")
[IMG]https://docs.google.com/file/d/0B5H5wnDHRk84S1lnNEczV2RrOXc/edit?usp=sharing[/IMG]

BTW:
ASUS says the max res. is 2048 x 1536.



Oh and.... Thanks for the fast reply!! :-)

---

