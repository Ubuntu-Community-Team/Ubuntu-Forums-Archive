---
title: "How do I undo the F12 link to '~' ?"
date: 2019-09-17
forum: New to Ubuntu
---

### Post by tianbuntu on 2019-09-17
I am using a Dell desktop with a standard keyboard (no fn button) was learn an external software which uses F12 as one of the short cuts.

However, the shortcut does not seem to work. Since this keyboard was handed down to me, I suspected that the button is faulty, so I opened a terminal and pressed F12 to see the output.

I got the '~' character. 

Is this a normal behaviour? If not, how do I set it back to be linked to F12?

---

### Post by Holger_Gehrke on 2019-09-17
It does the same thing on my machine if I hit F12 in a terminal. Try looking at the keypress event in xev. If I run 'xev' hitting F12 gives me a keyboard event looking like this:
```

KeyPress event, serial 34, synthetic NO, window 0x5800001,
    root 0x4e4, subw 0x0, time 610537995, (-159,-460), root:(712,19),
    state 0x10, keycode 96 (keysym 0xffc9, **F12**), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
Since F12 works as a shortcut in LibreOffice Writer (start numbered list) on my machine, I believe the behaviour in the terminal is normal.

Holger

---

### Post by Impavidus on 2019-09-17
That same ~ appears when I hit F5, F6, F7, F8, F10 or F12 in my xfce4-terminal. It seems normal.

Maybe on your system some other piece of software, like the window manager, intercepts F12 to use it for something. But then, I wouldn't expect to see it in the terminal at all.

---

### Post by cruzer001 on 2019-09-17
So your key is working, what is the software that will not respond?

---

### Post by tianbuntu on 2019-09-18
> **Holger_Gehrke said:**
> It does the same thing on my machine if I hit F12 in a terminal. Try looking at the keypress event in xev. If I run 'xev' hitting F12 gives me a keyboard event looking like this:
```

KeyPress event, serial 34, synthetic NO, window 0x5800001,
    root 0x4e4, subw 0x0, time 610537995, (-159,-460), root:(712,19),
    state 0x10, keycode 96 (keysym 0xffc9, **F12**), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
Since F12 works as a shortcut in LibreOffice Writer (start numbered list) on my machine, I believe the behaviour in the terminal is normal.

Holger


I have tried running 'xev' and it gives a similar output, I guess the F12 button is working well. Perhaps it is the software that is not.

---

### Post by tianbuntu on 2019-09-18
> **cruzer001 said:**
> So your key is working, what is the software that will not respond?

I am using ENVI, a commercial program for viewing satellite images.

---

### Post by cruzer001 on 2019-09-18
Well I can't help with the ENVI program.  My observation is any Function key that produces a "~" is unassigned in the terminal and I do wonder if you should be using another terminal emulator like xterm or...  This IMO should be posted in the ENVI forum.  Further help with Linux can of course be found here, but I think the ENVI pros would be better able to answer this.

That's my two cents :)

---

