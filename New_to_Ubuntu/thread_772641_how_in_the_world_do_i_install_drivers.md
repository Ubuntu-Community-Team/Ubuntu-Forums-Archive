---
title: "how in the world do i install drivers?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by markferrar on 2008-04-28
i am totally new to this i have no idea what im doing at all someone help please?

---

### Post by superprash2003 on 2008-04-28
what drivers are you planning to install?

---

### Post by russo.mic on 2008-04-28
Well,  You need to provide the forums here with more info.  Exactly what are you trying to install drivers for?  A graphics card?  a printer?  a scanner?  some kind of elaborate Electron microscope interface?

What hardware are you running on?  what version of ubuntu are you using?  

Let us know, and we'll all be glad to help i'm sure.

Russo

---

### Post by alienexplorers on 2008-04-28
If you are planning to install video drivers for an ATI or Nvidia card I would recommend using the Envy program which can be found in the repositories.

---

### Post by russo.mic on 2008-04-28
Well,  You need to provide the forums here with more info.  Exactly what are you trying to install drivers for?  A graphics card?  a printer?  a scanner?  some kind of elaborate Electron microscope interface?

What hardware are you running on?  what version of ubuntu are you using?  
You might as well walk up to a mechanic and ask "How do I fix my car?"  Well, is the tire flat, or won't it start...

Let us know, and we'll all be glad to help i'm sure.

Russo

---

### Post by gardara on 2008-04-28
Most of the time you don't need any drivers, since the linux kernel has most of the drivers built in.

---

### Post by markferrar on 2008-04-28
drivers i found after searching for a while for  a linksys wusb54g v.4 wireless adapter i think they are called ralink2500

and is it a different method to install drivers for  each individual piece of hardware?

youll have to forgive me for being  vague im totally in the dark with this

---

### Post by c4v3m4n on 2008-04-28
We need more info to help you out.  What kind of drivers?

---

### Post by conehead77 on 2008-04-28
> **markferrar said:**
> drivers i found after searching for a while for  a linksys wusb54g v.4 wireless adapter i think they are called ralink2500

and is it a different method to install drivers for  each individual piece of hardware?

youll have to forgive me for being  vague im totally in the dark with this

I think with the ralink 2500 you need to install the "ndiswrapper". I cant find a link at the moment, but a forum search should lead you in the right direction.
Usually you dont need to install drivers at all, most of them are built-in. Few (but important) drivers need to be installed separately. This happens when the manufacturer of the hardware doesnt release the specification for their hardware.

EDIT: Here is a link from the "wireless" section of this forum: [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by russo.mic on 2008-04-28
> **markferrar said:**
> drivers i found after searching for a while for  a linksys wusb54g v.4 wireless adapter i think they are called ralink2500

and is it a different method to install drivers for  each individual piece of hardware?

youll have to forgive me for being  vague im totally in the dark with this

So, I think what you want to do is used the windows driver and install what is called NDISWrapper.  You can download that from the repos, or compile it yourself.  That will use the windows driver to run the card from linux.

I would search for a how to, but to get you going, from a terminal run a 

sudo apt-get install ndiswrapper-common ndiswrapper-utils

after it installs,  

sudo ndiswrapper -i [name of driver .inf file]
sudo modprobe ndiswrapper

that should get the card working.  if that works you'll want to edit the file /etc/modules and add the line ndiswrapper at the bottom.

sudo gedit /etc/modules

Save the file, and that should make ndiswrapper start up at boot, without you haveing to load the module each time.

Sorry to give you a hard time earlier.  Stick with it! you'll figure it all out.

Russo

---

