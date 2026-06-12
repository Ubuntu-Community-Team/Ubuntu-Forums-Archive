---
title: "How to get used to Ubuntu?"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by clementchiew on 2013-04-08
Hi, I just switched from Windows like many others. The problem is, I am already very very accustomed to the graphical GUI found in Windows rather than the terminal commands commonly used in Linux. Usually in Windows when I google something, I can memorize which windows opens which settings to amend and tinker around with the buttons... but with Ubuntu these few days, I kept copying lines of commands to install stuff. Getting Chrome was a nightmare. I get the shift from C:/ to / quickly because it is just folder arrangement. I have no idea when I should use sudo, tar, wget, and all that stuff along with the syntax (what if I typed wrong?) to live properly in Ubuntu. I love the new interface of Ubuntu and its speed. But I just want to get a handle on how the commands are to be used to do anything productive like download packages, run repositories and etc.... I dont expect a step-by step guide but can you guys give me links to them please?

---

### Post by BlinkinCat on 2013-04-08
Hi,

Welcome,

I'm sure you will get plenty of other help, but there is one link in my signature to start.

Cheers - :P

---

### Post by oldos2er on 2013-04-08
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

You should be able to accomplish most package management tasks graphically, if you would prefer that over the command line.

---

### Post by mamamia88 on 2013-04-08
> **clementchiew said:**
> Hi, I just switched from Windows like many others. The problem is, I am already very very accustomed to the graphical GUI found in Windows rather than the terminal commands commonly used in Linux. Usually in Windows when I google something, I can memorize which windows opens which settings to amend and tinker around with the buttons... but with Ubuntu these few days, I kept copying lines of commands to install stuff. Getting Chrome was a nightmare. I get the shift from C:/ to / quickly because it is just folder arrangement. I have no idea when I should use **sudo, tar, wget, and all that stuff along with the syntax** (what if I typed wrong?) to live properly in Ubuntu. I love the new interface of Ubuntu and its speed. But I just want to get a handle on how the commands are to be used to do anything productive like download packages, run repositories and etc.... I dont expect a step-by step guide but can you guys give me links to them please?

sudo allows you to run commands that you normally can't as a standard user.  Tar is a command to extract files(think of it as zip in windows) Wget is used to download files.  You can customize the behavior of a command by adding options with a -  .  To get a list of available options type man command.

---

### Post by snowpine on 2013-04-09
Installing software in Ubuntu is really, really easy. Here's a great how-to: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You can use terminal commands if you like (some users prefer it) but nearly all tasks can be accomplished with a few mouse clicks. If you are ever in doubt how to do something in Ubuntu, just ask, and you will have a good answer within hours or even minutes as you have just experienced. :)

---

### Post by Algus on 2013-04-09
Learning the command line can be extremely useful and you will notice often when you ask for help on the forums that people are going to suggest things that involve the command line.  That is because it is easy to just post commands then give a detailed explanation of what to click and why.    And also because many Linux veterans find using the command line very easy.   I personally like this website for learning CLI (command line interface) 

[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

But if you look at the top of this forum, there is also an entire sticky thread with hundreds of posts dedicated to covering the topic of learning command line.  These are very useful resources! 

That said, Ubuntu is a terrific beginner version of Linux because so much can be done without ever having to look at the terminal.   Acquiring software can be done via the Ubuntu Software Center which you can access from the menu.   The software center has a search function and is very extensive if you are looking for a specific app.  This is a little different from the way in Windows where you would probably google a program, go to its website, download, and then install it.  You can do that in Linux too, though sometimes that process is a bit more involved.    You might also look into installing Synaptic Package Manager.  If you want to practice, you can do this from the command line via 

```
sudo apt-get install synaptic
```


Synaptic is pretty much the same idea as the Ubuntu Software Center but it is a bit more technical in nature, showing most software by the package names you would type into the terminal to install them.  

If you are comfortable learning CLI, I think you will find it rewarding and it will enhance your enjoyment and undertanding of how Linux work overall but if you prefer to stick with a GUI, the ones in Ubuntu are quite robust.

---

### Post by ppjdee on 2013-04-09
I'm still pretty new to Linux myself, that being said I hardly ever copy/paste commands into the terminal. I rather type it out, so I can learn the commands easier.
After a while you will see how the terminal is faster and (to me) more fun to use than a GUI. And don't worry if you "break" something in Linux you can always re install :D (just dont forget to backup your data) and you got Ubuntu Forums for help.

---

### Post by mastablasta on 2013-04-09
KDE found in Kubuntu has interface similar to windows. especially the classic menu.

plenty of commands have grapgical interface. for example wget has wgetgui, tar can be done by right clicking the file and then selecting extract, sudo (or gksu for graphical programmes) usually can be done if you open as root, but not always. it gives you the power to change system files.

the reason people give commands is because there are various interfaces (KDE, XFCE, LXDE, E17 etc.) but these commands work in all of them. furthermore they also work in various distributions especially Debian based ones.

For example i use KDE (Kubuntu) as i find it similar to what i am used in windows. i do most stuff withouth commands. i am not familiar with Ubuntu unity interface. so if i want to help you i can give you a terminal command how to do it but i do not know where these things are in the menu or what graphical applications you have installed that might do the same thing as those commands.

but hey at least in linux you can copy & paste commands into terminal. if chrome was difficult to install the thanks goes to google for that since they do not have a PPA. 

ther eis chromium available in repositories (software center) which i am told is not exactly the same as chrome (missing a few features, having some).

---

