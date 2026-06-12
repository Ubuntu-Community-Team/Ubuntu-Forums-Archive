---
title: "Why doesn't anyone use a root account?"
date: 2008-04-18
forum: Recurring Discussions
---

### Post by WBL on 2008-04-18
One of the first things I do after an Ubuntu install is enable the root account.  However, I've noticed that a lot of people around here use "sudo" instead.  Why is that?  :confused:

-WBL

---

### Post by smartboyathome on 2008-04-18
Because using the root account is a security risk. Any code can do anything to the os, thus allowing full control to anything run on the computer. Using sudo prevents this by requiring you to enter your password, thus ensuring that it is you who is running the script, not a script.

---

### Post by Triggerhapp on 2008-04-18
I learnt very early on in my server days that leaving myself logged in as root to get coffee (and subsequently fall asleep at the kitchen table waiting for the kettle to boil) was a very bad idea.

---

### Post by dndrich on 2008-04-18
There are many more experts on this forum than me.  But, using a root account causes a problem since as root, you can cause major problems with system files if you are not careful.  Using a standard account prevents all kinds of mayhem.  Furthermore, using sudo allows you to become root for the specific task, but not any task.  That is inherently much safer.  I'm sure others will chime in.  I would not recommend it.

---

### Post by malspa on 2008-04-18
I never use it once I found out that most Linux people advise against it.  Also because I don't need it at all.

---

### Post by WBL on 2008-04-18
I just find it annoying to have to keep typing "sudo."  Also, I live alone, so nobody touches my computer except me.  So I just keep 2 terminals open-one as root, and one as the regular user.

-WBL

---

### Post by RedSquirrel on 2008-04-18
You might want to read the following document if you haven't already:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by analoog on 2008-04-18
if you want to work as root for some time you can also enter sudo -i.
If you enable the root account I would advice to change the root name because attacks against root are common if someone wants to test/crack your box.

---

### Post by nemesis8601 on 2008-04-18
I'm still a relatively new user of Ubuntu, but I've learned that in fiddling around with the OS it's a good thing I'm not logged in as root, as I could have done a lot of damage. 

It's also good etiquette not to put anything on your computer at risk, and using sudo makes it easier.

---

### Post by Bachstelze on 2008-04-18
Why *should* anyone use the root account?

---

### Post by Dr Small on 2008-04-18
Please read the sticky:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by SlappyPappy on 2008-04-18
What's root?  :(


Hehehehehehehehehe

---

### Post by cardinals_fan on 2008-04-19
I use su.  Whenver I need to perform system tasks, I sign in using su, and sign out when I'm done.

---

### Post by jrusso2 on 2008-04-19
A root account is no more of a security risk then using SU or Sudo.  I always enable root but I rarely use it as I have gotten used to working with sudo now.

But I like having it for that emergency or time when I do need it.

---

### Post by p_quarles on 2008-04-19
Having a root account is not an added security risk, and neither is not having one. I have frankly never figured out where people get the idea that there is any kind of significant difference in terms of security.

A secure Ubuntu setup -- with the root password disabled -- is far more secure than a RHEL box with a bad root password. The inverse is also true. 

This forum's policy is to not support changing the default Ubuntu method of gaining root privileges. The reason for this is pretty simple: Ubuntu's security and system administration policies are structured around the use of "sudo" rather than the use of a separate root account. Basically, changing this kind of basic system policy has the potential to break things (e.g., single-user mode boot-up). That, combined with the fact that it is completely unnecessary for any purpose any of the staff have so far been able to think of, makes it officially not recommended.

---

### Post by Joeb454 on 2008-04-20
I use sudo to log in as root if ever I need to do extended work as root.

I just fire up my terminal, and type ```
sudo -i
``` that's it, I just type *exit* to end the session :)

---

### Post by ibutho on 2008-04-20
I also enable the root account and I go even further and remove all sudo privileges from the admin group. Its just the way I prefer to use my system and frankly I don't see how its less secure than using sudo.

---

### Post by SunnyRabbiera on 2008-04-20
Both systems have their faults and good points.

