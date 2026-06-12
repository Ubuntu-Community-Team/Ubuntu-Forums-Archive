---
title: "top bar problem"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by chase321 on 2012-02-18
ok so im not sure how exactly to explain this, but when i open applications in 11.10, i do not get the top taskbar on the application, which causes me the problem of not being able to close the app... any idea what's wrong here?

---

### Post by Lisiano on 2012-02-18
Do you mean this?
[IMG]http://ubuntuone.com/2WSgNVEG9G60fIRUEaxptj[/IMG]

You just hover your mouse over the panel and it should turn into this
[IMG]http://ubuntuone.com/1DXVRYI6ntqsrLFpNUUUih[/IMG]

11.10, 11.04 and all (I think) Ubuntu Netbook Editions maximize the usable screen space by integrating the applications decorations (Or their bar) into the top panel when you maximize the application.

---

### Post by chase321 on 2012-02-20
so here's my problem... when i turn on my computer for the first couple of minutes everything is fine... but then i open something like minecraft for example, and the top bar, where the x button and minimize buttons are located usually disappear... so i am forced to close the program by right clicking on the dock and quitting it... it's not a big problem... but it is kind of annoying.. any ideas?

---

### Post by chase321 on 2012-02-20
no i mean the top bar is not there at all i cannot sceroll over it because it is simply not there

---

### Post by grahammechanical on 2012-02-20
Please do not ask the same question twice. Do not expect instant replies. And do research. Use the search panel to search for previous answers to problems like your one.

Regards.

---

### Post by Lisiano on 2012-02-20
Hmm, are you using Unity2D or Unity3D?
If the former, can you open up a terminal (Ctrl+Alt+T) or a Run lense (Alt+F2) and type in this ```
unity-2d-panel
``` then hit Enter, it should load up the 2D top panel.

If the latter, try running this instead```
unity --reset
```
It should restart Unity 3D with default settings


EDIT: I have re-read the posts multiple times, are you implying that when you open anything, you don't see window decorations? As in the bar with the window name, close, minimize and maximize buttons? You also use it to drag windows around. If so, then please tell is if you have been playing with Compiz or CCSM (Compiz Config Settings Manager) or did anything related to virtual Cubes, if you have, try opening CCSM and make sure you have Move Window, Resize Window, Place Window and Window Decoration ticked. If you can't do anything, switch to Unity2D (Log out, click the cog near your username and select Unity2D) and run ```
unity --reset
``` from there then go back to Unity3D.

---

### Post by wildmanne39 on 2012-02-20
Hi, here is a good link for fixing that problem.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Thanks

---

### Post by cariboo on 2012-02-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by chase321 on 2012-02-22
i havent played with any settings and yes that is what i am saying-->EDIT: I have re-read the posts multiple times, are you implying that  when you open anything, you don't see window decorations? As in the bar  with the window name, close, minimize and maximize buttons? You also use  it to drag windows around.

---

### Post by chase321 on 2012-02-22
sorry i had forgotten that i had already posted the 1st one when i was posting the 2nd one

---

### Post by chase321 on 2012-02-25
ok... so new problem now, still related to the above problem... now my icons are all turning white... i would really like to know what's going on

---

### Post by TwistedTripper on 2012-03-02
To fix windows decoration (ie Top bar - minimise, maximise, close buttons) use this in Terminal;

> gtk-window-decorator --replace & disown

Or save the line in text editor like gedit, then right click the file to get properties. Under the permissions tab put a tick in "Allow executing  file as program" Then when you double click it it should give an option of Run, use that option and windows decorations should re-materialise, for a brief time anyway, the problem will probably come back. Well it does for me - I need a script that'll run it every minute or something LOL.

Maybe someone else knows of a permanent fix for disappearing windows decorations.

As for your other problem I have no idea.

---

