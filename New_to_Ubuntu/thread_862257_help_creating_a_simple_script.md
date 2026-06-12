---
title: "help creating a simple script"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by happyisland on 2008-07-17
Hi all,

Here's the issue I'd like to solve:

I have a music player that HAL doesn't like for some reason. This means that it has to be mounted manually, every time I connect it. The way I do this now is by issuing the following commands:

1. sudo mount -t vfat /dev/sde /mnt/lplayer  (this mounts the music player)

2. sudo gnome-open /mnt/lplayer     (this opens a browser window for easy drag and drop file transfer)

3. sudo umount -t vfat /dev/sde /mnt/lplayer     (this unmounts the player when I am ready to unplug it from the USB port on the computer.


What I'd like to do is somehow automate this process to approximate the work that HAL should be doing. Would it be possible to write a script that would allow me to double click on an icon on my desktop that would automatically connect the player and open its folder in a new window of its own? What about unmounting it too? 

Thanks in advance for the help. I tried reading a guide to bash scripting, which reminded me why I need to keep posting in "Absolute Beginner Talk". :)

---

### Post by hyper_ch on 2008-07-17
try this one here: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by scragar on 2008-07-17
just make a launcher to run:
```
gksudo mount -t vfat /dev/sde /mnt/lplayer && gksudo gnome-open /mnt/lplayer
```
which will mount and open gnome-open. You appear to have the same command twice though, so I'm gonna want to know about that.

---

### Post by benfindlay on 2008-07-17
Try this:

Open a terminal and type 
```
cd Desktop
touch [nameofyourscript]
nano [nameofyourscript]
```

Then paste this into it:
> #! /bin/bash
# [enter description here]
sudo mount -t vfat /dev/sde /mnt/lplayer
sudo gnome-open /mnt/lplayer
sudo gnome-open /mnt/lplayer
Then save and close. Next type ```
sudo chmod +x [nameofyourscript]
```
You should be good to go!

Hope this helps!

Ben

---

### Post by PinkFloyd102489 on 2008-07-17
If you're wanting to open a graphical window, you need to tell the script where to open it.

```
export DISPLAY=:0 && some other command
```

You need to put the export command before all commands involving a window.

---

### Post by scragar on 2008-07-17
> **benfindlay said:**
> Try this:

Open a terminal and type 
```
cd Desktop
sudo touch [nameofyourscript]
sudo nano [nameofyourscript]
```

Then paste this into it:

Then save and close. Next type ```
sudo chmod +x [nameofyourscript]
```
You should be good to go!

Hope this helps!

Ben
why when Ubuntu asks for confirmation before running an executable but doesn't for a launcher which can achieve the EXACT same effect? it's also more work. (and any reason why you expect the bash script to be run from a terminal since your using sudo and not the graphic gksudo or gksu ?)
Oh, and there is no reason, EVERY to make a new file in the users own home directory with **sudo**

---

### Post by benfindlay on 2008-07-17
> **scragar said:**
> why when Ubuntu asks for confirmation before running an executable but doesn't for a launcher which can achieve the EXACT same effect?

Good point, I always forget about making launchers! ;) Much simpler solution!

As for the rest of your post, happyisland wanted a script, so thats what I did! ;)

---

### Post by happyisland on 2008-07-17
> **scragar said:**
> just make a launcher to run:
```
gksudo mount -t vfat /dev/sde /mnt/lplayer && gksudo gnome-open /mnt/lplayer
```
which will mount and open gnome-open. You appear to have the same command twice though, so I'm gonna want to know about that.

1. Whoops - I pasted the wrong third command. It's now fixed in my edited first post. sudo umount -t vfat /dev/sde /mnt/lplayer

2. I created a launcher with the command you supplied. It mounts the player (I can find it when I browse to /mnt/lplayer), but strangely does not open the gnome window for the lplayer.

---

### Post by happyisland on 2008-07-17
It also doesn't seem to work at mounting the player every time. Weird. I tried unmounting the player and then using the launcher to remount it and nothing happened.

---

### Post by happyisland on 2008-07-20
Sorry to keep replying to my own posts, but I am still unable to get my lplayer to mount consistently by any other means than the command line.

I really wish that I could get HAL to just work with the player, but barring that it would be nice to have a slightly more user-friendly method.

---

