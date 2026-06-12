---
title: "to be able to run sudo as the regular daily user?"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by 1888software on 2013-09-10
Hello,
I logged in to the administrator account, tried to edit the administrator account (by trying to unlock) it *always* throws an error when i login: "System program problem detected" 

Then I ran the terminal, and entered:

sudo adduser laptop sudo

... where "laptop" is a daily user and not an administrator account

There were no errors reported in the terminal. I closed that.

When I logged out, and back into the user "laptop" I still get the same old error:

//////////////
laptop@ubuntu(........):~$ sudo /etc/init.d/apparmor start
[sudo] password for laptop: 
laptop is not in the sudoers file.  This incident will be reported.
/////////////


... all i want to do is to be able to run sudo as the user laptop because presumably this will help avoid having to repeatedly logging in as the administrator to do stuff...

Any ideas?

---

### Post by Kevin_Arnold on 2013-09-10
If the user is already created, you need to use usermod instead.

```

usermod -a -G sudo laptop 
```

You don't need to use sudo when logged in as root.

edit: Just read it again, it sounds like your main account isn't root (which is good) so you will need to use sudo.

---

### Post by TheFu on 2013-09-10
As the user allowed to run sudo, run visudo from the terminal and add the other user accounts to that file.
OR
manually add the new user to the sudo group in /etc/group file.

To learn more about the adduser command, run **man adduser**. There are lots of options.

I'd think that **adduser laptop -g sudo** would work, but I didn't check the manpage - it is from memory.

---

### Post by deadflowr on 2013-09-10
If I remember correctly, after changes such as the one you made of adding laptop to the sudo group, you need to reboot the system and not just log out and login again.
Of course my memory is scant and scattered.

---

### Post by squakie on 2013-09-10
Also, to me it sounded as if you want to be able to unlock the administrators account so you don't have to use sudo.  If so, please be aware that sudo is there so that you don't have to give root access.  I believe it is also forum policy not to post anything that would allow a user to essentially be root when logging in.  I could be wrong.

---

### Post by 1888software on 2013-09-10
Thank you for your collective responses. Rebooting resulted in an ability to use sudo running as "laptop". However, read on:


This is the Absolute Beginners section... I am an absolute beginner. So, is @[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1741485_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1741485") 				 				 					 						 	[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") suggesting that I should NOT enable the use of sudo with my regular daily "laptop" account or just what are you advising? Please clarify. Thank you.

---

### Post by whitesmith on 2013-09-10
You seem annoyed because you have to enter a password to install software and do other things that change the state of your computer, but this behavior is by design. Windows allows users to bypass a similar, but less effective, security procedure. Consider the result...viruses, malware, trojans, adware, crapware and the like routinely infect Windows systems, compromising their users' security and sometimes stealing their identity. This is nearly impossible in *nixland. A small price to pay for peace of mind. Don't even think of operating as a superuser all the time unless you have a death wish for your data.

---

### Post by deadflowr on 2013-09-10
As a sidenote, you can always su into another user and use that users rights.
```
su
``` 
by itself will prompt to become root, but 
```
su anotherusersname
```
Will prompt you to become the other user.
It'll ask for the other users password.
Typing exit will leave the other users session.

That way, you can keep the normal users rights to a minimum.

---

### Post by squakie on 2013-09-10
No, not at all.  What I'm saying is to USE sudo.  Some people want to "unlock" their account (or the root account) so they have all priviledges and can do everything without the use of sudo (this includes totally messing up their systems by not knowing or watching what they are doing).  Anything related to enabling this type of access is forbibben on the forums.

SUDO is the encouraged way to do things.  If you created a new user and want them to be able to use sudo - that's fine.  Heck, you can enable the root account if you want to - we just can't discuss that here.

---

### Post by TheFu on 2013-09-10
> **deadflowr said:**
> If I remember correctly, after changes such as the one you made of adding laptop to the sudo group, you need to reboot the system and not just log out and login again.
Of course my memory is scant and scattered.

Definitely no reboot is needed.  The impacted user needs a fresh login (logout/in) or the **newgrp** command can be used inside each shell to recognize the new group is added. So, if you want every open terminal to see the new group, .... 

For GUI apps to see it, you'd need to restart the main GUI app ... er ... it is easier for most people to just logout and back in again, but you can restart the main running process.  For LXDE, that is openbox.

Rebooting is only needed when a new kernel or libc are installed (and extra stuff isn't running to allow kernel replacement to a running system).  There are a few hardware things these days that seem to mandate rebooting to reset the hardware - usually USB chipsets, IME.  That happens to me a few times a year.

---

### Post by TheFu on 2013-09-10
> **deadflowr said:**
> As a sidenote, you can always su into another user and use that users rights.
```
su
``` 
by itself will prompt to become root, but 
```
su anotherusersname
```
Will prompt you to become the other user.

That was what I've thought and seen over the last 20+ yrs, however, a few weeks ago during a live demo to my LUG, **su** did not work from the **guest** user account.  I don't know if it is something about "guest" ... just that I was shocked and a little pissed that I couldn't su to my normal account to do a few other things.

Perhaps I hit an edge case or some protection just for the guest account.

---

### Post by deadflowr on 2013-09-10
Well, guest is a /tmp session, so maybe that has something to do with it.

All the same I can see it being an annoyance.

---

### Post by 1888software on 2013-09-10
Such a helpful group of Ubuntu users! Thanks everybody including [ 						 							[IMG]http://ubuntuforums.org/images/avatars/CircleofFriends80x80.png[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1850294") 				 				 					 						 	[**[COLOR=#000000]Kevin_Arnold[/COLOR]**]("http://ubuntuforums.org/member.php?u=1850294") 	 

 	[**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]

[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1276577_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1276577") 				 				 					 						 	[**[COLOR=#000000]deadflowr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276577")

[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1741485_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1741485") 				 				 					 						 	[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485")

and 

 	[**[COLOR=#000000]whitesmith[/COLOR]**]("http://ubuntuforums.org/member.php?u=664837") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]

Thanks again. Case closed.

---

