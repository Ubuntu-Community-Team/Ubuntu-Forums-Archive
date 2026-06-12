---
title: "[SOLVED] Ubuntu thinks right key is pressed; Hardware Drivers and Synaptic won't work"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by NerdWithNoLife on 2008-11-07
My main problem is Ubuntu thinks the right key is stuck down.  Here's why I think it's not a hardware problem:

In the BIOS, it's not stuck.  I even disabled my laptop keyboard and hooked up a USB keyboard - and things worked fine in Ubuntu.

This is a laptop with ATI restricted drivers running but remember: I can't access Hardware Drivers or Synaptic Package Manager under System > Administration.  I get the "thinking" symbol, then the screen turns grey for a fraction of a second, then Ubuntu forgets I told it to do anything.

I couldn't even post this message without using my other computer because I can't use dropdown boxes!  And it's hard to configure any settings when the rightmost tab is always selected.  I bought my computer to use it, not spend all day debugging.  Please help before I go back to Vista. :confused:

---

### Post by NerdWithNoLife on 2008-11-09
The problem is sometimes worse than other times, but it's always there. If I hover the mouse over the minimize/maximize buttons, I can see them flickering.

---

### Post by NerdWithNoLife on 2008-11-09
I came across this gem that resolved the problem!
> When using GNOME, with keyboard settings set with the GNOME keyboard capplet, keyboard modifiers (shift, caps lock, alt, etc.) will randomly be forgotten. It may be on next login, it may just happen while using the box. But it will happen at some point. Others (e.g. Amaranth on #gnome-hackers) have seen similar behavior, and it was Amaranth who showed me the workaround.

Steps to reproduce: Unknown

Details of my keyboard settings: Generic 105-key PC keyboard, USA layout. Layout options set are swapping ctrl and caps lock, and menu is compose key.

Symptoms: randomly, modifier keys will stop working. This may be all modifieres (e.g. shift, alt, ctrl, etc.) or it may be just a few of the settings (for example, it's happened that ctrl and caps lock got un-switched despite the capplet saying they were still switched). That one was sure odd. Usually, though, I'll notice that GNOME forgot my keyboard settings

Workaround: when the modifiers are forgotten, log out. Log in to a text terminal and kill any lagging gconf processes (I've had good luck with kill -9 -1 ;) Then rm -rf .gconf/desktop/gnome/peripherals/keyboard. Log out of the text terminal and log in to GNOME again. You'll have to reset your keybinding modifiers, but the keys will all work again.

---

### Post by Crafty Kisses on 2008-11-09
Please mark the thread as solved. :D

---

