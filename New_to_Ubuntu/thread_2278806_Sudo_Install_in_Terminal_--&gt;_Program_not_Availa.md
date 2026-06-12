---
title: "Sudo Install in Terminal --&gt; Program not Available?"
date: 2015-05-19
forum: New to Ubuntu
---

### Post by anotherman2 on 2015-05-19
I installed Transmageddon following the instructions found here ([link]("http://www.tuxarena.com/2014/07/transmageddon-1-3-video-encoder-released-ubuntu-installation/")).  I did this while being present in my regular every day user account with limited rights.  In order to be able to use "sudo", I used "su" in the terminal to change into my administrator account within that terminal.  

The installation seems to have gone fine (can post terminal output if needed), but there seems to be no trace of the program in my regular every day user account.  

Could it be that I unwittingly installed Transmageddon only in my administrator account?  And if so, how would I go about making it available for all users?

I tried finding out on my own through Google and forums, but coming from Windows I seem to know way too little about how Linux/Ubuntu organizes executable installs and files to even know what to be looking for.

Any help would be greatly appreciated!

EDIT #1: I have stumbled upon this now:
> In most cases if you're building from source, the results are stored in  the /usr/local branch with binaries in /usr/local/bin, libraries in the  /usr/local/lib, and configuration file in /usr/local/etc.
Assuming that is correct - can I simply copy the relevant content (relating to my program) of these folders into the same folder of the desired user account?  Will I then be able to run my program?

EDIT #2: Back to square one.
> /bin and /usr/bin is where the scripts are that start the programs.  The direct equivalent of "Program Files" though is probably /usr/share.  That directory contains the various support files for most programs.
  

  There probably isn't a direct equivalent however, since, for example, library files are shared across the system (in /lib) and options are either user specified (in the user's home directory) or universally located in /etc.
  So installing a program via a deb file, repository or build will likely place files in all of these locations.
  [EDIT] And as others note, there is also /sbin and /usr/sbin.  Plus /usr/local/bin, /opt/bin and even /usr/games/.  So definitely not a direct comparison to c:\program files

---

### Post by mastablasta on 2015-05-19
> **anotherman2 said:**
> 
In order to be able to use "sudo", I used "su" in the terminal to change into my administrator account within that terminal


Could it be that I unwittingly installed Transmageddon only in my administrator account? 
nothing unwitting about it. you wrote it yourself. you changed to admin user (possibly even root user) and installed to his account.

> 
 And if so, how would I go about making it available for all users?


I would say uninstall it first, especially if you installed it as root. then login as admin user and install there. it should then be available to all users.

