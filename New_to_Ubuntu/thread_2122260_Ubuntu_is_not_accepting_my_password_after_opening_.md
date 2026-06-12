---
title: "Ubuntu is not accepting my password after opening the GUI"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by dcwilson042 on 2013-03-04
Ubuntu was installed Friday, I closed it down prior to leaving for the day, on Monday I started Ubuntu up. On the login screen it displayed my name and a blank field to input my password.  I entered my password and it looked as though the password worked, however the login screen reappeared. FYI - I entered an invalid password and it recognized it as an incorrect password.

---

### Post by schragge on 2013-03-04
Are you still able to log in on a text console? Press **Ctrl**+**Alt**+**F2** to change to the 2nd text console, and try to log in. To log out, press **Ctrl**+**D**. To change back to GUI, press **Ctrl**+**Alt**+**F7**.

---

### Post by Mikhail.Inspired on 2013-03-04
Can you log into your account via the Ctrl+Alt+F1 display?

---

### Post by Mikhail.Inspired on 2013-03-04
Can you log into your account via the Ctrl+Alt+F1 display?
If so, one way to possibly reset it is to run
> sudo passwd *insert username here*
After doing that, you should be able to reset the password to your original one, or a different one if you wish.

---

### Post by dcwilson042 on 2013-03-05
I have follow the instruction from these responses and appreciate the directions, however I am stil in the same situation and cannot log into the GUI of ubuntu. Is there something more I should do?

---

### Post by steeldriver on 2013-03-05
Please log in at the virtual terminal (Ctrl-Alt-F1) and check the ownership and permissions of your home dir and ICE / X authority files e.g.  

```

ls -ld ~
ls -l ~/.{ICE,X}authority

```

---

### Post by kgriff on 2013-03-05
I'm having the same issue.  Mine started after installing AMD proprietary drivers, having them fail to work, then uninstalling.  This was all done following the linked instructions on AMD's website.  First reboot after the uninstall, and I can't login as me.  (Additionally, my username had changed to the Full Name specified on the account).  I could still logon as Guest.  I changed the Username on my account back to what it used to be, but still cannot login.
I can login, using my correct Username and password, from TTY1.  Even so, I did *sudo passwd *insert username here** and was able to set my password, even though I was setting it a password that already works.

Also, as my account is Administrator, every time I sudo I have to use my password, and it has continued to work.

> **steeldriver said:**
> Please log in at the virtual terminal (Ctrl-Alt-F1) and check the ownership and permissions of your home dir and ICE / X authority files e.g.  

```

ls -ld ~
ls -l ~/.{ICE,X}authority

```

Doing the above I get
[INDENT]-rw------- 1 username username 1908 Mar 5 17:12 /home/username/.ICEauthority[/INDENT]
[INDENT]-rw------- 1 root          root           251 Mar 5 16:43 /home/username/.Xauthority[/INDENT]

Anyone have any idea how I should proceed?

---

### Post by steeldriver on 2013-03-05
Your .Xauthority file needs to be owned by you (if it's owned by root, then your X session can't start)

Either

```
sudo chown *username*:*username *~/.Xauthority
```

or (doesn't need sudo since you own the containing dir)

```
rm ~/.Xauthority
```

In the latter case the file will be regenerated on your next successful X session

---

### Post by kgriff on 2013-03-05
Not to hijack the thread, but could this permission have been changed by installation of the AMD drivers and, if so, could that have been the cause of the failure of the drivers to work?  When I booted after installing the AMD drivers, I would boot to the generic background screen, but without anything else on the screen. (No clock, network indicator, Dash, launcher, nothing)

---

### Post by steeldriver on 2013-03-05
in my experience, it's usually caused by starting an X server using sudo - either by doing 'sudo startx' or possibly by doing 'sudo X -configure' or 'sudo Xorg -configure' to generate a new xorg.conf file

---

### Post by kgriff on 2013-03-05
Excellent.  That explains it.  The AMD instructions tell you to do 'sudo startx' if the X Server doesn't start correctly.  I did so, obviously not aware of the full implications.
Thanks for your assist.

---

### Post by steeldriver on 2013-03-05
Happy to help - glad that worked for you

---

### Post by dcwilson042 on 2013-03-07
I appreciate all your suggestions and comments, however I am still not able to log into the GUI.  Are there any other suggestions that might get me going with Ubuntu, before I uninstall and go back through the install process with this?

---

