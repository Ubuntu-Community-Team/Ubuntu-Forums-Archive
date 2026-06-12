---
title: "apt, aptitude, dpkg - commands not found"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by alexander29 on 2014-04-05
Hello world!  I'm a virgin to linux/ubuntu, but I grew up on DOS (which isn't helping at this point).  I'm interested in using linux for my work, but I'm having problems installing... anything at all.  I did manage to get Ubuntu (I'd tell you the version, but lsb-release returns 'command not found') installed on my Chromebook ([FONT=verdana]Acer C7 C710-2847 [/FONT][FONT=verdana]Intel Dual Core B847)[/FONT] so I'm happy about that.  I can bounce around with the cd and ls commands, and I've dowloaded several things I'd like to install.

The problem is every article I find on the topics of installing tell me to use apt or aptitude to install them.  But NOTHING out there (that I've found yet) explains how to actually INSTALL APT or INSTALL APTITUDE without ALREADY HAVING one or the other.  I did manage to find another command, dpkg, which is suposedly the backbone for both apt and aptitude.  But the dpkg command ALSO returns command not found.  So I found instructions on how to download and install dpkg, but those instructions assumed the dpkg install file would be a tar file.  (I have used the tar command successfully).  It is not.  The dpkg install file I downloaded is a .deb file - which needs dpkg to install!  ...wtf?

How can I install something without already having an install program?

Looking forward to being part of the community, and thank you in advance for your time and assistance!  :)

---

### Post by bapoumba on 2014-04-05
You'll probably need some reading :)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/community/SystemAdministration](https://help.ubuntu.com/community/SystemAdministration)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by steeldriver on 2014-04-05
Are you sure you're just not SEEING those commands (like apt, dpkg and so on) because of a PATH mess up? what do you get if you do

```

/bin/ls /usr/bin/{apt*,dpkg*}

echo $PATH

```

in a terminal? it's hard to see how you could remove so many things without knowing about it

---

### Post by vasa1 on 2014-04-05
> **alexander29 said:**
> ...  I did manage to get Ubuntu (I'd tell you the version, but lsb-release returns 'command not found') installed on my Chromebook ...
Could you please explain how you *did manage to get Ubuntu* installed? That may help people to help you.

---

### Post by oldos2er on 2014-04-05
The proper command is ```
lsb_release
``` and it would help to know which version you're using. If you type **lsb** in a terminal, then hit Tab twice, it'll show you the correct completions for that command.

Both dpkg and apt-get are installed by default in Ubuntu.

---

### Post by alexander29 on 2014-04-07
Thank you bapoumba!  Excellent reading.  Unfortunately the referred software installation pages still assumes apt-get just WORKS and in my case it does not. (I skipped the graphical based installation options - I'm hoping to learn the terminal, not another GUI.) 

Steeldriver, when I type in those commands I get:

"/bin/ls: cannot access usr/bin/apt*:  No such file or directory
/bin/ls: cannot access usr/bin/dpkg*: No such file or directory"

For echo $PATH I get:

"/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin:/opt/bin"

Vasa1, I installed Ubuntu using Crouton via "sudo sh -e ~/Downloads/crouton -t xfce" 
But I'm avoiding the Ubuntu GUI for now... 

oldos2er, sorry, typo in the post (not the terminal).  "lsb_release" returns "bash: lsb_release: command not found".  Also, "lsb" returns command not found.

---

### Post by grahammechanical on 2014-04-07
apt-get is usually installed by default on Ubuntu because the GUI utilities like Software Updater and Software Centre and synaptic Package Manager are just front-ends for apt-get. But Aptitude is not installed.

lsb_release is just a text file. It is found in the etc directory/folder. This is what my present lsb-release text file reads

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu Trusty Tahr (development branch)"


Different versions of Ubuntu will have different labels. There must be something very non-standard about your installation. It could be that what you have installed is a stripped down version of Linux done to stop users from installing and removing software. I can imagine such an OS being necessary in certain business environments.

Regards.

Edit: After reading this I do not think that this problem is to do with Ubuntu. I notice that you have downloaded not from an official Ubuntu server but from a Crouton server. I doubt very much that you are getting a standard version of Ubuntu. You must have some highly modified version.

[https://github.com/dnschneid/crouton](https://github.com/dnschneid/crouton)

---

### Post by alexander29 on 2014-04-07
I would have installed clean from a CD if this Chromebook had a optical drive, but it does not.

I think I do have a stripped down version of linux...  I can run a GUI using "sudo startxfce4" so that leads me to believe it is indeed some version of Ubuntu...  I'm working on finding that lsb_release file now.

---

### Post by alexander29 on 2014-04-07
Alright.  <snip> crouton <snip>.  It appears that's the problem, correct?  I'm going to look for another way of getting Ubuntu on this machine.

---

### Post by alexander29 on 2014-04-07
I'll try ChrUbuntu...

---

### Post by alexander29 on 2014-04-08
Minor update:  I probably was never at an Ubuntu shell from the beginning...   Sheesh.

---

### Post by alexander29 on 2014-04-09
OK, thank you everyone.  Happy ending:  I got the ChrUbuntu install to work!  Now I'm scaling the Mount Everest of learning curves with Vim, networking in Linux, and creating my own noobish mini-scripts.

Thanks again!  :)

Edit:  Oh yes, and apt-get and dpkg are both working fine now.  Aptitude I have yet to dowload, but I can't do that until I get networking running.  That however is a question for another thread.

---

### Post by bapoumba on 2014-04-09
Please mark your thread as solved (under Thread Tools), thanks!

---

