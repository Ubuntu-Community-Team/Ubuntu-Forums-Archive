---
title: "Modifying the /etc/hosts file in Percise Pangolin"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by hebrewofyhwh on 2014-02-05
I would like to modify my hosts file to block  a list of adservers with the 127.0.0.1  address,
This is what I have done but I have not been sucessfull yet in saving the new file or getting it installed properly
.
I typed ```
 
sudo vi /etc/hosts
    # You'll be prompted for your account password
    # Press the down arrow past any # comments to get to the list of hosts
    i
    # pressing i puts you into insert mode
    # press return and up arrow to create a blank line
    128.117.224.210 www.scd.ucar.edu
    # press the escape key
    :wq! 
    sudo killall -HUP lookupd
```

I pressed the escape key and it did not let me escape. and I didnot get the $ to enter the last command " sudo killall 

Any assistance on this issue. I did not see much in the way of this on the board.

---

### Post by Dave_L on 2014-02-05
vi is tricky to use. Why not use an easier one?

```
sudo nano /etc/hosts
```

or

```
gksudo gedit /etc/hosts
```

---

### Post by vitz_3 on 2014-02-05
Hi there :)

I think the problem might be an order of operations thing. Are you copy and pasting that from a post somewhere?

When you sudo it gives you permission to do things as the super user (root) such as modify system files. The next part of the command is vi which is command line accessible text editor. 

The line saying to press escape means to put vi in command mode and using the :wq command to write the changes and quit the program. The exclamation point isn't really needed.

An easier way for you to do the changes if you're using the Desktop version is to use:

```
sudo gedit /etc/hosts
```

This will give you a visual editor to use instead in a more familiar environment.

It might be worthwhile backing up your hosts file before doing the edits using something like

```
sudo cp /etc/hosts /etc/hosts.`date +%s`.bak
```

Best of luck!

---

### Post by deadflowr on 2014-02-05
gedit automatically creates a backup.

If you hit save once the original gets moved to a hidden file called /etc/hosts~.
If you  hit save again, then that newly made backup is overwritten. 

So if you only hit save once, you'll have a backup.

To see the backup in Files(nautilus) press ctrl+h to view hidden files.

---

### Post by hebrewofyhwh on 2014-02-05
Thank you for your speedy  and informative replies.  I am going to test this out right now! Thank you, all.

---

### Post by hebrewofyhwh on 2014-02-05
Ok, Feedback here, the ```
 
gksudo gedit /etc/hosts 
``` worked.  I was able to cut and paste the list into the file.  I did have one question though, When I tried to save  it asked Where to put the file and I didn't know. But I checked by  using ```
gksudd gedit /etc/hosts
``` and the amended file was in place.

---

