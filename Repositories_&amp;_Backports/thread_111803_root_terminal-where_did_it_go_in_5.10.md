---
title: "root terminal-where did it go in 5.10"
date: 2006-01-03
forum: Repositories &amp; Backports
---

### Post by mjezell on 2006-01-03
hi i'm mike.

i've been using ubuntu for about a year now and we've been get along just find.  Along comes 5.10 and and i want to upgrade but i can't find the root terminal.  i don't want to sudo i like using the terminal as root.  Tried konsole but you don't get root privilages with it.  it's probably right under my nose but i've been looking for it for several months and thought i might need some help.  thanks to anyone that is willing to spend the time on this.

regards,
mike

---

### Post by kingsidy on 2006-01-03
i think that the root terminal is in the application > system tools menu. sudoing is basically the same as using the root terminal.

---

### Post by equilibriusmind7 on 2006-01-20
[QUOTE=mjezell]hi i'm mike.

i've been using ubuntu for about a year now and we've been get along just find.  Along comes 5.10 and and i want to upgrade but i can't find the root terminal.  i don't want to sudo i like using the terminal as root.  Tried konsole but you don't get root privilages with it.  it's probably right under my nose but i've been looking for it for several months and thought i might need some help.  thanks to anyone that is willing to spend the time on this.

regards,
mike[/QUOTE]


Well, I've been using ubuntu lately, and i've come up with something. Perhaps this would be of help to you. on the main menu, go to "Applications-->System Tools-->Applications Menu Editor. 

On the left panel, scroll down and select system tools, then simply check the box "Root Terminal" (i belive it is unchecked by default. 

Another solution is by going to the terminal, typing in "sudo passwd" 
There you could enter your password, and create a password for you computer.
That way, you wouldnt have to type "sudo", but rather just "su" to get root privilages ;0)

Hope that helped

---

### Post by hav0x on 2006-01-20
"sudo -i" on any terminal gives you that # prompt you like so much too.

---

