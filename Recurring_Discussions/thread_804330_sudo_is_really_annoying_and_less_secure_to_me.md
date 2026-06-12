---
title: "sudo is really annoying and less secure to me"
date: 2008-05-23
forum: Recurring Discussions
---

### Post by rabbitnightmare on 2008-05-23
I was simply trying to set it up so I didn't have to type in the damn password everytime I wanted to sudo something and I hosed my config as [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) doesn't give clear instructions on how to sudo visudo and expects you to know what you are doing. I broke sudo and now have no friggen clue how to get it back! Why can't Ubuntu follow a simple guideline and allow root accounts.
I am logged into the sudoer account why do I need to type the password in when I am logged in chances are the one logged in knows the password. I am peeved to say the least and have a simple solution to a complex problem. Allow the root account. Why is this such an issue? I hate sudo and am about to switch distros as soon as I find the one I like simply because of my sheer hatred of sudo. This user unfriendly extra step is more annoying, imho, than the UAC. True it may not be so in your face but it is just as insulting and after a while it drives you to not want to use it anymore. Make it so it autologgs root off after 5 minutes of inactivity. Sudo has got to go! Reason I hate Macs!
UPDATE: I found instructions on how to fix it but this is really a deal killer for me. I am switching as soon as I find something better.

---

### Post by NightwishFan on 2008-05-23
Sudo is alright. I find that it makes some tasks real simple. (I setup sudo on my debian system)

---

### Post by Bubba64 on 2008-05-23
> **rabbitnightmare said:**
> I was simply trying to set it up so I didn't have to type in the damn password everytime I wanted to sudo something and I hosed my config as [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) doesn't give clear instructions on how to sudo visudo and expects you to know what you are doing. I broke sudo and now have no friggen clue how to get it back! Why can't Ubuntu follow a simple guideline and allow root accounts.
I am logged into the sudoer account why do I need to type the password in when I am logged in chances are the one logged in knows the password. I am peeved to say the least and have a simple solution to a complex problem. Allow the root account. Why is this such an issue? I hate sudo and am about to switch distros as soon as I find the one I like simply because of my sheer hatred of sudo. This user unfriendly extra step is more annoying, imho, than the UAC. True it may not be so in your face but it is just as insulting and after a while it drives you to not want to use it anymore. Make it so it autologgs root off after 5 minutes of inactivity. Sudo has got to go! Reason I hate Macs!
UPDATE: I found instructions on how to fix it but this is really a deal killer for me. I am switching as soon as I find something better.

From what I understand which is very little root account access is what makes windows so vulnerable, besides being around90% of the worlds computers used.

---

### Post by hyper_ch on 2008-05-23
> **rabbitnightmare said:**
> Allow the root account. Why is this such an issue?
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

> **rabbitnightmare said:**
> I hate sudo and am about to switch distros as soon as I find the one I like simply because of my sheer hatred of sudo. This user unfriendly extra step is more annoying, imho, than the UAC.
If you think so...

> **rabbitnightmare said:**
> but it is just as insulting and after a while it drives you to not want to use it anymore.
Hasn't happened...

> **rabbitnightmare said:**
> I am switching as soon as I find something better.
That, of course, is up to you. Good luck on your new OS.

---

### Post by kerry_s on 2008-05-23
> **NightwishFan said:**
> Sudo is alright. I find that it makes some tasks real simple. (I setup sudo on my debian system)

i agree, i always use sudo on debian, on mine i removed the root password manually from shadow, then "sudo passwd -l root" to lock it up tight.
the concept is simple, with a root account they know your name they only have to crack the password, with sudo they must guess your name and then crack your password.

i also make my life easier with the nopasswd for certain programs.

---

### Post by fuzzyk.k on 2008-05-23
well i think it is less secure after you enter the password once you can run administrative tools without it, i would suggest for GUI ubuntu should develop something like the PClinuxOS icon. with it you can tell the computer to forget the authorization once you are finished

no offence ment

---

