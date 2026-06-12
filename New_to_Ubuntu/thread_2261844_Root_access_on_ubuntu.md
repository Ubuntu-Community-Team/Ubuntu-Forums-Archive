---
title: "Root access on ubuntu"
date: 2015-01-21
forum: New to Ubuntu
---

### Post by Bryant_Cox on 2015-01-21
I recently just downloaded Ubuntu 14.04 on VMware workstation for class to get my degree in Computer Forensics.  We are learning about the Linux operating system and we chose to use Ubuntu.  So far I can say that I am impressed with the design and ease of use of Ubuntu 14.04.   The only issue I am haveing is giving myself root access, I have been searching online to do this and have found some options but haven't been successful.  Other than that I have enjoyed my initial use and look forward to learning more about Ubuntu.

---

### Post by slickymaster on 2015-01-21
Please have a thorough read at this: [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=1486138") and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by HermanAB on 2015-01-21
You can install Autokey and put your frequently typed phrases on two or three function keys, or you can just get used to typing sudo and the password manually the same as everyone else...

---

### Post by kerry_s on 2015-01-22
> **Bryant_Cox said:**
> I recently just downloaded Ubuntu 14.04 on VMware workstation for class to get my degree in Computer Forensics.  We are learning about the Linux operating system and we chose to use Ubuntu.  So far I can say that I am impressed with the design and ease of use of Ubuntu 14.04.   The only issue I am haveing is giving myself root access, I have been searching online to do this and have found some options but haven't been successful.  Other than that I have enjoyed my initial use and look forward to learning more about Ubuntu.

in terminal if want to become root:
sudo su

then you can run all the root commands you want or launch apps using: gksudo app-name

---

### Post by mastablasta on 2015-01-22
debian has root enabled by default. I installed sudo and made it look like ubuntu (using sudo to do all the admin work) :)

---

### Post by coldraven on 2015-01-22
Maybe gksu is what you want. It's very handy if you want to use Synaptic  to install programs instead of using the Software Centre
```
sudo apt-get install synaptic gksu
```

Then you can run it by using
```
gksu synaptic
```
The "Run" window Alt+F2 will remember this for you. It does for me but I cannot remember quite how I did it :)
OK I remember now! After Alt+F2 just start typing G K etc and it should appear

Or for a GUI method look at this
[http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-add-open-as-rootadministrator-to-context-menu/](http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-add-open-as-rootadministrator-to-context-menu/)

There may well be other solutions.


Edit: If you plan to be using the command line a lot, this is the best tip and one that I use all the time.
[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

---

### Post by Jonathan Precise on 2015-01-22
Yes, gksu can come handy. +1 to coldraven.

However, I'm in UbuntuGNOME right now, and the pkexec UI integration is better than gksu's here. As for synaptic, Ubuntu provides a neat wrapper script for running synaptic as root. Just run:

```
synaptic-pkexec
```

and synaptic opens, but with pkexec UI, no gksu UI.

---

### Post by greg69 on 2015-01-25
You can go into a terminal and type 'su'. However this isn't really recommended as it allows anything on that terminal to do what it likes so long as the terminal remains open.
'sudo' is a better option. Literally, su, do. It does something as a super user and then stops. However it does allow for a small amount of time to enter another sudo and it won't ask for the password.
sudo passwd is used if it asks for a root password and you only have a User password. I'm not sure if this works on a multi user system.

---

### Post by deadflowr on 2015-01-25
> **greg69 said:**
> You can go into a terminal and type 'su'. However this isn't really recommended as it allows anything on that terminal to do what it likes so long as the terminal remains open.
'sudo' is a better option. Literally, su, do. It does something as a super user and then stops. However it does allow for a small amount of time to enter another sudo and it won't ask for the password.
sudo passwd is used if it asks for a root password and you only have a User password. I'm not sure if this works on a multi user system.
 su alone won't work on Ubuntu, as you'd need the root password.
If you run su, it won't run sudo passwd, that command is what you would run to change the root password.
(The default is for root's password, if you add a user name then it'll want to change that user's password; ie sudo passwd bob will enable changing bob's password)
Instead it'll ask for a password, which is disabled on ubuntu, unless you set one...
I find the easiest way is to run root
```
sudo -i
```
which'll run root interactively, meaning you'll be running as root until you exit; hint type exit to exit.

But for the most part, unless you're going to be doing a lot of system tweaking; which i would assume you know what you 're doing, I would simply use sudo some-command, like normal.
And quite frankly, I find if I'm going to be doing any extraneous work on a system file, I'll simply copy that file into my user's home folder and work on it there, then sudo cp it back into the system folder, from whence it came. Keeping my root-enabled usage to a minimum. I tend to also make a quick backup copy of said file(s), for prosperity. 

Then again, I'm a Desktop user. My needs to run as root are not the same as someone running a Server might be.
Nor are my needs the same as someone running a development environment.
And I would assume someone running under either of those instances would have an advanced understanding of what they are doing.

---

