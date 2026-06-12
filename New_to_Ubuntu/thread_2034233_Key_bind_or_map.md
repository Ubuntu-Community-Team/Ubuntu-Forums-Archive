---
title: "Key bind or map?"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by ranea on 2012-07-28
Hi there,

My new notebook has one of those keyboards that has a Fn key on the lower left corner, so it makes it almost impossible to press both SHIFT and CTRL keys with the same finger. This may sound a bit extreme, but since I use this machine a lot I find it pretty annoying not being able to use this simple shortcut whit only one finger.

Since the Fn key seems useless to me I figured I could just make it work exactly like the left control key, so no matter which one of the two I press, I will get the same result.

So, I tried to do some research on the matter and found a great xev+xmodmap solution to bind this Fn key to CTRL. It sounded like a nice way to fix it, but it didn't change anything except that now when I run the test xev mode, every time I press the Fn key I get the KEYSYM for Control_L, which I guess means that now the Fn key sends a signal that is supposed to be just like the left CTRL key, but when I actually try to use it as CTRL, nothing happens.

Here's what I did to bind it:
```
xmodmap -e 'keycode 151=Control_L'
```

And here's the output from xev now:
```
KeyPress event, serial 36, synthetic NO, window 0x3a00001,
    root 0xb0, subw 0x0, time 43924424, (19,-10), root:(686,42),
    state 0x0, keycode 151 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3a00001,
    root 0xb0, subw 0x0, time 43924435, (19,-10), root:(686,42),
    state 0x0, keycode 151 (keysym 0xffe3, Control_L), same_screen YES,
    XKeysymToKeycode returns keycode: 37
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x3a00001,
    root 0xb0, subw 0x0, time 43924936, (19,-10), root:(686,42),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x3a00001,
    root 0xb0, subw 0x0, time 43925075, (19,-10), root:(686,42),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
The first two are from the Fn key and the last ones are from the actual left CTRL key.

So I wonder, am I confused about what a key bind is? How should I solve this?

Thanks in advance for ANY tip you can provide!

---

