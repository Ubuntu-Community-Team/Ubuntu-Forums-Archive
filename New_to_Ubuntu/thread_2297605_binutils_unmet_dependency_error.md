---
title: "binutils unmet dependency error"
date: 2015-10-05
forum: New to Ubuntu
---

### Post by post3 on 2015-10-05
I'm completely new to Ubuntu and I am having problems installing new software. Each time I try to install something new I get the same unmet dependency error for binutils.

e.g.
jasont@devjasont:~/git$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 gcc-4.4 : Depends: binutils (>= 2.20.1-15~) but 2.15.92.0.2-11 is to be installed
 gcc-4.6 : Depends: binutils (>= 2.21.1) but 2.15.92.0.2-11 is to be installed
 libc6-dev : Breaks: binutils (< 2.20.1-1) but 2.15.92.0.2-11 is to be installed
 vim : Depends: vim-runtime (= 2:7.3.429-2ubuntu2.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jasont@devjasont:~/git$


To resolve the problem I've tried:

sudo apt-get clean
sudo apt-get -f install
sudo dpkg --configure -a

As I am a complete noob, I don't understand what is going on and despite following several guides haven't been able to resolve the problem. Can anyone help?  I don't want to reinstall ubuntu as I have some software already installed (if possible).

Thanks,
Jason

---

### Post by ian-weisser on 2015-10-05
The short answer is that you seem to have introduced a *version conflict*.
This generally happens when you install non-Ubuntu versions of software. 

Software in the Debian/Ubuntu ecosystem is not usually self-contained - each package *depends* on functions and services provided by other packages. If two packages depend upon different versions of the same dependency, that's a *version conflict*. Software in the Ubuntu repositories is built from a common set of dependencies specifically to prevent those kinds of problems.


Here. Take a look at the version of binutils you want to install.

> **post3 said:**
> gcc-4.4 : Depends: binutils (>= 2.20.1-15~) but** 2.15.92.0.2-11** is to be installed
 gcc-4.6 : Depends: binutils (>= 2.21.1) but** 2.15.92.0.2-11** is to be installed
 libc6-dev : Breaks: binutils (< 2.20.1-1) but** 2.15.92.0.2-11** is to be installed

gcc-4.4 requires a much newer version of binutils.
gcc-4.6 requires a much newer version of binutils.
libc6-dev **breaks** binutils, but you want it installed anyway.

FYI - the versions of binutils in the Ubuntu repositories range from 2.22 (in Ubuntu 12.04) to 2.25 (in Ubuntu 15.04), any of which would solve those three problems. Binutils 2.15 really is ancient by comparison.

So, why are you trying to install an ancient (and unsupported) version of binutils?
Are you following some instructions from the internet? If so, a link to them would be helpful.

---

### Post by mc4man on 2015-10-05
run
apt-cache policy binutils
or
apt-cache madison binutils

Though the version you have is likely from 2004 & should have been updated no matter what version of Ubuntu you have going back to at least 8.04 (Hardy

Edit: note that many or even most times "is to be installed" actually means is already installed

---

### Post by post3 on 2015-10-06
thanks for the responses. I managed to resolve the problem using "sudo aptitude reinstall libc6" and now everything is working ok.

---

