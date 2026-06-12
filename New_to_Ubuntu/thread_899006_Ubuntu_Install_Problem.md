---
title: "Ubuntu Install Problem"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by myolbug on 2008-08-23
This happened a while ago, but I figured I would try and fix it now.  I tried upgrading from Ubuntu 6.XX to 8.04 and it filled my hard drive completely.  Now, when I try and boot into ubuntu, it loads normally, but all of the fonts are squares, instead of letters.  my bro said that the drive is too full to allow it to fully load.  I am wondering if there is some way of unloading 8.04 in boot up commands. 

Help on this would be greatly appreciated.

---

### Post by aysiu on 2008-08-23
I don't think you can just revert to 6.10 or 6.06 easily.

What you might be able to do is free up some space.

If you boot into recovery mode (in the boot menu, it's usually the second boot option - if you can't see the boot menu, press Escape during bootup to see it), type ```
apt-get clean
shutdown -r now
``` and that should free up some space.

---

### Post by myolbug on 2008-08-23
apt-get clean didn't do anything, so I tried apt-get autoclean, rebooting now.  Anyone have other ideas?

---

### Post by aysiu on 2008-08-23
It may not have *appeared* to have done anything, but it deletes all the download files for installing updates or new software. If your hard drive was full, the command should free up some space.

---

### Post by myolbug on 2008-08-24
> **aysiu said:**
> It may not have *appeared* to have done anything, but it deletes all the download files for installing updates or new software. If your hard drive was full, the command should free up some space.


I understand now thanks.  Unfortunately, it didn't help.  Unless that is a better idea, I am going to try taking the HD out and putting it in an External HD case and see if I can get access to it that way.  I am still open to suggestions.

---

### Post by aysiu on 2008-08-24
Are you sure the font problem really has to do with the hard drive being full? It may be another issue (locale installation gone wrong?).

---

### Post by myolbug on 2008-08-24
Honestly I am not certain.  My brother is a senior sys admin for Assurion, he helped me over the phone with it, and the full HD thing is what he said.  I am still a noob.  I really would like to know how to fix it if it is fixable due to the pics etc on the HD.

---

### Post by trash on 2008-08-24
in a terminal type

```
df -h
```

that will tell you if your drive is full

---

### Post by myolbug on 2008-08-24
> **trash said:**
> in a terminal type

```
df -h
```

that will tell you if your drive is full

Yep, drive is 100% full.  Now what?

/dev/hda2  Size 11G  Used 9G Avail 65M Use 100%

---

### Post by trash on 2008-08-24
in a terminal go to the folder where you keep all your files, you are going to need to delete some junk to free up space.

```
cd /your username/your files
```

will list the files in that folder
```
ls
```

Now be very careful with the rm command!
```
sudo rm /your username/your files/file to be deleted
```

post back before doing anything if you are not sure. good luck!

BTW, it's very rare that sudo apt-get clean doesn't free up space, can you do it agin to be sure.

---

### Post by myolbug on 2008-08-24
> **trash said:**
> in a terminal go to the folder where you keep all your files, you are going to need to delete some junk to free up space.

```
cd /your username/your files
```

will list the files in that folder
```
ls
```

Now be very careful with the rm command!
```
sudo rm /your username/your files/file to be deleted
```

post back before doing anything if you are not sure. good luck!

BTW, it's very rare that sudo apt-get clean doesn't free up space, can you do it agin to be sure.

This kind of works!  I am able to get into this somewhat, but it has been so long since I have used this pc, that I can't remember the file names.  I use ls at root and it shows two users, however, when I try to use the above command using randy, (one of the users) it can't find it.  Can you halp me find user names and folder directories?

---

### Post by trash on 2008-08-24
Oh thats right, hard to make out the little squares lol... ok you will need to use a terminal screen...

switch to terminal comand is:

```
ctrl+alt+F1
```

to switch back to your desktop is

```
ctrl+alt+F7
```

the F1 and F7 are the function keys:)

---

### Post by myolbug on 2008-08-24
I cannot get past the initial log on page when I try to load normally.  I do however have the ability to run commands as root in the recovery mode.  My difficulty is that I cannot get a complete list of documents, as it runs in a single row and goes off the screen.  is there away to show the documents as columns?  When I just us "ls" at root, it shows desktop (in blue font; network-settings in yellow font socket-randy-ubuntu in a different color, cache-randy-ubuntu in light blue, share in blue and tmp-randy-ubuntu in a different color.  Can I use any of these to my advantage?

Again, I only have access to commands in recovery, if that actually makes a difference.

can I use rm to remove tmp-randy-ubuntu to remove the corrupt install of 8.04?

---

### Post by trash on 2008-08-24
sorry, ctrl+alt+F1 and F7 are key combinations and can be pressed at the login screen to switch to a Virtual Terminal... once at the VT login, There is a way to stop the screen scrolling but I am not sure how.

---

### Post by myolbug on 2008-08-24
My bad, I didn't see that I needed to use the alt key too.  OOPS!

---

### Post by trash on 2008-08-24
hehe np i didn't read your question about the corrupt install lol.. but i don't know the answer anyway sorry.

---

### Post by myolbug on 2008-08-24
Thanks for your help thus far Trash.  Does anyone else have any ideas, or should I try putting the HD in an external case in another computer and see if I can access it that way?  If I use it as an external, will I then be able to use the other computer's internal HD to provide the additional space needed to finish the install??  I was told that the HD is too full to be able to create a copy to install.

---

### Post by myolbug on 2008-08-25
Anyone?

---

### Post by myolbug on 2008-08-27
Does anyone else have any ideas or should this be moved to a more appropriate forum?

---

### Post by myolbug on 2008-09-06
Ne1?

---

### Post by cwsnyder on 2008-09-06
Since you are attempting to install Ubuntu Hardy, you should be able to boot to the 'live' CD version and attempt to fix the problem from there.

---

