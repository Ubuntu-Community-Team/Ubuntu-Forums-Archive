---
title: "Running custom command on Terminal start-up"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by MHN on 2011-09-26
Hi,

I was running a telnet command on start-up of GNOME terminal. And had specified that the terminal exit when command exits. But, now that address is not valid.
Since, the terminal is unable to connect to that address it exits straight-away. Is there some other was, I can change the preferences. Because the terminal exits before I can select any menu on my terminal.


Thanks,
Mohan

p.s. typo --- The title should read "running custom command on Terminal start-up"

---

### Post by nothingspecial on 2011-09-26
> **MHN said:**
> 



p.s. typo --- The title should read "running custom command on Terminal start-up"

Now it does :)

---

### Post by WasMeHere on 2011-09-26
Will this help you?
Write _gconf-editor_ in the text-box created by Alt + F2, then use the menus!
Good luck/Olle
> **fernandinho said:**
> hi people,

I've had the same problem recently and after reset all my gnome settings to fix it, I discovered that it was more simple than I had thought.

All gnome-terminal settings can be changed there:

Alt + F2 > gconf-editor > apps > gnome-terminal

any problem with gnome-terminal can be solved there.

I hope that helps.

---

### Post by MHN on 2011-09-26
> **nothingspecial said:**
> Now it does :)
Thanks :)

---

### Post by MHN on 2011-09-26
> **Olle Wiklund said:**
> Will this help you?
Write _gconf-editor_ in the text-box created by Alt + F2, then use the menus!
Good luck/Olle
Thanks a lot. It did help.

Once I was there, I just deleted the old profile. So, it works fine now.

---

### Post by Robin Wynne-Lloyd on 2011-09-28
Great worked for me too. Thanks

---

