---
title: "Shift + d not working"
date: 2014-11-28
forum: New to Ubuntu
---

### Post by Aneesh_De on 2014-11-28
I have a weird bug that I'm not sure how to fix. It appears that Shift + D has been mapped to something else, somehow. The only way I can type a 'D' is with caps lock. Lower case d works just fine. Also, When I try Shift + d on the terminal, it reacts to it (the solid cursor box becomes hollow while the buttons are pressed. Both left and right shift are affected.

Any ideas? I'm on 14.041

---

### Post by GrouchyGaijin on 2014-11-29
wow - what happens when you press shift+d?  Just nothing?
Did you recently try to map any keyboard shortcuts?

---

### Post by chopra on 2014-11-29
type the following into your terminal, and then show what you get:

xmodmap -pk

You should get a list of all of the keys.

 40        0x0064 (d)    0x0044 (D)    0x0064 (d)    0x0044 (D)    

That's what I get for the "d" key on my keyboard.

What does it say for you for the d key, and is it just the letter d, or are your shift keys altered? You can check this by typing 

xmodmap -pm

and this will give you the modifier keys.

---

### Post by Aneesh_De on 2014-11-29
When I press Shift + d, usually nothing happens. In terminal, the solid cursor goes hollow. 
No, no mapping done recently (or ever).

My "d" key gives the same result.

> 40        0x0064 (d)    0x0044 (D)    0x0064 (d)    0x0044 (D)

The modifier's list didn't yield anything.
> shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

Please help me out, this is getting EXTREMELY annoying :(

---

### Post by Impavidus on 2014-11-30
The cursor going hollow suggests the window loses focus. In most applications you don't notice, except that the window decorations may turn grey (depending on your theme). The desktop environment (or whatever component exactly is responisble for that) seems to intercept shift+d and reacts by changing the focus to ... the desktop maybe?

---

### Post by Aneesh_De on 2014-11-30
> **Impavidus said:**
> The cursor going hollow suggests the window loses focus. In most applications you don't notice, except that the window decorations may turn grey (depending on your theme). The desktop environment (or whatever component exactly is responisble for that) seems to intercept shift+d and reacts by changing the focus to ... the desktop maybe?

Holy crap, you were absolutely right! I was using Cairo Dock, and one of the "Short Keys" is Shift + D. I never understood because the intended function never worked. I tried do disable it altogether, but I guess for now, assigning it to F1 is good enough.

Thanks a million!

---

### Post by GrouchyGaijin on 2014-12-01
You might want to use F2.  F1 is often used for help.

---

