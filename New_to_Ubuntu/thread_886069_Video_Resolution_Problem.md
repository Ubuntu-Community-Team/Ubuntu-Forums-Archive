---
title: "Video Resolution Problem"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by poscomp on 2008-08-10
I had Ubuntu 8.04 running but was unhappy with a 800x400 resolution which was the max my video card could give me. I went to Comp USA and purchased an eGeForce 6200 video card (nvidia). The card worked but the resolution didn't change. I reinstalled the system but now the resolution was lower. I installed FreeSpire and I had my 1024x768 resolution. I would rather run Ubuntu 8.04. Can anyone help me fix this problem?

Thanks in advance!!

---

### Post by tuxxy on 2008-08-10
Did you install nvidia-settings and attempt to change the res

---

### Post by halitech on 2008-08-10
did you install the restricted drivers for it?

---

### Post by peakshysteria on 2008-08-10
More than a few threads on this topic (both for nvidia and ATI cards).> This should work:
Quote:
Originally Posted by peakshysteria View Post
Code:

**sudo displayconfig-gtk**

And adjust the resolution.

(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

---

### Post by poscomp on 2008-08-10
Yes I loaded the restricted driver with no luck. With Freespire I didn't do anything but load the system.

---

### Post by peakshysteria on 2008-08-10
Did you try to go the way I mentioned above?
[[img]http://bildr.no/thumb/236351.jpeg[/img]](http://bildr.no/view/236351)

_________________

Also if you're not to familiar with screen card drivers **Envy** (Envy Legacy or EnvyNG, respective for x86 or x86_64) will install it for you. Just install it via the synaptic package manager. **Envy** will provide an easy to understand GUI which will ease the install process.

---

### Post by poscomp on 2008-08-10
I loaded Envy...ran it and now I have 640x480 resolution. I'm confused...the card will do hires because it does it in Freespire. Why won't it work in Ubuntu. Do I have to run Freespire?

---

### Post by peakshysteria on 2008-08-11
Have you tried the Screens and graphics manager as mentioned above?

---

