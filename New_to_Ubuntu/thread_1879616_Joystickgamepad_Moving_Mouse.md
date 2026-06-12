---
title: "Joystick/gamepad Moving Mouse"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-11-11
Whenever I use the D-Pad, or left joystick on my gamepad ([This one]("http://www.radioshack.com/product/index.jsp?productId=3964949&filterName=Category")) it moves my mouse. This is kinda good when I do things that require the mouse, as I can also click with some of the other buttons, but very, very annoying when I am playing a game, as it moves out of the screen then clicks out of it. 

So, I am hoping someone knows how to stop the controller from using the mouse functions. 
Beginner, ubuntu 10.04 lucid lynx

---

### Post by ulao on 2012-01-29
Hi mschooler93,I know this is a bit old but I know why you get that. You need to remove it from the core pointer. So first look at the list

xinput list
You will see your controller under "Virtual core pointer" 

to disable it from the list of virtual pointer do this
xinput --set-prop "your device as it spears in the list" "Device Enabled" 0


I'm also told this will work ( not tried it myself)

add these lines to you /usr/share/X11/xorg.conf.d/50-joystick.conf
Option "StartKeysEnabled" "False"
Option "StartMouseEnabled" "False"

---

### Post by Grumbel on 2012-02-07
> **mschooler93 said:**
> So, I am hoping someone knows how to stop the controller from using the mouse functions.
Try:

apt-get remove xserver-xorg-input-joystick

---

### Post by ulao on 2012-02-09
I tried to remove it but didnt stop the mouse from following the joystick. I also tried to reboot and still no luck.

---

### Post by mark bower on 2012-12-17
I posted all the following under >Games Leisure, but thot it appropriate to post here also since it addresses the request for help.

Following are now two scripts which work without generating error msgs. The 1st is the one discussed so far. The 2nd one works and seem to make the change permanent - I could not get back to a condition where the USB joysticks affected the mouse cursor. And of course, this is just fine since it is the condition I want. But it would be interesting to know where the change took place. Also, I was hoping to use the 2nd option on a second computer I have, but USB joystick activity was already separated from the mouse cursor. I do not know why as I had not yet looked at the separation issue on the 2nd computer.

Option 1 (do for each boot):
Code:

```
#!/bin/bash
NAME="WAILLY PPM"
ids=$(xinput list | grep $NAME | grep -o -e "id=.." | xargs | sed "s/id=//g")
for id in $ids; do
   echo "Disabling Mouse/Key events for ID $id"
   xinput set-prop $id "WAILLY PPM" "Generate Mouse Events" 0
   xinput set-prop $id "WAILLY PPM" "Generate Key Events" 0
done
```

Option 2 (which seems to make a permanent change):
Code:

```
#!/bin/bash
NAME='WAILLY PPM'

ids=$(xinput list | grep  "$NAME" | grep -o -e "id=.." | xargs | sed "s/id=//g")
for id in $ids; do
    echo "Disabling Mouse/Key events for ID $id"
    xinput set-prop $id "WAILLY PPM" "Device Enabled" 0
done
```

---

