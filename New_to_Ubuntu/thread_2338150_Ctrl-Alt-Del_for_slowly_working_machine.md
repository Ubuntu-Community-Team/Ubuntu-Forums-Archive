---
title: "Ctrl-Alt-Del for slowly working machine"
date: 2016-09-25
forum: New to Ubuntu
---

### Post by tonma on 2016-09-25
Hi,

I tried to install a software today that caused the OS to run very slowly, and it was basically stuck. I had to wait a few minutes for it to work again.

Is there a way to close the culprit without waiting / resetting? 

*The OS was not responsive with mouse or keyboard (But maybe there is a keyboard combination that might release it just like in Windows, where keyboard doesn't respond, but the magical Ctrl Alt Del takes you to the Taskbar)

Ty!

---

### Post by ajgreeny on 2016-09-25
Was this a GUI application or a command line utility running in the background, ie with no window to see?

For GUI apps that do this (very occasionally, I admit) I have set a keyboard shortcut of Winkey+Del to run xkill.  That turns the cursor into an X and any window you click on with that should close; when needed it has never failed me.

If a command line utility in the background you will need to know either the name of the program or the process-ID number.
You can then run command ```
pkill <program>
``` or ```
kill process-ID
```
Assuming you can open a terminal you can find the process-ID from the **top** command.

---

### Post by oldfred on 2016-09-25
If keyboard is working, you want to remember the elephants.

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by HermanAB on 2016-09-25
You can use htop or xkill to easily shut down problem programs.

---

### Post by colin.p on 2016-09-27
> **ajgreeny said:**
> For GUI apps that do this (very occasionally, I admit) I have set a keyboard shortcut of Winkey+Del to run xkill.  That turns the cursor into an X and any window you click on with that should close; when needed it has never failed me.

Thanks for that, works great.

---

### Post by ajgreeny on 2016-09-27
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by HermanAB on 2016-09-27
Just note that xkill is totally indiscriminate.  If you click on your desktop then it will close, leaving you staring at a black screen and scratching your head.

---

### Post by tonma on 2016-09-28
Thanks everyone

> **HermanAB said:**
> Just note that xkill is totally indiscriminate.  If you click on your desktop then it will close, leaving you staring at a black screen and scratching your head.

What should I do in that case to restore the desktop ? :D

---

### Post by howefield on 2016-09-28
> **tonma said:**
> What should I do in that case to restore the desktop ? :D

If you are using stock Ubuntu, ie, with Unity, it probably won't kill the desktop but will kill Files (Nautilus) so all that should happen is that files/shortcuts on the desktop will disappear. Loading a new instance of Files (Nautilus) should bring them back. 

Not sure about other desktop environments but I wouldn't suggest that you try it in any case :)

Worst case scenario a Ctrl+Alt+F1 to a tty should allow you to reboot safely.

---

### Post by tonma on 2016-09-28
Ctrl+Alt + F1 is buggy for me: All I get is black screen when doing it

---

