---
title: "Need a Better Backup Solution for Testing Desktop Environments"
date: 2022-02-02
forum: New to Ubuntu
---

### Post by chloz on 2022-02-02
I apologize in advance for formatting: Not only am I new to Ubuntu but I am new to forums.

So I have decided to start playing with display managers, desktop environments, those sorts of packages within Ubuntu. My attempt at this; I started with a fresh Ubuntu 20.04LTS install, ran the following:
```
sudo apt update && sudo apt upgrade -y && sudo reboot
```
I then used Deja Dup graphically to create a backup in my user's home folder (/home/username/Backups), then attempted:
```
sudo apt update && sudo apt install kde-plasma-desktop -y
```
And used the sddm display manager. Well I did not like the new login screen so I attempted switching to gdm3; results were back to the ubuntu desktop but with changed icons including a missing icon for the Ubuntu Software Store. I decided to attempt a restore in 3 ways, and all 3 failed:
1. Simply click to open Deja Dup and restore. The error given was unable to write to quite a few folders.
2. Attempted running Deja Dup from the terminal with sudo:
```
sudo deja-dup
```
Again an error (different than from way #1, but did not grab the details: I can if anyone feels inclined to try and fix Deja Dup).
3. Attempted running Deja Dup as su from the terminal:
```
sudo su
deja-dup
```
Same error from running Deja Dup from the terminal with sudo.

So my question: Is there a better backup and restore solution, at least for what I want to do? I'd prefer to not have to fresh install Ubuntu every time I don't like the desktop environment I'm currently trying out.

---

### Post by foxsquirrel on 2022-02-02
On the desktop version have you tried "Backups" its in the applications. Simple and works very well.

I make a build sheet and turn that into a script so its very easy to reinstall. Save all your really important files to a special folder on the server and do it without compression using something like filezilla. 

> $sudo apt install filezilla

If you keep all the important stuff in one directory its pretty easy to drag it all back from the server. If you have some complicated configurations I would include those in the "Backups" backup.

---

### Post by GhX6GZMB on 2022-02-02
I use Timeshift every time before I do modifications to my machine. Works perfectly.
Attention! Timeshift does not backup your user files (/home), only the system set up.
If you want to include the desktop, tick "Hidden Files" in Home in the TimeShift settings.

---

