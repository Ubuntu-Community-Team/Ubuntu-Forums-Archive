---
title: "Microsoft Software (EULA) and Bleachbit"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by dannyk2 on 2018-03-20
Have just got my new desktop computer booted up and i wanted to install Ubuntu Restricted Extras from the command line. Everything went well until i came to the End-User License for Microsoft software (EULA) page. Could someone tell me how to get past this page please. I would also like to install "Bleachbit" but have failed using: ```
 sudo apt install bleachbit 
```

I am running Ubuntu 17.10

---

### Post by yancek on 2018-03-20
The only microsoft software I've used on Ubuntu/Linux is the TTF fonts and during that installation, the default setting is NO or not to accept so that may be the case also in whatever you are insalling.  Check the option when you get to that point and use the tab or arrow keys to highlight Yes/OK or whatever you see.

So what happens when you run the command to install bleachbit, any messages/errors?

---

### Post by dannyk2 on 2018-03-20
Hello yancek
I have managed to install the Ubuntu Restricted Extras and Bleachbit now. Although i can only open bleachbit as a user and cannot  open bleachbit as root? Do i need to have a root password?

---

### Post by monkeybrain20122 on 2018-03-20
Bleachbit doesn't have EULA and it is not a Microsoft software, what are you talking about? 

There are two desktop files for bleachbit, one is called Bleachbit, the other is called Bleachbit(as root) use the second one for system.

---

### Post by jeremy31 on 2018-03-20
Poster likely installed recommends for ubuntu-restricted-extras and had the Microsoft fonts installed
[https://packages.ubuntu.com/xenial/ubuntu-restricted-extras](https://packages.ubuntu.com/xenial/ubuntu-restricted-extras)

---

### Post by dannyk2 on 2018-03-20
When i tried to install Ubuntu Restricted Extras during the install the End-User License for Microsoft software (EULA) page appeared and i didn't know how to get past it. That has now been sorted. The only problem i have now is that i cannot open either Bleachbit As Root or Synaptic Package Manager

---

### Post by coffeecat on 2018-03-20
> **dannyk2 said:**
> The only problem i have now is that i cannot open either Bleachbit As Root or Synaptic Package Manager

> **dannyk2 said:**
> I am running Ubuntu 17.10

Are you running in a Wayland session? That would be your problem with apps that need to run with root privileges. There is a workaround for this so-called feature here:

[https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w)

I'm referring to the xhost line a little way down the page. However, my preferred workaround is not to log into a graphical session that puts obstructions like that in my way, but instead log into an xorg session where I can run things like Synaptic the way I'm used to.

---

### Post by monkeybrain20122 on 2018-03-20
> **coffeecat said:**
> Are you running in a Wayland session? That would be your problem with apps that need to run with root privileges. There is a workaround for this so-called feature here:

[https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w](https://askubuntu.com/questions/961967/why-dont-gksu-gksudo-or-launching-a-graphical-application-with-sudo-work-with-w)

I'm referring to the xhost line a little way down the page. **However, my preferred workaround is not to log into a graphical session that puts obstructions like that in my way, but instead log into an xorg session where I can run things like Synaptic the way I'm used to**.

Agreed. Wayland is bad news. Instead of doing the workaround with a lot of  command line gibberish and fooling with config files to get basic functionalities back, -- new users don't  need to go through that crap,-- just logout and from the login screen choose the  xorg session. Problem solved. 

It is a boneheaded idea to default to wayland in 17.10, it is pushing alpha software in a way a hundred times worse than enabling proposed by default.  Thankfully they have the good sense to revert to xorg in 18.04.

---

### Post by dannyk2 on 2018-03-20
Hello coffeecat and monkeybrain20122
My grandson installed Ubuntu 17.10 for me, he made it so i don't have to sign in although i'd prefer to sign in with my password. Is there anyway i could change this so i could sign in with my password please?

---

### Post by yancek on 2018-03-20
If you want to remove the autologin and require a password, read the link below which explains how to set autologin.  Just reverse the process and set autologin to OFF.  Need to be root to do this so I would expect that you would be prompted for a password in the process.  That would be the password for the primary user created during the install, if you don't know it you will have to get it from your grandson as I do not believe it is possible to install Ubuntu without at least one user created with a password.

[https://websiteforstudents.com/setup-ubuntu-17-10-desktop-log-automatically/](https://websiteforstudents.com/setup-ubuntu-17-10-desktop-log-automatically/)

---

### Post by dannyk2 on 2018-03-21
Would just like to say a very big thank you to coffeecat, monkeybrain20122 and yancek. The suggestions you gave worked a treat! I when i boot up the machine i must type my password and i can now open bleachbit and synaptic package manager as root.

---

