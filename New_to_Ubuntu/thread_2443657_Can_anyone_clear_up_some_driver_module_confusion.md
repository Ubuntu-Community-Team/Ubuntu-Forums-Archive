---
title: "Can anyone clear up some driver module confusion?"
date: 2020-05-18
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-05-18
Hi all,

So I've just been poking about a bit learning how the driver modules work but as always it's ancient Greek. To keep it simple I'm looking at the 'hid' drivers displayed by using 'lsmod'. The hid drivers I have loaded are...```
lsmod | grep hid
hid_sony               36864  0
ff_memless             20480  1 hid_sony
mac_hid                16384  0
hid_generic            16384  0
usbhid                 53248  0
hid                   126976  3 usbhid,hid_sony,hid_generic


```I understand there will probably be one for my external keyboard, mouse and joystick. However my question is why do hid_sony (probably the joystick) hid_generic (maybe the mouse?) and usb_hid (keyboard??) all show as having 0 devices using them, but 'hid' shows as being used by the aforementioned 3 itself? Is it some kind of driver stack where some drivers are written to work via another driver? A laymans explanation would be much appreciated!

---

### Post by TheFu on 2020-05-18
If you post the output from **lsmod|grep hid** the answers may be clearer. Please use _code tags_ so things line up.

Here's on one of my systems:
```
$ lsmod|grep hid
mac_hid                16384  0
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic
```

Those zeros in the far right column mean no other modules reference those modules.
'hid' has a 2, which means 2 other modules, usbhid,hid_generic reference it.

Basically, the hid module cannot be rmmod'd until the usbhid and hid_generic are rmmod'd first.
That's the extent of what I've needed to know.  

No idea what mac_hid is related to this, but being exactly the same size as hid_generic is a little suspicious.

---

### Post by jcdenton1995 on 2020-05-18
Thanks, I edited my original comment to include the grep output.

Yes that makes sense, so I guess maybe it's the case that if a developer knows a certain module will be present on a system their developing for, they can write their own driver module to depend on some functions provided by another? Just me speculating.

---

### Post by TheFu on 2020-05-18
As a developer, but not kernel dev, I'd think the generic code provides well-known interfaces, then makes calls to the lower level, hw-specific code.  

There's a common code idea in OO design and coding from before OO existed called polymorphism.  Basically, a cat is a cat is a pet is a mammal is an animal.   So we can use an interface for an animal to cover many "cat" things.  i made the layers overly complex, as a beginner OOP might.  Almost always 1-2 layers are sufficient for most programming needs. 

There are lots of computer mice.  They have an X,Y  and usually 1 or more buttons.  Some mice have 2, 3, 5, 7, 11 buttons, so they need a way to tell the generic "mouse" code they have 11 buttons so the clicks can be registered to the OS and passed through each object until one handles that specific event.   That's how X11 works.  i was trained and coded in X11 programming for a few years.

---

### Post by jcdenton1995 on 2020-05-18
So sorry just to clarify, in this instance 'hid_generic' and 'usb_hid' would be the cats, and 'hid' would be animals in general. A bog standard mouse with two buttons and an XY could maybe function using 'hid' but a real fancy mouse with loads of functions would need it's own driver (a cat) to provide functions specific to that device?

(I know this is complicated by the fact one of the modules is called 'hid_generic' but as it depends on 'hid' I guessed it may be a "cat" providing some sort of extra functionality)

---

### Post by TheFu on 2020-05-18
You are seeking answers that I don't know. Sorry if that wasn't clear.  I was making a guess. Probably 50:50 whether it is correct or not.

Kernel stuff is usually different from application coding. They are clever folks and much more concerned about being efficient.

---

### Post by jcdenton1995 on 2020-05-19
No sure that's fine, I know you said you aren't certain but it's worth bearing in mind in the absence of anything concrete, especially since I don't have much else to go on! Thank you for the help :)

---

