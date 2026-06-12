---
title: "All Settings and Files Cleared"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-24
So I was following the instructions on how to use re-linux, and so I followed these steps:
> Before you start editing, if you want to save your settings/themes, do this (replace USERNAME by your actual username):

1. Press CTRL+ALT+F3
2. Log in as your normal user
3. Type: sudo passwd
4. Enter a password for root
5. Type: exit
6. Log in as root (with the password you gave for root)
7. Type: usermod -d /etc/skel USERNAME; chown -R USERNAME /etc/skel
8. Reboot your system (can be done with the reboot command)

Then you can log into your normal user, and all of your changes to the theme, desktop background, panel configuration etc&#8230; will be saved.

I logged into my account (Alden), and my settings were *definitely* not changed, as far as a noob like me can tell.

First of all, my desktop background is the standard now. Secondly, my home folder (alden) is now called "skel", and I have none of the files and folders I previously had - all there is are the standard folders.
Third, my panels are the standard panels, with all the standard things on them, not customized like they were right before I ran this code.
My installed applications are all there, oddly enough.

I just noticed something: in the "usermod.../skel" code above, the username I used was "alden", while on the login screen, I'm listed as "Alden". Is this the reason why it's messed up? Because in CTRL+ALT+F3 it let me log in as "alden"...

What did I do???

**EDIT:** I just found where my files are stored: /home/alden. Why is it showing my home folder as /etc/skel, then? And how do I restore it? And what exactly did that code do?

Sorry for all the questions, but I am really confused; I was just trying to create a custom iso in the first place, and now everything's messed up...

---

### Post by gsmanners on 2011-10-24
What you did was change your home folder to /etc/skel with that usermod command. If you want your old home folder back:

```
sudo chown -R root:root /etc/skel
sudo usermod -d /home/alden alden
```

---

### Post by DaimyoKirby on 2011-10-24
Oh. But what how did it "save" all my settings as it claims to do?

Or is that what I'm supposed to do in *skel*:
Change settings while "connected" to skel to my liking, switch back to normal home folder (alden), and continue on with the instructions?

**EDIT:** Thread Closed. I was informed that by logging into root in the way I did, I have compromised my system, and so will be re-installing Xubuntu promptly.

---

