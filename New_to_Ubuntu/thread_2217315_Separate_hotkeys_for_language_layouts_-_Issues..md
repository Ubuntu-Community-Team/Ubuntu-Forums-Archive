---
title: "Separate hotkeys for language layouts? - Issues."
date: 2014-04-16
forum: New to Ubuntu
---

### Post by Ssurge on 2014-04-16
I want to have a combination for several language layouts. 
  
[LIST]
[*]Ctrl + 1 - English US 
[*]Ctrl + 2 - Romanian STANDARD 
[*]Ctrl + 3 - German 
[*]Ctrl + 4 - Swedish 
[/LIST]
 

  I know this might have been asked before, but I need the Romanian standard one. I have done all the  Keyboard -> Shortcuts -> Costum Shortcuts thing, and using setxkbmap -layout ro does not do it for me, it just changes it to the Romanian one not the Romanian Standard one. How can I choose the Romanian STANDARD keyboard (as the default one for Romanian, maybe / anything like a setxkbmap -laout ro standard command?)? I don't want to press Alt Gr a every time I want to write &#259; and so on. I am a new Ubuntu user, so I am sorry for asking such basic questions.

---

### Post by jmbell on 2014-04-16
You might want to check this out. No guarantees on a solution, but it looks promising: [http://askubuntu.com/questions/356357/how-to-use-altshift-to-switch-keyboard-layouts](http://askubuntu.com/questions/356357/how-to-use-altshift-to-switch-keyboard-layouts)

---

### Post by sisco311 on 2014-04-17
Hi, Ssurge and welcome to the forums!

```
setxkbmap ro std
```
should do the trick.

---

