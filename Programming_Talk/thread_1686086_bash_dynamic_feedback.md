---
title: "bash dynamic feedback"
date: 2011-02-11
forum: Programming Talk
---

### Post by Simon Cropper on 2011-02-11
Hi,

I have a backup routine that copies my important files from one computer to another using rsync. I use 'notify-send' to provide immediate feedback to the user via the normal notification system.

I also dump the logs to a directory. Each log named "STEP 1 - Backup of HOME on Main Computer", 'STEP 2 - Backup of ...", etc. The aim is to provide a static log of the progress, which can at times take a couple of hours. All I do is view the backup log directory and I can see how far the backup has gone.

This slap up option was devised as I was unable to find a way of problematically providing a dynamic log. I am now looking at ways to make this feedback system more user friendly.

Ideally I would like to present a window showing progress of the backup (icons + text) with the ability of adding completed tasks to the bottom of the list as the outcome of each task is known. Successfully completed tasks would have a tick followed by text explaining the outcome and unsuccessful ones a cross with what error was encountered. The window once open should be able to be updated and refreshed from a bash script.

Initially I though I could do this by showing a text-info box in zenity but windows once opened could not be refreshed - so the window was not dynamic. I also thought of using an editor like gedit but once a text file was opened I was unable to have the editor refreshed from the script.

Does anyone have any other ideas? 

P.S. I had thought of using python but I have not started GUI development using this language and really don't know how to do this at this stage.  

Simon

---

