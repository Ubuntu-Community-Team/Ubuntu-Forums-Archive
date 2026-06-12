---
title: "How to enable admin privileges for terminal?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Alex_GT on 2008-05-31
I've just installed ubuntu, and now it says I need to install some critical updates.

When I do try however, it says to enter a line of code into the console/terminal, which fails because it says I do not have the permission to.

I do have the root password, but I'm not sure how to get "permission" to be able to use the console/terminal.

Thanks.

---

### Post by Crafty Kisses on 2008-05-31
> **Alex_GT said:**
> I've just installed ubuntu, and now it says I need to install some critical updates.

When I do try however, it says to enter a line of code into the console/terminal, which fails because it says I do not have the permission to.

I do have the root password, but I'm not sure how to get "permission" to be able to use the console/terminal.

Thanks.

That's weird. So anytime you try to open the Terminal you can't get permission, what version of Ubuntu?

---

### Post by kwacka on 2008-05-31
open a terminal and type: ```
sudo gnome-terminal
```

(or xterm if you prefer).

Enter your logon password, a new terminal opens.

---

### Post by mgranet on 2008-05-31
put the word ```
sudo 
``` in front of the command you want to run as root, then enter your user pass when it asks.

---

### Post by RATM_Owns on 2008-05-31
Use
```
sudo
```
before your program if it is a command line program.

Use
```
gksudo
```
before your program if it is a GUI program.

If you plan on using a lot of sudo stuff in one terminal window, consider using
```
sudo su
```
to switch to root.

---

### Post by The Cog on 2008-05-31
The command
**sudo -i**
changes your login to a root login with full privileges. Your prompt changes from $ to # as an indication that you are now root.

But why are you trying to install updates in terminal? Clicking the little orange star or choosing System->Administration->Update Manager is the way I install updates.

---

### Post by sayakb on 2008-05-31
You might also do:
```
sudo bash
```In that way, you will be root, plus, you will stay in bash.

Otherwise, Goto System->Preferences->Main Menu
Click on System Tools on left column and **enable  ***Root Terminal* under System tools category. It will launch a terminal as superuser.

---

### Post by Joeb454 on 2008-05-31
I wouldn't recommend **sudo bash** (for the same reason I don't recommend **sudo -s**) Just do a **pwd** and you'll see why (compared to **sudo -i**)

And to the OP - I'm guessing it was telling you to run ```
sudo apt-get update && sudo apt-get upgrade
```

---

