---
title: "log in bug"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by degarb on 2012-07-11
I turned off the auto login, since I saw no way of choosing a default desktop in gui (gnome 3, classic, etc).  Then I realized I didn't want to peckout a login password every boot--totally unnecessary, fig leaf security, and pita.  

To my horror, this option now blows me through the desktop choice dialog, where I am permanently locked into one type of desktop.  THERE IS NO WAY TO CHANGE IT BACK! Once this option is chosen, I cannot unchoose it.

---

### Post by LADmaticCA on 2012-07-12
Have you looked at the user accounts utility? Once you click "unlock," and enter the admin password you can enable/disable automatic login for a user.

---

### Post by degarb on 2012-07-13
> **LADmaticCA said:**
> Have you looked at the user accounts utility? Once you click "unlock," and enter the admin password you can enable/disable automatic login for a user.

If you read carefully, I wrote that I do NOT want the auto login, so I disabled it.  I want to choose between various desktops environments kde, gnome, lxde, xfce, etc. So naturally, this is disabled, but then I chose no password needed (this is a pain entering password, and often impossible if you can't type/read/are fingerless/memory impaired/lazy/busy/impatient/trying to be productive). 

THE gnome2 bug is that this option will not allow you to choose a desktop, just blows past the option. The second BUG is that once chosen, there is no unchoosing this option.  I had to create another user/admin that will use password and this original account is locked permanently in gnome2 classic with no password needed.  Nothing is auto log in---something different.

If you do not know where this option is: click password, then down arrow.   gnome 2 classic.

---

### Post by NikTh on 2012-07-13
Hi,
I just almost reproduced this.(Unity environment) I say almost cause i have the option to choose environments (gnome , gnome-classic etc) 
BUT
my password is no longer valid. Neither terminal or GUI (tried to unlock users account , not let me).

So if you want to report this , inform here (give the link) .

**EDIT: **
hmm.. i think just found a workaround. 
When you are at login screen , go to VT (Ctrl+Alt+F2). Login with username (only , passwd not needed) and then do 
```
sudo service lightdm stop 
sudo -i 
passwd username 
sudo service lightdm start
```username = Your username 
give a password that you want (i gave the same i had ) 
When lightdm starts you will see login screen with NO password , but your password it will be valid as before.(system-wide)
Thanks.

---

