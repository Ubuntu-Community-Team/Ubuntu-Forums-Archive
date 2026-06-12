---
title: "How to add a new user account  by terminal command ?"
date: 2022-02-09
forum: New to Ubuntu
---

### Post by gardenair on 2022-02-09
hi,
          I want to know that how can I add a new user account in my Ubuntu Linux. Already I have a account which was created during the installation.I wast same thing by creating by command line. Suppose I want to create a new user account "foo" which may have its own home directory and GUI interface. Yes password is also must.
In terminal what command may I write for it ? I doesn't want to do it by GUI.

Thanks.

---

### Post by jimmy-frydkaer on 2022-02-09
sudo adduser foo

---

### Post by QIII on 2022-02-09
useradd might be a better option than adduser.  For instance the following will create a user home directory in the typical place:

```
sudo useradd -m username
```

Then set the password

```
sudo passwd username
```

and enter prompted data.

If you want to give them sudo privileges, also run

```
usermod -aG sudo username
```

---

### Post by KBar on 2022-02-09
> **QIII said:**
> useradd might be a better option than adduser.

For whom? **useradd**(8) specifically recommends **adduser** instead:
[QUOTE=useradd(8)]```
**useradd** is a low level utility for adding users. On Debian, administrators should usually use **adduser**(8) instead.
```[/QUOTE]
An excerpt from **adduser**(8):
[QUOTE=adduser(8)]```
They are friendlier front ends to the low level tools like **useradd**, **groupadd** and **usermod** programs,
```[/QUOTE]

---

### Post by gardenair on 2022-02-09
Well the account has been created successfully but when I try to login with the user name and password it comes into loop.The dialog box appear again and again even i am give correct name and password.

---

### Post by KBar on 2022-02-09
[LIST=1]
[*]Which command did you issue? 
[*]What's in the systemd journal? 
[/LIST]
It sounds like a PAM module issue but it could be happening for a lot of other reasons as well. In any case, the logs will tell us more about it. Try reproducing it once, switch to any virtual terminal, run [FONT=courier new]journalctl --boot[/FONT] and press _End_ or _Shift_+_G_ to reach the bottom and start going up page by page with _PgUp_ or _B_ until you encounter problematic entries. They are usually colored in red.

---

### Post by ActionParsnip on 2022-02-09
[https://help.ubuntu.com/stable/ubuntu-help/user-add.html.en](https://help.ubuntu.com/stable/ubuntu-help/user-add.html.en)

---

### Post by KBar on 2022-02-09
ActionParsnip, they specifically said they don't want to do it in a GUI app (also clear from the subject of the thread):
[QUOTE=gardenair]In terminal what command may I write for it ? I **doesn't want **to do it by **GUI**.[/QUOTE]

---

### Post by ActionParsnip on 2022-02-09
> **KBar said:**
> ActionParsnip, they specifically said they don't want to do it in a GUI app (also clear from the subject of the thread):

Gotcha

In that case, this explains it quite concidesly. Gives an explanation of each part of the process
[https://www.cyberciti.biz/faq/create-a-user-account-on-ubuntu-linux/](https://www.cyberciti.biz/faq/create-a-user-account-on-ubuntu-linux/)

---

### Post by QIII on 2022-02-09
> **KBar said:**
> For whom?

Note your man excerpt: "... administrators ... usually ..."  It does not, in fact, specifically recommend adduser.  Notice that I used the word "might".  Like the author of the man, I did not make a recommendation.

Low level != "bad" and front-end != "better".  "Friendlier" = left ignorant of what lies beneath.

Low level = finer control, front-end = common assumptions.  Both may be useful.  An admin, for instance, understanding the low level commands, can choose to accept the common assumptions that come with the front-end.  Learning starting with the front-end leaves a lot of the knowledge of the power of the lower level commands that underpin the front end unlearned.  Further, by using the flags in useradd, much can be accomplished in a single line in the terminal.  Notice that I added the -m flag, which is one of the assumptions adduser makes.  Sticking to front ends without learning what is behind them is fine for Windows users.  For Linux users, not so much.

This is quite analogous to first learning to use the terminal to install applications and then learning to use Synaptic or another GUI.

In my first few years studying math, most of the work involved understanding the "low-level" concepts.  By years 7 and 8, I had certainly moved on the the "front-end".  But I had a deep understanding of what I was doing -- even though it seemed at times that it was a waste of my time having learned the basics I "really didn't need".  I found out better very quickly.

---

### Post by him610 on 2022-02-10
Method suggested by QIII in post #3 works. I just completed all three steps in post #3 without issue. 

Test of newuser - 
```

ssh [email]newuser@198.x.x.xx[/email] 
sudo apt update
sudo apt list --upgradable -a
sudo apt upgrade
exit
ssh [email]newuser@198.x.x.xx[/email] 
exit

```

QIII has been giving good advice for years.

---

### Post by gardenair on 2022-02-11
Thanks for your valuable guidance  and suggestions.I remove my VirtualBox and reboot my system.Again I try to login  and it successfully login.Even after I create a new user as "[**[COLOR=#990303][B]QIII**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=628170")" describe in his post .It was also done without any error .
Actually my oracle virtual box was creating problem and it stop the virtual machine during loading.As " 		KBar" wrote  there are  lot of other reasons as well . This  problem stop the authentication.I even try to install oracle virtual box again and after rebooting the system it again shows the authentication loop  issue. As a result I again remove it and then try .Things are working fine now.So why virtual box is creating the issue and how may I fix it I think this is out side scope of this thread but if someone guide  me  will be thankful.

---

### Post by TheFu on 2022-02-11
This book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) covers basic Linux commands.  Best to learn them in order, because the knowledge builds on prior topics.
Adding a new user leaves off how to handle groups, how to put users into groups so they can work on the same files, UNIX file/directory permissions which become more important as more users are involved.

All good stuff to know from the CLI.

---

