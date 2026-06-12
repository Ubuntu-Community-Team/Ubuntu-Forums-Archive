---
title: "Compiz problems"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by ulfuric on 2013-04-08
I'm fairly inexperienced with Ubuntu and I'm having trouble with Compiz. I went to the software center and installed Compiz config settigs manager, but when I go to applications its not there. I tried to remove it so I could try to reinstall but it fails to remove it and I get this:

installArchives() failed: dpkg: error processing compizconfig-settings-manager (--remove): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting a removal. 
Errors were encountered while processing: 
 compizconfig-settings-manager 
Error in function:  

  Not sure where to go from here, like i said I'm a noob, but any help would be appreciated!

 Oh and I'm running Ubuntu 12.10

---

### Post by Max Blyss on 2013-04-09
Try 'sudo apt-get -f install' ...  It's magically fixed a good few problems for me.

---

### Post by deadflowr on 2013-04-09
Hm, weird that that program is borking for you.
follow Max Blyss' suggestion to fix the broken packages and try this

First run an update
```
sudo apt-get update
```
so as to get the your system all updated with the repos.
Then try to do a reinstall
```
sudo apt-get install --reinstall compizconfig-settings-manager
```
Hopefully this will reinstall the program.

Then first try and launch the program.
Stay in the terminal and type ccsm.
At the very lest it should give out any errors or problems the program might be having.

If no errors happen and it launched, then the programs working.

If it doesn't work, then try purging it.

---

