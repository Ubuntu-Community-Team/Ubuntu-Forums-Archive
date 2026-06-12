---
title: "Guest account not working"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by SudeepShakya on 2012-05-27
I have installed Ubuntu 11.10 and i'am just a beginner, I have one root account and a guest account, But it been sometime, when i click guest account on the login screen, it displays texts on the black screen and returns again to the login screen. Everytime it is same, I cannot login to guest account, But the root account works normally and the systems runs well. I also tried User Accounts but couldn't solve.

---

### Post by SudeepShakya on 2012-05-27
Hello, anybody there ??

---

### Post by Old_Grey_Wolf on 2012-05-27
Enter this command in the terminal and post the results. ```
cat /etc/lightdm/lightdm.conf
```

---

### Post by gscratch on 2012-09-03
this is a brand-new 12.04 on 'generic' hardware

I have this exact problem.  my regular user account works correctly, but whenever I try to 'change accounts' to the "Guest" or reboot and try to log in to the "Guest" account, the screen goes black for a fraction of a second, then returns to the login screen.

The results of the cat recommended above are here
```
glen@wildcat:~$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
glen@wildcat:~$ 

```

thanks,

---

### Post by NikTh on 2012-09-03
Hello , 

try this 

```
gksudo gedit /etc/lightdm/lightdm.conf
``` 

and add this line to the end 

```
allow-guest=true
``` 

save the document and reboot to try again. 

Thanks

---

### Post by gscratch on 2012-09-03
thanks.  unfortunately, the problem remains.
since you didn't specify, I assumed that it made no difference where in file that line was put:

```
glen@wildcat:~$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
allow-guest=true
glen@wildcat:~$ 

```

---

### Post by Old_Grey_Wolf on 2012-09-03
Did you update after the fresh install of 12.04? There was a regression bug in lightdm that caused that problem but has been fixed.

---

### Post by gscratch on 2012-09-03
thanks.  I have just run Update Manager and it says 'There are no new updates to install" and "the package information was updated 8 hours ago"

Is there some separate update that I should run ?

---

### Post by Old_Grey_Wolf on 2012-09-03
That update would have taken care of the bug. You have some other problem. I will see if I can find a solution using google; however, most people have had problem with the user account not working but the Guest account does work.

---

### Post by gscratch on 2012-09-03
thanks for help.

it's not critical, but I'd like to have the "Guest" account working next week.

---

### Post by NikTh on 2012-09-03
Hello, 

really weired problem. Never faced again. Usually users have problems with their own accounts , not guest. 

I don't know if needs a re-installation of Ubuntu , but I think not worth it. 

A workaround might be to create a new user account , and remove all the privileges except the basics. Make the user "standard" user it will fill the privileges automatically. 

And remove the line we added before from /etc/lightdm/lightdm.conf 

Thanks

---

### Post by Old_Grey_Wolf on 2012-09-03
Edit: see previous post above by NikTh.

The edit "allow-guest=true" didn't actually do anything. That is the default if "allow-guest=false" is not present.

---

### Post by gscratch on 2012-09-04
Thanks, I have removed the line

Before reading the updates, I decided to just create a standard user account.  System Settings -> User Accounts.  click the 'unlock' button, authenticate (my Account type is shown as Administrator) click the +, enter a user name (leaving account type at Standard). When I click the Create I get a popup with an error: 'Failed to create user' and this message:

```
GDBus.Error:org.freedesktop.Accounts.Error.Failed: running '/usr/sbin/adduser' failed: /usr/sbin/adduser returned an error (1): groupadd: cannot lock /etc/gshadow; try again later.
adduser: `/usr/sbin/groupadd -g 1001 luser' returned error code 10. Exiting.
```

Do I need to do something first?  should  I try to add this user at the command line directly with useradd  ? 

thanks for your continued help

---

### Post by NikTh on 2012-09-05
Hello , 

I think here is your problem : [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/523896)

Confirmed bug with High Importance. 

Just wait for a fix. 

So probably your first problem (with guest account) has a connection with this.

Thanks

---

### Post by gscratch on 2012-09-05
thanks.  I will wait.

---

### Post by gscratch on 2012-10-20
I haven&#8217;t been very diligent about working on this, but I don't see a perfect fix.

However, based on the linked-to in a previous post, I did a 

$ sudo mv /etc/gshadow.lock  /etc/gshadow.MOVEDlock

and now the Guest account appears to be working.

thanks for the help

Since I did not start this thread, I will not mark it 'Solved' but for me, it is.

---

