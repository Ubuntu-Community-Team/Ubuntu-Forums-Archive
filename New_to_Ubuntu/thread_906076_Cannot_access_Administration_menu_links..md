---
title: "Cannot access Administration menu links."
date: 2008-08-31
forum: New to Ubuntu
---

### Post by WVSteelers28 on 2008-08-31
Hi all.

Just recently, I've installed Ubuntu 8.04 on my older laptop.  For some reason when I click on some of the items under the Administration I get an error that says:

"The configuration could not be loaded.  You are not allowed to access the system configuration."

I'm the only person using this computer and all.  I'm getting this on certain links like 'Network', "Services", "Users and Groups", etc.

And help is appreciated.

Thanks,
WVSteelers22

---

### Post by jemate18 on 2008-08-31
> **WVSteelers28 said:**
> Hi all.

Just recently, I've installed Ubuntu 8.04 on my older laptop.  For some reason when I click on some of the items under the Administration I get an error that says:

"The configuration could not be loaded.  You are not allowed to access the system configuration."

I'm the only person using this computer and all.  I'm getting this on certain links like 'Network', "Services", "Users and Groups", etc.

And help is appreciated.

Thanks,
WVSteelers22

Which items on the Administration are you referring to?
Can you please tell us your exact actions? What did you clicked?

---

### Post by Oldsoldier2003 on 2008-08-31
please check to see if you accidentally removed yourself from the admin group by running this command in a terminal ```
id
``` If you are not part of the admin group then reboot your system and select the recovery mode option from the grub menu. This will boot you into single user mode as root. then issue this command:```
usermod -aG admin <your_username>
``` be sure to replace <your_username> with your actual username :)

After you have done that do this: ```
reboot now
``` and everything should be sorted.

---

### Post by WVSteelers28 on 2008-08-31
Hi all.

Oldsoldier, for some reason I'm still denied access to some of the items in the Administration menu (I may have messed up some where, I'll try again).  Attached is the output of 'id'.

What I am doing to get these errors.  I click on the 'System' menu, click on 'Administration', then selecting (For example) 'Network', and I get the error, screenshot attached. 

I'm still poking around the forums and Google trying to find myself 'some' help, but appreciate your help as well.

Thanks.
WVSteelers28

---

### Post by WVSteelers28 on 2008-09-01
Anyone?

---

### Post by jemate18 on 2008-09-01
> **WVSteelers28 said:**
> Anyone?

I found one problem similar to yours, but it is in Edgy Eft, anyway, you can try it, here is the link
> [http://ubuntuforums.org/showthread.php?t=286260](http://ubuntuforums.org/showthread.php?t=286260)

look for the post/instruction of phansiizwe

I hope this solves the problem

_______________________
Mark this thread SOLVED
"https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are
able to do what you intend to do and DONT FORGET to THANK the people
who HELPED YOU by clicking the "thanks" button on the lower right
"medal icon" for their help and useful post

jemate18

---

### Post by WVSteelers28 on 2008-09-01
Okay.  I followed the steps that were outlined in the post in the other thread.  I inserted 'gksu' in front of the 'Command' text.  I don't get the error message that says that I'm denied access to the item, but now it doesn't load anything.  I click on an item (Ex. Network) and nothing happens.

---

### Post by jemate18 on 2008-09-01
> **WVSteelers28 said:**
> Okay.  I followed the steps that were outlined in the post in the other thread.  I inserted 'gksu' in front of the 'Command' text.  I don't get the error message that says that I'm denied access to the item, but now it doesn't load anything.  I click on an item (Ex. Network) and nothing happens.

Did you tried restarting your computer? Just a suggestion....

---

### Post by WVSteelers28 on 2008-09-01
jemate18.  Still nothing.

---

### Post by jemate18 on 2008-09-01
> **WVSteelers28 said:**
> jemate18.  Still nothing.

CHeck the last post of this thread.. might help
> [http://ubuntuforums.org/showthread.php?t=824769](http://ubuntuforums.org/showthread.php?t=824769)

---

### Post by xeth_delta on 2008-09-01
Let's make sure you actually are in the admnistrative group.
open a terminal and type one by one:
```
whoami
id
cat /etc/group | grep -i your_user_name

```
Please post the output.

---

### Post by WVSteelers28 on 2008-09-03
Hey guys.  Unfortunately, I forgot to check my thread yesterday, and so I reinstalled the OS (I know it's the 'easy' way out).  I had changed quite a few things so I figured that I would just do a fresh install just to correct everything at once. 

Thanks for the help all.  I really do appreciate it a lot.

WVSteelers28

---

