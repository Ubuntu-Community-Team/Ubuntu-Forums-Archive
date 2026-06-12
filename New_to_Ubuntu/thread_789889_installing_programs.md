---
title: "installing programs"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-10
when i try to install a program it says i cant have 2 installers at once or something then it says end these tasks but i cant find where to end them and when i shut down the computer it still does the same thing

---

### Post by markbusu on 2008-05-10
Which installer are you using?? Add / remove ... Synaptic... apt-get?

Do have some updates running maybe... and being installed?

Note: Apt-get in shell is also considered as an installer...

---

### Post by nynoah on 2008-05-10
You might have both synaptic package manager open and the updater going at the same time.  See if your updater is on.  I think that is what is going on.  This has been my problem when I had the same thing going.  Don't get too frustrated.  Ubuntu requires you to learn a few different things that seem strange but make sense soon enough to you.

---

### Post by tjwoosta on 2008-05-10
when it says that, do you have both synaptic and the add/remove.. open?

or are you trying to do apt-get with synaptic open?

---

### Post by mr-Kirch on 2008-05-11
no i wont have ANYTHING open at all..i try to install limewire for example go to install package after everything then this pops up..

 "only one software management tool is allowed to run at the same time.. then under it it says "please close other applications e.g. update manager, aptitude, or synaptic first

that is exactly what it says and i go to system>administrator>system monitor>process but none of those things are there

---

### Post by nynoah on 2008-05-11
I know what the problem is.  I can not remember the code to put in the termenal at this time.  I have toe search.  Its something like sudo depak config a.   But wait while I look.  You had a problem with a file that did not complete so it is caught in limbo right now till that is fixed.

one sec

---

### Post by mr-Kirch on 2008-05-11
okay this is exacly what happens no bs no fillers...

>i go to limewire.com (as an example)
>click get it now
>click get basic
>click i will not use limewire for copyright infrigment
>go to linux (ubuntu, debian)
>then a box pops up w/ opening limewirelinux.deb
>i just click open with GDebi Package Installer
>then hit okay
>then a box pops up that says package installer-limewire-basic
>i click install package 
>put in my password
>then it says 
"only one software management tool is allowed to run at the same time.. then under it it says "please close other applications e.g. update manager, aptitude, or synaptic first

---

### Post by nynoah on 2008-05-11
open your terminal and run this

sudo dpkg --configure -a

let the system configure all unconfigured packages and then retry update manager or retry installing limewire.

---

### Post by mr-Kirch on 2008-05-11
where do i find update manager again

---

### Post by jamieh on 2008-05-11
Is Update Manager open?

---

### Post by mr-Kirch on 2008-05-11
k i updated let me check if it works

---

### Post by nynoah on 2008-05-11
upper left corner if in ubuntu

System-administrator-update manager

main thing is you have to run the code I said in your terminal in order for things to correct themselves.

---

### Post by tjwoosta on 2008-05-11
update manager is the little update icon that shows up on your gnome panel

Edit: sry bout that apparenty i should refresh the page before i respond

---

### Post by mr-Kirch on 2008-05-11
This is what happened..i got everything to work again, BUT one of my Java updates wont work so limewire cant install. But **** LIMEWIRE i'm setting up compiz-fusion 
[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

and i can get other things besides limewire now

---

### Post by nynoah on 2008-05-11
are you on Fiesty?

If not, DON'T use that tutorial.  

Just open up synaptic and type in compiz

just check the box for this "Compiz configuration settings manager"

---

### Post by Sef on 2008-05-11
> where do i find update manager again

System > Administration > Update Manager

---

### Post by mr-Kirch on 2008-05-11
THANK YOU...EVERYBODY
i got everything to work and i learned alot about linux while downloading things

---

### Post by nynoah on 2008-05-11
Glad to help.  Linux is not too hard, you get better over time, and so too does Ubuntu get better after every release.  God is Hardy great compared to some of the older distros.  Good luck and hit up the forums for more info.  If you want to learn more about compiz.  Do a google search and find their site.  On there is a lot of explanations how to use all the compiz settings in the manager.

---

