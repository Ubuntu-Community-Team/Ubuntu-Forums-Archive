---
title: "Bash commands: what do you use when you don't have apt-get installed?"
date: 2013-06-27
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-27
I'm working toward a dual partition for Ubuntu and OS 10.6, but my bash doesn't include "apt-get." 

What command would you use to GET apt-get (and install it)? 

Is there a command that updates all of bash, zsh ... and other shells?

---

### Post by steeldriver on 2013-06-27
The apt-get command isn't part of the shell - it's a separate executable (usually /usr/bin/apt-get)

What system are you running on now (Ubuntu? OSX?) - if it's Ubuntu then what is the exact error you get when trying to run apt-get (it may be a path problem)?

---

### Post by Lars Noodén on 2013-06-27
Also, the shell is just a user interface through which you access other programs.  Nearly everything you would do via the shell is based upon calling other programs.  /usr/bin/apt-get is just one of thousands.  Even [ls](http://manpages.ubuntu.com/manpages/raring/en/man1/ls.1.html) and [cd](http://manpages.ubuntu.com/manpages/raring/en/man1/cd.1posix.html) are just programs that you run from the shell.  

bash, ksh, zsh and dash are just variations on the theme of user interface.

---

### Post by whatthefunk on 2013-06-27
What happens when you type in "apt-get"?

---

### Post by jps2012 on 2013-06-27
Folks: I'm trying this command: "[B][I]sudo apt-get install unrar-free" 

[/I][/B]I'm getting this response: [B]command not found

[/B]I get the same response if I just type "apt-get"****
I understand apt-get isn't part of the shell--that it's a command accessed by the shell (IF it's in the path). I'm on a new used Mac (an Intel dual-core purchased a couple days ago, with OS 10.6), but I'm been trying to run Virtual Box before I partition the hard drive to install Ubuntu (and struggling with that, too--learning Virtual Box).

---

### Post by Lars Noodén on 2013-06-27
What are you running?

```

lsb_release -rd
uname -a

```

---

### Post by steeldriver on 2013-06-27
What exactly are you trying to do? have you successfully created a virtual machine in VirtualBox, and if so what OS have you installed in it? 

Pretty much any Debian-based OS should have apt tools (apt-get or aptitude) as standard - but if you have installed a non-Debian/Ubuntu OS, it may use completely different package management tools

---

### Post by VMC on 2013-06-27
> **Lars Noodén said:**
> What are you running?

```

lsb_release -rd
uname -a

```

Yes, we need to find out where he's coming from. Also maybe try to find it: ```
sudo find /usr -name apt-get
```

---

### Post by Impavidus on 2013-06-27
Is there a problem with your PATH? Try```
echo $PATH
#Or, if that doesn't work
/bin/echo $PATH
```According to post #5 it cannot even find sudo, so I suspect something wrong with the PATH.

---

### Post by grahammechanical on 2013-06-27
Perhaps the command is wrong. Have you tried

```
sudo apt-get install unrar
```

[http://download.gna.org/unrar/](http://download.gna.org/unrar/)

Regards.

---

### Post by Cheesemill on 2013-06-27
> **jps2012 said:**
> I'm on a new used Mac

The apt-get command is for Debian and Ubuntu based systems only.

If you want to install VirtualBox on a Mac then download the .dmg file from the VirtualBox website...
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by jps2012 on 2013-06-27
Cheesemill: I THINK you're saying that apt-get wouldn't typically be found on a Mac. That isn't not part of bash or any of the standard scripts that comprise bash. Is that right? 

If I ask for the man page on "sudo" and get the man page, that means the command exists in my system, right? (I don't want to assume that's true for all commands, but maybe it is.) 

"echo $PATH" results in "/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/X11/bin"

I hope that's helpful. Mainly, I THINK the responses I'm getting mean ... that I'm thinking about bash and apt-get wrong. That I'm trying to accomplish something on a Mac that can only be done in Linux (by using apt-get). 

[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"): I did try the command and got the same response: "command not found" 

But sudo does seem to be there.

---

### Post by SeijiSensei on 2013-06-27
Yes. Apt and its tools like apt-get are designed to handle packages for Debian-flavored Linux systems.  Moreover there is a whole other class of Linux systems based on RedHat Enterprise Linux which use an entirely different package management system called RPM.  Neither of these are designed to run on anything other than a Linux system.

sudo is an entirely different type of command, one that runs on most any Unix derivative like Linux, BSD, Solaris, or OS X.  Not having sudo would be like not having mkdir to create directories.

---

### Post by whatthefunk on 2013-06-27
I a little confused.  Have you actually installed Ubuntu yet?

---

### Post by jps2012 on 2013-06-27
No, I haven't installed Ubuntu yet. I was trying to understand differences between the terminals in both systems (and didn't realized that they're 'quite' different). The goal is to partition the harddrive to have OSX and Ubuntu. But I'm trying to resolve some questions about issuing commands before I do something as drastic as partitioning. 

Sorry to have confused folks. I did install Virtual Box so I could use Ubuntu before partitioning (one thing that's slowing me down is that I'm having to write 100 gigs of files onto DVDs onto an external, so that the external can be reformatted to accept a Time Machine backup ... so I can do a backup BEFORE partitioning the harddrive to have OSX riding shotgun with Ubuntu. 

Now maybe it's clear why I didn't want to wax Homeric ...

---

### Post by alan9800 on 2013-06-28
if you wish to try apt-get under OSX, you might follow these instructions:
[LIST]
[*]download [macports]("http://www.macports.org/install.php")
[*]in a Terminal window, run```
port selfupdate
```
[*]when the above command has finished, run```
port install apt
```
[/LIST]

---

### Post by Lars Noodén on 2013-06-28
I haven't used it for a few years but [fink](http://fink.thetis.ig42.org/) will provide APT for OS X, if that is indeed the system you are trying to run these programs on.

Again, what are you running?

```

lsb_release -rd 
uname -a

```

---

