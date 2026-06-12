---
title: "[SOLVED] no caps, shift key doesn't seem to be working"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-11
well, obviously this post is going to be in all lower case letters, UNLESS I USE THE CAPS LOCK BUTTON...:lolflag:

  my keyboard was working fine this morning, but for some reason it's not now, when i hold down the shift key to type a capital letter, it doesn't type anything at all, of course i could work around that for a little while by using the caps lock button, but unfortunately that doesn't help me out on typing e-mail addresses. and thats a bummer, tried hardware testing but that was no help. even launchpad wanted me to put in my e-mail address. 

 any ideas on what i can do to check this out/...oops cant type a question mark either. this is odd. 
 thought maybe some of you keyboard gurus out there could shed a little light on the subject. as far as i can tell it is just the shift keys, good thing you have to log in with lower case.

thanks

---

### Post by Ripfox on 2008-06-11
Shift keys go bad...try a different keyboard first then assume it's a software issue.

---

### Post by Dutch70 on 2008-06-11
Still no go, I tried a different keyboard, same problem. So I thought I would log into Vista just to be sure, and as you can see. it's working fine.
 I just got Ubuntu installed correctly and was getting all my updates and things, so if I have to I'll just reinstall again, but I would really like to try and fix things. Or figure out what I did wrong So I dont do it again. 

BTW a week ago, I didnt even know what linux was. So I am learning ever so fast. If it was the entire keyboard, I'd have a better Idea where to search for a solution.

does anyone have any other ideas they wouldnt care to suggest, at this point ll try just about anything before reinstalling..

---

### Post by Dutch70 on 2008-06-11
reinstall didnt fix anything. seems i have bigger problems than a shift key not working, i am marking this solved.

---

### Post by thestef on 2008-11-05
> **Dutch70 said:**
> reinstall didnt fix anything. seems i have bigger problems than a shift key not working, i am marking this solved.


i confirm this bug, suddely the shift key stops working

---

### Post by bluefightingcat on 2008-11-06
Hi I have the same problem however only my question mark and underscore are not working. It has something to do with Xorg or xserver and the keymap. 

Did you manage to get your keyboard working.

BFC

---

### Post by jesuspresley on 2009-01-10
can you please mark this thread as unsolved again - because there is no solution for the initial problem. 

thanks ahead.

---

### Post by bluefightingcat on 2009-01-10
Hi,

I managed solve my problem by deleting .kde4 in my home directory. 

Maybe that will help you. 

BFC

---

### Post by flyboyinpa on 2009-02-18
i'm having the same problem as dutch 70, i tried switching keyboards, didn't help

---

### Post by AlexanderDGreat on 2011-03-29
Is anyone using vmware? Type in terminal, setxkbmap

---

### Post by White_Hat_Maurok on 2011-03-30
This definitely isn't solved because I'm having the same issue. Tried 4 different keyboards... under ubuntu, no shift but under windows its fine.

---

### Post by White_Hat_Maurok on 2011-03-30
A little bit of data here to hopefully help in the diagnostics of this issue...

I ran xkbevd to obtain the following data:

On pressing the left shift key)
XkbStateNotify event, serial 13, synthetic no, device 3, time 7595924,
keycode 50, eventType KeyPress,
group= 0, base= 0, latched= 0, locked= 0.
mods= 0x11*, base= 0x01, latched= 0x00, locked= 0x10
grab mods= 0x11*, compat grab mods= 0x11*
lookup mods= 0x11*, compa lookup modes- 0x11*
compatState = 0x11*, ptr_buttons= 0x0000

the right shift key reports keycode 62

This is how the values change between Press and Release (if its not listed, it didn't change)

value name=Press>Release
---------------------------------
mods=11>10
base=01>00
grab mods=11>10
compat grab mods=11>10
lookup mods=11>10
compat lookup mods=11>10
compatState=11>10

While I'm a noob to ubuntu / linux, I can tell from this that it is not a hardware problem because obviously the keypress is being passed to the system. The question now I guess is what is the next step in making a letter either shifted or not?

---

