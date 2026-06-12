---
title: "help me create something that will launch mplayer /dev/video0 and have channel change"
date: 2008-07-19
forum: Programming Talk
---

### Post by Mysticle31 on 2008-07-19
I have been trying to create a simple stupud thing that will launch mplayer playing /dev/video0 and be able to send change channel commands to the ir blaster.  That way if I just want to browse around TV I can run that app and not have to go use MythTV with my PVR150.  

With my limited programming knoledge and poking around on other forums with other projects here is what I came up with.

```
#!/bin/bash


#Channel Changer
APPS=([0]="0" [1]="1" [2]="2" [3]="3" [4]="4" [5]="5" [6]="6" [7]="7" [8]="8" [9]="9")
APPNAMES=([0]="0" [1]="1" [2]="2" [3]="3" [4]="4" [5]"5" [6]"6" [7]"7" [8]"8" [9]"9")


BUTTONS="2:0"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done


BUTTONS="2:1"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done


BUTTONS="2:2"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done


BUTTONS="3:3"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="4:4"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="5:5"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="6:6"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="7:7"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="8:8"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="9:9"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

xmessage -buttons '0:0,1:1,2:2,3:3,4:4,5:5,6:6,7:7,8:8,9:9' 'Channel Changer.'
APP="${APPS[$?]}"

irsend -d /dev/lircd SEND_ONCE DCT2000 $APP

```

There are some problems with this.

1) Won't stay open.  The channel change part needs to stay open.  
2) It has to run mplayer and be open at the same time.  Right now it will launch mplayer but won't display the channel change part until I close mplayer.
3) How can I add a channel up or channel down?  The script would have to know what channel is currently at because my lirc does not currently support non-number entries.
4) How can I make it look like a number pad and not all in one line
5) Is it possible to make it also use the numberpad on the keyboard whenever the applet has focus?
6) Is it possible to make this little channel change window a part of the mplayer window as if it was all one window?  Maybe a WM trick?
7) Any general clean up code stuff I don't know?

Thanks for your help. 

Being I have a mpeg2 card the TVtime and things of the sort don't work.  And I'm not using the Hauppague blaster it's MCEUSB2

---

### Post by nanotube on 2008-07-20
i don't know much (well, anything), about the specifics of what you are trying to do with the channel changing, the remote, etc., but i can give you some general suggestions:

> **Mysticle31 said:**
> 
1) Won't stay open.  The channel change part needs to stay open.  


put the whole thing in an infinite while loop. that way, it will stay running until you manually kill it.

> 2) It has to run mplayer and be open at the same time.  Right now it will launch mplayer but won't display the channel change part until I close mplayer.

launch mplayer in background ```
mplayer &
``` rather than foreground. that way, it won't wait for mplayer to exit to do stuff.

> 3) How can I add a channel up or channel down?  The script would have to know what channel is currently at because my lirc does not currently support non-number entries.

store current channel in a variable? increment/decrement it when you get the channel up/down command?

> 4) How can I make it look like a number pad and not all in one line

from "man xmessage", it doesn't look like that can be done with xmessage. you might have to roll your own little gui, if you really care about how it looks.

> 5) Is it possible to make it also use the numberpad on the keyboard whenever the applet has focus?

hm, looks like you'd have to roll your own little gui for that one too. maybe with python+pygtk?

> 
6) Is it possible to make this little channel change window a part of the mplayer window as if it was all one window?  Maybe a WM trick?

don't know about that...

> 7) Any general clean up code stuff I don't know?

well, one thing is that you are mapping numbers to their corresponding strings. you don't have to do that:
```
$number=0
$string="$number"
```

i don't know what you are trying to accomplish there with the "apps" and the "buttons" and those little for loops and all that, but i suspect strongly that you can avoid a lot of that code duplication (all your for loops are the same!)

hope all that is at least somewhat helpful ;)

---

### Post by Mysticle31 on 2008-07-20
Awesome thank you!  Your tips helped me make a script that workes quite well, although crude.

Sorry for not being so clear as to what I am doing.

I have a PVR150 and Motorola Cable Box.  Since the PVR150 is a MPEG2 Hardware Encoder Card I can't use anything like TVTime.  It's MythTV or nothing.  Mplayer, however can play the device like a file.  That doesn't help me because since I have a cable box I can't change channels easily.  That's where the script comes in.  It uses irsend to change channels though the mceusb blaster.

How can I add a button that is not related to the channel buttons?  One that issues a completely seperate command.  I would like to add a change input button.  I need to issue this command.  v4l2-ctl --set-input=0

---

### Post by Mysticle31 on 2008-07-20
In Case someone wants something similar.  Here is what I've got

```
#!/bin/bash

mplayer /dev/video0 &

while [ 1 ] 
do
#Channel Changer
APPS=([0]="0" [1]="1" [2]="2" [3]="3" [4]="4" [5]="5" [6]="6" [7]="7" [8]="8" [9]="9")
APPNAMES=([0]="0" [1]="1" [2]="2" [3]="3" [4]="4" [5]"5" [6]"6" [7]"7" [8]"8" [9]"9")


BUTTONS="0:0"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done


BUTTONS="1:1"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done


BUTTONS="2:2"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done


BUTTONS="3:3"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="4:4"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="5:5"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="6:6"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="7:7"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="8:8"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

BUTTONS="9:9"
for appi in ${!APPSNAMES[@]}; do
  BUTTONS+=",${APPNAMES[$appi]}:$appi"
done

xmessage -buttons '0:0,1:1,2:2,3:3,4:4,5:5,6:6,7:7,8:8,9:9' 'Channel Changer.'
APP="${APPS[$?]}"

irsend -d /dev/lircd SEND_ONCE DCT2000 $APP
done
```

---

### Post by nanotube on 2008-07-20
cool glad it works :)

to add a button to do something different - just add a button, give it a different label and return value, and then put an if statement in there that says "if buttonpressed == yourbutton" do that v4l2 thing

---

