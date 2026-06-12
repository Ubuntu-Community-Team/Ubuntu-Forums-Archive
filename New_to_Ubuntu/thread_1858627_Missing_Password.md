---
title: "Missing Password?"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by Desktop_n00b on 2011-10-12
Ok, so I upgraded to 11.10 today and was making 2 user accounts. I decided to make neither of them need a password to log in. After doing this I can not install programs or make any changes to system settings. The Reason is when I put in my password, it says try again. I made sure I typed it correctly.

My password is gone, so what do I do to get it back?

(yes I looked for already existing thread, if I missed one sry.)

I am really frustrated, spent at least an hour trying to get my wife's yahoo account to work in evolution. I finally gave up on that after following the 5th "how to" then this happens.

---

### Post by Lisiano on 2011-10-12
Reboot your PC and hold Shift to get a Grub menu. Now press down once (So it says Recovery on the end of the line) and press Enter/Return

After it is done booting, you will see a menu, pick "Root" then you will get a root prompt, now just type this 
```
passwd USER
```
Where USER is your username.
You will be asked twice for a new password (Won't be echoed, just like sudo)
Now just type ```
reboot
``` and you will... Well.. Reboot.

---

### Post by Desktop_n00b on 2011-10-12
ok, I held down shift, went to recovery, selected root, then typed passwd ace (which is my user name) then put in my password twice, but then I get this message


passwd: Authentication token manipulation error
passwd: password unchanged

---

### Post by Lisiano on 2011-10-12
This is unexpected. Could you try typing a very simple password? Say... ```
1
``` This is just to see if you made a mistake or there is something seriously wrong. If it errors, just in case of a very bad keyboard, try it 2 more times.
If it doesn't error, just do the command again and try to type your password correctly.

---

### Post by haqking on 2011-10-12
> **Lisiano said:**
> This is unexpected. Could you try typing a very simple password? Say... ```
1
``` This is just to see if you made a mistake or there is something seriously wrong. If it errors, just in case of a very bad keyboard, try it 2 more times.
If it doesn't error, just do the command again and try to type your password correctly.

the default minimum required is 4 characters

---

### Post by Lisiano on 2011-10-12
Whenever I try doing a very short, (Which I tested before posting the post before) it let me change the password to 1. I have to admit to making my grandmas password a 2 char password, she is not an admin though so not a real security breach since it's set to never ask for the password, be it login or unlocking the desktop, beside TTY. Also SSH Server only allows me and my cousin to log in, we both have secure passwords.

EDIT: Though yes, if it errors and says that the password is too weak or short, try using 1234 or something.

EDIT 2: Just tested. If I passwd as root/sudo or make a user, there is no limit. If I try to passwd from a user, I get a reply from passwd to pick a longer password. Since the OP is in Recovery, thus using Root, using 1 as a test should work since Root is not limited on what password he wants to set.

---

### Post by Desktop_n00b on 2011-10-12
ok, I tried it (3 times) and I still get the same error. 

I also tried the other user, and get same error. Tried to check to see if capital letters changed anything, then it said no user, so I am typing in user names and password
correctly

---

### Post by Lisiano on 2011-10-12
This is interesting... Could you try using this command to see that you didn't erase or corrupt your /etc/shadow and /etc/passwd files. **_*[COLOR="Red"]DO NOT POST /etc/shadow UNDER ANY CIRCUMSTANCES![/COLOR]*_** This file contains logins and passwords (Hashed but can be cracked given enough time), never post this file to ANYONE, including anyone claiming to be a close relative that has a login on that machine. Never.

So. To see if you have a /etc/shadow and your user has a password set, type this
```
cat /etc/shadow | grep ace
```
You will get something along this line
```
ace:VeryBigAndRandomStringOfTextThatYouMustKeepSecret:15221:0:99999:7:::
```
To better understand this line, take a look at [http://www.cyberciti.biz/faq/understanding-etcshadow-file/](http://www.cyberciti.biz/faq/understanding-etcshadow-file/)
Now for /etc/passwd. Basically the same and this one is safe to post if you wish to.
```
cat /etc/passwd | grep ace
```
Should yield something along theses lines
```
ace:x:1000:1000:Ace:/home/ace:/bin/bash
```

---

### Post by Desktop_n00b on 2011-10-12
ok, they both worked. what does that mean?

---

### Post by Lisiano on 2011-10-12
This just means that both files exist and both have you in them.
I don't know how to find anything else that might be the problem beside those 2 files, but I have an idea of trying to manually change the password, while this is risky, I also have no idea how Linux hashes passwords.

---

### Post by haqking on 2011-10-12
> **Desktop_n00b said:**
> ok, they both worked. what does that mean?

so how many users are on the system ?

yours and the 2 accounts or your accounts is one of the 2 you created ?

sounds like a simple broken sudo to me ?

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Desktop_n00b on 2011-10-12
I was reading something about if they don't match you might get that error. That sound legit?

---

