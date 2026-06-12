---
title: "Massive error in Software Center"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by sombranegra79 on 2011-11-12
I'm using Ubuntu 11.10 and ran into a massive problem as I was trying to install the anonymity software JonDo. I am not familiar with Ubuntu, having only used it for a few months on one of two computers I own. I downloaded the software repository for JonDo and ran it using Ubuntu Software Center. The Software Center, which had already been slow to load, lagged unacceptably after I clicked "install". The "install" button then became "installing" with the accompanying progress bar, but then became "install" again. So I pressed "install" again, after which the "installing" tab appeared. I clicked on that and it showed me two copies of JonDo being installed, one queued up after the other. I canceled the second, but after returning to the previous tab, it appeared that **both** copies had stopped installing. I assumed the installation had failed and restarted my computer in the hope that the Software Center would run more quickly.

After rebooting I noticed that JonDo had in fact installed, which was surprising. It started up fine but later froze. I rebooted again to make JonDo go away. This time after rebooting I got an error on the top taskbar, saying the following:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Unknown Error: '<type 'exceptions. SystemError'>' (E:The package jondo needs to be reinstalled, but I can't find an archive for it.)'. This usually means that your installed packages have unmet dependencies"

The Package Manager is not working at all and gives me the same error message. The Update Manager says "not all updates can be installed" and offers me a "partial upgrade", after which it gives me the following message:

"Remove package in bad state: The package 'jondo' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?"

I have clicked "yes" several times, but the Update Manager does nothing and the corrupted JonDo software remains partially installed, rendering the Package Manager inoperative. I have tried to use the Software Center to uninstall JonDo, but when I open up the .deb software repository, I only get a "reinstall" button and no "remove" button, even though it tells me it's "installed". JonDo is also not listed under "history". I can find no way to remove the file. Can anyone suggest any solutions at all?

---

### Post by LinuxFan999 on 2011-11-12
Open the terminal and type this:
 
```
sudo apt-get purge jondo
```

---

### Post by sombranegra79 on 2011-11-12
> **LinuxFan999 said:**
> Open the terminal and type this:
 
```
sudo apt-get purge jondo
```

It gives me the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package jondo needs to be reinstalled, but I can't find an archive for it

---

### Post by LinuxFan999 on 2011-11-12
It looks like someting in your system is broken. I hate to say this, but it looks like you will have to reinstall Ubuntu. There are other options for anonymity, like Tor.
Here is the link to the Tor project: [http://www.torproject.org](http://www.torproject.org)

---

### Post by bapoumba on 2011-11-12
Please try :
```
sudo dpkg --remove --force-remove-reinstreq jondo
```

---

### Post by sombranegra79 on 2011-11-12
> **bapoumba said:**
> Please try :
```
sudo dpkg --remove --force-remove-reinstreq jondo
```

Works perfectly. Thanks!

---

### Post by bapoumba on 2011-11-13
> **sombranegra79 said:**
> Works perfectly. Thanks!

No problem, you are welcome :)

---

