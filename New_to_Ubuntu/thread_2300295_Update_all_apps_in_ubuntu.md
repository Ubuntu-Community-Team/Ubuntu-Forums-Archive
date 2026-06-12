---
title: "Update all apps in ubuntu"
date: 2015-10-24
forum: New to Ubuntu
---

### Post by Thien on 2015-10-24
[FONT=arial]Hi :) I'm new to Ubuntu
I just wanna ask if it is possible (and how) to update all the apps in Ubuntu, such as Ubuntu tweak, steam, ect
Some of those apps don't have an "update" button and I'm not sure if software updater supports all the apps on my computer

Also... I'm using a triple a triple boot (Windows 10, OS X 10.11, Ubuntu 15.10) and Clover  as  the bootloader... so is there anyway to skip grub when I boot to Ubuntu? 
Sorry for my bad English btw
[/FONT]

---

### Post by Sweet_Baby_Jamie on 2015-10-24
There is a way, but the "all-or-nothing" approach makes some users uneasy.  A nice graphical way is to open **Synaptic Package Manager** (you'll need your root password).  When it loads, click on the **Reload** button at the top, and it will download a fresh list of all updates available for all software installed on your computer.  When it's ready, click on **Mark All Updates**, and then click **Apply**.  That updates all the installed software!

---

### Post by grahammechanical on 2015-10-24
Applications full into a different category. Not all developers update their apps. Often the way to get updated applications is to install the latest release of Ubuntu. Anyway, Ubuntu developers put stability over latest. I have never seen an application with an update button.

---

### Post by Thien on 2015-10-24
[FONT=arial]GREAT! I'll try it right  away...
BTW, there's one problem with Ubuntu 15.10
I'm not sure if it is caused by Ubuntu itself or by bleachbit/ ubuntutweak  but sometimes I  press "shutdown", it only logs me out... 
Does anyone have the same problem?
[/FONT]

---

### Post by Dennis N on 2015-10-24
Hi Thien, and welcome to the forums.

Here is a tutorial on updating your system. Read the introduction and the section on _Ubuntu Linux_. Although the article is dated 2009, the procedure is basically the same today. 

[https://www.linux.com/learn/tutorials/234011-linux-101-updating-your-system](https://www.linux.com/learn/tutorials/234011-linux-101-updating-your-system)

---

### Post by Thien on 2015-10-24
[FONT=arial]Thank you so much for your help :) Is the Update Manager in the post the same as software updater in 15.10?

What about the problem that keeps logging me out instead of shutting down? Does anyone have the same problem? xD 

[/FONT]

---

### Post by Dennis N on 2015-10-24
> **Thien said:**
> [FONT=arial]Thank you so much for your help :) Is the Update Manager in the post the same as software updater in 15.10?

What about the problem that keeps logging me out instead of shutting down? Does anyone have the same problem? xD 

[/FONT]

No idea really. The best thing to do is to start a new thread with a new issue. Give it a title to reflect the problem and wait. Remember, forum viewers and members are from around the world and the one having an answer may not be logged in. Sometimes may take a day or so. Patience.

Software updater has the same function as Update Manager. Slight name change.

---

### Post by Thien on 2015-10-24
[FONT=arial]Oh btw, my software updater keeps saying "check your internet connection"  while I'm connecting to the internet normally :/ help[/FONT]

---

### Post by Dennis N on 2015-10-24
> **Thien said:**
> [FONT=arial]Oh btw, my software updater keeps saying "check your internet connection"  while I'm connecting to the internet normally :/ help[/FONT]

See the advice in post #7 - you probably overlooked it - about starting a new thread.

---

### Post by Kpenguin on 2015-10-25
You could also use the terminal to update all software.
```
sudo apt-get update
sudo apt-get upgrade
```
This is my preferred method of updating the software on my computer.

---

### Post by deadflowr on 2015-10-25
> **Dennis N said:**
> 
Software updater has the same function as Update Manager. Slight name change.

Same package in fact.
But beside the what-user-sees-it-as name change, there was a concurrent function change when they changed it from being called update-manager.
The new function was to automatically launch it with the Check function.
Earlier versions opened as is, so if you opened it sometimes it would simply show a blank window.
You would have to manually click on the Check button to get the latest package info, then the blank window would return 
with the list of available updates.

My thinking is too many users would not run the Check, so they'd think all was peachy-keen.
Which in turn was not the case, and in some cases (some of which have threads in these forums) users would try to install packages that their systems told them where one package, but had since been updated on the Ubuntu servers. And when they tried to install said package, all they got where broken dependency issues and 404s. Sometimes, comically, they'd mangle their systems even more.
When the solution was as simple as just updating the package lists, easily done with the check button.

But overall the package is still update-manager, and the cli is still update-manager, fwiw.

Arm-chair history 101, ftw

---

### Post by Geoffrey_Arndt on 2015-10-25
Intesting deadflowr . . . I've always wondered why the Update-Manager was so "un-intuitive" for the casual user.   Not really a good human factors design.

---

