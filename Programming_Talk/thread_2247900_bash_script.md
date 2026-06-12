---
title: "bash script"
date: 2014-10-11
forum: Programming Talk
---

### Post by pingaan on 2014-10-11
I need some help correcting the wrong in this script:
```

#!/bin/sh -e

# Script to launch mupen64plus with correct settings

move_and_fullscreen(){
NAME='mupen64plus'

while [ -z "`wmctrl -l | grep \"$NAME\"`" ]
do
sleep 1
done

wmctrl -r "$NAME" -e '0,1920,-1,-1,-1'
wmctrl -r "$NAME" -b toggle,fullscreen

# rom file
ROM=/home/pingaan/download/mario64.z64

# mupen64plus executable
MUPEN64PLUS=mupen64plus

# emulator process name to kill
MUPEN64PLUS_PS=mupen64plus

$MUPEN64PLUS --gfx mupen64plus-video-glide64mk2 --osd --resolution 1920x1080 --fullscreen "$1"killall $MUPEN64PLUS_PS $GAMEPAD_PS 
}
```

So what I'm trying to do is loading a Nintendo 64 rom in Mupen64plus, move it to my secondary screen and fit the emulator to the screen with the proper resolution.
Not working! =P
The terminal just keeps looping "Screen not found", or something similar.

Regards.

---

### Post by steeldriver on 2014-10-11
"or something similar" doesn't help us much - most Linux errors are pretty specific and do actually help locate the problem

Presumably 
```

$MUPEN64PLUS --gfx mupen64plus-video-glide64mk2 --osd --resolution 1920x1080 --fullscreen "$1"killall $MUPEN64PLUS_PS $GAMEPAD_PS 

```

is actually supposed to be 2 different commands? something like 

```

$MUPEN64PLUS --gfx mupen64plus-video-glide64mk2 --osd  --resolution 1920x1080 --fullscreen "$1" 
killall $MUPEN64PLUS_PS  $GAMEPAD_PS

```
or
```

killall $MUPEN64PLUS_PS  $GAMEPAD_PS
$MUPEN64PLUS --gfx mupen64plus-video-glide64mk2 --osd  --resolution 1920x1080 --fullscreen "$1" 

```

---

### Post by pingaan on 2014-10-12
Of course, I forgot the enter after "$1". Also "$GAMEPAD_PS should not be there at all.

This is what it looks like now:
```

#!/bin/sh -e

# Script to launch mupen64plus with correct settings

move_and_fullscreen(){
NAME='mupen64plus'

while [ -z "`wmctrl -l | grep \"$NAME\"`" ]
do
sleep 1
done

wmctrl -r "$NAME" -e '0,1920,-1,-1,-1'
wmctrl -r "$NAME" -b toggle,fullscreen

# rom file
ROM=/home/pingaan/download/mario64.z64

# mupen64plus executable
MUPEN64PLUS=mupen64plus

# emulator process name to kill
MUPEN64PLUS_PS=mupen64plus

$MUPEN64PLUS --gfx mupen64plus-video-glide64mk2 --osd --resolution 1920x1080 --fullscreen "$1"
killall $MUPEN64PLUS_PS
}
```

I was wrong about the screen not found msg looping, that must've been an old script i mixed this one up with. Sorry.
When I run this script nothing at all happens. mupen64plus doesn't even start.

---

### Post by steeldriver on 2014-10-12
If that's your entire script, then you have **defined** a shell function - but don't actually **call** it. You either need to remove the 

```

move_and_fullscreen(){
.
.
.
}

```

structure around your commands and run it as a simple script, or add a function call that passes in the appropriate positional parameters - something like

```

move_and_fullscreen "$1"

```

or

```

move_and_fullscreen "$@"

```

at the bottom.

---

### Post by pingaan on 2014-10-12
Hmm.. You're right! I'm going to try that when I get home.
But let's say we started from the begining and built a new script.
What would be the proper line of commands to move and fullscreen a program? I thought this would work for any program:

```

move_and_fullscreen(){
NAME='x'

while [ -z "`wmctrl -l | grep \"$NAME\"`" ]
do
sleep 1
done

wmctrl -r "$NAME" -e '0,1920,-1,-1,-1'
wmctrl -r "$NAME" -b toggle,fullscreen
}

move_and_fullscreen &

```

---

