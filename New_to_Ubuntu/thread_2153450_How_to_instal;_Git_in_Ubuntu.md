---
title: "How to instal; Git in Ubuntu"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by database1 on 2013-06-11
I am new to Ubuntu, recently tried to install Git on Ubuntu but I got a installation error . I just followed the commands given in this article [http://www.begin2code.com/how-to-install-and-use-git/](http://www.begin2code.com/how-to-install-and-use-git/) but it has not worked, I think there is something skipped in this article, Can anyone illustrate on how to install Git in a detailed format.

---

### Post by slickymaster on 2013-06-11
All you have to do, to install it, is to run the following command in a terminal window:```
sudo apt-get install git
```

After Git is installed, you need to copy your username and email in the gitconfig file. You can access this file at **~/.gitconfig**. 
Open again a terminal window and run the following:```
sudo nano ~/.gitconfig
```and use the follow commands to add in the required information.
```
git config --global user.name "NewUser"
git config --global user.email newuser@example.com
```You can see all of your settings with this command:```
git config --list
```

---