having a root/administrator account can be good for those who do not understand how a linux system works with administration. But look at what having administrative access in windows can do, its no wonder why it attracts so many viruses and stuff.

having sudo takes away the risk of having an administrative account but with having access to administrative services when needed.
look at what apple has done with sudo, it has made OSX very quick on installing apps without much risk to the main OS but the lack of a master password can be a drawback too.... having the sudo password be the same as your password makes it more vulnerable.

---

### Post by pjkoczan on 2008-04-21
The only reason I can think of offhand why root could be less secure than sudo is that it's one less variable to brute force (just the password, since the username is known). With sudo on a multiuser box, a cracker would need to brute force a username *and* its password, and the cracked account would have to be a sudo'er (that's three things to get right instead of one).

Still, proper policy (frequent password updates, strong passwords, etc.) and proper, limited usage of root/sudo are worth much more than the simple choice of root vs. sudo.

As for me, I use sudo at home, as I find it works for 99.95% of my administrative tasks. The only time I've found root to be truly *necessary* is when there are filesystem errors at boot time, the kind where it says "Enter root password for maintenance." If anyone knows a way around this, I'd like to know as well.

At work, however, I use root because sudo is disabled. Getting sudo to work in our environment would be an exercise in madness.

---

### Post by WBL on 2008-04-21
It seems that a root account is created anyways during installation.  Even with a fresh installation, I can go to System-->Administrion-->Users and Groups, and see that there is a user called "root".

-WBL

---

### Post by aysiu on 2008-04-21
> **WBL said:**
> It seems that a root account is created anyways during installation.  Even with a fresh installation, I can go to System-->Administrion-->Users and Groups, and see that there is a user called "root".

-WBL
The root account exists, but it isn't activated for login. See the /etc/shadow file for more details.

---

### Post by p_quarles on 2008-04-21
> **aysiu said:**
> The root account exists, but it isn't activated for login. See the /etc/shadow file for more details.
Right, the account exists and works, but cannot be accessed via any login dialogue. The password is hashed to match no possible value, making it effectively disabled. 

You can disable password authentication for any account in the same way:
```
sudo passwd -l *username*
```

---

### Post by aysiu on 2008-04-21
> **p_quarles said:**
> The password is hashed to match no possible value, making it effectively disabled. Actually, believe it or not, the root account has no password - it is disabled for login completely.

This is the line for the root account in the /etc/shadow file: ```
root:!:13976:0:99999:7:::
```

---

### Post by Griff on 2008-04-21
Sudo isn't just a workaround for total root access.  It's a way of delegating users/groups certain administrative privileges without giving them ALL of them.  Take a look at your own /etc/sudoers file.  It's probably very blank.  It's because ubuntu puts the first created user into an admin group and through the sudoers file allows all rootly powers to that group.  You can learn a lot by looking at your own files.  Look at:
```

cat /etc/passwd | grep username
cat /etc/group | grep username
cat /etc/shadow | grep username
cat /etc/sudoers

```
And why I don't use a root account:
```
su
```
sucks because it doesn't record the commands executed as root, only who logged in as su and when.  Bad bad bad.  Harder to fix errors when there's no log of past history.  Is typing sudo really that inconvenient?

A root account is also completely unnecessary (or at least has been for me) since there's already another active account with full privs.  It just seems like a security vulnerability.

---

### Post by p_quarles on 2008-04-21
> **aysiu said:**
> Actually, believe it or not, the root account has no password - it is disabled for login completely.

This is the line for the root account in the /etc/shadow file: ```
root:!:13976:0:99999:7:::
```
Well, yes, it's disabled, but the text you pasted is a hash, like all the passwords stored in /etc/shadow. The only difference between that hash and the one for your user is that the root password (along with any other "locked" passwords) don't match any value. In that particular instance, the "!" character doesn't work with the encryption method used by shadow, so won't match any password.

---

### Post by qazwsx on 2008-04-22
su for me.

I have disabled root ssh log in.  After that I feel it is more secure to have 2 strong passwords (+15 characters omg :lolflag:) than just one. 

But there are some advantages in sudo method as well.

---

### Post by elamericano on 2008-04-22
I enter a root password only to use it as my sudo password. I firmly believe that sudoers should have a different password for their administrative access than for an ordinary login. Otherwise every login is another chance to expose a root password for your computer.

Looks like nobody agrees with me, or this would be supported better.

---

### Post by saulgoode on 2008-04-22
> **elamericano said:**
> Looks like nobody agrees with me, or this would be supported better.

Actually, every other Linux distro out there agrees with you.

---

### Post by billgoldberg on 2008-04-22
> **WBL said:**
> One of the first things I do after an Ubuntu install is enable the root account.  However, I've noticed that a lot of people around here use "sudo" instead.  Why is that?  :confused:

-WBL

Take a security 101 class.

---

### Post by Rinzwind on 2008-04-22
> **p_quarles said:**
> Having a root account is not an added security risk, and neither is not having one. I have frankly never figured out where people get the idea that there is any kind of significant difference in terms of security.

A secure Ubuntu setup -- with the root password disabled -- is far more secure than a RHEL box with a bad root password. The inverse is also true. 

<..>

I can think of 1 thing...
If root is enabled and someone gets to your login remotely they know they need to get your root password ('root' + unknown password). With no root enabled they also need to get your sudo account name (unknown account + unknown password). I think the last one makes an OS more secure. 

But this is getting near borderline paranoia :lolflag:

Both the 'root' and 'sudo' way are secure. Periode.
It is the password that is most important. Use an 'a' as password ... or use a 'srgh2$wlf@#" as password ... makes a difference.

---

### Post by LinuxRocks713 on 2008-04-22
Mainly because it is unsafe (don't follow Windows XP's example) and if you accidently execute a wrong command in root... be prepared to fix up the mess.

---

### Post by p_quarles on 2008-04-22
> **LinuxRocks713 said:**
> Mainly because it is unsafe (don't follow Windows XP's example) and if you accidently execute a wrong command in root... be prepared to fix up the mess.
The "Windows example" is running as root all the time. That is not the same as having the root account available. Furthermore, you can do anything with sudo that you can with a root account, including executing a wrong command that leaves you with a huge mess.

Again: there is no substantiated difference between sudo and root in terms of real security. They are simply different models, each with their own convneniences. Some will argue that the unknown username on a sudo account makes that account more secure against remote intruders, but in reality, a good password is far more effective. After all, an intruder that gained limited shell access would be able to easily discover user names, but would have a much more difficult time deciphering their hashed passwords. That's why everyone says that a good password is the foundation of good security.

---

### Post by phrostbyte on 2008-04-22
Enabling root is probably a good idea on an Ubuntu box if you use LDAP authentication. Since if the Internet goes down and your set up for LDAP, if you don't have a root account you can be pretty much locked out of your computer. But that's the only reason I can think of.

---

### Post by phrostbyte on 2008-04-22
> **p_quarles said:**
> Right, the account exists and works, but cannot be accessed via any login dialogue. The password is hashed to match no possible value, making it effectively disabled. 

You can disable password authentication for any account in the same way:
```
sudo passwd -l *username*
```

There are certain huge advantages to sudo versus standard root.

1) Audited. Even sudo -i. So anything you do as sudo is logged. This is useful if multiple people have sudo since it promotes accountability.
2) Easy to add and remove sudo access from people. Nuff said.
3) Fine grained controls. For instance you can give someone access to apt-get but not to anything else.

