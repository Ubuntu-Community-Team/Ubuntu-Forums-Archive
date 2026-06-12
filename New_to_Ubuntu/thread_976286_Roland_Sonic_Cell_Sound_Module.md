---
title: "Roland Sonic Cell Sound Module"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by sharondenscabbia on 2008-11-09
Whilst not an absolute beginner to Ubuntu, I feel this is where this query 
belongs, as I'm still learning.

I own a Roland Sonic Cell USB sound module/synth. I used to use it perfectly with vista (dual booted), but after some hard drive problems, vista has gone away, for better or for worse! However, I'd still like to use it with Ubuntu.

After googling how to do this, _[this](http://www.linuxhq.com/kernel/v2.6/26-git17/sound/usb/usbquirks.h)_ came up. It looks promising, but I've no idea what it is.

What is it, can I use it, and how do I implement whatever it is supposed to do?

Thanks,
Sharon

---

### Post by dracayr on 2008-11-09
that is a patch for the linux Kernel v2.6.26-git17. If you're not a linux expert I wouldn't recommend to use it, as you will have to recompile your kernel to do this. However, if you really want to do it: [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2) as you probably already know, it is not recommended to activate the root user in ubuntu (as described in the howto). you  can use *sudo -s* instead.

dracayr

---

### Post by sharondenscabbia on 2008-11-09
Ah, thanks. The reason I lost vista in the first place was by messing with things I don't understand! I've learned my lesson... I won't be doing that!

If thats so, would you know how I would be able to use it? It's effectively a collection of a USB sound card, USB midi input/output device, USB audio recorder and playlist editor. Would I be able to possibly treat it as a generic USB device in order to get one(or some) of the functions to work?

Thanks,
Sharon

---

### Post by greg-lyons on 2008-11-19
If you're using Ubuntu 8.10, that patch is already incorporated into the drivers for the most recent kernel.  I haven't upgraded my primary computer yet, so I haven't tried audio or other features, but MIDI I/O seemed to work well for me on another machine.

---

