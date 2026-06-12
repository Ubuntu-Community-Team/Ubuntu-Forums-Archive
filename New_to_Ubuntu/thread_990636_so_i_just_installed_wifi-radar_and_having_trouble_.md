---
title: "so i just installed wifi-radar and having trouble getting it to work"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by keith071482 on 2008-11-22
i try to open up the program and it gives me an error message, failed to execute child process "su-to-root" [no such file directory] i even tryed reinstalling, im just having trouble all around just getting wifi to work, i dont have a switch to turn wifi on its a little touch button but its not working ??? any ideas need help thank you

---

### Post by cpu_medic on 2008-11-22
Is your wireless card on?

---

### Post by cpu_medic on 2008-11-23
Bump!!!

---

### Post by cpu_medic on 2008-11-23
no one knows huh? wow. that is a first.

---

### Post by Locutus_of_Borg on 2008-11-23
open terminal
sudo -i
wifi-radar

ta-da


first have wireless working

---

### Post by Bucky Ball on 2008-11-23
Yep, you need to have wifi happening so maybe start a thread to get that problem fixed first. I just installed wifi-radar, went to Applications->Internet and there it was. Started app and works perfectly so I would say your wifi is down. That should be first cab off the rank. Make a reliable, stable connection. Or at least get the light on!

---

### Post by Mike Beatty on 2008-12-06
> you need to have wifi happening so maybe start a thread to get that problem fixed first.
The program should still start regardless of whether the wifi is working or not.
MY wifi is working and I get the same error message. This has to do with permissions, as wifi-radar needs to be run as root.I used to be able to run it from the menu but since I had to reinstall Intrepid, it doesn't.
The question I hope someone can answer is how do I make the shortcut run as root?

---

### Post by fredbird67 on 2008-12-09
If you're running GNOME, try this:

1) Right-click on "Applications" (or whatever you have for a menu or "Start" button -- sorry to borrow a Windows term there).

2) Click on "Internet" to display all Internet-related programs in the pane on the right.

3) Right-click on "Wifi-Radar" and click "Properties" in the menu that pops up.

4) In the box where it says "Wifi-Radar", add "gksudo " before the command to start the Wifi-Radar".  You'll still have to enter your password, though, but at least it'll run with sudo privileges.

---

