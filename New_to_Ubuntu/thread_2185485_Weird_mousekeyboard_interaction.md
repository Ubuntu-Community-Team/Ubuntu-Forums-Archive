---
title: "Weird mouse/keyboard interaction"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by klytu on 2013-11-02
I have an irritating issue with my mouse & keyboard that I'd like some help troubleshooting. The functions normally associated with left-clicking my mouse seem to cycle back and forth between the left mouse button and a particular button on my keyboard. When the keyboard button is active, the left mouse button does nothing and vice-versa. How I can I figure out why this is happening and hopefully stop it? Here's my setup (I can give more details if needed ...):

Intel D975XBX2 motherboard
E6600 processor
Saitek Eclipse II keyboard
Logitech M510 mouse 

Other mouse buttons and keyboard functions are normal. I have this issue running either Linux Mint 14 or Ubuntu 12.04. Any help or ideas appreciated!

---

### Post by heir4c on 2013-11-03
What button is it on the keyboard?

---

### Post by klytu on 2013-11-03
> **heir4c said:**
> What button is it on the keyboard?

It's the button that changes the color of the keyboard back lighting.

---

### Post by klytu on 2013-11-03
OK. It appears I'm not alone. I googled ```
saitek eclipse ii ubuntu
``` and found posts going back a couple of years with the exact same issue. Here's a few:

[http://askubuntu.com/questions/248143/my-keyboard-is-bugging-out-on-12-04-ubuntu](http://askubuntu.com/questions/248143/my-keyboard-is-bugging-out-on-12-04-ubuntu)
[http://ubuntuforums.org/showthread.php?t=1842524](http://ubuntuforums.org/showthread.php?t=1842524)
[http://www.reddit.com/r/Ubuntu/comments/18b7xt/back_lit_keyboard_issue_saitek_eclipse_ii/](http://www.reddit.com/r/Ubuntu/comments/18b7xt/back_lit_keyboard_issue_saitek_eclipse_ii/)

I didn't think to search just for the keyboard at first; I'll check to see if a bug report has already been filed.

---

### Post by klytu on 2013-11-03
This thread on Debian forums from a couple of years ago looks promising for my troubleshooting purposes:

[http://forums.debian.net/viewtopic.php?f=7&t=70507](http://forums.debian.net/viewtopic.php?f=7&t=70507)

Meanwhile a couple of workarounds:

- On a re-boot or a fresh boot set the keyboard backlight color as Ubuntu/Mint is loading (e.g. while the animated start-up screen is visible). Then don't touch the backlight button anymore.
- Or just never touch the backlight button, leaving the keyboard at the default blue backlight.
- If you forget and touch the backlight button during a session, unplug the keyboard then plug it back in. This seems to restore normal mouse functioning.

Although these don't solve the problem, they should help reduce the annoyance. I'll mark this thread as solved and post back if I ever find a real solution.

---

