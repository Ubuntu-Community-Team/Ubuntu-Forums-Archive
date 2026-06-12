---
title: "Lots of Keycode errors in logs"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by MaxVK on 2008-08-23
Iv read a few posts about this already, but the solutions where suggested, do not work or are not relevant.

First, the machine is an AMD 3000X, 2 gig RAM, Creative Live, NVIDIA GFX, MS Wireless Natural Multimedia keyboard, Logitech Trackball.

I'm using 7.10 and everything works fine.

However, in the logs I am seeing lots of these messages:

```
Aug 23 09:47:55 max-desktop kernel: [ 2555.513532] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Aug 23 09:47:55 max-desktop kernel: [ 2555.513538] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Aug 23 09:50:31 max-desktop kernel: [ 2711.181051] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Aug 23 09:50:31 max-desktop kernel: [ 2711.181057] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Aug 23 09:59:59 max-desktop kernel: [ 3278.741562] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Aug 23 09:59:59 max-desktop kernel: [ 3278.741567] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
```

Is there some way to stop these clogging up the logs - remembering that Iv read a few posts on this already, and the solutions didn't seem to work at all.

Cheers

Max

---

### Post by Titanitus on 2008-11-02
Hi MaxVK!

I do not know if it is still actual for you, but this one should help:

Check for free keycode with command
```

sudo dumpkeys|more

```
For me was free 128 and higher

Open your rc.local file:
```
sudo gedit /etc/rc.local
```

Add this code before "exit 0"
```

setkeycodes e001 128

```

Now restart your computer

regards

Titanitus

---

### Post by MaxVK on 2008-11-03
Aha! Now then! That seems to have worked! Excellent!

Very many thanks for that Titanitus, but I have to ask, how did you work this out when there are so many people trying to sort this out (and failing)?

Anyway, good job!

Regards

Max

---

### Post by Titanitus on 2008-11-05
Hi!

*but I have to ask, how did you work this out when there are so many people trying to sort this out (and failing)?*

It is not a solution, it is a "workaround". Some keyboards (specialy wireless) are sending special keycodes for their internal things (battery or signal status and so on). With this workaround you just say that "this keycode is okey and it is assigned".
I have just red other posts and deducted it ;o)

have fun

Titanitus :lolflag:

---

### Post by MaxVK on 2008-11-05
Workaround or not this sorted a problem that has been bugging me (on and off) for months!

Nice one, thanks very much. I'm sure this will help out a great many people besides myself.

---