All these promote better security. But it makes little difference on a personal computer or single user laptop or something, but Ubuntu is also being used in big organizations and the sudo really helps. 

PolicyKit (and Linux ACLs, and SELinux and AppArmor) will take this a step further :)  All these tools including sudo are part of an toolset to make managing the security and global policy of many deployed Ubuntu desktops much easier. Right now quite frankly Windows does it better though. But we are moving in the right direction.

---

### Post by aysiu on 2008-04-22
I agree with phrostbyte on this one. The two security models seem interchangeable to a lot of users here, because we are home users who may be the only users on our respective computers, but if you have several people sharing the same computer or network, *sudo* is a much better security model in terms of the control and auditing it gives you.

---

### Post by munkyeetr on 2008-04-22
I always change the root account password to something I know (a very secure one mind you - 12+ mixed characters). As the administrator of my system I want to know the root password, I don't want it to be some jumble of unknown characters. For me it's about having control of my system.

And I have come across a time or two when I *needed* to use it, where for whatever reason using **sudo** did not work, but su*ing* into **root**, then running the command did. 99% of the time I use sudo. I also make it so that sudo requires a password everytime I use by disabling the grace period.

---

### Post by aysiu on 2008-04-22
It's not a jumble of unknown characters. It doesn't exist.

The exclamation point doesn't match any encryption method's output, so it basically doesn't exist. You could guess jumbles of unknown characters to your heart's content and never be able to log into the root account on a default Ubuntu installation.

