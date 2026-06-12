---
title: "[HowTo] Install Flock on Ubuntu"
date: 2009-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by MadnessRed on 2009-05-19
This guide is for installing Flock on Ubuntu, In this case [s]Flock 2.0.3[/s] [s]Flock 2.5.1[/s] Flock 2.6.0 on Ubuntu [s]9.04[/s] 10.04. I have literally just done in now so tutorial should be up-to-date. ([s]19th May 09[/s] [s]31st July 09[/s] 18th June '10)
My first tutorial so please feel free to comment.

1) Download flock
You can download flock from the following page.
[http://flock.com/versions](http://flock.com/versions)
make sure you get the linux one, its in the far right column.
Save it to you desktop, will make things easier.

2) Extract
Right click on the the archive and click Extract here, a folder should appear called 'flock'.

3) Become root
3 options here, 1 you login as root, I don't recommend that though, 2 you do this through terminal and type sudo in front of everything and 3, you just open nautilus as root. Feel free to do what you want but my guide assumes that you have done either 1 or 3. I recommend 3, in which case, open terminal and type.
```
gksu nautilus
```

4) Move flock
Go to the Directory where you downloaded flock, click no the flock folder and copy it, Control + C
Now still in the root nautilus, go to /opt and paste. (Control + V)
You can close nautilus. (You can check weather you are right so far by putting this into terminal)
```
/opt/flock/flock-browser
```
If flock starts then its all good.

5) Create link
Now to make a simple command to run flock we will make a link in bin. Because its only a user program we will install in /usr/bin.
Copy the following into terminal
```
sudo ln -s /opt/flock/flock-browser /usr/bin/flock-browser
```
(note you should always "man" a commands before running it, "man ln", just so that you know what i am telling you to do)

6) Create shortcuts
The easiest way to do this is to make a link in the main menu and then just copy it to panel or desktop as required.
System > Preferences > Main Menu
Select Internet on the left then click the new item button.

Type: Application
Name: Flock
Command: flock-browser
Comment: Flock Web Browser

Now in the top left there is a strange panel on a spring, no idea what its meant to be but click it. a window called "Browser icons" will appear with a text box at the top. Copy this into the text box.
> /opt/flock/icons/mozicon128.png
And the spring board thing should become the flock icon. press close, and then close again. And you are done.

Now if you want icons on your desktop or panel, Click Applications > Internet, right click on Flock and select "Add this launcher to panel" or "Add this launcher to desktop" as desired.

7) Done!!!
Any questions I'll try to answer.

---

### Post by JakcV on 2009-05-21
I follow the flock.desktop in the flock web page but the path has some problem. Error.
Then, i try to make the link myself. A simple GUI method, which similar to add in the application > internet. I right click at desktop > launcher. Then, the command is pointed to the 'flock-browser' which i put in my home folder.

---

### Post by MadnessRed on 2009-05-21
> **JakcV said:**
> I follow the flock.desktop in the flock web page but the path has some problem. Error.
Then, i try to make the link myself. A simple GUI method, which similar to add in the application > internet. I right click at desktop > launcher. Then, the command is pointed to the 'flock-browser' which i put in my home folder.

Sorry, you aern't making comlete sence there, which tutorial isn't working?

---

### Post by MadnessRed on 2009-07-31
Updated thread for Flock 2.5.1 - Fixed a few typos and changed "sudo nautilus" to "gksu nautilus" which is better.

---

### Post by ben1986 on 2010-04-23
Hey man, great tutorial.


Had a little issue with the icon step. Had to copy into /usr/share/icon/hicolor/apps/scalable before it would work, but now its good.



Cheers!

---

### Post by MadnessRed on 2010-04-23
> **ben1986 said:**
> Hey man, great tutorial.


Had a little issue with the icon step. Had to copy into /usr/share/icon/hicolor/apps/scalable before it would work, but now its good.



Cheers!

ok, thanks, maybe it needed public read permissions. I will recheck the tutorial with the new version and see.
Glad to be of help

---

