---
title: "[SOLVED] Flash with FireFox (need to uninstall)"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by vistasucksss on 2008-07-07
just tried to download the flash plugin through firefox by clicking on the info bar that drops down letting you know that a plugin is needed. when i did this and selected the first option (installer) it appears that it froze almost 3/4 way through. when i tried to do it again it said flash was already installed but i still have no flash.

how do i uninstall what i have installed? i tried looking in the 'etc'folder? and then did a search for my harddrive and found a few 'flash' files..when i tried to delete them it said access denied even though i had firefox closed..

thanks in advance.

---

### Post by alienexplorers on 2008-07-07
check in your .mozilla plugins folder for a file called libflashplayer.so and delete the flashplugin if it is there.  It could also be in the /usr/lib/firefox directory in the plugin folder if there delete it.

---

### Post by gandaran on 2008-07-07
everything you install from the repos you use synaptic package manager to install/remove it, open synaptic and find the flash you installed (swfdec or gnash) check-mark for complete removal, next find the flashplugin-nonfree package (adobe flash), mark for install and click the apply button.

---

### Post by ChameleonDave on 2008-07-07
> **vistasucksss said:**
> .when i tried to delete them it said access denied 
.

You probably didn't delete them with root access.  You need to use "sudo rm" on the command line, or open Nautilus as root with "gksu nautilus".

That's assuming that it is a good idea to delete those files.

---

### Post by vistasucksss on 2008-07-07
hey thank you all for the help.

to chameleondave: 

i am still a noob and not familiar at all with command lines. i did try to delete the files by right clicking on them and clicking 'delete'. is this not a proper way to delete items? 

to alienexplorer:
do i have to use the command line to do this?

thanks again for the help to everyone in the thread :)

---

### Post by ChameleonDave on 2008-07-07
> **vistasucksss said:**
> hey thank you all for the help.

to chameleondave: 

i am still a noob and not familiar at all with command lines. i did try to delete the files by right clicking on them and clicking 'delete'. is this not a proper way to delete items? 


Yes, but it only works for files owned by you.  You only own files in /home/YOURUSERNAME.  Files elsewhere are owned by "root" (the system itself).

---

### Post by vistasucksss on 2008-07-07
is there a way to avoid this or to gain access?? and if not and i must use the terminal.. is this what i must do anytime i want to delete a file from root? please bare with me i am a former vista user ](*,)

thanks again
-chris

---

### Post by isaacj87 on 2008-07-07
> **vistasucksss said:**
> is there a way to avoid this or to gain access?? and if not and i must use the terminal.. is this what i must do anytime i want to delete a file from root? please bare with me i am a former vista user ](*,)

thanks again
-chris

Hey man,

I feel your pain. I don't mind using the terminal, but I'm a visual person. Sometimes, I use...

```
gksudo nautilus
```

...to have the ability to modify files and folders (that are owned by root). I would do that sparingly though, because you could do serious damage if you don't know what you're doing. If you want to delete something as root and your sure you don't need the files and/or folders, you can do a "shift+del" to permanently delete files...otherwise, they just end up in your root trash.

EDIT: I see someone else has mentioned that...I need sleep..:)

---

### Post by bhadotia on 2008-07-07
Well , I don't know about how to avoid it but you don't want to do that coz thats what makes your linux safe from viruses and all!

---

### Post by vistasucksss on 2008-07-07
hey isaac,

thanks for the tip but i didnt see anyone else mention that lol

anyways i will have to give it a try but now i am not sure if it is a good idea to delete the flash files i found? i basically just want to reinstall the flash plugin for firefox.. am i missing vista already? :(

---

### Post by isaacj87 on 2008-07-07
> **vistasucksss said:**
> hey isaac,

thanks for the tip but i didnt see anyone else mention that lol

anyways i will have to give it a try but now i am not sure if it is a good idea to delete the flash files i found? i basically just want to reinstall the flash plugin for firefox.. am i missing vista already? :(

Ah...ChameleonDave mentioned it above...

There are certain times when you just can't avoid files being installed as root. Programs are often installed system wide. However, in this particular situation with Flash, it only needs to be installed locally (i.e. in your home folder). I remember trying to install Flash within the browser and it didn't install. You can try something. In the address bar in Firefox (where you put URLs) put this:

```
about:plugins
```

This will tell you what is truly installed or not. If you don't see any Flash plugin, head on over to this site:

-- [http://www.adobe.com/products/flashplayer/]("http://www.adobe.com/products/flashplayer/")

...and download the .tar.gz. Simply download the file to your desktop, open the folder containing the files, click on the installation script and choose "Run in Terminal" and follow the instructions. This will install Flash locally and you can do whatever you please with it. It will be located (as mentioned in another post) in /home/YOURNAMEHERE/.mozilla/plugins.

Concerning those "Flash" files you found. As far as I know, the Flash plugin is only one file called "libflashplayer.so" You can do a system search and see if it comes back with anything. Otherwise, you probably don't have anything installed.

---

### Post by bhadotia on 2008-07-07
That is very easy-  easier than in vista:
Go in synaptic package manager (System>Administraton>Synaptic Package Manager) and find (scroll down) to the package flashplugin-nonfree.
Now right click on the green box next to it and choose 'completely remove'
After it is removed, install it again by right - clicking on the box again and choosing to install.

See, very easy.:)

---

### Post by vistasucksss on 2008-07-07
> **isaacj87 said:**
> Ah...ChameleonDave mentioned it above...


haha sorry didnt even see it but now i do :) ok now lets see what you said 

sorry!

---

### Post by vistasucksss on 2008-07-07
HEY! ok i just went to youtube and flash is working! checked the about:plugins and i saw it was installed??? and enabled! i have no idea what happened maybe i needed a restart (which i did about 5 minutes ago) but i guess problem solved. learned a few things though and i really wanna thank you guys for all the help. star badges for everyone!

i really hate being a noob.. i wish i was a linux/ubuntu guru but i guess it will be a loong ways before that happens.  but having great people on this forum really make it alot easier to cope with my lack of knowledge. thanks again guys

off to starting another thread... :)

---

### Post by isaacj87 on 2008-07-07
Good to hear! Glad everything is working now :)

---

### Post by bhadotia on 2008-07-07
Great!:popcorn:
Please don't forget to mark the thread as solved.
Have fun!

---

