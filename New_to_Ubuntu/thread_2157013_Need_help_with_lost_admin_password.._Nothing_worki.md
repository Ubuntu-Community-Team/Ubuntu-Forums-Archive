---
title: "Need help with lost admin password.. Nothing working"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by trubloodfan on 2013-06-23
I just now got a new computer today from a friend. I have researched all  the posts on Google to try to find out how to reset the root password  since I do not know it and cannot get ahold of him. Tried remounting,  tells me it cannot find it. Tried going through the recovery menu, of  course I get the error since it is in read-only. When I tried to go  through the fdisk to get it into read-only, it said something about  checked etc clean blocks and then sits there. I do not know what to do  at this point. Any help would be appreciated

---

### Post by Bashing-om on 2013-06-23
trubloodfan; Hi ! Welcome to the forum:

Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT]enjoy, we are here to help you over the rough spots[/INDENT]

---

### Post by Impavidus on 2013-06-24
BTW, it's not the root password you want to reset. It's the password of the user who has the right to use sudo. By default the root password doesn't exist on Ubuntu. See here for more details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by newb85 on 2013-06-24
> **trubloodfan said:**
> I just now got a new computer today from a friend.

Do you mean that you're borrowing the machine from a friend, or that you've acquired the machine from a friend, and it's now yours?

If it's now yours, I would suggest re-installing Ubuntu, unless that friend has Ubuntu set up a special way that you prefer to keep.  Do you need all your friend's files, programs and settings hanging around?

---

### Post by trubloodfan on 2013-06-24
To answer all of these questions, I tried resetting the password. The screen doesn't move after I start fdisk to where it is RW, nor will it let me restart it. I bought it yesterday from a friend. I am trying to get in to change the admin password that will let me change the boot sequence to where I can wipe everything and thats the password it wont let me change.

---

### Post by vipulkumar7 on 2013-06-24
To Recover root password, You need to reboot the system Pree ENTER /Press ESC  Hold down shift key,Then go to Recovery mode Type mount -rw -o remount/ then passwd root [press ENter]

---

### Post by Cheesemill on 2013-06-24
> **trubloodfan said:**
> I am trying to get in to change the admin password that will let me change the boot sequence to where I can wipe everything and thats the password it wont let me change.

If this is the BIOS password that you're talking about then it has nothing to do with Ubuntu.

It is possible to reset the BIOS password but the method varies for each machine and you are going to have to take it apart.
Just google for 'bios password reset' along with the model number of your motherboard/laptop to get instructions.

---

### Post by deadflowr on 2013-06-24
I agree with Cheesemill on that if it's a bios issue, you'll need to reset it.
Depending on the type of machine it could be easy or quite difficult.
A tower machine might only require remove the side panel and removing the cmos battery, and resetting the jumper.
A laptop might be more difficult.
Locate the machines manual from the makers website, if possible.
Normally, it'll show what jumpers are what, or something like that.
Or at least how to reset the bios settings to the defaults.

---

