---
title: "[SOLVED] A question about installing other themes"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-11
I was looking at this theme [here]("http://gnome-look.org/content/show.php/Rainy?content=76649") 

And downloaded the file - it is a bin file and I may sound stupid but Im not sure what to do with it?? where to put it and how to install so on and so on 

~D

---

### Post by macaholic on 2008-05-11
It should be a .emerald file, which you can install in System > Preferences > Emerald Theme Manager.

---

### Post by autocrosser on 2008-05-11
Well, that is a Compiz Fusion/ Emerald/ Beryl theme. You need to be running Compiz with Emerald to use it. To install:
Open the Emerald theme manager & "Import Theme"

If you don't use Compiz or have Emerald installed, you will need to use/install the proper parts from Synaptic Package Manager.

That theme will not work with Metacity (stock Gnome system)

---

### Post by tjwoosta on 2008-05-11
i jsut downloaded the one from the link you pasted and it says .emerald not .bin

---

### Post by HunterThomson on 2008-05-11
you can jsut drag and drop it on the apprentice GUI

---

### Post by hufferd on 2008-05-11
> **autocrosser said:**
> Well, that is a Compiz Fusion/ Emerald/ Beryl theme. You need to be running Compiz with Emerald to use it. To install:
Open the Emerald theme manager & "Import Theme"

If you don't use Compiz or have Emerald installed, you will need to use/install the proper parts from Synaptic Package Manager.

That theme will not work with Metacity (stock Gnome system)


Ah yes thanks for all the help I have compix installed but not emerald manager ... 

will try that thank you :)

---

### Post by hufferd on 2008-05-11
Ok installed emerald theme manager but-- not to sure where togoto from this point.....

---

### Post by tjwoosta on 2008-05-11
Go to System-Preferences-Emerald Theme Manager  then click Import (use your .emerald file)

after, push alt-f2  and type emerald --replace  in the box that pops up (press enter)

and the theme should be changed

if you want emerald to start every login you will need to add the command i gave you to the startup programs

to do this go to System-Preferences-Sessions  and click add

just put the command in the box that says command and put whatever you want in the other two boxes

---

### Post by autocrosser on 2008-05-11
You can also install Fusion-Icon (I think it's available in Gutsy--I know that it is in Hardy)--It will put a Compiz icon in your notification area--you can use it to start/stop Compiz, change settings & run Emerald Theme Manager.

It's a very nice, clean way to do all the changes you want/need to do with Compiz.

You need compiz, compizconfig-settings-manager, compizconfig-backend-gconf, compiz-core, compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-gnome, compiz-plugins, emerald, fusion-icon & their depends

---

### Post by hufferd on 2008-05-12
Hey thanks for all your help :)

Have a great day! 
~D

---

