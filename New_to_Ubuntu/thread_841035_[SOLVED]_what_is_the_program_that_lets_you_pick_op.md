---
title: "[SOLVED] what is the program that lets you pick open in terminal?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-06-26
I had this nifty little thing in ubuntu once, which allowed me to pick open in terminal from nautilus, and it would bring up a terminal, already in the directory I was in while I was in nautilus. Since then, I have reinstalled, and I miss it. Can you please tell me what it was called, so I can apt-get install it again. 

thanks in advanced.

---

### Post by iaculallad on 2008-06-26
> **barbedsaber said:**
> I had this nifty little thing in ubuntu once, which allowed me to pick open in terminal from nautilus, and it would bring up a terminal, already in the directory I was in while I was in nautilus. Since then, I have reinstalled, and I miss it. Can you please tell me what it was called, so I can apt-get install it again. 

thanks in advanced.

Would that be:

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by cdtech on 2008-06-26
sudo aptitude install nautilus-open-terminal

---

### Post by barbedsaber on 2008-06-26
> **iaculallad said:**
> Would that be:

```
sudo apt-get install nautilus-open-terminal
```

Thanks for your reply, I ran that command, and It installed, but it still doesn't give me the option to open in terminal. I believe that the last time I installed it, I had to install 2 things. hmm...

---

### Post by iaculallad on 2008-06-26
> **barbedsaber said:**
> Thanks for your reply, I ran that command, and It installed, but it still doesn't give me the option to open in terminal. I believe that the last time I installed it, I had to install 2 things. hmm...

Try to open any folder using Nautilus and righ-click on/inside that window, you can see an option w/c say's "Open in terminal".

---

### Post by cdtech on 2008-06-26
You may need to restart gnome / nautilus for the change to take effect. Just ctrl + alt + backspace to reset.....

---

### Post by barbedsaber on 2008-06-26
> **iaculallad said:**
> Try to open any folder using Nautilus and righ-click on/inside that window, you can see an option w/c say's "Open in terminal".

tried that, might try restarting X (restarting stuff seems so windowsy)

---

### Post by barbedsaber on 2008-06-26
ooh, thanks, if you need me, I will be at a terminal.

---

### Post by iaculallad on 2008-06-26
> **barbedsaber said:**
> tried that, might try restarting X (restarting stuff seems so windowsy)

Just try to logoff then log back in instead of doing "so windows" :)

---

### Post by cdtech on 2008-06-26
If you want functionality for nautilus check out this site for scripts to add to nautilus:

[[COLOR="DarkRed"]http://g-scripts.sourceforge.net/[/COLOR]]("http://g-scripts.sourceforge.net/")

Drop them into ~/.gnome2/nautilus-scripts and set them to executable.

---

