---
title: "Messed with keyring and have locked myself out of my Administrator account"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by altheablue on 2012-02-18
Hello all. I'm using Ubuntu 11.10, and I was having an issue in which Ubuntu kept asking me to unlock my default keyring, saying that it didn't get unlocked when I logged in. I assume this was because I had enabled auto-login.
So, I went looking for a "solution" to this, and for whatever reason I wound up deleting my default keyring (I *believe* that's what I did; I know!).

Now, I can't log in as administrator. The log-in screen says my password is invalid. I have Googled and searched this forum but not found anyone with my exact problem. I tried resetting my password to the same password from User Accounts (when logged in as Guest), but that didn't help. Tried resetting my password to the same password from console, but no luck. 

So here I am, logged in as Guest, hoping someone can tell me how to undo my foolishness. :) Many thanks in advance for any thoughts.

---

### Post by Rodney9 on 2012-02-18
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Rodney

---

### Post by altheablue on 2012-02-18
Thank you! Psychocat's tutorials have helped me in the past. Off to try...

---

### Post by Lisiano on 2012-02-18
First off, what "solution" did you follow? Post a link to it, as for getting you back into your account, can you still log in under your user using the Terminal? Either Ctrl+Alt+T or find in the Dash, then just type this ```
su username
``` where username would be your username, example
```
guest@Lisiano-Ubuntu:/$ su lisiano
Password: 
lisiano@Lisiano-Ubuntu:/$ 
```


EDIT: Nevermind my attempt at loging under a terminal, that won't work. Do the psychocat tutorial and report back.

---

### Post by altheablue on 2012-02-18
Ok, I followed psychocat's tutorial and got this: "Authentication token manipulation error" / "password unchanged".

One weird thing is that when I try to log in, it doesn't say "password invalid." The screen blinks black and then just puts up the login screen again. (Does that make sense?) 

The 'solution' I used was on askubuntu.com. I will try to find it. Thanks for your help, guys!

ETA: askubuntu is offline for maintenance. Criminy.

---

### Post by altheablue on 2012-02-18
Ok, I was wrong; the solution I used was here: [http://ubuntuforums.org/showthread.php?t=1623347](http://ubuntuforums.org/showthread.php?t=1623347). 

Specifically this (from that thread): "If you don't want to have to unlock the keyring, either use normal login  (and make sure your keyring password is same as your login password) or  set the keyring password to empty one (which will make the keyring to  store the keys unencrypted, which is less secure but probably not a  problem since you are already using automatic login).

If you wish to remove the keyring password, just go to  System/Preferences/Passwords and Encryption Keys, right-click the  "Passwords:login"-keyring and select "Change Password". type in your  current password and leave the fields for new one empty."

---

### Post by altheablue on 2012-02-18
Thanks for the help guys. Looks like I'm going to have to reinstall from my Windows partition as I can't find a solution anywhere. :( Thanks again.

---

### Post by sailor2001 on 2012-02-18
I have found the same thing, but wasn't for the system password, it was actually for gmail that I had  go online at start-up. Re-install gmail for that.

---

### Post by Orcris on 2012-02-19
Hold down shift when booting to access the recovery mode. Next, reset your password from there.

---

### Post by altheablue on 2012-02-19
Thanks Orcris. Unfortunately when I tried that I got an error and wasn't able to change the password. So I've already done a fresh install, and now I'm trying to get everything set back up again. (Fun weekend activity, right?)
Thanks! :)

---

### Post by wildmanne39 on 2012-02-19
Hi, also it is recommended for security reasons that you not disable your key ring and it is against forum policy to tell people how too, and yes I know that people were not being told how too, but it is worth mentioning for all the new people that read these forms.
Thanks

---

### Post by altheablue on 2012-02-19
Good to know. I certainly won't be doing it again. I'm slowly learning, with Linux, not to do things that I don't fully understand the consequences of. That seems obvious, but it can be hard to know sometimes. :)

---

### Post by wildmanne39 on 2012-02-19
Hi, you are correct, I have hosed my system many times in the past but almost everything can be fixed without a reinstall.

I now use virtualbox to experiment with ubuntu if I am unsure that way I do not mess up my system.
Thanks

---

### Post by john wagner on 2012-02-20
> **wildmanne39 said:**
> Hi, you are correct, I have hosed my system many times in the past but almost everything can be fixed without a reinstall.

I now use virtualbox to experiment with ubuntu if I am unsure that way I do not mess up my system.
Thanks

I find it to be more fun to hose my system.  It's always fun to start over...

---