### Post by niteshifter on 2008-05-23
Hi,

Nice vent. So let me get this straight: You attempted to circumvent a protective measure, one designed to keep the system from getting whacked by people doing things at full privilege, when they shouldn't because they didn't think it through / didn't know all they thought they did / and now have a whacked system?

There's a clue there :rolleyes:

Fix it up, then use that handy Root Terminal. Or sudo su, or sudo -i. A bit of googling will disclose how to fully enable root user in Ubuntu.

---

### Post by ASULutzy on 2008-05-23
The idea that sudo is less secure is so flawed. The idea that somehow because your user password is the sudo password that the system is less secure is wrong.

Either way it comes down to choosing a strong password.

If you had a root account and had a weak root password it could be guessed.
If you have a normal user with sudo rights and it has a weak password it could be guessed.

Strong passwords are where it's at.

And if you really want to be "root" there's about 10 different commands you could type in that give you a root shell.

Go run linspire or something ;)

---

### Post by Dr Small on 2008-05-23
I even installed sudo on Arch, because I was annoyed at having to login as root everytime I wanted to execute a command by root.

---

### Post by Cap'n Skyler on 2008-05-23
cant the time allowed for the password to be valid be changed?up the availablilty of access.would that be of any help?:popcorn:

---

### Post by Steve413z on 2008-05-23
I agree that sometimes having to enter your password for sudo could be a security problem

for example... shoulder surfers

---

### Post by Steve413z on 2008-05-23
```
sudo visudo
```.

---

### Post by yaztromo on 2008-05-23
I have to agree with the OP, I don't feel about it so strongly. I certainly don't hate sudo, but it's the first thing I disable when I set up SSH access to my box. It's far more secure to disallow root logins on the sshd.conf and disable sudo for your user name. So if somebody breaches your own account, they at least can't sudo.

For normal desktop use sudo is alright, but for servers with remote admin SSH it's dangerous.

---

### Post by kerry_s on 2008-05-23
> **Steve413z said:**
> Play with these settings: (make sure to backup the file first) not sure exactly what you are trying to do
```
sudo nano /etc/sudoers
``````
gksu gedit /etc/sudoers
```

that will break things real fast, they'll find it's read only than want to change it, next thing you know no more sudo. sudoers should always be edited with sudo visudo.

---

### Post by ASULutzy on 2008-05-23
> **yaztromo said:**
> I have to agree with the OP, I don't feel about it so strongly. I certainly don't hate sudo, but it's the first thing I disable when I set up SSH access to my box. It's far more secure to disallow root logins on the sshd.conf and disable sudo for your user name. So if somebody breaches your own account, they at least can't sudo.

For normal desktop use sudo is alright, but for servers with remote admin SSH it's dangerous.

huh? If you don't allow root logins in sshd.conf, and you disable sudo for your user name... then how are you supposed to actually use SSH to do anything useful other than browse your home folder?

A much better solution would be to use a public/private key pair to secure your ssh. And if you did it that way you'd still be able to do useful things remotely, like install new applications.

---

### Post by ASULutzy on 2008-05-23
> **kerry_s said:**
> that will break things real fast, they'll find it's read only than want to change it, next thing you know no more sudo. sudoers should always be edited with sudo visudo.

Yea, he's 100% right. Never edit that file in any way other than through sudo visudo.

If you use gedit or nano and hose it, you'll lock yourself out of your own system.

---

### Post by yaztromo on 2008-05-23
> **ASULutzy said:**
> huh? If you don't allow root logins in sshd.conf, and you disable sudo for your user name... then how are you supposed to actually use SSH to do anything useful other than browse your home folder?

Use su. This way to SSH root admin a server you have to know both your own password and then the root password when you su. With sudo all you have to know is one password.

---

### Post by Steve413z on 2008-05-23
> **kerry_s said:**
> that will break things real fast, they'll find it's read only than want to change it, next thing you know no more sudo. sudoers should always be edited with sudo visudo.

