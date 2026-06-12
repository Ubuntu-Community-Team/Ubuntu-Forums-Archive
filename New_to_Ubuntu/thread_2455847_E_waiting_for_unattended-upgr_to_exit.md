---
title: "E: waiting for unattended-upgr to exit"
date: 2020-12-29
forum: New to Ubuntu
---

### Post by ianp5a on 2020-12-29
My daughter can't install Zoom because of this error: 
> Unable to install Zoom. E: Could not get lock /var/dpkg/lock-frontend. It is held by process 6462 (unattended-upgr)
And then attempting to Update gets: >  Waiting for unattended-upgr to exit
All the online help we found suggests complicated IT solutions. But we need a user friendly solution. 

Searching shows this issue is not new or uncommon and is costing many people time and stress.
E.G. [https://ubuntuforums.org/showthread.php?t=2430061&highlight=unattended-upgr](https://ubuntuforums.org/showthread.php?t=2430061&highlight=unattended-upgr)

Does anybody know a user friendly solution? Thanks.
Ubuntu 20.04.1 LTS Gnome 3.36.8 X11 (Fresh install). See Screenshots below

---

### Post by howefield on 2020-12-29
Generally means that the operating system is updating itself and you would need to wait till it is finished before carrying out another software install.

Give it another go in 30 minutes or so.

---

### Post by ianp5a on 2020-12-29
Thanks. Sadly the error message did not say that. My daughter is talking of going back to Windows. Maybe changing the error message to add what you said would help people.

---

### Post by grahammechanical on 2020-12-29
Ubuntu will automatically check for updates as soon as it is loaded. We can regulate how often it checks by opening Software & Updates>Updates tab and changing the settings using the drop down menus. The options are daily; Every two days: Weekly; Every fortnight: Never. If we set it to never then the system will only be updated if we run these two commands

```
sudo apt update
sudo apt upgrade
```

That error message could also be due to the user shutting down or a disconnection from the ISP occurs stopping the update process before it is finished.

Regards.

---

### Post by ianp5a on 2020-12-30
> **grahammechanical said:**
> Ubuntu will automatically check for updates as soon as it is loaded. We can regulate how often it checks by opening Software & Updates>Updates tab and changing the settings using the drop down menus. The options are daily; Every two days: Weekly; Every fortnight: Never. If we set it to never then the system will only be updated if we run these two commands
```
sudo apt update
sudo apt upgrade
```
That error message could also be due to the user shutting down or a disconnection from the ISP occurs stopping the update process before it is finished.
Regards.

Thanks. I assume, once the Option is set to 'Daily' or whatever, and then the install error message occurs, switching it to 'Never' will not fix the problem right away? The install is still blocked. Is there no way forward at that point?

So the solution, as I see it, it to fix the error message. Currently the message is useless to non IT users. There is no suggestion of what to do. Either to wait for a given period or perform some command. There is no button to "Add to queue" as app stores sometimes do.

---

### Post by dino99 on 2020-12-30
From the icon menu, select "system monitor", then select the upgrade process to kill it.
Or follow the solutions given here: [https://unix.stackexchange.com/questions/374748/ubuntu-update-error-waiting-for-unattended-upgr-to-exit](https://unix.stackexchange.com/questions/374748/ubuntu-update-error-waiting-for-unattended-upgr-to-exit)

mainly:
> sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock

---

### Post by ajgreeny on 2020-12-30
In my opinion the best way to avoid this is to disable the unattended upgrades but set the system to notify you of all available upgrades daily and then carry out the upgrades at a time you choose, not one chosen by the system?

I always uninstall the package ***unattended upgrades*** and do them manually but daily.

---

### Post by ianp5a on 2020-12-30
> **dino99 said:**
> From the icon menu, select "system monitor", then select the upgrade process to kill it.
Or follow the solutions given here: [https://unix.stackexchange.com/questions/374748/ubuntu-update-error-waiting-for-unattended-upgr-to-exit](https://unix.stackexchange.com/questions/374748/ubuntu-update-error-waiting-for-unattended-upgr-to-exit)
mainly:
> sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
Is it safe to do those commands?  Maybe the error message should include a button to do it? So the user can continue and the problem is *really* solved.

---

### Post by mrdc76 on 2020-12-30
I would just reboot rather than run the rm's.

---

### Post by Impavidus on 2020-12-31
Processes can communicated with each other. It's fairly simple on Linux. However, to communicate, the processes (an their developers) have to agree on a communication protocol and as the number of possible interactions increases with the square of the number of processes, this quickly gets problematic. There will be bugs. So to keep things reliable, it's best to keep the number of interactions low. In this case, that means a simple lock. As long as one tool is working with software packages, a different tool is blocked. It's more reliable than giving Gnome Software (or whatever) a button to interupt unattended-upgrades. And there are many more tools dealing with package management.

---

### Post by ianp5a on 2020-12-31
> **Impavidus said:**
> Processes can communicated with each other. It's fairly simple on Linux. However, to communicate, the processes (an their developers) have to agree on a communication protocol and as the number of possible interactions increases with the square of the number of processes, this quickly gets problematic. There will be bugs. So to keep things reliable, it's best to keep the number of interactions low. In this case, that means a simple lock. As long as one tool is working with software packages, a different tool is blocked. It's more reliable than giving Gnome Software (or whatever) a button to interupt unattended-upgrades. And there are many more tools dealing with package management.

Thanks. But the **lock** is not the problem though is it? 

The error message referring to a lock is a *failure* in this case. Pushing the user to go online to find all sorts of over-complicated or non-recommended and maybe dangerous suggestions. Instead of giving information to help the user progress.

---

### Post by vmpx on 2021-10-13
I have changed the Unattended-Upgrade on Ubuntu from every day to 14 days:

/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/20auto-upgrades

```
APT::Periodic::Unattended-Upgrade "14";
```

"0": means is disabled

---

