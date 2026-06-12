---
title: "Computer went to switch user screen while performing update"
date: 2013-12-16
forum: New to Ubuntu
---

### Post by winslowevan2 on 2013-12-16
I was updating my computer from 10.04 to 12.04 and it had 4hrs left or so so i just left it running, when I came back the screen was black and it had gone to the switch user screen.

The problem is that now I cannot log in to see the progress and when I try to login it just gets stuck on 'logging in', this also means I cannot accept any of the installation prompts from the update

[SIZE=3]The login screen is different because I must have pressed something, it is a grey box with a picture of a computer that says "user-laptop" under it and it asks for the username. I can also choose from 'user defined session' or 'recovery console'
[/SIZE]
Other than that I can only choose the power button in the upper right to reset, turn-off or w/e.

Please give me whatever help you can, this is an M1300 tablet pc and I had to pxe install which was a hassle so I'd rather not do that again. Thanks!

---

### Post by asus-user on 2013-12-16
> **winslowevan2 said:**
> I was updating my computer from 10.04 to 12.04 and it had 4hrs left or so so i just left it running, when I came back the screen was black and it had gone to the switch user screen.

The problem is that now I cannot log in to see the progress and when I try to login it just gets stuck on 'logging in', this also means I cannot accept any of the installation prompts from the update

[SIZE=3]The login screen is different because I must have pressed something, it is a grey box with a picture of a computer that says "user-laptop" under it and it asks for the username. I can also choose from 'user defined session' or 'recovery console'
[/SIZE]
Other than that I can only choose the power button in the upper right to reset, turn-off or w/e.

Please give me whatever help you can, this is an M1300 tablet pc and I had to pxe install which was a hassle so I'd rather not do that again. Thanks!

Give this a try:
From the "Recovery console" type:
```
ls -lah
```
look in the output, if you find a line which look like this:
```

-rw-------  1 root root   55 Dec 16 17:35 .Xauthority
```
then you need to type:
```
chown username:username .Xauthority
```
Now try to login.

If this didn't work, try:
```
ls -ld /tmp
```
Check for the first 10 letters in the left, they should be exactly: drwxrwxrwt, for example:
```
drwxrwxrwt 18 root root 4096 Dec 16 23:33 /tmp
```
if that wasn't the case then type:
```
sudo chmod a+wt /tmp
```
and check again, and try to login afterwards.

Report here any messages or errors you get.

---

### Post by winslowevan2 on 2013-12-16
Thanks again! I actually just signed into the recovery console and it went to my desktop right away, I was just afraid to press it thinking it would mess up the update haha.

---

### Post by winslowevan2 on 2013-12-16
Okay, now, likely due to the installation getting interrupted I get stuck at 'starting up...',  I can boot into recovery mode and I tried to update and reinstall the update but I couldn't connect to the servers, then I just typed in the sudo init 2 command and I can get it to boot but I have to do that every time. 

I also got error messages about packages and the Ubuntu claimed it was version 10.04

---

### Post by deadflowr on 2013-12-16
> **winslowevan2 said:**
> Okay, now, likely due to the installation getting interrupted I get stuck at 'starting up...',  I can boot into recovery mode and I tried to update and reinstall the update but I couldn't connect to the servers, then I just typed in the sudo init 2 command and I can get it to boot but I have to do that every time. 

I also got error messages about packages and the Ubuntu claimed it was version 10.04

Do you know what those error messages about the packages were?
Or where you saw those messages.

And...
Do you know how far into the upgrade the system was when it went black?
was it still in the download stage or was it unpacking and installing what it had downloaded.

I'm guessing, since so many problems have occurred that it had already begun to install the new packages.
This might help
[http://askubuntu.com/questions/204200/ubuntu-12-10-broken-shutdown-while-updating](http://askubuntu.com/questions/204200/ubuntu-12-10-broken-shutdown-while-updating)
Though it is for an update from 12.04 to 12.10 the principle is the same.

---

### Post by winslowevan2 on 2013-12-17
Yes, it was during an install, I ended up getting one kernel to work and removed the others, however startup is now slow and there is a splotchy glitched out screen that pops up for a second or two before login loads.

---

