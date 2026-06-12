---
title: "Force Quit"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by beanstalker on 2008-07-19
I use a very slow old laptop to run my ubuntu system and frequently have problems with unresponsive applications. In Mac OSX there is a force quit menu that you can open to terminate any application, using a keyboard shortcut. The only similar application that I can find in ubuntu is system monitor and I cannot find how to add a keyboard shortcut for it. I have had several incidents where the entire system freezes and I can do anything except crash using the power button. Does anybody know of anything that might help? Perhaps something similar to windows Ctrl-Alt-Del?

Cheers,
Jack

---

### Post by Oldsoldier2003 on 2008-07-20
> **beanstalker said:**
> I use a very slow old laptop to run my ubuntu system and frequently have problems with unresponsive applications. In Mac OSX there is a force quit menu that you can open to terminate any application, using a keyboard shortcut. The only similar application that I can find in ubuntu is system monitor and I cannot find how to add a keyboard shortcut for it. I have had several incidents where the entire system freezes and I can do anything except crash using the power button. Does anybody know of anything that might help? Perhaps something similar to windows Ctrl-Alt-Del?

Cheers,
Jack

right click a panel, select add to panel. select the force  quit application and add it to the panel.

---

### Post by beanstalker on 2008-07-20
Brilliant! That´s perfect, Thanks! :)

---

### Post by carandraug on 2008-07-20
It's called REISUB (one of the mnemonics is Raising Elephants Is So Utterly Boring). Press in this order and give 2-3 seconds of interval between them
Alt + SysRq + R  <-- tries to get keyboard back
Alt + SysRq + E  <-- term signal
Alt + SysRq + I  <-- kill signal
Alt + SysRq + S  <-- synchronizes filesystems
Alt + SysRq + U  <-- unmount and mounts filesystems in read-only mode
Alt + SysRq + B  <-- reboot

SysRq is the Print screen button (in some laptops you may need to press Fn at the same time)

This will give you a safe reboot. You can use Alt + SysRq + O in the end for shutdown instead of reboot.

Edit: upps, I'm back from the time when Ctr + Alt + Del was mostly used twice to reboot windows instead of killing just an application. Ignore the post then.

---

### Post by beanstalker on 2008-07-20
Do you have to go through all of the commands or can you stop at some point if the system restabilises?

---

### Post by hansdown on 2008-07-20
Hi beanstalker. You can get the ubuntu cheatsheet here.[http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/](http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/)

---

### Post by Jim! on 2008-07-20
You may find this useful: Press "Alt +F2" and type "xkill" then just click on whatever you want to close;)

---

### Post by beanstalker on 2008-07-20
Ok, I just had a go at using the REISUB method and it seemed to work until it began the reboot. It restarted up to the point where it shows a blank white screen similar to just after you log in but before the desktop loads. It got totally stuck there, I left for about 10mins as I know my laptop is very slow, but in the end I had to crash using the power button again. Is there a set of commands needed to make it load?

---

### Post by sharks on 2008-07-20
type in terminal killall nameoftheprocess

Or if u want instant logout press ctrl+alt+backspace

---

### Post by carandraug on 2008-07-20
> **beanstalker said:**
> Do you have to go through all of the commands or can you stop at some point if the system restabilises?Yes, you can stop in the middle of the combination. Take a look at [wikipedia's page]("http://en.wikipedia.org/wiki/Magic_SysRq_key") about it.> **beanstalker said:**
> Ok, I just had a go at using the REISUB method and it seemed to work until it began the reboot. It restarted up to the point where it shows a blank white screen similar to just after you log in but before the desktop loads. It got totally stuck there, I left for about 10mins as I know my laptop is very slow, but in the end I had to crash using the power button again. Is there a set of commands needed to make it load?
What do you mean by a set of commands to make it load? Anyway, the blank screen that you got is not normal at all and the REISUB thing is something that one will rarely need. You're basically sending orders directly to the kernel (and by the way, the kernel is what should be called Linux, not the pack of software that comes with a distro) and if even if everything else is frozen, the kernel should still answer.

---

### Post by Catbells on 2012-11-24
oops

---

### Post by Catbells on 2012-11-24
> **carandraug said:**
> Yes, you can stop in the middle of the combination. Take a look at [wikipedia's page]("http://en.wikipedia.org/wiki/Magic_SysRq_key") about it.
What do you mean by a set of commands to make it load? Anyway, the blank screen that you got is not normal at all and the REISUB thing is something that one will rarely need. You're basically sending orders directly to the kernel (and by the way, the kernel is what should be called Linux, not the pack of software that comes with a distro) and if even if everything else is frozen, the kernel should still answer.

Really like this idea, though I haven't had an opportunity to try it  yet.  I saved it in a text file, went to gconf-editor -> metacity,  set command_1 to open my text file, and set F9 to be the key binding for  run_command_1.  Pressing F9 opens my text file.  At least I have some  emergency help should a program crash taking my cursor with it.

---

### Post by wildmanne39 on 2012-11-24
Old thread closed.

---

