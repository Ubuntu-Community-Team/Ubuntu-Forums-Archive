---
title: "How to run as root/admin"
date: 2012-08-30
forum: Recurring Discussions
---

### Post by cbennett926 on 2012-08-30
Hello, 

I have always wondered, is there a way to run your computer solely as an admin or root? So you do not have to authenticate anything, or type sudo when you run terminal commands etc etc?

---

### Post by Petro Dawg on 2012-08-30
Its a bad idea, and I hesitate to post but here it is...
Info found [here]("https://help.ubuntu.com/community/RootSudo").

> Remove Password Prompt For sudo

If you disable the sudo password for your account, you will seriously compromise the security of your computer. Anyone sitting at your unattended, logged in account will have complete Root access, and remote exploits become much easier for malicious crackers.

This method is NOT suggested nor supported by the designers of Ubuntu.

Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as Root.
These instructions are to remove the prompt for a password when using the sudo command. The sudo command will still need to be used for Root access though.

Edit the sudoers file

Open a Terminal window. Type in sudo visudo. Add the following line to the END of the file (if not at the end it can be nullified by later entries):

```
<username> ALL=NOPASSWD: ALL
```
Replace <username> with your user name (without the <>). This is assuming that Ubuntu has created a group with the same name as your user name, which is typical. You can alternately use the group users or any other such group you are in. Just make sure you are in that group. This can be checked by going to System->Administration->Users and Groups

Example:

```
michael ALL=NOPASSWD: ALL
```
Type in ^x to exit. This should prompt for an option to save the file, type in Y to save.

Log out, log back in. This should now allow you to run the sudo command without being prompted for a password.

Reset sudo timeout
You can make sure sudo asks for password next time by running:

```
sudo -k
```
The default sudo timeout length can be changed by following this article: RootSudoTimeout.

---

### Post by 2F4U on 2012-08-30
Of course there is and a quick search on the web gives the required information, for example

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cbennett926 on 2012-08-30
> **2F4U said:**
> Of course there is and a quick search on the web gives the required information, for example

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Thank you!! I feel really dumb for not thinking to search for it!

---

### Post by mastablasta on 2012-08-30
it opens the computer to malware attacks. since they do not need user password to access the system. if you use it don't come here opening "i think i've been hacked" thread :-P
 
perhaps in some testing environment the use is justified (to work faster).

---

### Post by Primefalcon on 2012-08-30
> **mastablasta said:**
> perhaps in some testing environment the use is justified (to work faster).
maybe I've never needed it though, at most I do a sudo su - or a gksudo dolphin/nautilus.... but usually just good ol sudo <command> does me fine...

---

### Post by Jakin on 2012-08-30
> **mastablasta said:**
> it opens the computer to malware attacks. since they do not need user password to access the system. if you use it don't come here opening "i think i've been hacked" thread :-P


Exactly, thats your safety belt.

---

### Post by Gone fishing on 2012-08-31
Don't do it!

If you need root for some time open a terminal and sudo -i will act like a root shell without having to keep typing sudo, I do this sometimes. You can even enable the root account but to use it on a casual basis would be madness. I have enabled root in the past but to setup things where I needed a lot of access to a root terminal but...

If you need a root terminal and internet best use sudo -i or ssh in from another box.

---

### Post by lisati on 2012-08-31
> **Gone fishing said:**
> Don't do it!

If you need root for some time open a terminal and sudo -i will act like a root shell without having to keep typing sudo, I do this sometimes. You can even enable the root account but to use it on a casual basis would be madness. I have enabled root in the past but to setup things where I needed a lot of access to a root terminal but...

If you need a root terminal and internet best use sudo -i or ssh in from another box.

+1

If you choose to use *sudo -i* don't forget to *exit* out of it when you're done.

---

### Post by 3rdalbum on 2012-09-01
> **cbennett926 said:**
> Hello, 

I have always wondered, is there a way to run your computer solely as an admin or root? So you do not have to authenticate anything, or type sudo when you run terminal commands etc etc?

Yes, it's called "Install Windows XP".

But to be serious, there is a way, but you'd be turning off a fundamental security system, and most Linux software assumes that the security system remains intact. To put it bluntly, you may find that some programs won't work if you turn off the security.

If you do it, it's at your own risk; and WHEN you regret doing it you'll probably find yourself having to reinstall Ubuntu entirely.

---

