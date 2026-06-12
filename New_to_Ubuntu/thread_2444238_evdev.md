---
title: "evdev"
date: 2020-05-27
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-05-27
Hello!


So I'm a bit confused about what evdev and evdev devices are...

the evdev man page says it is an "Xorg input driver for Linux's generic event devices"

Does this mean it is like a compatibility layer between a device node and the X server?

As in it would go; device > device driver > device node > evdev > X server > application


If someone could give a bit of a layman's explanation that would be great, as I feel like I'm just splashing theories around!

---

### Post by CatKiller on 2020-05-27
> **jcdenton1995 said:**
> Does this mean it is like a compatibility layer between a device node and the X server?

Not really. It's more like a window or a read out. 

The kernel takes all the various signals from the hardware and turns it into a standardised input stream, which is accessed just like a file (lots of things that aren't really files are accessed as if they were a file, since it's handy and lots of things already know how to access files). The input stream will contain things like you pressed a button, or you stopped pressing a button, or the coordinates changed, or whatever. Exactly the kind of thing you'd be interested in if you were a display server, like X or Wayland, and you were trying to translate input signals into actions on a screen.

You can use evtest to read the input stream from a particular input "event device" abstraction.

---

### Post by jcdenton1995 on 2020-05-27
Thanks!

What I don't understand is why evdev is described as a driver, but doesn't show up when I run lsmod, even when I have a gamepad connected that I calibrate using evdev-joystick - meaning surely that's an evdev device?

I know some modules use an alias?

---

### Post by CatKiller on 2020-05-27
I agree that it's confusing wording. 

*Technically* evdev is the part that creates those event device interfaces so could be thought of as a driver in the Linux kernel sense, but it's not super helpful to call it that for anyone that is used to "driver" meaning "the thing that makes hardware work."

It's the driver for the *input event interface*, not the driver for the *hardware*. The hardware driver is part of the kernel, either the base kernel or a loaded kernel module.

---

### Post by CatKiller on 2020-05-27
I'll mention another thing because it's likely to come up with what you're trying to understand.

For devices in general you've got udev to handle access and notifications and things, and for input devices in particular you've got that input event stream. If you're a display server you're interested in *both* those things together rather than only one or the other.

Libinput is the abstraction that does that.

---

### Post by jcdenton1995 on 2020-05-28
Thanks, I'll look into that too. I've learned how to sucessfully create udev rules, which is the important thing, but I'm trying to develop a better understanding of the system in general as I've found that the vast majority of guides for Linux related things deffinitley dont hold your hand, and assume an almost professional level of competence, and the guides that dont, tend to not be great or make vauge statements and generalisations.

---

