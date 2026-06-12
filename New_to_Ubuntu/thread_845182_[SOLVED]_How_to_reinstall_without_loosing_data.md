---
title: "[SOLVED] How to reinstall without loosing data?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by sufyan on 2008-06-30
Hardy Crashed, The Desktop is not loading, I tried changing sessions, and the kernells (at the start-up), now I was thinking about transfering the data and going for a fresh install. 

I am runnng the terminal from the sessions menu at log in screen.  

Can anyone tell me how to transfer files using the 'terminal' to a USB or a CD/DVD? or a Better option if any. 

Thanks in Advance

---

### Post by Inxsible on 2008-06-30
Have you tried issuing this command to start the GUI```
startx
```If that doesn't work then you can copy all the contents to a usb by```
cp /path/to/source/directory /path/to/destination/directory
```Of course you will first need to mount the usb by checking its name under /dev, if its not already mounted

---

### Post by bumanie on 2008-06-30
Before reinstalling try > sudo apt-get install ubuntu-desktop

---

### Post by sufyan on 2008-06-30
> Code:
startx
I tried the command got the following error:

X: user not authorized to run the X server, aborting.
xinit: Server error.
Couldnt get a file descritor reffering to the console

> 
sudo apt-get install ubuntu-desktop  


Made no difference, Thanks neway

---

### Post by Claus7 on 2008-06-30
Hello,

about the startx command you should be root in order to do that (type sudo in front of the command and give your password when prompted).

Regards!

---

### Post by sufyan on 2008-06-30
> **Claus7 said:**
> Hello,

about the startx command you should be root in order to do that (type sudo in front of the command and give your password when prompted).

Regards!

I just did that, Now it says

X: warning; process set to priority -1 instead of requested priority 0 

Fatal server error:
Serve is already active for display 0
       If this server is no longer running, remove /tmp/.XO-lock and start again.

---

### Post by Claus7 on 2008-06-30
Hello, 

my suggestion should be to move (mv "name of the file" new name") instead of deleting the file, that the message tells you and retype the startx command as root. Does it make any difference?

Regards!

---

### Post by sufyan on 2008-06-30
With sudo i was able to move it. Upon startx Now it says I am using as a previleged user, and The Desktop is as it was when i first installed hardy. Now what do you recommend I should do?

---

### Post by Inxsible on 2008-06-30
> **sufyan said:**
> It says operation not permitteddid you use sudo mv ?

---

### Post by sufyan on 2008-06-30
With sudo i was able to move it. Upon startx Now it says I am using as a previleged user, and The Desktop is as it was when i first installed hardy. Now what do you recommend I should do?

---

### Post by Inxsible on 2008-06-30
> **sufyan said:**
> With sudo i was able to move it. Upon startx Now it says I am using as a previleged user, and The Desktop is as it was when i first installed hardy. Now what do you recommend I should do?You wanted to get to the desktop ..didn't you?

You are there now, what else do you want to do?

Just try and reboot and see if it works the second time as well.

---

