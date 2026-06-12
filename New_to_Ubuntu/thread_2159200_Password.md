---
title: "Password"
date: 2013-07-02
forum: New to Ubuntu
---

### Post by 2good2btrue on 2013-07-02
Hi
When I installed version 12.4 I set up an account for my self, administrator, and one for my wife in the user account.
I quickly became tired of having to insert a password and disabled this in the user account. Unfortunately now when I go
to download new software, for example, it asks for the password but does not recognise the original
password and will not let me download the app. I tried to unlock the user account to re-establish the password but it wil not let me
as it does not recognise the password!

I would be gratful for some help - thank you.

---

### Post by mastablasta on 2013-07-02
try reseting the password on first user. that one is super user by default.

furthemore you should understand why the password is there. it is only envoked when doing changes to system files. so if a malware would want to run and change system files it would first need to know your password. after you setup everything you want to setup/install the password is only needed when installing updates - security patches and software updates (since they need to change current system files). it's is one of many security layers.

---

### Post by 2good2btrue on 2013-07-02
Thank you for replying. Yes in hindsight I see the security issues you mention and I wish I had not turned off the password.
I can't reset the password on the first user. I put in the password and it will not authenticate it. How can I see the password
or change the password?

---

### Post by p-dh on 2013-07-02
To change an account password without admin access, you will need to reboot and choose "Recovery Mode". When you are presented with the option about how to boot, choose the "Root" option. At the command line, type the following commands:
```
mount rw -o remount /
passwd <useraccount>
sync
reboot now
``` The first command allows you to write to the hard drive. In the second command, the <useraccount> is the one whose password you want to change. For instance, if i log in as frodobaggins and want to change the password for the account, I would type:
```
passwd frodobaggins
``` The third command ensures that the changes have been written and the final command reboots the PC.

You should be able to login to your account with the new password, install software, etc.

Peace,
Paul :cool:

---

### Post by Impavidus on 2013-07-02
See [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

(That's probably one of the most provided links here)

Edit: Ah, p-dh just beat me. His explanation is nearly identical to psychocats's.

---

### Post by 2good2btrue on 2013-07-02
Thanks for the instructions. Could not find the root option?!
I decided to reload the os. Any advice on how to delete the
original download of the os??????

Thanks

---

### Post by mastablasta on 2013-07-02
what do you mean you can nto find the root option? did you access th erecovery mode? hold left shift on boot to get the grub menu and then select recovery mode.:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
password reset is much easier and painless....

to delete the original download select to use full disk on install. note this will also erase any data you might have. so backup first.

option two that migh also work is to overwrite the current OS with a new install (no disk format). that way you should  keep the data however since you were messing with system and user settings i am not sure what that means and what will happen (though you should be able to cretae new user on install and delete the old users)

---

### Post by dannyboy79 on 2013-07-02
when you did a new install, what option did you choose? if you choose to use entire drive, then it overwrote your previous installation and you should now only have 1 ubuntu install on your computer.

---

### Post by 2good2btrue on 2013-07-03
Just to say thanks and close this thread. I re-installed from the CD.I purchased a new pc without an OS so Ubuntu runs alone. I'm still using XP on another machine for day today work.
I'm going to try and get some help locally - although I'm not hopeful. I'm thinking now in terms of a duel boot with Windows7 as  an option. I have tried Shotwell and like it. I have now downloaded Openshot
and need to see if this meets my needs. Probably the acid test will be if my wife can take her 2007 Word files/templates for the local village magazine and work with them in Libre office. Also all her contacts
have word docs what will happen when she tries to accept/transmit files over the internet. I suppose she will have to convert everything into pdf?
** Mastablaster **I down loaded your links for the manual and fire wall which are very helpful. **dannyboy79** I enjoyed your youtube channel, however, I have very little interest in gaming.
Over and out.

---

