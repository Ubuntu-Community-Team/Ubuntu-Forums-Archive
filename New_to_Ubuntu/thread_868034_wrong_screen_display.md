---
title: "wrong screen display"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by westentertainer on 2008-07-23
hello after my pc shut down unexpecedly my screen display asdefaulted back to 800x600 and normaly it 1200x000  how can i get it back .i have checked the nvida drivers all ok can find anything  many thanks

---

### Post by northern lights on 2008-07-23
If 800x600 is the maximum under "System > Preferences > Screenresolution, run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

Check back if you can select higher...

---

### Post by westentertainer on 2008-07-23
oh no before i tried the above i rebooted to see the log on screen down in the bottom right hand corner ,,so i cant log on  what do i do now

---

### Post by westentertainer on 2008-07-23
tried above now i am stuck in terminal

---

### Post by northern lights on 2008-07-23
How are you "stuck"?

What error message do you get when running "sudo /etc/init.d/gdm start"?

---

### Post by westentertainer on 2008-07-23
please help

---

### Post by westentertainer on 2008-07-23
when i start ubuntu now i can only see the log in screen in the bottom right hand corner   so i can log in to it

---

### Post by northern lights on 2008-07-23
I'm sorry. Please try again and give a full on description. I just can't picture the scene.

Where is the login screen and where is it not?

What happens if you push "Ctrl+Alt+Backspace"?
Can you login via "Alt+F1", then?
Can you start the desktop environment from there?

---

### Post by westentertainer on 2008-07-23
nothing happens with any of them key board commands   the screen looks like it has been shifted down to the right hand bottom corner all i can see is the top left hand corner of my MYTHBUNTU log in screen

---

### Post by northern lights on 2008-07-23
mkey.

Have you tried booting in "Recovery Mode" and reconfiguring x again?

---

### Post by westentertainer on 2008-07-23
MANNNNNNY THANKS recovering x worked

---

