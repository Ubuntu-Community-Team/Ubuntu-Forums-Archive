---
title: "Launcher not working for standard user."
date: 2012-07-26
forum: New to Ubuntu
---

### Post by sir.Evan on 2012-07-26
I am running the latest version of Ubuntu 12.04 LTS on a powerful HP laptop.
It is running fine when logged in as administrator, but it had lately reported some internal errors, which might be in the latest update today.
The problem is that the launcher does not work for the standard user. 
I have activated it under System settings-Appearance-behavior and tried top left and side but nothing works.
I have restarted after the last update but still no launcher for the the standard user.
I can therefore only run the system as an administrator which I do not like.
Any suggestions out there???

---

### Post by NikTh on 2012-07-26
Hi , 
at Ubuntu the system administrator has no extra privileges if not apply sudo command (or gksudo for GUI apps) . Its not like Debian or other Linux Distros when you can login in Desktop like root and have full system admin privileges , so its nothing to fear . 

As for other user (standard) , his/her username its not in sudo groups , so cannot run anything with sudo (administrative privileges) . I don't know if explained that clearly so understand the difference.

For launcher problem , login with your standard user account , open a terminal and give this command ```
unity --reset
``` , May take a while to complete , but maybe fix your problem .

Thanks

---

### Post by sir.Evan on 2012-07-26
Thanx Nikth.
I have entered the command unity --reset in the terminal and a lot of things happened in terminal window.
The launcher is still not there.
You said it could take long time..... is 1 hour long enough?? but the launcher is still not there.

What else can I do?

---

### Post by NikTh on 2012-07-26
> **sir.Evan said:**
> 
What else can I do?

You can install ccsm and see if Unity plugin is enabled for standard user. 

```
sudo apt-get install compizconfig-settings-manager
```open it by write in terminal ```
ccsm
``` and see if Unity plugin is enabled. 

Alternative method might be to create another standard user and see if Launcher works there.

Thanks

---

### Post by sir.Evan on 2012-07-26
Hi NikTh,
My machine got sooo slow that and acted strange,(I could not get rid of the terminal I opened for the standard user), that I decided to delete the standard user in question. 

That brought my laptop back to normal.

The same problem (no normal launcher ) exists for the Guest user. Well the launcher is there but it just a stationary black box. When the cursor stands on that black box a a text window pops up with the name of the application at that place. When you click, the application opens.
I can live with that error for a while.

I will however create another standard user and try your second suggestion.

---

### Post by sir.Evan on 2012-08-30
I have found the reason why the launcher isn't working for a standard user!
The problem is only there when the laptop is mounted in the base station!!!!

If I run the laptop alone there is no problems.

I do not know why it is like that but I just avoid running from the base station.

Thanx for for all the good help.

---

