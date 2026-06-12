---
title: "[SOLVED] add a folder link to panel in hardy heron"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by DarinB on 2008-08-13
How do i add a folder link to panel in hardy Gnome Desktop...when i drag the link to the panel it works until the next reboot then it becomes unusable.
when i drag the folder from the source in this case from the documents folder the same thing happens?????
what am i missing????

---

### Post by Elfy on 2008-08-13
Try this - right click panel - add to panle - custom app launcher, in type make it a location - navigate to location - ok.

Works for me ok, at least with a doc it does.

---

### Post by DarinB on 2008-08-13
won't let me pick a folder only a file
strange because i have Documents on my panel...why not a different folder.

---

### Post by Elfy on 2008-08-13
Make a launcher on the panel and instead of browsing to the location fill it in - it has worked here after a logout

I have a launcher to the documents folder in /home, location is - chnage user to suit yours.

> file:///home/*user*/Documents

---

### Post by rbc on 2008-08-13
Try this. Follow the instructions above, but instead of clicking the Browse button, type this in the location field:
file:///path to folder. In other words, the path to my Documents folder was file:///home/bcc/Documents
Problem is, the icon will be the generic launcher icon, not a picture of a folder. That can be changed though. I did not test to see if it survived reboot

---

### Post by anotherdisciple on 2008-08-13
I could be wrong, but I don't think it allows you to go to folders... so you have to trick it I guess. Add a launcher as mentioned above, but for the command type this: 
```
nautilus /path/to/folder
```

That should tell nautilus to open exactly where you want it to.... example:
```
nautilus /home/nick/Pictures
```

That would lead me right to my pictures folder... Also note... CAPS do matter.

---

### Post by DarinB on 2008-08-17
thanks it seems silly once it works but i had to add in the command manually and select location to get to stay after reboot.
to get it right i opened another window navigated to the file and cut and pasted the location after the file:// part. thanks all now i have a clean desktop and all my stuff i use on the panel. i'm happy.

---

