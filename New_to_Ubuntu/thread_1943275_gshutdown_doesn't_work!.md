---
title: "gshutdown doesn't work!?"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by P-rench on 2012-03-19
When I first installed gshutdown I expected it to just shutdown my computer, well it didn't. Instead it only logged me out of my current session. so I did a little searching around and tried doing a custom command for the "Turn off computer" option. I used "shutdown -h now" , "sudo shutdown -h now" and "poweroff" all of which did absolutely nothing, didn't even log me out of my current session like previously. Does anyone have ideas what is going on here and a possible solution to it?

---

### Post by TeoBigusGeekus on 2012-03-19
Try with
```
sudo halt
```
Also, do you get any error messages with the commands you've mentioned?

---

### Post by jerrrys on 2012-03-19
Your running 10o4.  Don't you have extra shut down options (buttons) in "add to panel"?

---

