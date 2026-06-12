---
title: "How to save changes made to my keyboard key assignment via 'xmodmap'"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Nmalik31 on 2013-03-10
HI:

[h=1]How to save changes made to key assignment in ubuntu?[/h][COLOR=#333333][FONT=arial]I have made changes to keyboard keys' assignments by way of "**xmodmap**" ,method successfully. **But I want to save these changes permanently for future use as otherwise they go away after I reboot the machine. What command or steps are needed to save them.  I am a beginner in Ubuntu, so please easy simple steps are needed.**[/FONT][/COLOR]

---

### Post by Sylslay on 2013-03-11
Write some line to file, add 

xmodmap -e "keycode 57 = n N nacute Nacute nacute Nacute" 

to

/etc/rc.local

It might works but isn't very elegant :-)

---

