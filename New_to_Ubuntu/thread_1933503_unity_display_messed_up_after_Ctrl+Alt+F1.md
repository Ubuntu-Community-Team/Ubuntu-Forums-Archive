---
title: "unity display messed up after Ctrl+Alt+F1"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by souravc83 on 2012-02-29
When I go to the text terminal with Ctrl+Alt+F1, and then return to Unity with Ctrl+Alt+F7, the unity screen is messed up, with green dots in a black background. The apps are still running. The sidebar sometimes works. But I cannot get the screen to refresh and be normal.

I found from the forums that unity --replace at the text terminal replaces the unity with a new one. This works (although sometimes gives me segmentation faults) but it is not convenient to start up unity every time I switch between the text and the Window Manager.

I was wondering if there is a solution to this bug.
I am using Wubi and Unity 4.28.0. 
Let me know if you need any further info.

---

### Post by d4m1r on 2012-02-29
Are you able to take a picture of the screen?

CTRL + ALT + F1 is the tty1 screen, which is basically a command line and everyone has it...

---

### Post by souravc83 on 2012-02-29
Here is a picture of the screen.

---

### Post by cortman on 2012-02-29
Have you tried Alt+F2, then entering "r" enter, in the dialog box, to reset the desktop?

---

### Post by souravc83 on 2012-03-02
I tried that. Didn't do anything for me.
The Alt+F2 command brought up the searchbar on the dashboard.
I pressed "r" and the "Enter" key. No action. 

This messing up of the screen also happens when I open the computer after standby. So I am starting to believe it might be a video card issue?

---

### Post by souravc83 on 2012-03-09
Can anyone help me with this. Previously, I was using Wubi.
Now, I have done a clean hard drive install, but the problem persists.

---

### Post by d4m1r on 2012-03-09
Something is screwed up with your gnome desktop/unity session....

I would google around on how to "reinstall unity ubuntu" or "reinstall gdm" (gnome desktop manager).

---

### Post by yetiman64 on 2012-03-09
> **d4m1r said:**
> ... or "reinstall gdm" (gnome desktop manager).
In Unity on 11.10 "lightdm" is the default . Cheers.

Edit: @ OP, just noted the problem is still with a full partition install as well. Could you please post some hardware details for checking (video mainly of course)? 

Try the command,
```
sudo lspci | grep VGA
``` this will at least tell us what the make of the video card is, others here may need more info from other commands once this is known. Just a starting point :).

---

### Post by acimi66 on 2012-03-09
I'm not sure if I had the exact same problem but I fixed it by using "CTRL+ALT+F2".

Hope that helps

---

