---
title: "[How-To] Dual/Triple Desktopping"
date: 2007-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by bobbocanfly on 2007-06-20
As almost everyone knows, in Linux you get multiple desktop environments. Not everyone knows that you can easily use multiple desktop envrionments, without overwriting your current one.

This tutorial will show you how to set up KDE on top of your GNOME installation so you can choose whether you want a KDE or GNOME day when you login.

**Step One - Stuff to do before you KDE it**

First of all you have to make sure you have the latest Feisty repositories. Check your sources list then open up the terminal and run 
```
sudo apt-get install update
sudo apt-get install upgrade
```

Once this is done your system will be fully up to date and ready to install KDE.

**Step Two - Installing KDE**

There are two different versions of KDE in the Ubuntu Repos, kde-core and kubuntu-desktop. kde-core is recommended if you want to use GNOME as your main environment and keep all of the standard Ubuntu splash screens/boot screens etc. as it just installs the basic KDE desktop environment and a few basic apps. Kubuntu-desktop includes a lot more applications and will *probably* overwrite your boot and splash screens with the Kubuntu ones. This is more useful if you want to use KDE as your main environment and use Gnome on the side.

To install run
```
sudo apt-get install kde-core
```
or
```
sudo apt-get install kubuntu-desktop
```

Both are fairly big packages but kubuntu-desktop is a lot larger and will take a long time to download and install. You could spend this time searching KDE look for your new themes ;)

**Step Three - Running KDE**

To run KDE you should restart your X11 server. To do this you should simply restart your computer, though some users have it set up to run every time they logout of a session.

Once your X Server is restarted you need to set up your Session. On your login screen go to either your Main Menu -> Sessions and click KDE or if you have a sessions menu simoply click on KDE. (If KDE is not there, it hasnt installed properly or your X Server hasnt been restarted).

Now type in your username and password and KDE will start to boot.

Wahey! You are now a dual desktopper.

**Other desktop environments**

GNOME and KDE arent the only Linux Desktop Environments. TO install a different one follow the same instructions above just replacing the package names with:

Fluxbox : sudo apt-get install fluxbox
XFCE : sudo apt-get install xfce4
Crystal : subo apt-get install fvwm-crystal
Unix Desktop Environment (UDE) : sudo apt-get install ude

---

### Post by rfcompte on 2007-09-10
Hi, I'm into it. I'm following your instructions. But I think you made a mistake. It's not

```
sudo apt-get install update 
```

       but 

```
sudo apt-get update

```
The same with the upgrade commands. And of course -for the folks that don't like the terminal- it can be done with synaptic

Thanks,

RF

---

