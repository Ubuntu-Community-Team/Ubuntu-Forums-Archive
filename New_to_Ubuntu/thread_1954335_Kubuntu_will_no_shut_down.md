---
title: "Kubuntu will no shut down"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Norman Thom on 2012-04-07
I have just installed Kubuntu 11.10
I am not too familiar with the KDE interface
But it seems to be running fairly well
The problem I'm having is that it will not shut down
The screen goes to black and then freezes
Does anyone know how to fix this problem

Norm

---

### Post by Zorael on 2012-04-08
At what point does it freeze like this? Do you still have a cursor on the screen (and if so, can you move it?), or has it managed to get as far as the shutting-down splash screen?

If you hit **Ctrl+Alt+F1**, do you get a textual login prompt? If nothing at all happens, does it work if you hit **Alt+SysRq+R** and then try the first key combo again?

If it works, try **Ctrl+Alt+F2**, **Ctrl+Alt+F3** etc all the way up to **F8**. Is there at any point any messages listed about the progress of the shutdown procedure?

If you get to the textual login prompt through **Ctrl+Alt+F1**, can you type anything or is it deaf to input? If you can, log in normally and type **dmesg**. Is there anything of interest output at the end? Like, errors, warnings.

If you find nothing at all, try **sudo shutdown now**. That really should get it all rolling.

---

### Post by baruch60610 on 2012-04-08
> **Zorael said:**
> If it works, try **Ctrl+Alt+F2**, **Ctrl+Alt+F3** etc all the way up to **F8**. Is there at any point any messages listed about the progress of the shutdown procedure?


Just one comment: Ctrl-Alt-F7 will bring you to the desktop, if it's still running.  The other combinations will take you to virtual terminals.

---

### Post by PaulW2U on 2012-04-08
> **Norman Thom said:**
> I have just installed Kubuntu 11.10
I am not too familiar with the KDE interface
But it seems to be running fairly well
The problem I'm having is that it will not shut down
The screen goes to black and then freezes
Does anyone know how to fix this problem


This is probably a longstanding bug that seems to affect a few users like myself. I have had to apply a fix to every Kubuntu installation that I've used from 10.04 onwards to enable clean shutdown and logout. I think you may need to edit kdmrc.

You'll find this old thread - [http://ubuntuforums.org/showthread.php?t=1665405](http://ubuntuforums.org/showthread.php?t=1665405) - will explain it just as well as I can.

If this doesn't solve your problem please let us know.

---

