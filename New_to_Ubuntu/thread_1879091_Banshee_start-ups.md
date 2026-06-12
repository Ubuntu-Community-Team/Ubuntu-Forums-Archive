---
title: "Banshee start-ups"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by bellee on 2011-11-10
Hello

Whenever I try to open an external drive Banshee starts up in its place since my upgrade to 11.10.. help!






bellee

---

### Post by ubuntu27 on 2011-11-11
Go to **System Settings**---------> removable media

And, select "Ask what to do" OR "Do nothing" on a media of your choice.


I hope that helps.

---

### Post by bellee on 2011-11-11
Much thanks ubuntu27.. I selected "do nothing" away from the default "ask what to do" Banshee is now blank and whatever directory selected now appears.. but sticks with just that - singular. Now unable to launch anything else whereas on the Natty version was able to have different  directories on my desktop in order to move files around.

---

### Post by ubuntu27 on 2011-11-12
> **bellee said:**
> Much thanks ubuntu27.. I selected "do nothing" away from the default "ask what to do" Banshee is now blank and whatever directory selected now appears.. but sticks with just that - singular. Now unable to launch anything else whereas on the Natty version was able to have different  directories on my desktop in order to move files around.

Can you post a screenshot?

Also, try opening Banshee with the Terminal, and post the output here.

Just, open the terminal and type "banshee"




Try deleting the banshee config files.
To do this, go to

1) Close all instances of Banshee (You can use System Monitor to help you with this)

2) **/home/Your-User-Name/.config/**, and then copy the directory called "banshee-1" or "banshee" for backup. (You can rename it to "banshee-backup or similar", and save it somewhere else)

3) Next, delete the directory "**banshee-1**"

[Note: Deleting the configuration files, will make banshee forget all your settings. This means that Banshee will act as if it is your first time running the program]

4) [Optional] Log Out of your user secession

5) Start Banshee

6) Close Banshee


Now, let's hope it works.

---

