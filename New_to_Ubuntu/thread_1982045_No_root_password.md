---
title: "No root password"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by saponempotenti on 2012-05-17
So I finally got passed the live CD stage and fully installed Ubuntu on my laptop.  Remembering you are not supposed to run as root I changed my user account(the only account) to standard privilege.  I now cannot use anything that requires root privilege like Synaptic Package Manager.  I enter my user password and it says failure to authenticate.  So my question is, how do you give a regular permissioned user root privilege without knowing the root password?  -Thanks

---

### Post by Tamalin on 2012-05-17
Well, generally users do not log in as root, and the root account is disabled on Ubuntu.  Instead, administrative users can temporarily switch to root using sudo or gksu.  Standard users can not do this, so if you have a standard account, you will not be able to use administrative functions like synaptic.

---

### Post by lisati on 2012-05-17
The root password is disabled by default in Ubuntu. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by searchfgold6789 on 2012-05-17
It's OK to keep a user account that has root privileges, it's just that you don't normally want to use the root account itself.
Boot into recovery mode (This is done by selecting the entry that ends with the words "(recovery mode)" in the Grub menu. If you don't see the Grub menu, hold the shift key down as the computer boots up, use the arrow keys to select Recovery Mode, and press enter). Once in recovery mode, use the arrow keys to select the Root prompt option. Once the prompt appears, type in: ```
adduser {your username} admin
```
And reboot.
That should make you a sudoer again.

---

### Post by saponempotenti on 2012-05-18
> **searchfgold6789 said:**
> It's OK to keep a user account that has root privileges, it's just that you don't normally want to use the root account itself.
Boot into recovery mode (This is done by selecting the entry that ends with the words "(recovery mode)" in the Grub menu. If you don't see the Grub menu, hold the shift key down as the computer boots up, use the arrow keys to select Recovery Mode, and press enter). Once in recovery mode, use the arrow keys to select the Root prompt option. Once the prompt appears, type in: ```
adduser {your username} admin
```And reboot.
That should make you a sudoer again.

Followed those exact instructions and got an error message along the lines of - usergroup admin does not exist.  I then replaced "admin" with "root" and got the following error message - "Gpasswd: cannot lock /etc/group; try again later"

any ideas on how to correct that? -Thanks

---

### Post by saponempotenti on 2012-05-18
> **Tamalin said:**
> Well, generally users do not log in as root, and the root account is disabled on Ubuntu.  Instead, administrative users can temporarily switch to root using sudo or gksu.  Standard users can not do this, so if you have a standard account, you will not be able to use administrative functions like synaptic.

Correct, I cannot use sudo to open synaptic or other programs. This is my problem.  I do not have the sudo password or root password or whatever you want to call it :(

---

### Post by saponempotenti on 2012-05-18
> **lisati said:**
> The root password is disabled by default in Ubuntu. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I believe you misinterpreted my question.  I do not have a full understanding of how sudo and root work.  When you first install Ubuntu it asks you to make an account with root privilege.  You are then logged into that account, but given standard privilege(even though you technically are logged in a root account) and asked to enter in your password for each specific task.  My problem is that I denoted my account privilege to standard privilege, so now when it asks for sudo password, I type in my password that used to work, and it says that is not the correct password.  There is no password for any root or sudo tasks :'(  -thanks for your time and corrections to my confused understandings

---

### Post by wilee-nilee on 2012-05-18
> **saponempotenti said:**
> I believe you misinterpreted my question.  I do not have a full understanding of how sudo and root work.  When you first install Ubuntu it asks you to make an account with root privilege.  You are then logged into that account, but given standard privilege(even though you technically are logged in a root account) and asked to enter in your password for each specific task.  My problem is that I denoted my account privilege to standard privilege, so now when it asks for sudo password, I type in my password that used to work, and it says that is not the correct password.  There is no password for any root or sudo tasks :'(  -thanks for your time and corrections to my confused understandings

Open users and take a screen shot and post it.

How long ago did you install as well.

---

### Post by saponempotenti on 2012-05-18
> **wilee-nilee said:**
> Open users and take a screen shot and post it.

How long ago did you install as well.

I put the screen shot as an attachment, not sure how else to upload the thing.  And I just installed it earlier today.  I would rather not reinstall, trying to prove to my subconscious that Ubuntu will be workable and problems like this are easily fixable.

---

### Post by wilee-nilee on 2012-05-18
Yeah you made the admin account which is safe to run in as a full use account, into a standard account, I just wanted to see it to confirm this.

It is possible I think to change this back but this is fairly geeky stuff, you have to basically break into the account I believe.

If it was me I would just pull out anything you need like media....etc and just do a reinstall.

Not sure if this is going to work for you so let us know.

The way you get superuser  access also called root is to use sudo, then enter the password you set on the install. For example if you wanted to do  a update and upgrade in a terminal you would run.

```
sudo apt-get update && sudo apt-get upgrade
```You would then be asked for that password and you would be set. When you close the terminal you are out of the superuser privileges, this privilege is also stopped even with the terminal left open for a specific time, used to be 15 min, not sure how long now.

You might take a look at this link for more info on sudo, and how the setup runs, ask any questions as well. :)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by saponempotenti on 2012-05-18
> **wilee-nilee said:**
> Yeah you made the admin account which is safe to run in as a full use account, into a standard account, I just wanted to see it to confirm this.

It is possible I think to change this back but this is fairly geeky stuff, you have to basically break into the account I believe.

If it was me I would just pull out anything you need like media....etc and just do a reinstall.

Not sure if this is going to work for you so let us know.

The way you get superuser  access also called root is to use sudo, then enter the password you set on the install. For example if you wanted to do  a update and upgrade in a terminal you would run.

```
sudo apt-get update && sudo apt-get upgrade
```You would then be asked for that password and you would be set. When you close the terminal you are out of the superuser privileges, this privilege is also stopped even with the terminal left open for a specific time, used to be 15 min, not sure how long now.

You might take a look at this link for more info on sudo, and how the setup runs, ask any questions as well. :)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for the link and explaining it.   It would figure that I would break Ubuntu within the first couple of hours..but then again you should of seen me with windows... :p  I will do a reinstall of Ubuntu and post back when it is all fixed up :)  Thanks again!
FYI, I am all about the geeky stuff, I would be able to fix this if it was a windows box.  I actually study cyber security in my free time and know a decent amount when it comes to hacking into windows.  I do not know hardly anything about Linux.. and thats why I am installing it.

---

### Post by saponempotenti on 2012-05-18
> **saponempotenti said:**
> Thanks for the link and explaining it.   It would figure that I would break Ubuntu within the first couple of hours..but then again you should of seen me with windows... :p  I will do a reinstall of Ubuntu and post back when it is all fixed up :)  Thanks again!
FYI, I am all about the geeky stuff, I would be able to fix this if it was a windows box.  I actually study cyber security in my free time and know a decent amount when it comes to hacking into windows.  I do not know hardly anything about Linux.. and thats why I am installing it.

Reinstalled Ubuntu and everything is fine.  Thanks for the help.

---

### Post by wilee-nilee on 2012-05-18
> **saponempotenti said:**
> Reinstalled Ubuntu and everything is fine.  Thanks for the help.

Cool, enjoy. :)

---

### Post by Tamalin on 2012-05-18
> **saponempotenti said:**
> Followed those exact instructions and got an error message along the lines of - usergroup admin does not exist.  I then replaced "admin" with "root" and got the following error message - "Gpasswd: cannot lock /etc/group; try again later"

any ideas on how to correct that? -Thanks

Try "adm" as the group name instead of "admin".

---

### Post by wilee-nilee on 2012-05-18
> **Tamalin said:**
> Try "adm" as the group name instead of "admin".

You are not really supposed to advise people on a no password setup on the forum as far as I know.

Look at post #3.

As well if you looked at the thread the user had no admin account anymore.

---

### Post by critin on 2012-05-18
Question to anyone:  Why couldn't the poster just change the user acct back  to administrator?  

Thanks,

Oh I know why.  He was not administrator--silly me.  Thanks.

---

### Post by wilee-nilee on 2012-05-18
> **critin said:**
> Question to anyone:  Why couldn't the poster just change the user acct back  to administrator?  

Thanks,

Oh I know why.  He was not administrator--silly me.  Thanks.

You got it. :)

I'm surprised Ubuntu will allow you to just wipe the admin privileges really.

---

### Post by pablo180 on 2012-05-18
> **wilee-nilee said:**
> You got it. :)

I'm surprised Ubuntu will allow you to just wipe the admin privileges really.

I was just thinking the same thing; that is a serious flaw. That means that if you're changing around user privileges or swapping accounts and do it in the wrong order, there is a very real chance of locking yourself out of your own system. With seemingly no way back. 

That worries me. You'd think that there would be some safeguard, or even a fallback password. I am surprised this doesn't happen more often. I am now thinking that I should add another admin account, just in case.

---

### Post by critin on 2012-05-19
> **wilee-nilee said:**
> You got it. :)

I'm surprised Ubuntu will allow you to just wipe the admin privileges really.

Maybe there should be a safeguard, but I don't know.    This is a mistake one would only make once, I think.  A lesson well learned for those who read the thread.  

Confusion between running as 'root' and running as 'administrator' should be clear now, and this poster had the right idea about not working in root.

---

### Post by saponempotenti on 2012-05-19
> **pablo180 said:**
> I was just thinking the same thing; that is a serious flaw. That means that if you're changing around user privileges or swapping accounts and do it in the wrong order, there is a very real chance of locking yourself out of your own system. With seemingly no way back. 

That worries me. You'd think that there would be some safeguard, or even a fallback password. I am surprised this doesn't happen more often. I am now thinking that I should add another admin account, just in case.

I was surprised as well, I tried booting in safe mode and trying quite a few commands and "back corner of the Internet" theories but nothing worked.

---

### Post by mabo5184 on 2012-05-20
I just made the same mistake .... 
 
I had been looking for way to add my user to another group to fix another issue I was having and I did click on the account field to see what options were available, but I didn't realize I had actually changed the setting until later when I was trying use sudo and started getting wrong password errors.
 
I think adding a warning message to prevent this from happening would be a good idea.
 
I'm really disappointed because I had just completed a fresh install of 12.04 and installed all addition software I usually use, I was just looking forward to enjoying, but now I have to start all over again ...

---

### Post by coffeecat on 2012-05-20
> **mabo5184 said:**
> now I have to start all over again ...

If you've removed yourself from the admin group, all you have to do is follow case 1 in the following guide:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

One command in recovery mode - that's all.

**EDIT**: in 12.04, the command needs to be "adduser *username* sudo", although I believe "adduser *username* admin" will still work.

---

### Post by saponempotenti on 2012-05-20
> **coffeecat said:**
> If you've removed yourself from the admin group, all you have to do is follow case 1 in the following guide:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

One command in recovery mode - that's all.

**EDIT**: in 12.04, the command needs to be "adduser *username* sudo", although I believe "adduser *username* admin" will still work.

I tried that exact thing and it said there was no user group "admin".  Also tried replacing admin with root with no success.  Perhaps the "sudo" would of made it work.

---

### Post by mabo5184 on 2012-05-20
I did try the previously suggested fixes ...
 
adduser *username* admin, error no group ...
 
and
 
adduser *usern*ame adm, error group file locked ...
 
 
I will try "adduser *username *sudo" tonight and let you know how it goes ...

---

### Post by mabo5184 on 2012-05-21
Success, my admin privilege has returned ...
 
I tried "*adduser username sudo" *, but received the same error "gpasswd: cannot lock /etc/group; try again later."
 
I tried "*mount *" and my partition was reported to be mounted "rw", but there was also a warning message indicating that the information may not be up to date, and it suggested checking the /proc/mounts file ...
 
I tried "*cat /proc/mounts" ,* and sure enough the my drive was mounted "ro", so I issued the command shown in the above link " Fix Broken Sudo".
 
The comman was "*mount -o rw,remount /* " which remounted my drive "rw", and then I reissued the command "*adduser username sudo" *job done.
 
Thanks

---

### Post by wilee-nilee on 2012-05-21
> **mabo5184 said:**
> Success, my admin privilege has returned ...
 
I tried "*adduser username sudo" *, but received the same error "gpasswd: cannot lock /etc/group; try again later."
 
I tried "*mount *" and my partition was reported to be mounted "rw", but there was also a warning message indicating that the information may not be up to date, and it suggested checking the /proc/mounts file ...
 
I tried "*cat /proc/mounts" ,* and sure enough the my drive was mounted "ro", so I issued the command shown in the above link " Fix Broken Sudo".
 
The comman was "*mount -o rw,remount /* " which remounted my drive "rw", and then I reissued the command "*adduser username sudo" *job done.
 
Thanks

Still does not really consider the users tweaking that may have made the OS a security risk. Just getting back a admin account on your machine, does no equate to another’s set-up.

---

### Post by mabo5184 on 2012-05-21
In my case I don't think there was any user tweaking ...
 
I just accidentally changed my user account to standard ...
 
Do you think I have a security risk?

---

### Post by Lynceus on 2012-05-21
> **mabo5184 said:**
> In my case I don't think there was any user tweaking ...
 
I just accidentally changed my user account to standard ...
 
Do you think I have a security risk?

I don't think so

---

### Post by saponempotenti on 2012-05-22
> **mabo5184 said:**
> Success, my admin privilege has returned ...
 
I tried "*adduser username sudo" *, but received the same error "gpasswd: cannot lock /etc/group; try again later."
 
I tried "*mount *" and my partition was reported to be mounted "rw", but there was also a warning message indicating that the information may not be up to date, and it suggested checking the /proc/mounts file ...
 
I tried "*cat /proc/mounts" ,* and sure enough the my drive was mounted "ro", so I issued the command shown in the above link " Fix Broken Sudo".
 
The comman was "*mount -o rw,remount /* " which remounted my drive "rw", and then I reissued the command "*adduser username sudo" *job done.
 
Thanks

Thats awesome, great work figuring it out!

---

### Post by saponempotenti on 2012-05-22
> **Lynceus said:**
> I don't think so

I do not believe there is any security issues, just a simple mistake that has major consequences.

---

