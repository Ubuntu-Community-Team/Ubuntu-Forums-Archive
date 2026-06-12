---
title: "Run out of disk space?? Screenshot attached"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by goldfoot777 on 2012-04-21
Hi

I just 'made the switch' to Ubuntu 11.10 from Windows XP on a spare netbook I have. Loving the interface, user-friendliness of it all etc...that was until I tried to put 2 episodes of a program (360mb each) from my pen drive to my 'desktop'...message came up saying I didn't have enough space. I've got a 160gb HDD so couldn't understand why.

I did a little digging round on the net and it seems it's a pretty common problem, although I struggled to find an ultra-idiot's guide to sorting this silly problem out.

I would be extremely grateful if someone could point me in the right direction - i've attached a screen shot via gparted. 

Would I be right in thinking Ubuntu is aimed more towards devs and programming-savvy folk than us mere mortals? lol

All help would be extremely gratefully received.

Many thanks

---

### Post by DJ_Max on 2012-04-21
> **goldfoot777 said:**
>  

Would I be right in thinking Ubuntu is aimed more towards devs and programming-savvy folk than us mere mortals? lol


No its the exact opposite, Ubuntu is aimed for people who have no experience with Linux.

Run from terminal
```
df -h
```

---

### Post by 0011235813 on 2012-04-21
OK, why don't you try and copy the files to the Videos folder? Just open up the home directory by clicking on the second icon down and then going to your pen drive, right click "copy" and then go to videos on the right, right click "paste". If that doesn't work, you may have flunked the install.

PS: To open the terminal, you press Ctrl+Alt+T or click the dash (top one on the right) and search "terminal". Wait for it to say *<yourusername>@<yourcomputername>:~$* first.

---

### Post by goldfoot777 on 2012-04-21
Thanks, copying directly into Video folder works...but still find it perplexing as to why it's a bit awkward just throwing it on the desktop, is this not the same hard-drive space? I've attached a pic of the df -h thing...does that show anything that has been done wrong?

Cheers

---

### Post by strask on 2012-04-21
You are certainly not out of disk space. Try opening a terminal and typing ```
ls -ld Desktop
``` and paste the results in here... I'm curious if the permissions are wrong on your desktop folder.

---

### Post by goldfoot777 on 2012-04-21
The message I get is:

drwxr-xr-x 2 goldfoot goldfoot 4096 2012-04-18 22:15 Desktop

---

### Post by 0011235813 on 2012-04-22
> **goldfoot777 said:**
> Thanks, copying directly into Video folder works...but still find it perplexing as to why it's a bit awkward just throwing it on the desktop, is this not the same hard-drive space? I've attached a pic of the df -h thing...does that show anything that has been done wrong?

Cheers
Unity was never really meant as a desktop type OS, I personally find searching for files with the Dash to be much faster. Although I think you can put files directly on the Launchbar, but I think you need to install something... I'll look into it. But the desktop issue could indeed be incorrectly set permissions.

---

### Post by strask on 2012-04-23
> **0011235813 said:**
> But the desktop issue could indeed be incorrectly set permissions.

Except the permissions on his Desktop folder, shown above, look correct.

---

