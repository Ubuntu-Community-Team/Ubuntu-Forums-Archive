---
title: "No Power OFF option on Hardy?"
date: 2008-05-01
forum: Philippine Team
---

### Post by killer_d76 on 2008-05-01
i just re-installed Hardy last night and now i noticed that the "turn off" option is gone!.. i only have the option of "suspend, hibernate, log-out, lock screen and switch user" only?. is it just mine or talagang wala po option na'to?

---

### Post by yssida on 2008-05-01
did u change the settings in gconf-editor? I know it must be there somewhere, I just forgot where it is. DOn't panic. I myself removed the Suspend and Hibernate option (they didn't do crap on my laptop). I just can't remember where it is. But it's there.

---

### Post by yssida on 2008-05-01
for the mean time, try logging out, and there should be a power off option from there

---

### Post by killer_d76 on 2008-05-01
thanks for the quick reply!.. i'll wait 'till you remember where you found the on/off button before i go there ;).. i don't want to mess that thing anymore! :(

---

### Post by yssida on 2008-05-01
I remember, it was in gconf-editor>>apps>>gnome-power-manager......but  can't seem to find the poweroff option....another way to turn your computer off is by going to the terminal and typing,,,i'll try to find other solutions.

```

sudo poweroff

```

---

### Post by yssida on 2008-05-01
I like it slightly more than

```

sudo shutdown -h time

```

since you have to specify time. 

But if you want, here'sthe code:

```

sudo shutdown -h now

```

-h means that you halt the computer rather than rebooting/restarting, if you want to reboot then just replace -h with -r

'now' means that you want it to do the specified action now

---

### Post by killer_d76 on 2008-05-01
thanks yssida, turning off the power using terminal is not a problem for me, but my wife and my children whose using this more than i use this will have a hard time turning off this laptop.. does pressing the "power button" to turn off my laptop is okey?.. or do i really need to go thru the process of shutting down the computer?.. but without the shutdown button i may likely to brick my laptop won't i?

---

### Post by yssida on 2008-05-01
I'd advise against switching the power button directly. :(

I just did that with my laptop now, (dont ask), and the hard drive made a strange zip noise. Just...don't....do...it. You could make a script for it. and make that executable, then add a shortcut on your desktop. As to how you make the script executable, i have no idea. :(

---

### Post by loell on 2008-05-01
try to renew your gnome session, log off then , choose options in the login manager --> select sessions --> gnome.

---

### Post by killer_d76 on 2008-05-01
thanks loell.. but could you guide me on how to do that.. thanks ;)

---

### Post by loell on 2008-05-01
when you log off, you'll see the login screen, right? then in the low left corner there is this "Options" menu , after clicking it youll see sessions, click it then choose gnome, see if that can fix the no shutdown button.

maybe another workaround could be to create a new user.

---

### Post by killer_d76 on 2008-05-01
thanks loell.. i'll try that!, i'll keep you posted ;)

---

