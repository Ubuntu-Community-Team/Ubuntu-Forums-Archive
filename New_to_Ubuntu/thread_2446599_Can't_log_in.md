---
title: "Can't log in"
date: 2020-07-03
forum: New to Ubuntu
---

### Post by rhg141 on 2020-07-03
I have just installed Ubuntu 20-04 as a dual boot option on my Windows PC. I am new to Ubuntu but used Unix many years ago.  During installation I gave my name in the form "John E Smith" and selected "jesmith" as my username. I then clicked on "Log-in Automatically" but it still needed a password before I could move on so I supplied one - let's say it was "Earw1g3*".  Having concluded the installation I then clicked restart and, eventually, the grub menu came up and I selected Ubuntu. 

At  this point I was presented with a login screen, with the name "John E Smith" showing and a box to enter the password.  Having asked for automatic login I tried ignoring the password and just pressing return but nothing happened.  I then tried entering "Earwig3" in the password box (with the eye open) but, again, nothing happened.  I then clicked on "name not shown" (or something like that) and entered the name "jesmith" and the password but, yet again, nothing happened.  I have run out of ideas so can anyone tell me how to negotiate this impasse please?

---

### Post by ActionParsnip on 2020-07-03
If you press CTRL + ALT + F1 and log in there is it OK? If so then run:
```

passwd

```
Then change your password (You won't get any feedback as you type). You can then run:
```

sudo reboot

```
Then try logging in with the new password (If autologin fails). If you cannot log in after pressing CTRL + ALT + F1 then you can use this guide:
[https://psychocats.net/ubuntu/resetpassword](https://psychocats.net/ubuntu/resetpassword)

You can reset your password in root recovery mode

---

### Post by rhg141 on 2020-07-04
Thank you.  During the normal boot process I couldn't find anywhere where Ctrl-Alt-F1 had any effect.  I therefore tried your second option of resetting the password in root. This appeared to work but I was taken into Ubuntu LTS where I was challenged for my password (a message about a "keylocker") and it would only accept the old password not the one I had just set.  I shut down and restarted and, on selecting Ubuntu in Grub, the login screen was bypassed and I was taken straight to the LTS screen.  There I was again challenged with the keylocker message for a password.  However this time both my keyboard and mouse were frozen and there was nothing I could do but switch the machine off.

---

### Post by rhg141 on 2020-07-04
I've now solved this by reinstalling Ubuntu.  Thanks,

---

### Post by CelticWarrior on 2020-07-04
Yes, reinstalling is the fastest option as also the one with best chances of success in cases like this.

In the future please avoid bad practices like autologin. Even in Windows that is NOT the default option for many years now.

---

