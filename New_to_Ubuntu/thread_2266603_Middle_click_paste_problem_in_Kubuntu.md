---
title: "Middle click paste problem in Kubuntu"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by MrSlip on 2015-02-24
I have this problem, and reboots definitely do NOT solve it.  I've also been using Linux for 15 years, and Kubuntu for about a year.  The middle-button paste has always worked fine, until several months ago, I'm guessing sometime after an update.  Impossible to say exactly when.  Anyway, I've tried rebooting but it doesn't help.  I tried setting up a pristine new account, and it also does not work.

I've tried tinkering with the settings in Klipper, but nothing there works. From my research into this, it should not effect anything anyway, since middle-button paste is an xorg thing, not a KDE thing.

When I highlight text, it does get copied into Klipper.  I can paste the text from the keyboard by pressing SHIFT-INSERT.  But the middle button will not work.

Let me stress that I did not do anything different, such as change hardware, or install any special or unusual software.  I have tried swapping out another mouse, just to rule out a bad switch, but I get the same non-functional behavior.

I'm using a Toshiba Qosmio X875-Q7190, running Kubuntu 14.04 (lsb_release reports 14.04.2).
My mouse is a Logitech M310, it has left/right buttons, and a middle scroll wheel which is also a button.

I have an xorg.conf file which was created by nvidia-settings, and which did not reference the mouse at all.  I found information in a forum in which someone had my problem, and they said putting the following lines in their xorg.conf file solved their problem:
[https://bbs.archlinux.org/viewtopic.php?id=107490](https://bbs.archlinux.org/viewtopic.php?id=107490)

Section "InputClass"
    Identifier "whatever"
    MatchIsPointer "on"
    Option "Emulate3Buttons" "on"
EndSection

It did **not** solve my problem.  And yes, I restarted the X Server, and even rebooted.

I really miss middle-button paste.  Any help will be appreciated.

---

### Post by coldraven on 2015-02-24
I'm using an A4Tech Glaser mouse and the scroll wheel will paste in 14.04. Have you tried using another mouse? Maybe your mouse is faulty.

---

### Post by coffeecat on 2015-02-24
@MrSlip, the thread you posted to was old, occasionally necromanced and the first post read more as a rant than a request for support. You'll do better in a fresh thread, so I've moved your post plus the reply to its own thread, and retitled the thread.

---

