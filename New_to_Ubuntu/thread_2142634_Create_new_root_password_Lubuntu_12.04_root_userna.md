---
title: "Create new root password? Lubuntu 12.04 root username deleted!"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by imacg3ppc on 2013-05-06
After an exhausting weeks long epic of getting an xorg.conf to work with with my 2001 imac flower power G3, i was managing my accounts and adding new users... Somehow my root account was deleted. I can now only log in as Guest or as my 2nd username.

So now i have no root password, and i can not install packages, connect with wifi, or pretty much anything except play penguin golf etc.

Please someone tell me theres a workaround to make my new username ROOT.
The reason this is a problem is because normally i would just do a new fresh install, but my cd drive effin died on me right after my 90 day warranty was up! so i cant even reinstall until i get the cd drive! My kids have projects to do as always and i get it working... then mess it up!

Any help would be greatly apprciated! thanks guys n gals.

---

### Post by steeldriver on 2013-05-06
It sounds like what you mean is that your *primary sudoer* account was deleted - if so you can boot into the recovery console and add your 2nd user to the list of sudoers by following the instructions here

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

(of course you could add back your original user if you prefer). Here is some more info about the difference between *root* and *sudo*

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Cheesemill on 2013-05-06
The root account is locked in Ubuntu as it's not meant to be used. If you are asking how to add a user to the sudo group then you can do the following...

Boot into recovery mode and drop to a root shell.
Mount the / partition in read-write mode so you can make changes to it...
```
mount -o rw,remount /
```
Add your user to the sudo group...
```
usermod -aG sudo <USER>
```
replacing <USER> with your actual username. If you are unsure of your username you can look in the /home directory by doing '*ls -l /home*'.
Type '*exit*' to return to the recovery menu and select '*resume normal boot*' to finish booting your system.

Your user is now a member of the sudo group so you should now have all the permissions you need.

---

### Post by imacg3ppc on 2013-05-06
Sounds like a great fix and I'm going to try this tonight when i get out of work.

Just want to make sure we all understand.. I deleted my main account created during installation; lets say the username was "lubuntu" and the pass was "lubuntu". So when prompted for my "root" password, this would be it.

Now, since it was deleted, i am being prompted "Password for root:" and the password which would be "lubuntu" is no longer working... this is why i say i have deleted my root account.. Sooo haha does this change anything? will this sudo fix be able to help me out?

---

### Post by imacg3ppc on 2013-05-08
> **Cheesemill said:**
> The root account is locked in Ubuntu as it's not meant to be used. If you are asking how to add a user to the sudo group then you can do the following...

Boot into recovery mode and drop to a root shell.
Mount the / partition in read-write mode so you can make changes to it...
```
mount -o rw,remount /
```
Add your user to the sudo group...
```
usermod -aG sudo <USER>
```
replacing <USER> with your actual username. If you are unsure of your username you can look in the /home directory by doing '*ls -l /home*'.
Type '*exit*' to return to the recovery menu and select '*resume normal boot*' to finish booting your system.

Your user is now a member of the sudo group so you should now have all the permissions you need.


I was not able to boot into recovery mode... Holding shift does not bring up a boot menu as described in one of the links i was provided :see above post:

i have a usb keyboard, not wireless.

So i think that the instructions tell me to hold shift based on the fact that older versions use GNU Grub... i have a single boot system with yaboot as my only loader installed on the apple bootstrap... so any one know how to enter recovery mode with 12.04 and yaboot on a single boot linux ppc?

---

### Post by imacg3ppc on 2013-05-09
Problem solved.

First attempt i launched "Linux single" and it still launched X.... don't know why.
Second attempt, same command "Linux single" and 1 minute goes by and success in the form of root@localhost~$.

So i used
```
adduser <username> sudo
```
and told me user added. 
I then tried
```
adduser <username> admin
```
and it said admin doesnt exist.

But it worked and as a superuser i am no longer prompted for "root" password after the primary account was deleted.
Hope this helps someone in the future i always refer to old posts for help.

---

