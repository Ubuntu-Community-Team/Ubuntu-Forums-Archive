---
title: "&quot;check if typing&quot; bash script needed"
date: 2011-09-27
forum: Programming Talk
---

### Post by sonicb00m on 2011-09-27
I need to create a new script to enable/disable my vostro touchpad since it is unsupported by X and is detected as a generic mouse.

I need to loop and see if there is any keyboard input going on and then disable the touchpad with the following command

xinput set-prop 13 "Device Enabled" 0

and reenable it after a second or two 

How do i find out if the keyboard is in use?

---

### Post by SecretCode on 2011-09-27
Interesting ... this might help: [detecting keyboard, mouse activity in linux - Stack Overflow](http://stackoverflow.com/questions/222606/detecting-keyboard-mouse-activity-in-linux)

---

### Post by sonicb00m on 2011-09-27
Thanks very much. That should do the trick. I'll post the results here once I get it working.

---

### Post by sonicb00m on 2011-09-27
The idle time trick works unless you are using the mouse which then makes my script code kick in to disable the touch mouse :D

So if the mouse is in use I don't want to execute the idle time stuff.

---

### Post by SecretCode on 2011-09-27
I'm sure "disable the mouse when using the mouse" is a valid use case :D

---

### Post by sonicb00m on 2011-09-27
Maybe i wasn't being clear. I want to disable the touchpad when I am typing and re-enable it when I stop. If i use the touch mouse my script disables it. 

I already have a script to disable the touchpad if a mouse is plugged in. But I am trying to emulate the "disable touchpad while writing" feature but X11 doesn't support the Vostro touchpad.

---

### Post by SecretCode on 2011-09-27
It was me that was being unclear, not you - my last post was a joke. Obviously mouse activity should not disable the touchpad, but I haven't seen anything that detects keyboard activity and ignores mouse activity.

ANyone else?

---

### Post by sonicb00m on 2011-09-28
Haha no worries! I'm not against a bit of sarcasm now and again :D

---

