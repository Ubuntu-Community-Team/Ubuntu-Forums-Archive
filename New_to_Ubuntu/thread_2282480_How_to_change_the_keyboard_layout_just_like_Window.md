---
title: "How to change the keyboard layout just like Windows?"
date: 2015-06-14
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-06-14
Hello guys 
Is there a way to change the keyboard layout by pressing Alt+Shift just like in Windows.
Thanks

---

### Post by Vladlenin5000 on 2015-06-14
The default for Ubuntu is SUPER (the Windows key) + SPACE and SUPER + SHIFT + SPACE to toggle to the previously used keyboard layout (the first key combo can be used as well, the difference being it'll toggle to the different keyboard layouts sequentially... So, if you only have two different layouts configured, SUPER+SPACE is all you need.

It can be changed to another key combination but I strongly advice against it because it could mess with other default shortcuts.

---

### Post by chopra on 2015-06-16
You can also write a script to change the keys, and another one to  restore them.  For instance, I sometimes need to swap the numeric keypad  home and end with the standard home and end, as well as the numeric  keypad arithmetic with that of the standard keyboard arithmetic, so I wrote a  script as follows:

```
xmodmap -e "keycode 87 = End KP_1 End KP_1"

xmodmap -e "keycode 110 = KP_Home NoSymbol KP_Home"

xmodmap -e "keycode 104 = Return NoSymbol Return"

xmodmap -e "keycode 86 = plus plus plus plus plus plus XF86Next_VMode"

xmodmap -e "keycode 82 = minus minus minus minus minus minus XF86Prev_VMode"

xmodmap -e "keycode 63 = asterisk asterisk asterisk asterisk asterisk asterisk XF86ClearGrab"

xmodmap -e "keycode 106 = slash slash slash slash slash slash XF86Ungrab"

and to restore all back to normal:

xmodmap -e "keycode 87 = KP_End KP_1 KP_End KP_1"

xmodmap -e "keycode 110 = Home NoSymbol Home"

xmodmap -e "keycode 79 = KP_Home KP_7 KP_Home KP_7"

xmodmap -e "keycode 104 = KP_Enter NoSymbol KP_Enter"

xmodmap -e "keycode 86 = KP_Add KP_Add KP_Add KP_Add KP_Add KP_Add XF86Next_VMode"

xmodmap -e "keycode 82 = KP_Subtract KP_Subtract KP_Subtract KP_Subtract KP_Subtract KP_Subtract XF86Prev_VMode"

xmodmap -e "keycode 63 = KP_Multiply KP_Multiply KP_Multiply KP_Multiply KP_Multiply KP_Multiply XF86ClearGrab"

xmodmap -e "keycode 106 = KP_Divide KP_Divide KP_Divide KP_Divide KP_Divide KP_Divide XF86Ungrab"
```


Not sure if that's the kind of thing you're after or not.

---

### Post by wildmanne39 on 2015-06-16
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

