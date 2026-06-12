---
title: "Problems with disabling guest log-in"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by zirgut on 2012-07-10
[FONT=monospace]Sometime ago I tried to disable the guest log-in, successfully actually. However I encountered some problems following that with the system going in to low graphics mode. Being a complete novice I am probably at fault for not getting the instructions right.
What I did is as follows. I went to terminal and entered this command 
[/FONT]#gksudo gedit /etc/lightdm/lightdm.conf#
No problem.
Then the edit window appeared and in that was a space followed by the code
#[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter#

So before this I entered the following
#allow-guest=false#

I then saved the file.This is where the problems started as I was asked what folder to save it in. No idea! However there was only one suggested so I saved it in that.Then closed the edit window.Closed terminal and went to restart and got the low graphics mode message.
After trying to resolve the problem with forum help I finally reinstalled ubuntu 1204 LTS. After re-installation I tried one more time with the same result and had to reinstall again.
I would really like to not have the  guest log-in but needless to say without having to deal with low graphics issues and other problems.
Is it me or the system .
I have a Nvidia graphics card if that is relevant.
Suggestions are extremely welcome.
Thanks

---

### Post by papibe on 2012-07-10
Hi zirgut.

Could you post the complete content of this file?
```
/etc/lightdm/lightdm.conf
```
Please paste the content inside code tags (available when you reply).

Regards.

---

### Post by NikTh on 2012-07-10
I had disable guest account with no problems in Ubuntu 12.04  

In terminal 
```
sudo nano /etc/lightdm/lightdm.conf
``` 
add this line to the END. 
```
allow-guest=false
``` 
Ctrl+x , then y(es) and finally Enter to save it. 
Restart. 
If something go wrong again , you can boot from recovery mode and first HIT "network" to mount read-write the filesystem , then HIT "root" and with same way ```
nano /etc/lightdm/lightdm.conf
``` you can remove the line. Don't forget to save (Ctrl+x , y(es) , Enter)

---

### Post by zirgut on 2012-07-12
> **papibe said:**
> Hi zirgut.

Could you post the complete content of this file?
```
/etc/lightdm/lightdm.conf
```Please paste the content inside code tags (available when you reply).

Regards.
Thanks Papibe ,
Here is the result of that command

[CODE][/bash: /etc/lightdm/lightdm.conf: Permission denied
CODE]

---

### Post by zirgut on 2012-07-12
Many thanks for that Nikth. Followed those instructions and it worked with no side effects.
Job done. Regards

---

