---
title: "Ubuntu freezing, any option for CTRL+ALT+DEL?"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-29
Using Ubuntu 13.10 with Gnome 3.8 on an DELL Inspiron 1525, quite an old computer but still works great.

Sometimes it just freezes though, happened a few time for me with FireFox where I use an imacro at.
And I wonder if there is anything I can unfreeze this?

Like in Windows, the CTRL+ALT+DEL trick use to work for this.
Is it anything like this for Ubuntu?

The only way I find to unfreeze this sometimes (when it is freezed for like minuts), then I just shut down the computer and starting it up again.
But any other solution where I maybe can stop the processes somehow and wont be able to restart the computer? Where it just kills whatever that freezing it up.

---

### Post by Bashing-om on 2013-11-29
Niemil; Hi !

Try this :
depress the alt and prt scrn keys together, and while holding them down press s l o w l y the key sequence r s e i r b.

Which should kill all processes gracefully and reboot the system.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by peter d on 2013-11-30
Surely it's alt + printscreen and then r e i s u b (that's busier backwards). Doing it slowly is important though.

---

### Post by Impavidus on 2013-11-30
Actually, it's alt+SysRq, which may be the same key as printscreen, but this is not the case on all keyboards.

---

### Post by ciroberts on 2013-11-30
I agree with peter d, it is Alt+PrtSc and  R E I S U B (busier backwards)...this brings about an intelligent shutdown, much safer than just holding the power button :)

---

### Post by Bashing-om on 2013-11-30
The way I learned it:
Raising Skinny Elephants Is Risky Business. 
Works well, the wife's machine - for no known reason locks up now on occasion - 13.04 Lubuntu .

[INDENT][INDENT]ubuntu, many roads to one end
[/INDENT][/INDENT]

---

### Post by Iowan on 2013-11-30
A similar discussion:
[http://ubuntuforums.org/showthread.php?t=1509765](http://ubuntuforums.org/showthread.php?t=1509765)

---

### Post by electrohandyman501 on 2013-11-30
Is the whole system freezing or just the forground program. 
Windows C+A+D would let you bring up task manager to be able to close the frozen program. The equivelent here is System Monitor. With it you can close (end processes) that are causing issues without killing entire machine.

By default in Ubuntu Gnome desktop the C+A+D sequence brings up the "log out" popup. You can change that hot key sequence to bring up "gnome-system-monitor" instead. I just experimented with mine and it works..... 

It's under 'system settings>keyboard>shortcuts' and make your entry on the custom shortcuts header.. If you still want the "log out" popup change the hot key sequence to something else. I changed mine to 'ctl+alt+o' so then I could use the del key with my custom. Realistically you can use any key sequence you want that isn't already used for something else.

Read here:
[http://lifehacker.com/5426289/use-system-monitor-to-kill-stuck-processes-in-linux](http://lifehacker.com/5426289/use-system-monitor-to-kill-stuck-processes-in-linux)

---

### Post by GGG83kf on 2013-11-30
I am not entirely sure about this. Perhaps we can press Ctrl+Alt+F1 to switch to tty1, and control the system from there?

---