option 2 is to add the regular user to the group that is allowed to use the program. :[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I think there is an app for that in Ubuntu. somewhere in administration.at least Kubuntu has something like that.

---

### Post by anotherman2 on 2015-05-19
Thank you, mastablasta, your reply helps a great deal!

This is the way I will go then:

> I would say uninstall it first, especially if you installed it as root.  then login as admin user and install there. it should then be available  to all users.

I have just used: ```
sudo apt-get --purge remove transmageddon
``` 

Now I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'transmageddon' is not installed, so not removed

```

Now I am even more confused.  I know there is a transmageddon.desktop linking to an executable transmageddon file, and so forth - how comes I am told it is not installed?

> nothing unwitting about it.
Unfortunately, it was very much so for me.  Coming from Windows and having installed several programs using Ubuntu's Software Center, I am used to using admin credentials to install software into the account I am currently using.
I can see now how it happened that I installed Transmageddon into my admin account, but I neither had any intention of doing so, nor was I aware of doing so.

Am I right to assume that there is no way of installing software w/o changing into the admin account unless it is found in Ubuntu's Software Center or pre-packaged for Ubuntu?

---

### Post by The Cog on 2015-05-19
Firstly, in Ubuntu you can't use su to change to root because root's password is disabled (by default). So either someone has already been tinkering with the root password it or it's not Ubuntu you're installing on. You don't need to use su to be able to use sudo - you just use sudo when you want root priviledges:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Secondly, depending on what arguments you gave su and sudo, you might have been in your own home directory or in that of root. Either way, the **make install** will probably have installed the application somewhere that is available to all users (needing extra rights to be able to write outside of your home directory hence sudo):
> In most cases if you're building from source, the results are stored in the /usr/local branch with binaries in /usr/local/bin, libraries in the /usr/local/lib, and configuration file in /usr/local/etc.  So just launch the program wherever it is installed. There is no need make another copy in your home folder. Have you looked in /usr/local/bin to see if the installer put it there?

Assuming the program executable name is transmageddon, this should find it:
```
sudo updatedb
locate transmageddon
```
then launch it with a command like /usr/local/transmageddon/transmageddon

---

### Post by anotherman2 on 2015-05-19
> **The Cog said:**
> Firstly, in Ubuntu you can't use su to change to root because root's password is disabled (by default). So either someone has already been tinkering with the root password it or it's not Ubuntu you're installing on. You don't need to use su to be able to use sudo - you just use sudo when you want root priviledges:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I must say you saying this scares me a bit.  I am using Ubuntu 14.04, and I have not been able to use sudo unless logged in to my admin account. I keep getting an error telling me that my user is not in the sudoers file. ([EDIT] Is this probably b/c I use a regular user account and not an admin account?)

Since I did not want to have to go switch to my admin account simply to install Transmageddon, I had to find a way to do so in the terminal.  I am pretty sure I used "su" to change into my admin account, though I cannot tell you exactly what that command was.  (I cannot find the source for the command, and I can also not see it anymore in my terminal window. It is also not part of the terminal's history.)

So are you telling me I should be worried about my install, since I could do what I did?

[EDIT] I figured out what I did.  I used "su <admin account  name>" to change into my admin account.  Would you still consider this problematic?

> **The Cog said:**
> Secondly, depending on what arguments you gave su and sudo, you might have been in your own home directory or in that of root. Either way, the **make install** will probably have installed the application somewhere that is available to all users (needing extra rights to be able to write outside of your home directory hence sudo):

I did this:

```
sudo apt-get build-dep transmageddon
```

Changed into the folder where I had unpacked the transmageddon files after download, then did this:

```
 sudo make install
```


 > **The Cog said:**
> So just launch the program wherever it is installed. There is no need make another copy in your home folder. Have you looked in /usr/local/bin to see if the installer put it there?

I have located several files that the installer put in several locations, but I was not able to run it within my regular user account.

> **The Cog said:**
> Assuming the program executable name is transmageddon, this should find it:
```
sudo updatedb
locate transmageddon
```
then launch it with a command like /usr/local/transmageddon/transmageddon

This gives me quite a long list of files.  I guess I located the executable "transmageddon" in /usr/local/bin/transmageddon.

I could run the file being in the terminal window as admin (transmageddon throws an error in the terminal, but that is a different problem).

If I would like to uninstall Transmageddon - since it all seems quite messed up -, how would I go about it? 

(And what could have gone wrong during install?  I am quite confused.)

BTW - thank you for helping me out!

---

### Post by grahammechanical on 2015-05-19
May I explain something for the sake of clarity and for all new users who are viewing this thread?

When we install Ubuntu we set a user name and password. That user becomes both a standard user and an administrator. When we load Ubuntu and log in we work as a standard user. When we try to do something that requires administrator authorisation we are asked to authenticate the action. We enter our password and for a few minutes as the task is running we are working as the administration. After a short time delay we cease working as an administrator. And so, the next time we are try to do something that only an administrator can do we need to authenticate again.

In Ubuntu we do not have what is called an "administrator account." That first user with his/hers password is the administrator. This means that I can leave my computer running and if someone should gain access they can do what a standard user can do but should they try something that only the administrator (that's me) can do they will be asked to authenticate and without my password they will be blocked.

When we work in a terminal if the command needs administrator authentication (privileges) we put "sudo" in front of the command  and we are asked to put in the password to run the command. Commands that need sudo will not run without the word sudo in front of the command. the immediate response it to be informed that we do are not root. In other words we are not the administrator. For example:

```
apt-get update
```

gives

> graham@sdb1-Uplus1:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

But this

```
sudo apt-get update
```

gives

> graham@sdb1-Uplus1:~$ sudo apt-get update
[sudo] password for graham:

This is how we work in Ubuntu

Regards.

---

### Post by anotherman2 on 2015-05-19
Thank you very much for clearing that up, grahammechanical!

So there is basically no need to create a separate "regular" user account right after install?  I was so used to doing this in Windows that I just did it in Ubuntu, too.

---

### Post by mastablasta on 2015-05-19
> **anotherman2 said:**
> 
So there is basically no need to create a separate "regular" user account right after install? 

Correct. default user is regular user. only he has the power to elevate himself to super user. or mayb ebetter to ask super user to do something for him. (sudo = _s_uper _u_ser _do_). root user (administrator) is disabled by default in Ubuntu. 

I thougth you are trying to lock yourself down more on purpose (e.g. some additional security concerns).

> 
 I was so used to doing this in Windows that I just did it in Ubuntu, too.

well say you install Debian netinstall or CenoOS. by default you will get root use there and that one would act as administrator does in windows. so you would need to switch to it in order to perform root tasks. but ther eis a good reason why root is disabled by default in Ubuntu. and I also disabled it in debian. PC security is made of various layers and this is one of many that helps protect the user (and computer from the user). if nothing else - if you need to type in sudo to do something then you are making certain and important change in OS that oculd impact other things. so one should be sure they really want that privilege.

on the more practical side - by default all ports to PC are closed, but say you want to open one to be bale to remotely connect to your PC form your phone or from work. it them means PC is listening on that port and there are people constantly scanning for such openings and when they detect it they see the OS and immediately try to login as root. if they get confirmation that root is available - all they need to do is guess the password. without additional protection in place such as fail2ban, proper firewall setup (say you opened SSH server, have it accessex by password and have user root enabled), and some dedication & descent hardware on hacker's end it should take them less than 10 minutes. anyway scary. so better have them guess the user name first. ha, ha....

anyway it's just one of many security layers.

---

### Post by The Cog on 2015-05-19
> I figured out what I did. I used "su <admin account name>" to change into my admin account. Would you still consider this problematic?
Ah now I understand. That's not really a problem. If you use **su** without the username you are changing to, it tries to change to user root (which is not allowed in ubuntu because the root password is disabled). I had assumed you were doing this. I assumed that you meant the root account when you said the admin account. As far as I know, the difference between your normal account and the "admin" account is that the admin account is allowed to use the sudo command. It's a bit convoluted but not a problem at all. 

Mastablasta kind of explains why the root password is disabled by default - an obvious target for password guessers.

Should you want to uninstall the program again, change to the admin account again (I guess that's where the build folder and files have been left) and **sudo make uninstall** should remove all the files that the installer placed. Then you can just delete the transmageddon folder that you unzipped earlier.

---

### Post by anotherman2 on 2015-05-19
Thank you, mastablasta and The Cog, for your replies.  Things make a lot more sense now!

> Should you want to uninstall the program again, change to the admin  account again (I guess that's where the build folder and files have been  left) and **sudo make uninstall** should remove all the files that  the installer placed. Then you can just delete the transmageddon folder  that you unzipped earlier.

I tried doing that - changed to admin and went into the unzipped folder -, but all I got was this:

> make: *** No rule to make target `uninstall'.  Stop.

How would I proceed now if I wanted to uninstall this program?

---

### Post by The Cog on 2015-05-19
> How would I proceed now if I wanted to uninstall this program? 
Ooh. I don't know. I could be wrong about "uninstall" - I've never actually used that. 
Google found this: [http://stackoverflow.com/questions/1439950/whats-the-opposite-of-make-install-ie-how-do-you-uninstall-a-library-in-lin](http://stackoverflow.com/questions/1439950/whats-the-opposite-of-make-install-ie-how-do-you-uninstall-a-library-in-lin)
So you may have to track down and remove the files by hand.

---

### Post by anotherman2 on 2015-07-22
A belated thank you @TheCog!

---

