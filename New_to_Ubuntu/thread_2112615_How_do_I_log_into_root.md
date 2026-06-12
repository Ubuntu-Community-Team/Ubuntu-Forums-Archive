---
title: "How do I log into root?"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by rtroxel on 2013-02-05
When I installed Ubuntu 12.10  last week, I forgot to set up a root account. Is this still possible?

Thanks,

Roy

---

### Post by snowpine on 2013-02-05
Root account is locked in Ubuntu; use 'sudo'.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

---

### Post by TheFu on 2013-02-05
There is little need for root under Ubuntu. To become root in Debian and Ubuntu, we use sudo.

$** man sudo** can explain how.

The short answers are:
* use** sudo** to run 1 command as root; sudo /ls /var/log/*
* use** sudo -s** to get a root prompt, but keep your environment
* use** sudo -i** to get a root prompt, but get the safer, root environment.

The root account exists on every UNIX/Linux machine, but it is considered poor form to use it from remote locations i.e. through a password.  The best-practice is to remote in using your normal account, then to sudo for any specific needs.  sudo commands are logged, so any abuse can be uncovered.

---

### Post by grahammechanical on 2013-02-05
Whenever you try to do something that a standard user is not allowed to do, then Ubuntu will ask you to Authenticate the action. You enter the password that you set up during the installation and for the time that the action takes to complete you will be the Administrator (or have Root privileges).

If someone else tries to run that activity then they will not be able to authenticate the action (unless they know your password). So, Ubuntu protects you unauthorised people changing the OS. You would not have this protection if you loaded the OS as a Root user.

Regards.

---

### Post by SBFree on 2013-02-05
The root account is always there. If you have to function as root in the terminal you precede your command by 'sudo'. For example:
as the logged in user you would type:
gedit
to launch the editor as the logged in user. You would not be allowed to edit root's files.
sudo gedit
would launch the editor and let you edit files owned by root.

---

### Post by Cheesemill on 2013-02-05
> **SBFree said:**
> The root account is always there. If you have to function as root in the terminal you precede your command by 'sudo'. For example:
as the logged in user you would type:
gedit
to launch the editor as the logged in user. You would not be allowed to edit root's files.
sudo gedit
would launch the editor and let you edit files owned by root.
Except you should never use sudo for graphical applications, you should always use gksudo instead.

---

### Post by rtroxel on 2013-02-05
Works for me!

Thanks,

Roy

---

### Post by iponeverything on 2013-02-05
> Except you should never use sudo for graphical applications, you should always use gksudo instead.

never? Its just a wrapper. There is no reason not to use sudo.

---

### Post by haqking on 2013-02-05
> **iponeverything said:**
> never? Its just a wrapper. There is no reason not to use sudo.

yes there is, home folders can become owned by root.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://www.mail-archive.com/arch@archlinux.org/msg04963.html](http://www.mail-archive.com/arch@archlinux.org/msg04963.html)

I have seen it happen.

gksudo for graphical apps.

Peace

---

### Post by bkratz on 2013-02-05
Actually there is.  

From:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)




You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root.

---

### Post by iponeverything on 2013-02-05
> **haqking said:**
> yes there is, home folders can become owned by root.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[http://www.mail-archive.com/arch@archlinux.org/msg04963.html](http://www.mail-archive.com/arch@archlinux.org/msg04963.html)

I have seen it happen.

gksudo for graphical apps.

Peace

I am sure you have. Never is one those words that tweaks me. In this case the worst case is ownership getting changed on your .x files...

---

### Post by haqking on 2013-02-05
> **iponeverything said:**
> I am sure you have. Never is one those words that tweaks me. In this case the worst case is ownership getting changed on your .x files...

yes, it has never happened to me personally but I have seen the results of it on anothers system.

It is merely a best practice thing, same as not logging in as root, you can but it "may" result in damage.

Peace

---

### Post by jfbooth on 2013-02-05
> **Cheesemill said:**
> Except you should never use sudo for graphical applications, you should always use gksudo instead.


What are some examples of 'graphical applications'?

Can you just use gksudo exclusively and thereby not have to remember?

---

### Post by haqking on 2013-02-05
> **jfbooth said:**
> What are some examples of 'graphical applications'?

Can you just use gksudo exclusively and thereby not have to remember?

anything that has a graphical front end and doesnt run in text mode in the command line.

gedit is a graphical editor
vi/nano etc are command line editors

and so on.

---

### Post by jfbooth on 2013-02-05
> **haqking said:**
> anything that has a graphical front end and doesnt run in text mode in the command line.

gedit is a graphical editor
vi/nano etc are command line editors

and so on.

**This is an example only:**  so **sudo thunar** ... that would be?

To avoid the liability .. can one simply JUST use gksudo in all cases ... as in gksudo vi (to be safe) as well as gksudo gedit (to be safe)?

being a rookie .. I don't really know what is graphical and what isn't until I run it.  Gotta start learning from some point.

---

### Post by bodhi.zazen on 2013-02-05
> **jfbooth said:**
> **This is an example only:**  so **sudo thunar** ... that would be?

To avoid the liability .. can one simply JUST use gksudo in all cases ... as in gksudo vi (to be safe) as well as gksudo gedit (to be safe)?

being a rookie .. I don't really know what is graphical and what isn't until I run it.  Gotta start learning from some point.

As a new user, probably not the best idea to run $random_applications as root.

---

### Post by Paqman on 2013-02-05
> **haqking said:**
> 
gksudo for graphical apps.


Indeed, or kdesu for our KDE bredrins.

---

### Post by lisati on 2013-02-05
> **Paqman said:**
> Indeed, or kdesu for our KDE bredrins.

+1, particularly if you are using a KDE-based system such as kubuntu.

---

### Post by Paqman on 2013-02-05
> **jfbooth said:**
> 
being a rookie .. I don't really know what is graphical and what isn't until I run it.

If you're in a terminal, use sudo. If you're launching a normal desktop app as root (for example by hitting Alt-F2) then use gksudo. You shouldn't have much need to run desktop apps as root though. For any system-tinkering that requires root you'll probably find you use the terminal anyway.

---

### Post by haqking on 2013-02-05
> **Paqman said:**
> Indeed, or kdesu for our KDE bredrins.

> **lisati said:**
> +1, particularly if you are using a KDE-based system such as kubuntu.

Indeed, I should of said that seeing as I am a devout KDE user ;-)

---

### Post by jfbooth on 2013-02-05
> **Paqman said:**
> If you're in a terminal, use sudo. If you're launching a normal desktop app as root (for example by hitting Alt-F2) then use gksudo. You shouldn't have much need to run desktop apps as root though. For any system-tinkering that requires root you'll probably find you use the terminal anyway.

Thank you ALL for the advice.  I appreciate your time and support.

---

### Post by TheFu on 2013-02-06
> **bkratz said:**
> You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root.

One should never use a program they do not understand, especially sudo OR any variant.

sudo -i {some other program} will set HOME properly, so the idea that it should "never" be used is an *over simplification* of the issues.  Any program that takes ownership of any entire subdirectory tree without being explicitly told to do that is flawed.  OTOH, if I $ **sudo chmod -R root.root $HOME,** then I deserve what I get.

I must admit that I have **never** used any GUI interface to sudo on purpose myself. NEVER and I have not had any major issues.  I don't use GUI programs as root very much without knowing where the impacted files are located.  However, once I used sudo with Back-In-Time GUI to create a backup job settings file on Mom's Lubuntu box.  It placed it into my .config/...... area, but I intended to run the backups as root, so I moved the file into the same location under /root/ .  The crontab entries had already been placed into the root crontab - guess that program used LOGNAME or USER to determine which crontab to modify.  backups, as root, worked perfectly.

Never is a very long time.

---

