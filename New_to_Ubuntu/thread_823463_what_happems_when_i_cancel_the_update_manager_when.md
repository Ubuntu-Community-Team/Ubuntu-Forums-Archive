---
title: "what happems when i cancel the update manager when its halfway done?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by guest_user on 2008-06-09
will it resume the next time i start it up? or would it start anew and leave extra unwanted files on my computer?

---

### Post by Joeb454 on 2008-06-09
It wouldn't start anew, but it may spit out an error, that tells you to run ```
sudo dpkg --configure -a
``` From a terminal :)

---

### Post by kpkeerthi on 2008-06-09
The update manager downloads .deb files from the repositories in the internet. All the downloaded deb files are stored in /var/cache/apt/archives folder. 
Cancelling the update manager is safe and it only downloads the files that are NOT already downloaded to the above folder unless the file on the server is 'latest' (by version# and timestamp)

---

### Post by kpkeerthi on 2008-06-09
> **Joeb454 said:**
> It wouldn't start anew, but it may spit out an error, that tells you to run ```
sudo dpkg --configure -a
``` From a terminal :)

This is not needed if you cancel the update by clicking on the 'Cancel' button when the updates are downloading. 

But you may have to fix broken packages using **dpkg --configure -a** if the update manager is forced to stop abruptly when it performs package installation.

---

### Post by SunnyRabbiera on 2008-06-09
just be careful when doing this, the update manger in ubuntu is smart, but if you cut it during a kernel update you will face issues.

---

### Post by Joeb454 on 2008-06-09
That's why I said it "**may** spit out an error" :)

---

### Post by guest_user on 2008-06-09
what does sudo "dpkg --configure -a" do?

---

### Post by SunnyRabbiera on 2008-06-09
> **guest_user said:**
> what does sudo "dpkg --configure -a" do?

it basically fixes a common issue that comes up every so often, sometimes updates can go a little wonky and a error comes up asking to do sudo dpkg --configure -a in a terminal

---

### Post by kpkeerthi on 2008-06-09
> **guest_user said:**
> what does sudo "dpkg --configure -a" do?

Think of it as a magic code that scans through the installed packages and fixes them by downloading (if required) the missing pieces. 

Basically it restores the integrity of the installed packages. 

For more information, type ```
man dpkg
``` in a terminal window.

---

### Post by Joeb454 on 2008-06-09
Technically it doesn't ask you to run it as sudo - which is where people get confused. Anyway, I digress :)

SunnyRaberia is right - it fixes any packages that get broken for any reason :)

---

### Post by guest_user on 2008-06-09
so after that command, does it mean i wont have any more unwanted and uneeded packages on my system?

---

### Post by Joeb454 on 2008-06-09
If you wanted to remove un-needed packages you could run ```
sudo apt-get autoremove
``` :)

---

### Post by guest_user on 2008-06-09
what about stopping the synaptic package manager or with add/remove halfway through with cancel? Does it work the same as with the updater software?

btw i lost connection while reloading the package lists and there were some entries which said "hit", what do i do now?

---

### Post by SunnyRabbiera on 2008-06-09
> **guest_user said:**
> what about stopping the synaptic package manager or with add/remove halfway through with cancel? Does it work the same as with the updater software?

yes, as synaptic and add/remove has this functionality.
Now its not like you cant cancel a update or anything, its just not advised.

---

### Post by guest_user on 2008-06-09
i lost connection while reloading the package lists and there were some entries which said "hit", what do i do now? can i just reload the package lists again or do i have to do dpkg --configure -a?

---

### Post by kpkeerthi on 2008-06-10
> **guest_user said:**
> i lost connection while reloading the package lists and there were some entries which said "hit", what do i do now? can i just reload the package lists again or do i have to do dpkg --configure -a?

Just reload the list. dpkg --configure -a is not required unless synaptic/update manager/apt-get/aptitude asks you to do so **specifically**.

An easy way to upgrade from command line is
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by tvillamil on 2010-01-19
I'm attaching to this thread because I am having issues with Update Manager after cancelling an Update.

The Update Manager shows a number of required updates, but when I click on Install Updates... Nothing happens

When I launch sudo dpkg --configure -a in a terminal I receive the following message:

dpkg: status database area is locked by another process.

On another forum i saw something regarding a gksu.lock file that needed to be deleted... but I can't find any such file....

If I try to launch update manager via a terminal:  sudo update-manager I get the following error:

requiredDownload could not be calculated: E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (1), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (1)

Anyone have any ideas... I'm two clicks short of re-installing from a backup.  :(

Thanks,

---

### Post by louieb on 2010-01-19
> **tvillamil said:**
> 

When I launch sudo dpkg --configure -a in a terminal I receive the following message:

dpkg: status database area is locked by another process.


Usually you get this message if you have update-manager or synaptic open at the time. - Only one update process is allowed to run.

---

