---
title: "Steam &amp; Xboxdrv (I can't get any input to go to steam?)"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by MarcosCosmos on 2012-03-08
A while ago I started trying to use xboxdrv to play the binding  of isaac on steam, eventually I worked out how to get it to start up, but only to the point where I can see the inputs in the terminal, It's probably just because I'm not familiar with shells or bash, my best guess is I'm missing crucial code but if anyone could explain it to me/help me get it running, I'd be very grateful!

I am trying to run it with this:
```

#!/bin/sh

exec xboxdrv
  --daemon
  --config ./home/isaac.xboxdrv 

# EOF #

```
Where isaac.xboxdrv is:

```

[xboxdrv]
silent=true
deadzone=6000
dpad-as-button=true
trigger-as-button=true

[ui-axismap]
x2=REL_X:10
y2=REL_Y:-10
x1=KEY_A:KEY_D
y1=KEY_W:KEY_S

[ui-buttonmap]
a=KEY_LEFTSHIFT
b=BTN_C
x=BTN_EXTRA
y=KEY_C

[ui-buttonmap]
lb=BTN_RIGHT
rb=KEY_SPACE

[ui-buttonmap]
lt=KEY_Z
rt=BTN_LEFT

[ui-buttonmap]
dl=KEY_4
dr=KEY_2
du=REL_WHEEL:-1:150
dd=REL_WHEEL:1:150

[ui-buttonmap]
back=KEY_TAB
start=KEY_ESC

# EOF #

```

Thanks in advanced,
Marcos Cosmos

---

