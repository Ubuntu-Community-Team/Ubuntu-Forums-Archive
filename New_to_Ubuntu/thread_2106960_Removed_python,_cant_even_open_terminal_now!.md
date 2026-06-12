---
title: "Removed python, cant even open terminal now!"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by f1ndingwalden on 2013-01-20
So last night I had installed a pythn 2.7 because the python that shows up when I type in "python" in the terminal is version 4. somthing. Anyways, as soon as it finished I noticed that alot of my programs quit working, my sound wouldnt come on and my computer didnt even recognize that there were sound drivers, and its now a giant mess because I ran "sudo apt-get remove python" like a complete retard, without even googleing it first, thinking this would get rid of my problem, not realizing that amount of devastation I was about to slew onto my computer. I slowly watched by idly as everything was removed.. bit.. by bit, until it I realized what a crucial error I made and shutdown the terminal. Some how I still have firefox and clementine, but I cant even open a freaking terminal now!!! I have tried ctrl+alt+t countles times, and unity is completely worthless now, not to mention my options to change into gnome or cinnamon. I am usually up for a challenge, but I am to tired for this. please. somebody, help me.

---

### Post by f1ndingwalden on 2013-01-20
Got into a terminal!! I right clicked on my desktop background and clicked open in terminal. except its a different species of a terminal... Black and white from the ancient days when everybody using a terminal actually knew what they were doing, and people like me were behind a TV where we belong.

---

### Post by MG&amp;TL on 2013-01-20
Have you tried reinstalling python? ;)

```
sudo apt-get install python
```

---

### Post by f1ndingwalden on 2013-01-20
first thing I did after I got into a terminal.. followed by sudo apt-get update. however nothing seems to have changed.. although my software updater is now running and ill let you know what that says once its done loading.

---

### Post by The Cog on 2013-01-20
Sorry, but I don't think there is much you can do except re-install. A lot of the software installation and removal is done by python scripts, so without it you can't install it. 

It might be worth waiting for a while to see if someone knows better than I do though.

---

### Post by MG&amp;TL on 2013-01-20
> **f1ndingwalden said:**
> first thing I did after I got into a terminal.. followed by sudo apt-get update. however nothing seems to have changed.. although my software updater is now running and ill let you know what that says once its done loading.

Try re-installing bits you may have removed:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by f1ndingwalden on 2013-01-20
And by software updater, I dont mean the command, I mean the actual program thats built in. The command finished already, but the program is frozen.

---

### Post by f1ndingwalden on 2013-01-20
currently installing ubuntu desktop.. thanks for your help by the way

---

### Post by f1ndingwalden on 2013-01-20
Success! Thank you.

---

### Post by MG&amp;TL on 2013-01-20
> **f1ndingwalden said:**
> Success! Thank you.

Awesome, now you know how to get out of any future python-relatd holes you may get yourself stuck in. ;)

Mark thread [SOLVED] please!

---

