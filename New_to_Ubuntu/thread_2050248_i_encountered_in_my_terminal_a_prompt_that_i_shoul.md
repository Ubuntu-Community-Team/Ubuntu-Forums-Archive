---
title: "i encountered in my terminal a prompt that i should install a SHOW"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by tosdek on 2012-08-30
while working on my terminal this afternoon, i typed a SHOW ROOT command and i got in response


root@ubuntu:/root# show root
The program 'show' is currently not installed.  You can install it by typing:
apt-get install nmh
root@ubuntu:/root# apt-get install nmh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  daemontools fastforward fgetty procmail qmail qmail-run qmail-uids-gids
  runit ucspi-tcp
Suggested packages:
  exmh mh-e mh-book dot-forward qmail-tools socklog-run
Recommended packages:
  mail-transport-agent metamail
The following NEW packages will be installed:
  daemontools fastforward fgetty nmh procmail qmail qmail-run qmail-uids-gids
  runit ucspi-tcp
0 upgraded, 10 newly installed, 0 to remove and 388 not upgraded.
Need to get 3,193 kB of archives.
After this operation, 8,938 kB of additional disk space will be used.
Do you want to continue [Y/n]? 



i really dont understand this so i paused to come ask about this in the forum before taking any action. i need an assistance on this

---

### Post by MG&amp;TL on 2012-08-30
What exactly is it you're trying to do?

The nmh package is a collection of mail utilities....

---

### Post by oldos2er on 2012-08-30
What exactly did you expect **show root** to do? 

Here is a description of the package nmh:

 A set of electronic mail handling programs
 This is the nmh mail user agent (reader/sender), a command-line based mail
 reader that is powerful and extensible.  nmh is an excellent choice for                       
 people who receive and process a lot of mail.
 .
 Unlike most mail user agents, nmh is not a single program, rather it is a
 set of programs that are run from the shell.  This allows the user to
 utilize the full power of the Unix shell in coordination with nmh.  Various
 front-ends are available, such as mh-e (an emacs mode), xmh, and exmh (X11
 clients).
 .
 nmh was originally based on MH version 6.8.3, and is intended to be a
 (mostly) compatible drop-in replacement for MH.

---

### Post by jerome1232 on 2012-08-30
> **tosdek said:**
> while working on my terminal this afternoon, i typed a SHOW ROOT command and i got in response


root@ubuntu:/root# show root
The program 'show' is currently not installed.  You can install it by typing:
apt-get install nmh
root@ubuntu:/root# apt-get install nmh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  daemontools fastforward fgetty procmail qmail qmail-run qmail-uids-gids
  runit ucspi-tcp
Suggested packages:
  exmh mh-e mh-book dot-forward qmail-tools socklog-run
Recommended packages:
  mail-transport-agent metamail
The following NEW packages will be installed:
  daemontools fastforward fgetty nmh procmail qmail qmail-run qmail-uids-gids
  runit ucspi-tcp
0 upgraded, 10 newly installed, 0 to remove and 388 not upgraded.
Need to get 3,193 kB of archives.
After this operation, 8,938 kB of additional disk space will be used.
Do you want to continue [Y/n]? 



i really dont understand this so i paused to come ask about this in the forum before taking any action. i need an assistance on this

Ok, so if you type a command, and a program that uses that command exists in the repository but the program is not installed you will get that message saying essentially "Hey, that program isn't installed, this is the package name if you want to install it!"

In this case the command "show" applies to this mail utility you were prompted to install.

---

### Post by tosdek on 2012-08-30
Now I get that, I actually wanted to get check the root details, so I tot the command 4:+1 3++( would give me the details I wanted. Fanks for the responses. Am learning every minutes. Thanks

---

