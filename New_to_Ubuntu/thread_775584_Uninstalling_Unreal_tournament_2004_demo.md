---
title: "Uninstalling Unreal tournament 2004 demo?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by sevenape on 2008-04-30
Hi, I installed this demo earlier today and it doesn't run unfortunately... I guess I need to uninstall it but don't know how. When I go to the Folder in my home directory it seems to be locked. 

Thanks for any help :)

---

### Post by hermes0710 on 2008-04-30
> **sevenape said:**
> Hi, I installed this demo earlier today and it doesn't run unfortunately... I guess I need to uninstall it but don't know how. When I go to the Folder in my home directory it seems to be locked. 

Thanks for any help :)

How did you install it?

---

### Post by sevenape on 2008-04-30
I typed this into the terminal: 

cd ~/Desktop
sudo chmod +x ut2004-lnx-demo3334.run
sudo sh ut2004-lnx-demo3334.run

---

### Post by hermes0710 on 2008-04-30
> **sevenape said:**
> I typed this into the terminal: 

cd ~/Desktop
sudo chmod +x ut2004-lnx-demo3334.run
sudo sh ut2004-lnx-demo3334.run

Any readme present? Try running ```
sudo sh ut2004-lnx-demo3334.run --uninstall
``` or ```
sudo sh ut2004-lnx-demo3334.run --help
``` to see available options

---

### Post by sevenape on 2008-04-30
results in this: 

sh: Can't open ut2004-lnx-demo3334.run

Is that cos I deleted the original file off the desktop once it was installed?

I'm such a windows user! :D

---

### Post by BB_DaKraxor on 2008-04-30
I have the full version installed, and in the game directory, there is a script called "uninstall". I'm pretty sure you have the same script, try running it.

If you don't know where you installed the game, try ```
locate ut2004
```.

---

### Post by hermes0710 on 2008-04-30
> **sevenape said:**
> results in this: 

sh: Can't open ut2004-lnx-demo3334.run

Is that cos I deleted the original file off the desktop once it was installed?

I'm such a windows user! :D

Check this out:

[http://forums.fedoraforum.org/showthread.php?t=97756]("http://forums.fedoraforum.org/showthread.php?t=97756")

---

### Post by sevenape on 2008-04-30
tried that locate command and it just brought the prompt up again immediately. 

I can see the folder in my home folder but when I click on properties it's says the folder is unreadable.

---

### Post by sevenape on 2008-04-30
thanks i'll check that link now.

---

### Post by BB_DaKraxor on 2008-04-30
You could do ```
updatedb
``` to update the database for locate, then try to locate again. Or you could use the find command, which is a bit slow, or just try and search manually. I'm sure the installation directory is something like /usr/games/ut2004 or something similar. If you find it, cd into it and start the uninstall script by typing```
./uninstall
```

---

