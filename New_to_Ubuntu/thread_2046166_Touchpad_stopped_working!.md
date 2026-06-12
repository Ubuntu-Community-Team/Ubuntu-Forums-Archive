---
title: "Touchpad stopped working!"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Sly14Cat on 2012-08-22
I just installed Ubuntu and it was installing updates and I was doing stuff in the other workplace when everything froze. So I used the power button to reboot and now the touch pad won't respond. The keyboard works fine and if I boot into windows the mouse is fine but just not in Ubuntu. I think I may have damaged a driver. Do you know what I could do to fix it? I know the main problem is that I booted while updating.

---

### Post by Lisiano on 2012-08-22
Try to continue the install, just do the following.
Open a terminal (Ctrl+Alt+T)
Type the following
```
sudo apt-get -f install
```
You will be asked for a password, provide your user password, it will not be visible when you type it, not even stars.
Now continue the update using this
```
sudo apt-get update
sudo apt-get upgrade
```
You hopefully will have it fixed.

---

### Post by Sly14Cat on 2012-08-22
I did what you said and after putting in my password it told me the update was interrupted and I needed to input a certain command and I did and the mouse started moving and it's updating via the terminal. Since it updated do I still need to use 

sudo apt-get update sudo apt-get upgrade

**THANK YOU SO MUCH!!!**

---

### Post by Lisiano on 2012-08-22
The last 2 commands will just update the list and install any update that might've come out after your last attempt and any update that wasn't installed. The first command would only try to finish installations (Although in your case it was a bit worse since it asked you to use dpkg-reconfigure).
Anyway, running the last 2 commands will just make sure your system is 100% up-to-date.

Anyway, glad I was of help, have fun and enjoy your stay with Ubuntu!

---

