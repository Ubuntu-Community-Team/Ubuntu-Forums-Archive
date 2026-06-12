---
title: "Loads to my Background.. and nothing else"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by stevemav on 2012-06-24
I attempted to clean up my comp with ubuntu tweak, once I cleared all the files it recommended, the screen only showed my background. When I restart or shut down and boot the system up again, it returns to showing the background. 

I can press ctrl+alt+t for the terminal, and I'd rather not reinstall the OS. 

I am running Ubuntu 12.04. 

I'm guessing I didn't check the files I was deleting closely enough, and that one or more were important for showing the launcher/dash/desktop etc.

---

### Post by Frogs Hair on 2012-06-24
I have never known Ubuntu Tweak to remove needed packages. If no terminal is available try the following if using Unity.

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next, enter user name, password, and run the following command.```
unity --reset
```

Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu.

---

### Post by Fernhill Linux Project on 2012-06-24
From a terminal you could install gnome shell using

```
sudo apt-get install gnome-shell
```

Then logout and click the ubuntu logo by your name and select gnome or gnome classic and then log back in. 

It wont fix your problem, but at least you will have a working desktop enviroment until some one gives you a better answer. :o

---

### Post by Frogs Hair on 2012-06-24
Unity needs to be reset if the OP wants to use it again . TTY is one way to do that without a  another terminal available . Installing another DE such as the Gnome Shell  is a  work around if the OP wants to do that. Either way Unity needs to be reset to be used again.

---