---

### Post by munkyeetr on 2008-04-22
> **aysiu said:**
> It's not a jumble of unknown characters. It doesn't exist.

The exclamation point doesn't match any encryption method's output, so it basically doesn't exist. You could guess jumbles of unknown characters to your heart's content and never be able to log into the root account on a default Ubuntu installation.

Corrected and noted.

---

### Post by saulgoode on 2008-04-22
> **aysiu said:**
> I agree with phrostbyte on this one. The two security models seem interchangeable to a lot of users here, because we are home users who may be the only users on our respective computers, but if you have several people sharing the same computer or network, *sudo* is a much better security model in terms of the control and auditing it gives you.

If you have several people sharing your computers, you still want one or two to have complete control. The SUDO package can still be used on a system which has root's password enabled -- in fact, that is why SUDO was created twenty years before Ubuntu existed (and a decade before Linux). There is no extra control available in a SUDO-only system and logging can  still be available, if desired, with a root-based system. Also, in a SUDO-only system an audit trail can be avoided, if desired, unless the logs are being appended to a write-only store. 

As has been pointed out, Ubuntu does not disable the root account, it merely prevents password-based logins. Other authentication methods can be used besides passwords and any administrator of a SUDO-only system (in a secure environment) better be aware of how that is accomplished and check regularly that his system has not been compromised and a passwordless root login enabled. An intruder who has attained access to root could in theory be able to prevent a mere SUDO-authorized administrator from discovering the compromise. By never logging into a root account, the task of a root exploit hiding from the SUDO administrators is made that much simpler. 

While using SUDO in addition to a root account can be quite useful in maintaining control of a system, I disagree that Ubuntu's SUDO-only approach is more secure. Far from it, it makes the task of insuring the integrity of a system more difficult.

---

### Post by ntowakbh on 2008-04-22
I use root sometimes.  It kind of depends.  

If I have several commands in a row I need to run as root, I use su to become root for a little while, as it saves me repeatedly typing sudo.  However, I use sudo when I have just one or two commands to run as root in a row.

---

### Post by cardinals_fan on 2008-04-22
> **Griff said:**
> 
And why I don't use a root account:
```
su
```
sucks because it doesn't record the commands executed as root, only who logged in as su and when.  Bad bad bad.  Harder to fix errors when there's no log of past history.  Is typing sudo really that inconvenient?

Sorry, but this is totally incorrect.  Root has a bash history too...

---

### Post by vexorian on 2008-04-23
Because, I don't have to.

sudo would also allow me to give and drop root rights from people, instead of me having to give root's password to everyone.

Besides, if I wanted to I would just do a sudo -i in the terminal and voila! "root account"

---

### Post by jken146 on 2008-04-23
I use sudo for the insults.

---

### Post by Trail on 2008-04-23
> **pjkoczan said:**
> As for me, I use sudo at home, as I find it works for 99.95% of my administrative tasks. The only time I've found root to be truly *necessary* is when there are filesystem errors at boot time, the kind where it says "Enter root password for maintenance." If anyone knows a way around this, I'd like to know as well.

I'd like to know that as well...

---

