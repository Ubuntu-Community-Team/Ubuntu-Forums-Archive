---
title: "Steering Wiimote/Nunchuk"
date: 2013-05-30
forum: Programming Talk
---

### Post by trotithuthur on 2013-05-30
Hello! I am a french ubuntu user, so I apologize for my english.
I discovered this [turorial]("http://doc.ubuntu-fr.org/wiimote") and I can use wminput as I want. I programm a litlle and I want to create my own configuration's scripts to steer my Wiimote with wminput. I would like to steer my mouse with the nunchuk of my Wiimote. Before, under Windows I wrote a script like this one : 


```
mouse.DirectInputX=mouse.DirectInputX+5*Wiimote.Nunchuk.JoyX
mouse.DirectInputY=mouse.DirectInputY+5*Wiimote.Nunchuk.JoyY
```
      But with Ubuntu when I launch  a script like this one:


```
Nunchuk.Stick.X=ABS_X
Nunchuk.Stick.Y=-ABS_Y
```
And when I launch it with:
```
$sudo wminput -c myscript
```

      ... It works but when I release the joystick, the pointer returns on his original position (when I use the joystick, the cursor's trajectory is like a circle around his original position...). Si it works but not as I want... When I try to ensure that the pointer stays where it is once moved, like this :


```
ABS_X+Nunchuk.Stick.X=ABS_X
ABS_Y+Nunchuk.Stick.Y=-ABS_Y
```
      ... It does not work... wminput returns me an error... So, how fix the coordinates of my pointer once I released the joystick...?
I also tried something like this :
```



Nunchuk.Stick.X=REL_X
Nunchuk.Stick.Y=-REL_Y
```
But the pointer stays blocked in the right down corner of my screen...
Thank you in advance for your help! :o

---

### Post by trotithuthur on 2013-06-01
Can somenone help me please??

---

### Post by trotithuthur on 2013-06-02
Up...?

---

