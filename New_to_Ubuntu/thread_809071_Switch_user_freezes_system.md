---
title: "Switch user freezes system"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by milanvora2 on 2008-05-27
Hi

- log in as user A and then switch to user B -> system hangs up
- log as user A, log out and log in as user B -> works fine

I'm stuck as the computer is used by the whoel family and switching users is an improtant feature.

I already posted a similar thread a week back, but I couldn't get any response.

Can anyone help ?

---

### Post by alexandremrj on 2008-05-27
Hi,

there seems to be some errors regarding that in launchpad but i must ask a question:

When systems freezes what do you get? The desktop but simply frozen, a blank screen or a dark screen?

If the case is a blank screen you can type the user password and press enter and automatically the system will change user (it simply doesn't show the screen it was supposed to). The other seem like bugs but then there will be the need for more information about your pc.

---

### Post by milanvora2 on 2008-05-27
the system simply freezes. Keyboard does not react,

my system specs:
E8200 CPU
ATI 3650 Radeon HD card
Gigaybte P35 chipset based mainbaord
17" LG LCD Monitor

Using Hardy 8.04, with Compiz enabled and using the restricted ATI 8.5 Catalyst Drivers

How should i proceed ?

---

### Post by alexandremrj on 2008-05-27
[https://bugs.launchpad.net/ubuntu/hardy/+source/gdm/+bug/118605](https://bugs.launchpad.net/ubuntu/hardy/+source/gdm/+bug/118605)

This is one of the errors in launchpad.

There are several bugs that exibhit the same symptons and so it's a bit hard to trace. You may try disabling the restricted driver and see if that solves the issue.

If that doesn't work then i'm not any help, sorry.

---

### Post by kc600 on 2008-06-07
I have the same behaviour:
When i login as user A, and then switch to user B and back to user A again a couple of times, the systems hangs.
Things to note:
- Most of the time, when both users have been logged in for a while, i get this after only one switch-and-back cycle. When both users have just logged in, i have to repeat it a couple of times in order to get the freeze.
- Switching via the fast-switch applet and via the logout menu produces the same result.
- For both user A and B, screen locking when switching users is disabled.
- Killing X by pressing Ctrl-Alt-Backspace doesn't work, neither does restarting by pressing Ctrl-Alt-Delete 
- It's not just a stalled gdm, the entire system freezes. For example, if i'm logged in on the computer via ssh, that session freezes too. Music still playing on one of the users (Amarok) will quit or stall. Caps lock and Num lock don't work, either.
- I use the open source ati driver.
- I do not have desktop effects (compiz) enabled. (I can not enable these; why this is is perhaps a related issue. Whenever i try (via preferences > appearance > tab visual effects), it says "desktop effects could not be enabled".)
- Removing ~/.kde doesn't help
- Ubuntu 8.04 (Hardy)

Bug 118605 in Launchpad is about the fglrx driver, so that's a different story.
It seems this bug is more like it: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/119635](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/119635)

---

### Post by byStanderone on 2010-05-16
...this also applies to nvidia, in lucid this problem still exist.

---

### Post by gagan.gupta on 2010-11-21
> **byStanderone said:**
> ...this also applies to nvidia, in lucid this problem still exist.
Doing Ctrl-Alt-F1 and then Ctrl-Alt-F7 seems to help.

---

