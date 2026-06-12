---
title: "Password problems"
date: 2019-07-16
forum: New to Ubuntu
---

### Post by hk42 on 2019-07-16
Hi
First many thanks to the community for this nice release 19.04 that worked first time dual boot on my Beelink BT3pro.
I used my usual password ,common with all my windows machines.
I was told when installing that it was too weak.
By chance I didn't change it as later it was asked lots of times.
I also created another account 
My idea was to give it a strong password and then to remove admin rights
to my usual account.
But ,for a start, I gave it an even weaker password.
Being French I thought it a good idea to choose french for this account.
This is bad as many graphical error messages are truncated and/or hard to understand.
To make a long story short it seems that in the accounts parameters windows
when admin is selected it is grayed so it is easy to end with no admin at all.
The problem I am left with is that when connecting to a samba share I am always asked 
for name and password in spite of the fact that "remember for ever is selected".
It seems related to the fact that each time I am also asked for a password for something called 
"trousseau de clé" that seems to mean key ring and none of the ones I ever used works.
All this is very time consuming and I hope there is a simple solution.

---

### Post by dino99 on 2019-07-16
Some readings for summer time  :p

[https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)
[https://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/](https://www.cyberciti.biz/faq/ubuntu-linux-root-password-default-password/)
[https://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](https://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

and a nice place too: [https://forum.ubuntu-fr.org/](https://forum.ubuntu-fr.org/) ):P

---

### Post by TheFu on 2019-07-16
I can only guess that different programs support of UTF8 characters can be different, based on configuration and programming.  I have no proof, it is just a theory.  I don't use the "key ring" that is built-into Ubuntu, so I'm completely unfamiliar with that aspect.

I would look for unicode/utf8 settings in every tool. For example, Samba has specific unicode and utf8 support options. 
[https://launchpad.net/ubuntu/disco/+source/samba](https://launchpad.net/ubuntu/disco/+source/samba) says that samba v4.10.x is used.  That means this [https://www.samba.org/samba/docs/4.10/man-html/smb.conf.5.html](https://www.samba.org/samba/docs/4.10/man-html/smb.conf.5.html) is the relevant documentation.
There is a setting for  **unicode** and  **unix charset**.

No idea if this will help with anything else.  I don't use the GUI much. Sorry.

Hopefully, someone with direct experience will post.

---

### Post by oldrocker99 on 2019-07-18
On my laptop, since I'm the only person who will ever use it, I use a 4-character password. Makes logging in and entering my password a lot faster. You'll be told that it's a "short password," but it'll accept it.

---

### Post by TheFu on 2019-07-19
> **oldrocker99 said:**
> On my laptop, since I'm the only person who will ever use it, I use a 4-character password. Makes logging in and entering my password a lot faster. You'll be told that it's a "short password," but it'll accept it.

If you have **any** remote connection protocol enabled, this is terrible advice.  Use samba?  ssh? sftp?  scp?  sshfs?  rsync?  Any network backup tool?  Terrible idea.  Of course, if you don't do anything off the system and don't have any remote connection methods allowed or enabled, then any password isn't important.

---

### Post by GhX6GZMB on 2019-07-19
This could be related to the keyboard layout. English is QWERTY, German is QWERTZ, French is AZERTY and so on.
This is well-known also on Win systems. The BIOS default keyboard layout is US, but when getting deeper into login, the layout changes to your local setting, so a complete disconnect between the passwords happens.

---

### Post by hk42 on 2019-07-27
Thanks for the replies.
Unfortunately none worked.The Key Ring is still a mystery for me.
The solution I found was to create a third user with admin rights.
His Key ring password seems OK as I am never asked for it  so I don't know what it is.
So I'm left with 3 users with admin rights and very weak passwords.
In the meantime the icon that allowed me to add or delete users has ceased to work .
To say the least I'm not impressed with the security aspect of Ubuntu.:(
On the other hand it is quite stable and recognized all my hardware.

---

### Post by TheFu on 2019-07-27
Well, Unix systems seldom use GUIs for user management. It is always handled from a shell with normal CLI tools.

The tools normally used are:```

useradd      userdel      usermod
groupadd  groupdel  groupmod
```

Or is it 
```
adduser addgroup deluser   delgroup
```
I always get those mixed up and have to check the manpages for which are low-level and which are more convenient.

To fix your passwords, use the **passwd** command.  20+ characters, random, if you use any network protocols.  Don't use the same passwords on different systems. Use keys for authentication whenever possible.  Passwords are so 1990s. Using passwords is a security failure without 2FA.

I good beginner book that has a chapter on this stuff is [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  I've used that chapter in my Linux classes.

---

### Post by oldrocker99 on 2019-07-30
> **TheFu said:**
> If you have **any** remote connection protocol enabled, this is terrible advice.  Use samba?  ssh? sftp?  scp?  sshfs?  rsync?  Any network backup tool?  Terrible idea.  Of course, if you don't do anything off the system and don't have any remote connection methods allowed or enabled, then any password isn't important.

 At 70, and living alone, I am 100% the only user at all, and I don't do any of those things. I do use grsync to do a local backup, of course.

---

### Post by cruzer001 on 2019-07-30
> **oldrocker99 said:**
> On my laptop, since I'm the only person who will ever use it, I use a 4-character password. Makes logging in and entering my password a lot faster. You'll be told that it's a "short password," but it'll accept it.
I run 10-character password on host system and 6 on the guest for ease of use, with vpn and so far sleep good at night :)

---

### Post by NM5TF on 2019-07-31
@HK42....

have you tried to reset your password yet ??? it's not really that hard to do so...
 1. Boot into RECOVERY MODE
 2. Drop into the ROOT shell
 3. Type mount -o rw, remount /
 4. Type [COLOR="#FF0000"]passwd and your username[/COLOR]
 5. Type your new password twice
 6. Type exit
 7. Reboot

tommy

---

### Post by haplorrhine on 2019-08-05
This will be outside-the-box and definitely incomplete.  The basic idea is a script that removes the user's admin privileges _*after*_ the user has accessed the samba share *et cetera.*
I always wondered how programs like Tripwire and AIDE can check the integrity of files against a hash file that is encrypted without explicitly decrypting the hash file.  Moreover, I do not think scripts are allowed to enter passwords for the user.  I was thinking the script would (1) be executed by the user, (2) receive inputs from the user or his system, (3) process those inputs into a password, (4) change the admin password to it, (5) use the admin password again to remove the user's admin privileges.

---

### Post by haplorrhine on 2019-08-06
Follow-up
Under this system, you could essentially have sub-passwords and a master password, but the master "password" would actually be an encrypted "master file" that translates certain inputs into sub-passwords that are combined to form a larger password, the larger password being the next password in the rotation.  The script might use something like the date, translating the date into the next password; or the script could ask for human input, trusting the human to know what the date is or whether he even wants to use the date again.

---

### Post by blumkram on 2019-08-09
[FONT=Verdana]I ran a 7-character password with numbers and special symbols, works for me. [/FONT]Even though [FONT=Verdana] when I ran out of imagination I just use some  [/FONT]Password Manager, for example, RoboForm [https://www.bestadvisor.com/password-managers](https://www.bestadvisor.com/password-managers) can be useful, if you dont have any thought about setting up a particular  password.

---

### Post by hk42 on 2019-08-10
Thanks again for all your contributions.
I think I found a solution to my keyring password problem:


In a text console using "Midnight Commander " as admin
sudo mc
I found a directory:
/home/problemuser/.local/share/keyrings
I renamed the 2 files in it as *BAD .(I think it would be better to move them in a new keyringsbad directory)
Then back in graphic mode I connected to a samba share selecting "remember connection password for ever".
This time (for the first time) I was asked to choose a password for my "Keyring".
It seems that those files are not updated when using "recovery" in text mode as I did.

---

### Post by TheFu on 2019-08-10
Be very careful using sudo for any GUI programs or for anything inside a users' HOME.
If you need to use it for something like MC, use **sudo -H mc** to prevent any config/status files from being written to the wrong HOME.

If sudo is needed to handle any files inside a user's HOME, that is a failure.  Someone used root or sudo incorrectly.

---

### Post by hk42 on 2019-08-11
Yes you are right.
In fact I just did the same thing on my other broken account and sudo isn't needed.
It is just useful to look into other home directories to see any difference.

---

### Post by hk42 on 2019-09-06
> **TheFu said:**
> Be very careful using sudo for any GUI programs or for anything inside a users' HOME.
If you need to use it for something like MC, use **sudo -H mc** to prevent any config/status files from being written to the wrong HOME.

If sudo is needed to handle any files inside a user's HOME, that is a failure.  Someone used root or sudo incorrectly.
With my  small ,but nice, experience of Ubuntu 19.04 I can only approve this.
If you want to try "sudo startx" don't do it from your usual optimized account.

---

