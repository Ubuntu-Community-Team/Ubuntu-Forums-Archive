---
title: "Themes and Docks"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by singh763173 on 2008-07-08
Hi all again!

After recieving great help from yourselves, i thought id bug you all one more time :D

ive been looking to enhance my ubuntu experience by tweaking the appearance.

ive found themes online like this [http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791](http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791) and was wondering if someone could help me install it (also is that available in english)

also i wanted to install the mac like dock, and ive read AWN is what im after :/ once again what where and how :|

many thanks in advance

---

### Post by tjwoosta on 2008-07-08
well you can get AWN right from the repository
(system-Administration-Synaptic Package Mananger)

but if you get AWN there it has no applets


where i got mine is here (it comes with like 30 different applets)
[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive]("http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive")

(just scroll down till you see **Reacocard's PPA ** (the packages you want are avant-window-navigator-bzr and awn-manager-bzr , but you will have to install the extra repositories first)

**note that the repositories they show are for Ubuntu Gutsy, not hardy, but they do give you a link to the hardy repository**


EDIT: i think that is a login screen theme  (just go to System-Administration-Login Window and click the "local" tab, then just drag and drop your .tar.gz right into it)

---

### Post by Ryadt on 2008-07-08
Hi. Try using kiba dock, it's about the same as the mac dock.
This tutorial should help you installing it.
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

---

### Post by acidsolution on 2008-07-08
> **singh763173 said:**
> Hi all again!

ive found themes online like this [http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791](http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791) and was wondering if someone could help me install it (also is that available in english)



Certainly the GDm available is in English from the same link 
Just download it 
and than go to 
System->Administration->Login Window
Now click on the Local Tab and than select *** option Now locate the tar.gz file and than click install 
After installing you select the theme as your GDM from the list 
and than just Log out to see the effect 
this might help you :)

---

### Post by singh763173 on 2008-07-09
tjwoosta, sorry to be a pain, but ive had a look through there and tried to paste a command into terminal, then put my password in and i got Avant Navigation thingy could not be found :/ would it be possibly for you to post up the commands i have put in please?

and also, wen u see applets, do u mean program applets or applets like in vistas side bar? 

thanks for the advice on how to install the login theme (works a treat)

are there any full themes around? summin that changes the toolbar, login theme and the desktop?

Thanks in advance

---

### Post by singh763173 on 2008-07-09
okkk.... ive done this :|

sudo apt-get install avant-window-navigator

the bar came up after i wernt to applications accessries and clicked the bar. the applets in there are jus the progs i have open. also how do i get it like in all those pics... opaque and like 3d'ish :/

---

### Post by nothingspecial on 2008-07-09
go to system > administration > software sources. Press add. Copy and paste this in

```
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

Press add again, copy and paste this
```

deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```
 Close the window. It will ask you if you want to reload (or something like that) Do it.

go to system > administation > synaptic package manager

Click search. Type awn

Find the packages, install them.

I think awn is in accessories (avant windows navigator)
Avant windows manager (to configure your dock) is in system > prefernces.\\:D/

---

### Post by nothingspecial on 2008-07-09
You`d figured it while I was typing.
To get a launcher on your bar lets use firefox as an example -
Go to your home directory
Right click and create a new folder, call it anything you like (launchers would be a good idea). Open this folder.

Go to your menu. In internet, right click on the firefox thingy.
Select "add to desktop". Drag it from your desktop into your new launchers file. From the launchers file, drag it onto the bar.
Notice during this process, the launcher will disappear from your desktop but remain in your launchers folder.
The reason for this is that if you don`t create that folder and put your launchers in it, they won`t be there next time you launch awn.

---

### Post by nothingspecial on 2008-07-09
> **singh763173 said:**
> also how do i get it like in all those pics... opaque and like 3d'ish :/

System > preferences > avant window manager

Click on the bar appearance tab and experiment from there. There are loads of options eg bar angle will lie it flat. You can adjust the transparency just mess about and see what you like.

One thing worth mentioning is that if you select "start bar at login" or whatever it says, don`t add awn to your start up list in sessions otherwise 2 bars will appear when you login.

:guitar:

---

### Post by singh763173 on 2008-07-10
cheers lads... i think i got it working :D now time to mess about with the launchers :P

once again youve all proved to be a great help

very much appreciated 


cheers

---

### Post by billgoldberg on 2008-07-10
> **singh763173 said:**
> Hi all again!

After recieving great help from yourselves, i thought id bug you all one more time :D

ive been looking to enhance my ubuntu experience by tweaking the appearance.

ive found themes online like this [http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791](http://www.gnome-look.org/content/show.php/Doe+GDM?content=52791) and was wondering if someone could help me install it (also is that available in english)

also i wanted to install the mac like dock, and ive read AWN is what im after :/ once again what where and how :|

many thanks in advance

Look at the customizing link in my signature.

And you want cairo-dock, not awn.

---

### Post by tjwoosta on 2008-07-10
**CAIRO DOCK SUCKS**

awn looks so much better

also you could try kiba dock  (even that looks way better then cairo dock)

EDIT:  i feel kinda stupid now but Linuxisinnovation just pointed something out to me

with AWN you cant place the dock at the top of the screen

also in awn if you have icons set to zoom effect they look kinda blurry when zoomed

---

