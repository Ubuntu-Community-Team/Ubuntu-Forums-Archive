---
title: "Navigation pad on the main keyboard (TouchCursor under Linux)"
date: 2009-11-22
forum: Programming Talk
---

### Post by merindol on 2009-11-22
Hi.

I'm trying to do something like [_TouchCursor_]("http://touchcursor.com/") does. It uses the spacebar as a meta-key to give access to the navigation keys (and more) from the main keyboard, like Space+L for Right-key  (see the video).

Atm, it almost works. E.g. I can Shift+Ctrl+Space+L to select the word to the right of the cursor.

But my spacebar no longer works as a spacebar. I'm trying to find a way to make it works like with TouchCursor : **when I press than release the spacebar, and only if no other keys have pressed, it should spawn a space character**.

I tried with Xbindkeys :
```
"/usr/bin/xvkbd -xsendevent -text '\[space]'"
Mode_switch+Release
```
but it prevents the new arrow keys from working.

**Anyone has an idea ?**

Btw, here is the ~/.Xmodmap code for the navigation pad feature (keycode 65 is my spacebar ; you can use an other key to test safely) :
```
keycode 65 = Mode_switch Mode_switch space space nobreakspace U202F
add mod3 = Mode_switch
keysym i = i I Up NoSymbol icircumflex Icircumflex
keysym k = k K Down NoSymbol idiaeresis Idiaeresis
keysym j = j J Left NoSymbol udiaeresis Udiaeresis
keysym l = l L Right NoSymbol U0140 U013F
keysym h = h H Prior NoSymbol eth ETH 
keysym n = n N Next NoSymbol notsign rightarrow
keysym u = u U Home NoSymbol ucircumflex Ucircumflex
keysym o = o O End NoSymbol oe OE
keysym comma = comma question Delete NoSymbol questiondown U2026
keysym p = p P BackSpace NoSymbol ocircumflex Ocircumflex
keysym y = y Y Insert NoSymbol ydiaeresis Ydiaeresis
```

**Maybe should I try Xkbd ? Is it more powerful ?**

Regards.

---