i never had a problem using nano
the only difforence is visudo does some error checking before it makes the changes, but if you don't know vi, it's nearly impossible to use

---

### Post by Dr Small on 2008-05-23
> **Steve413z said:**
> i never had a problem using nano
the only difforence is visudo does some error checking before it makes the changes, but if you don't know vi, it's nearly impossible to use
You could simply use:
```
export EDITOR="nano"; sudo visudo
```

---

### Post by jrusso2 on 2008-05-23
> **ASULutzy said:**
> The idea that sudo is less secure is so flawed. The idea that somehow because your user password is the sudo password that the system is less secure is wrong.

Either way it comes down to choosing a strong password.

If you had a root account and had a weak root password it could be guessed.
If you have a normal user with sudo rights and it has a weak password it could be guessed.

Strong passwords are where it's at.

And if you really want to be "root" there's about 10 different commands you could type in that give you a root shell.

Go run linspire or something ;)

Linspire is based on Ubuntu and uses Sudo the same way Ubuntu does

---

### Post by stream303 on 2008-05-24
For historical reasons, remember that this sudo vs non-sudo issue has been with us since about 4.1BSD in 1980 afaik....

---

### Post by Eman1955 on 2008-05-24
I agree with you to an extent.  I used Xandros for a while and wow, what an easy way to use root - sign in as root!

I'm trying to edit a root file and it won't let me save the changes even when I'm logged in as the root user.  What the *^%^(#@

At least I think I'm logged in as root:  Terminal shows root@bob-laptop:~#

Please help or let me die on the vine!

E

---

### Post by cmay on 2008-05-25
if you like ubuntu but want the root account like default debian then use the alternate install cd.
i did that the first time i installed ubuntu.
how ever in time i have come to like sudo pretty much
so i use visudo on all distros i try that has  
debians default set up scheme.

---

### Post by p_quarles on 2008-05-25
Moved to Recurring Discussions.

This is really a dead topic. Anyone who has an opinion either way should know already how to change the settings to their liking. That said, Ubuntu's model for root access is to use the sudo application, and other configurations are not supported on this forum. See [here](http://ubuntuforums.org/showthread.php?t=765414) for further details.

---

### Post by Raccoon1400 on 2008-05-25
I prefer su

---

### Post by zetetic on 2008-05-25
> **rabbitnightmare said:**
> I was simply trying to set it up so I didn't have to type in the damn password everytime I wanted to sudo something and I hosed my config as [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) doesn't give clear instructions on how to sudo visudo and expects you to know what you are doing. I broke sudo and now have no friggen clue how to get it back! Why can't Ubuntu follow a simple guideline and allow root accounts.
I am logged into the sudoer account why do I need to type the password in when I am logged in chances are the one logged in knows the password. I am peeved to say the least and have a simple solution to a complex problem. Allow the root account. Why is this such an issue? I hate sudo and am about to switch distros as soon as I find the one I like simply because of my sheer hatred of sudo. This user unfriendly extra step is more annoying, imho, than the UAC. True it may not be so in your face but it is just as insulting and after a while it drives you to not want to use it anymore. Make it so it autologgs root off after 5 minutes of inactivity. Sudo has got to go! Reason I hate Macs!
UPDATE: I found instructions on how to fix it but this is really a deal killer for me. I am switching as soon as I find something better.

The problem is you, not Ubuntu. It easy very easy to disable sudo, configure sudo the way you would like it to work, activate the root account, etc.

Only problem here is at your side... You can't understand what you read.

---

### Post by cardinals_fan on 2008-05-25
> **Raccoon1400 said:**
> I prefer su
+1

---

### Post by smartboyathome on 2008-05-25
I enabled sudo on arch as well. I don't like having to login as root either just to run a command, and it is more "automatic" for me than using su -c for everything. I keep it enabled though, in case I need to resque my system and my user account isn't working. It is a bad idea to log in as root, as a script can be run from the internet on your computer, but not with sudo/su.

---

