---
title: "Problem with permissions and user menu"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by KursiBro on 2012-12-22
Hi... I have a serious problem. I was playing with my Ubuntu 12.04 LTS root permissions for LAMP and now I cant enter to the system. 

-I turn on my computer and I get the  user menu.
-I enter my password for my user.
-It appears a black screen for 1 second with letters.
-Im back to the user menu.

I tried with invited user but the same thing happens.

Can someone help me please. I hope i can restore mi ubuntu =(


Thanks!

pm: im now on windows >=(

---

### Post by Wim Sturkenboom on 2012-12-22
If you don't know what you've changed, a re-install of Ubuntu is probably the easiest. If you ran e.g. a recursive chmod or chown, it will be a mission to restore permissions.

You can use a liveCD to inspect the log files of your system for pointers, but it's probably a useless exercise.

---

### Post by zombifier25 on 2012-12-22
Log in a tty by pressing Ctrl + Alt + F1, log in, and type this command:
```
sudo chown yourusername:yourusername ~/.Xauthority
```
see if it helps.

---

### Post by Temporarily on 2012-12-22
You have the exact same question here : [https://answers.launchpad.net/ubuntu/+source/lightdm/+question/217405](https://answers.launchpad.net/ubuntu/+source/lightdm/+question/217405)

Follow the answer from there or here.. (it is the same) and remove .Xauthority file .. 

If the problem is deepest , then I tend to agree with [Wim Sturkenboom]("http://ubuntuforums.org/member.php?u=5214") suggestion.

Thank you

---

### Post by KursiBro on 2012-12-22
All your post's did not help unfortunatly.

But... I kind of solved the issue without erasing my files. I installed  ubuntu in another partition and mounted the old partition in the new one. Then I saw that al my folders files and subfolders were blocked only for root users. I changed the persmission from the new ubuntu partition and it  finally worked.:guitar:

Thanks anyway!

---

### Post by audiomick on 2012-12-22
A very creative solution. Well done.:popcorn:

---

### Post by Wim Sturkenboom on 2012-12-23
Congrats, you can mark your thread as solved using the thread tools just above the first post.

There is no easy way of restoring permissions without knowing for sure that you haven't missed one somewhere. What can help is to install tree (_sudo apt-get install tree_) and run _sudo tree -pug / > tree.txt_. Store the file for later reference; it contains all information that you basically need (user, group and standard permissions).

---

