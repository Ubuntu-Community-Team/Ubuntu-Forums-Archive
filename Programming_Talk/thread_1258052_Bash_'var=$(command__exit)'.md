---
title: "Bash 'var=$(command || exit)'"
date: 2009-09-04
forum: Programming Talk
---

### Post by Penguin Guy on 2009-09-04
I have a program that needs to get a list of options from a zenity front-end. Everything works fine apart from the cancel button which, when pressed outputs an error message as expected, but does not end the program as expected. 

**[Bash]** (wrong)
[PHP]
options=$(install-gui || zen error 'User pressed cancel button, aborting.' 'Aborting')
[/PHP]

**[Bash]** (right)
[PHP]
options=$(install-gui) || zen error 'User pressed cancel button, aborting.' 'Aborting'
[/PHP]

Thanks [DaithiF]("http://ubuntuforums.org/member.php?u=867532")!

---

### Post by DaithiF on 2009-09-04
[COLOR=#000000][COLOR=#0000BB]try:
[/COLOR][/COLOR]```
options=$(install-gui) || zen error 'User pressed cancel button, aborting.' 'Aborting'
[COLOR=#000000][COLOR=#007700][/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700] 

otherwise the zen function gets called as a sub-process and so its exit only affects the 
result of that sub-process rather than the top-level script.

[/COLOR][/COLOR]

---

### Post by Penguin Guy on 2009-09-05
> **DaithiF said:**
> [COLOR=#000000][COLOR=#0000BB]try:
[/COLOR][/COLOR]```
options=$(install-gui) || zen error 'User pressed cancel button, aborting.' 'Aborting'
[COLOR=#000000][COLOR=#007700][/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700] 

otherwise the zen function gets called as a sub-process and so its exit only affects the 
result of that sub-process rather than the top-level script.

[/COLOR][/COLOR]
Ahhh, yes I thought it might be something like that but didn't know how to fix it. Thanks, everything works great now. :D

---

