---
title: "Issue with keyboard keys combinations"
date: 2022-10-13
forum: New to Ubuntu
---

### Post by eventine on 2022-10-13
Hi all,


I'm not very familiar with Ubuntu, and when I used it, it was generally through the terminal only. I decided to install Ubuntu 22.04 on my workstation since I was tired of VMs. 
But I'm having some issue with keyboards: one keyboard is working perfectly fine, while with another one (a ThinkPad notebook keyboard I'm using through VNC, they both have the same layout) combinations of keys does not work at all:
for example, ALT_R+ other keys are not working, and SHIFT+TAB is not working too.
It has been 3 weeks that I'm trying to make it work, and I scrambled all the forum posts I found, but nothing worked for me.
Do you have any suggestions?


Thanks to everyone,
Eventine

---

### Post by patrick2957672 on 2022-10-13
setxkbmap us 

us, de, it, ... any kind of keyboard.

---

### Post by MAFoElffen on 2022-10-14
```

setxkbmap -query

```
Will show what the current keymap is set to... And adjust to the last poster's recommendation, from there.

---

### Post by eventine on 2022-10-21
It made no difference.
I also tried to disconnect one keyboard, but still no changes.


Do you have more ideas on what to try?


E.

---

### Post by eventine on 2022-11-04
I'm sorry for popping the thread but I have no solution atm, and cannot find one online either.

Best,
E.

---

### Post by QIII on 2022-11-04
You are welcome to bump a thread after about 12 hours without a response.  You left this thread so long that it sank to the bottom of the sea and was covered by ooze and whale bones.  Nobody would have found it.

---

### Post by MAFoElffen on 2022-11-05
I asked you what the current keymap was. Depending on that keymap, you could then dump the keymap to see if those keys were defined.

The exception to that is that certain applications, remap keys, and key combinations.

EDIT:

I, myself, have started to play with this to create my own personalized keymap... Something that I have control over.

---

### Post by eventine on 2022-11-09
> **MAFoElffen said:**
> I asked you what the current keymap was. Depending on that keymap, you could then dump the keymap to see if those keys were defined.

The exception to that is that certain applications, remap keys, and key combinations.

EDIT:

I, myself, have started to play with this to create my own personalized keymap... Something that I have control over.

Sorry I did not understand what you were asking. The result of the query is:
```

rules:      evdev
model:      pc105
layout:     it
options:    lv3:ralt_alt

```
Sometimes the mapping get changed (dunno by what) to this:
```

rules:      evdev
model:      pc105
layout:     it,us,us
variant:    ,intl,
options:    lv3:ralt_alt

```
and when it happens, also other key combinations don't work (such as @, #, ... -aka ALT_R+key) in both keyboard, and have to change them back using setxkbmap it
Anyway, the SHIFT+TAB is never working on the vnc keyboard.

Also sorry for the late replys, but I don't get notification from this forum, and it's hard to keep up with everything these days.

E.

---

### Post by MAFoElffen on 2022-11-09
> **eventine said:**
> Anyway, the SHIFT+TAB is never working [COLOR=#ff0000]on the vnc keyboard.[/COLOR]
That is another layer that would have been good to know from the start.

Which VNC front-end are you using to what remote VNC Guest?

---

### Post by ya8785995 on 2022-11-11
It didn't change anything[.]("https://printerchief.com/")
I additionally attempted to unplug one keyboard, but nothing changed.

---

### Post by eventine on 2022-11-14
> **MAFoElffen said:**
> That is another layer that would have been good to know from the start.

It was in the OG post:
> **eventine said:**
> 
... while with another one (a ThinkPad notebook keyboard I'm using through  VNC, they both have the same layout) combinations of keys does not work ...

> **MAFoElffen said:**
> 
Which VNC front-end are you using to what remote VNC Guest?

Using f-e: VNC viewer 6.21.406, remote: x11vnc

Thanks
E.

---

