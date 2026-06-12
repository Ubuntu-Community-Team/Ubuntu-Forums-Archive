---
title: "Envy Problems"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Floyd923 on 2008-10-22
Trying to install Envy to update some Nvidia drivers.  But I messed something up.  When I try to install it either by .deb or through terminal, it says that the most updated version is already installed.  But its not.  I tried removing the old one, to put back in a new one, but all the help online I can find doesn't work.

NOOB ALERT:  Did something stupid.  Used the search tool to look for any file that has envy in it, and manually deleted it in the terminal.  

how to I tell Ubuntu that the latest version is not installed, and how do I re-install it?

Thanks for any help

New Linux NOOB

---

### Post by robert shearer on 2008-10-22
Are you trying to install/uninstall the package 'Envy', or are you trying to install/uninstall the Nvidia drivers.??

What version of Ubuntu are you using?

If 8.04 Hardy then the package that one installs to automatically load and set up the Nvidia drivers is called 'envyNG, and is in the repositories.
Install envyNG using Synaptic package manager.
Uninstall envy using Synaptic package manager first.

---

### Post by aimpau on 2008-10-22
Just to point out that indeed, envy AND envyNG, though has the same developer, is different in all aspects.

---

### Post by Floyd923 on 2008-10-23
The Synaptic Package Manager is what I was needing.  Thanks for the tips.  By uninstalling, then reinstalling EnvyNG...and eventually uninstalling xgl (which I did with the manager, see I can learn!), I now have my dual monitors working perfect.  

Thanks for the help and understanding my babble...look for more requests for help to counter my stupid ubuntu noob maneuvers!

---

### Post by robert shearer on 2008-10-23
Good to see it went so well for you :)

Doing and learning makes the 'buntu experience so rewarding.

Here's to many more happy experiments.

---

### Post by adept_king on 2008-10-23
i keep hearing about the "envy tool" but i installed envyng and rebooted and i see no envy tool. i dont know where it lives.  its not in the command line either. "unknown command" is what i get. 

how do you invoke envy?

--

after installing and uninstalling and re-installing, i found the program.

---

