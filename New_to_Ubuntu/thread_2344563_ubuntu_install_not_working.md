---
title: "ubuntu install not working"
date: 2016-11-26
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2016-11-26
hello , 

I cant install anything on ubuntu it says the following

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension


what could be the problem?

---

### Post by oldrocker99 on 2016-11-26
Try this:```
sudo mv  /etc/apt/apt.conf.d/20auto-upgrades.ucf-dist  /etc/apt/apt.conf.d/20auto-upgrades
```

The **mv** command moves *and* renames files. The ".ucf-dist" was indeed an invalid filename extension. Renaming it should solve that problem. Let us know if it worked.

---

### Post by weirdygeekpsych on 2016-11-26
I run your above command, it prompted for password and I got my terminal back ., when I checked into the folder it was renamed. so I tried to install software, but it says

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by Bucky Ball on 2016-11-27
Yea, you have a package manager open and trying to run these commands in the terminal by the looks. See this:

```
E: Unable to lock the administration directory (/var/lib/dpkg/), ***is another process using it?***
```

There is another process, i.e. a package manager, open. Close everything and just run the command in a terminal. 

So, the unattended updates is having issues at the moment. Known issue and you are not the only one with it. Your error message is nothing to worry about. Ignore unless you really want to dig into. It will fix itself eventually. Basically, automatic updates is broken and if you find a fix, congratulations as no-one else seems to be able to so the community will be thrilled.

As for not being able to install anything. I see no issue whatsoever with what you've posted which looks like you've tried to run a regular upgrade, not install anything. You've run 'sudo apt update' (which ALWAYS should come before the next command you ran) then 'sudo apt full-upgrade' or possibly 'sudo apt-get dist-upgrade' and there is nothing to upgrade.

The title of your thread alludes to the fact that you can't install anything, but you aren't trying to install anything from what you've posted. Do you have a problem installing things from the repositories as well, and I'm talking installing an application, not doing an update?

Try this:

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

Does the last command show any upgrades now? If not it should look exactly the same as what you posted in your first post and your machine is fully up to date.

PS: Please use code tags for terminal output. See the green link in the first line in my signature at the bottom of this post. Thanks.

---

### Post by weirdygeekpsych on 2016-11-27
thanks , now everything is fine, my machine is up-to date

---

