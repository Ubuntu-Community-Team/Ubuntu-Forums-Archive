---
title: "Howto get (almost) same effects as beryl offers in Kubuntu without beryl installed"
date: 2007-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by sal on 2007-02-22
This is for people who's video cards do not support beryl or people who don't want to install experimental software on their computers.

This HOWTO is for the KDE Desktop Environment.

the two applications were going to be installing are called Kompose and 3ddesktop. so to start things off you do an

sudo apt-get install 3ddesktop kompose

now, once you have those packages installed you going to see that kompose is already in your Kmenu but 3ddesktop is not so your going to have to add an entry for 3ddesktop to the Kmenu.

adding the 3ddesktop entry to the Kmenu:

Right click on the kmenu to start the menu editor. once in the menu editor pick which category you want to place 3ddesktop entry into and open that category.

Now your going to make the following settings:
application name: 3d desktop
command: 3ddesk –view=carousel

make sure to uncheck “enable launch feedback”

now add a shortcut key sequence in the “Current shortcut key section” and save the changes you have made. I use (alt+a) you can use another as long as it dose not conflict with another programs shortcut key bindings.

now for the options of Kompose:

all the kompose options can be left at the defaults but the ones you change will help a grate deal in your experience with the program:
Delay until active (ms): change this to a 0
Auto activate when mouse moves into: set this to  Top-right corner


reference images here:

[IMG]http://farm1.static.flickr.com/174/399100655_5a17be3581.jpg[/IMG]

[IMG]http://farm1.static.flickr.com/116/399100585_83b75960d8_o.jpg[/IMG]

---

### Post by lanchongzi on 2007-03-11
thank you very much

the kompose effect is a real beauty :) 

but 3d desktop doesn't have any effect at all :( 

is there a newer version out? ( mine doesn't even have an icon :confused: )

well, thank you any way

lanchongzi

---

### Post by fkdev on 2007-03-11
small typo: ```
3ddesk -view=carousel 
``` should be: ```
3ddesk --view=carousel 
``` Then 3ddesk will work Small hint for beginners: to autostart the kompose or 3ddesk daemon, just put a startup script in ~/.kde/Autostart like so, for example kompose: ```
 #!/bin/sh kompose 
```

Good job on the howto

---

### Post by lanchongzi on 2007-03-11
hmmm... still doesn't work
well, at least the kompose works fine
and it is REALLY handy

a very nice ap

thanks to the developers, and thanks to the How To
:)

---

### Post by MontanaMax on 2007-03-13
These are both very cool!!

To get the 3d desktop to work correctly, just replace the single hypen before the view parameter with two dashes - must delete the hypen and then add the dashes. Works great!

---

### Post by lanchongzi on 2007-03-13
ok now the command is correct
just my 3d acceleration is not configured yet ( shoot that i had to find it out that way...)
so i installed envy  and did sudo envy in a shell
with the result of a blank screen in the middle of all the fun
well i restarted my PC ( which is allready strong enough to steal lollies from the hard grip of a 3 year old :)  ) and did it again
same **** just couple o' minutes later...
soooo, what now?

---

### Post by lanchongzi on 2007-03-13
so, now i followed this advice:

Nvidia Driver Install and Config

To start off, it is a good idea to install Nvidia drivers. This can be accomplished by opening a terminal and typing:

Code:

sudo apt-get install nvidia-kernel-common nvidia-glx

This will install the Nvidia driver. You can then have it configure your Xorg.conf by running in the terminal:

Code:

sudo nvidia-xconfig

To make sure everything was configured right, let's check out the file and make sure. In the terminal, type:

Code:

sudo kate /etc/X11/xorg.conf

Scroll down to the "Modules" section, and make sure that GlCore and dri modules are commented out (or do not exist, due to nvidia-xconfig). The glx module should be enabled. Next, scroll down to the Device section. The Driver should say "nvidia". Underneath it, add in: Option "RenderAccel" "true"

The next section is "Screen" Ensure that the DefaultDepth is set to 24!!! Save the file, and close it.


taken from : [http://ubuntuforums.org/showthread.php?t=271533&highlight=Nvidia+Kubuntu](http://ubuntuforums.org/showthread.php?t=271533&highlight=Nvidia+Kubuntu)

and it didn't die in the middle.
but. now my panels are gone???
that kinda suxxx, after it took me so long to configure them just the way i wanted....
sad sad sad 
any ideas?

---

### Post by MontanaMax on 2007-03-13
I don't think I can help with the panel question unless just adding them back through the "Panel Menu" "Add Applet to Panel" works.

I have noticed a strange thing with the 3ddesktop however - once I installed it, my open GL screen saver slowed to an absolute crawl. After removing 3ddesktop the screen saver is back to normal. Has anyone else experienced this? 

Thanks,

---

