---
title: "How to disable guest account in Ubuntu 11.10 ?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by nipunshakya on 2012-01-03
Hello friends. I have a dual boot in my machine, using Ubuntu 11.10 / Win 7. Recently i noticed that i don't want any Guest account in my Ubuntu so that none can access my privacy. I have an administrator privileged account under my name and so i would like to know how can i disable this unwanted Guest account. I found this link on Googling, but i would like to know the Guru's consent over this article provided to make sure if i can rely on it or not to disable my Guest account . . . 
Thanks in advance.

[http://www.tejasbarot.com/2011/11/25/howto-disable-guest-account-from-login-screen-ubuntu-11-10-oneiric-ocelot/](http://www.tejasbarot.com/2011/11/25/howto-disable-guest-account-from-login-screen-ubuntu-11-10-oneiric-ocelot/)

Regards, WinixUser):P

---

### Post by fdrake on 2012-01-03
> **WinuxUser said:**
> Hello friends. I have a dual boot in my machine, using Ubuntu 11.10 / Win 7. Recently i noticed that i don't want any Guest account in my Ubuntu so that none can access my privacy. I have an administrator privileged account under my name and so i would like to know how can i disable this unwanted Guest account. I found this link on Googling, but i would like to know the Guru's consent over this article provided to make sure if i can rely on it or not to disable my Guest account . . . 
Thanks in advance.

[http://www.tejasbarot.com/2011/11/25/howto-disable-guest-account-from-login-screen-ubuntu-11-10-oneiric-ocelot/](http://www.tejasbarot.com/2011/11/25/howto-disable-guest-account-from-login-screen-ubuntu-11-10-oneiric-ocelot/)

Regards, WinixUser):P
I would suggest you to use gedit instead of "vi" to edit the file... if you'r not confortable
sounds good to me or you can unistall the guess package
```
sudo apt-get purge gdm-guest-session
```
whatever works for you..

---

### Post by nipunshakya on 2012-01-03
> **fdrake said:**
> I would suggest you to use gedit instead of "vi" to edit the file... 
```
sudo apt-get purge gdm-guest-session
```whatever works for you..
do i need to be root for this code to be effective too??  Because i tried your code, restarted it, didn't work out and i got the same 'guest session' and 'other' session too.
Thanks for your quick reply.:D

---

### Post by fdrake on 2012-01-03
> **WinuxUser said:**
> do i need to be root for this code to be effective too?? 
Thanks for your quick reply.:D

sudo gives you root priviledges without being logged as root. But you need to be an admin user. see [sudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by dcsoldschool53 on 2012-01-03
**In the terminal,```
sudo gedit /etc/lightdm/lightdm.conf
```**[B]Under,

 [SeatDefault] section[/B]
[B]greeter-session=unity-greeter
 user-session=ubuntu
Add this code to it[/B].```
 **allow-guest=false**
```[B]This should remove your guest account. Now save and exit the lightdm.conf file. Then, reboot to see the changes.
[/B]

---

### Post by nipunshakya on 2012-01-03
Dear sir, i followed your instructions, booted from my administrator privileged account and it even removed one of the items (i don't remember the name of package uninstalled, sorry). I restarted, and now, i am commenting this thread using guest session. :( 

I tried to follow up the commands provided on the link i posted, but it resulted the following(see image)

---

### Post by nipunshakya on 2012-01-03
> **dcsoldschool53 said:**
> **In the terminal,```
sudo gedit /etc/lightdm/lightdm.conf
```****Add this if it is not there under [SeatDefault] section**```
**allow-guest=false**
```[B]This should remove your guest account. Now save and exit the lightdm.conf file. Then, reboot to see the changes.
[/B]

Sir, i tried your help too...but it seems that my Ubuntu isn't working as it is meant to be. The Guest account hasn't vanished, and now i am commenting this post logging in as Guest in my own machine !:(

---

### Post by nipunshakya on 2012-01-03
Now this might seem a bit wired, i checked the lightdm.conf file, it has **allow-guest=false **on it too, saved . Even the command worked well, **sudo apt-get purge gdm-guest-session **coz when i reentered the same command, it gave the following(see image). so this literally means that my guest session has been removed, but still, i can't get rid of logging in using my Guest Account. :(

---

### Post by dcsoldschool53 on 2012-01-03
OK I see what you meant.

---

### Post by fdrake on 2012-01-03
> **WinuxUser said:**
> Dear sir, i followed your instructions, booted from my administrator privileged account and it even removed one of the items (i don't remember the name of package uninstalled, sorry). I restarted, and now, i am commenting this thread using guest session. :( 

I tried to follow up the commands provided on the link i posted, but it resulted the following(see image)

my bad! I made a typo:
```

sudo apt-get remove --purge gdm-guest-session

```

to veryfy that is no installed do
```

sudo apt-get install aptitude
sudo aptitude show gdm-guest-session | grep State

```
and check the last line! it should say "State: not installed"

---

### Post by nipunshakya on 2012-01-03
> **dcsoldschool53 said:**
> OK I see what you meant.
Sir, the file is totally saved, i checked it again.:)

---

### Post by nipunshakya on 2012-01-03
> **fdrake said:**
> my bad! I made a typo:
```

sudo apt-get remove --purge gdm-guest-session

```
doing this gave me a notification on terminal that package guest-session not installed.
> **fdrake said:**
> 
to veryfy that is no installed do
```

sudo apt-get install aptitude
sudo aptitude show gdm-guest-session | grep State

```and check the last line! it should say "State: not installed"
and doing that too said the same thing you mentioned "State: not installed"
i guess either procedures meant the same thing, but still im on my Guest Account now and this thing is getting wired here.....:(

---

### Post by fdrake on 2012-01-03
> **WinuxUser said:**
> doing this gave me a notification on terminal that package guest-session not installed.

and doing that too said the same thing you mentioned "State: not installed"
i guess either procedures meant the same thing, but still im on my Guest Account now and this thing is getting wired here.....:(

while in guess session can you type:```

whoami && echo $DESKTOP_SESSION
```

---

### Post by nipunshakya on 2012-01-03
> **fdrake said:**
> while in guess session can you type:```

whoami && echo $DESKTOP_SESSION
```
The image might be self explanatory sir. :)
and thank you for quick replies to help me solve this issue

---

### Post by nipunshakya on 2012-01-03
Dear friends, i didn't know restart and shut down would be a great difference until now. I just shut down my machine and then turned it on . . . strange but the guest session has gone. Thank you guys for your help, and now i am marking this thread as solved.. :)

Thanks again to those who helped.
Regards, WinuxUser

---

### Post by fdrake on 2012-01-03
are you sure it's a guest session , what you are using maybe it's just a user that you created as guest in users&Groups (from System>Administration) that doesn't require a password. Guess-session it's another thing , it creates a session in the /tmp folder. basically you don't have any access to the filesistem and other users' data.


edit: I just saw your last post so I guest it's ok

---

### Post by nipunshakya on 2012-01-04
Sir, im sure that i once used to be greeted with the welcome screen that included login as <my_username> and password, next was a "Guest Session" and the last one was "Other". I still remember that i haven't created any other group as guest, otherwise it would have been shown under "Other". i had the problem with your prescribed codes not workiing at each restart, but now, a shut down solved it all.... Thanks for your help.

Regards, WinuxUser

---

