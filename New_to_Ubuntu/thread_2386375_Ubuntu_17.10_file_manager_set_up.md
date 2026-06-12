---
title: "Ubuntu 17.10 file manager set up"
date: 2018-03-05
forum: New to Ubuntu
---

### Post by jobtmp on 2018-03-05
**Set up:** Ubuntu 17.10

**Problem:** The File Manager starts at the user home directory (sergey@home-X200CA). Cannot see mounted devices. 

[B]Questions:
[/B]1. How to change the starting point of the FM to root (/)
2. What else if any should be done to see the mounted devs?

Thanks in advance,
jobtmp

---

### Post by kerry_s on 2018-03-05
problem: mounted devices should be on the left side of the file manager

1. why ? there's no real need to be messing around on the /root side
2.do you have desktop icons turned on ? install gnome tweaks & select what you want to show.
[ATTACH=CONFIG]278806[/ATTACH]

---

### Post by jobtmp on 2018-03-05
TY for the prompt answer. 

[B]Re: Mounted devs.
[/B] Actually I can see the devs when I open files say for sending via email etc. But I cannot see them in the FM per se. I understand that the list of the devs should show in the left side bottom of the FM but it doesn't.

**Re: desktop Icons**
I can see the icons on the desktop. Do I still need   the "[COLOR=#000000]gnome tweaks[/COLOR]". Pls advise how to attach files here so I could send a printscreen.

---

### Post by ajgreeny on 2018-03-05
It sounds as if the settings for nautilus (gnome file-manager) are not to show the side panel when it is opened.

I no longer use Ubuntu but Xubuntu with another file-manager, thunar, but I'm sure there must be some way to get to the preferences for your file-manager and make sure the side panel always shows.

---

### Post by cruzer001 on 2018-03-05
> How to change the starting point of the FM to root (/)

Untried by me, but sounds like this:

[https://askubuntu.com/questions/706672/how-to-set-default-opening-folder-for-nautilus-file-manager](https://askubuntu.com/questions/706672/how-to-set-default-opening-folder-for-nautilus-file-manager)

---

### Post by kerry_s on 2018-03-05
if you have gnome, it's nice to have gnome tweaks for the extra settings.

how are these devices mounted ? 
or 
what kind of devices ?

this is the way it's suppose to work:
when you plug in a device you get a notification, which you can click on for quick access
it shows in the fm on the left with a ejection button to the right
on mine it also shows on the desktop

i don't have my sidebar showing on my setup, so i use the other options for access

---

### Post by deadflowr on 2018-03-05
> Pls advise how to attach files here so I could send a printscreen.
Click on Reply to Thread.
Then click on the paperclip icon in the toolbar.
Then in the pop-up window in the top left corner click on Add Files. (then click on Choose file)
Then find your file in your folders. And highlight the file to select.
Then click on Upload to upload the selected file.
Uploaded attachments automatically get placed in the post's queue, so no need to drag anything around (exceptions being they uploaded out of order, in which case you can switch them around if you want)
Then click Done at the bottom right corner of the pop-up window to exit.

Hope it helps

---

### Post by jobtmp on 2018-03-06
It looks like I cannot see the left-hand side of the FM panel (pls see the screenshot below).
However it can be seen if the FM is started not from the task panel but from another application, e.g. mail agent . Please advise if possible.

---

### Post by kerry_s on 2018-03-06
click on files at the top-> check sidebar

---

### Post by jobtmp on 2018-03-06
Yes it has helped. Thank you. Pls see the response below.

---

### Post by jobtmp on 2018-03-06
> **kerry_s said:**
> click on files at the top-> check sidebar

Yes, it has worked. Thank you..
With my eyesight not being very good just missed the smallish menus.

---

### Post by kerry_s on 2018-03-06
yeah, i feel ya. 
i'm diabetic my sight goes in & out depending on my sugar level. i turn off all those smooth fonts cause it's easier on my eyes.

---

### Post by ajgreeny on 2018-03-06
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

