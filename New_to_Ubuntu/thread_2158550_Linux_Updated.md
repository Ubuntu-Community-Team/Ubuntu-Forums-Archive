---
title: "Linux Updated?"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-06-29
How can I tell if Ubuntu is up to date, or how to force an update, instead of waiting for it to check?
Ubuntu 12.04
Thanks for the help

---

### Post by grahammechanical on 2013-06-29
It is hard to remember for me as I stopped using 12.04 when development work started on 12.10. Do you not have an option in the power/cog menu to run system updater? That action runs a check for updates. I think. also if you select About this Computer that will open the Details page of System Settings and there should be a button there labelled Check. I think. It my start a check for update after a few seconds even if you do not click the button. Or you could open a terminal and type

```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```

In System Settings you can open Sofware Sources and adjust the setting for when Ubuntu checks for updates. And leave it for the OS to do what you have told it to do.

Regards.

---

### Post by deadflowr on 2013-06-29
To force an update through a gui app in precise, open the update manager and click on the "check" box.
This will run the update command, and refresh the package listings.
In later versions like quantal or raring, the gui app switched over from update manager to software updater, which automatically refreshes the listing when the updater is launched.

---

### Post by coldraven on 2013-06-29
As mentioned above, the cog/power icon has "About this computer", the button in the bottom right changes after a few seconds to "Install Updates".
Or type "up" in the dash (Winkey+A) for the Software updater.

---

### Post by GUZZLR on 2013-06-29
Hello All,
How do I force 13.04 to check for updates, instead of having to wait for it to check daily automatically?
Thanks for the help!

---

### Post by Bashing-om on 2013-06-29
GUZZLR; Hi !

I prefer to check and update from the command line.
Terminal codes:
```
sudo apt-get update
sudo apt-get upgrade
```

no fuss, no muss, and one see all that takes place, and error reports.

[INDENT][INDENT]no place like home[/INDENT][/INDENT]

---

### Post by kostkon on 2013-06-29
Open the software updater and press the... Check button.

---

### Post by deadflowr on 2013-06-29
Once you open the software updater, it automatically runs an update.
This is oppose to the update manager in 12.04, where you had to click on the check button.
Running the apt-get commands, does the same thing.
If no updates come up, then the system is up to date.
If something bothers you, running the apt-get update command should either alleviate the concern or point out any problems.

---

### Post by newb85 on 2013-06-30
Just to clarify
```
 sudo apt-get update 
```
Checks for updates, and
```
 sudo apt-get upgrade 
```
Installs them.

---

### Post by oldos2er on 2013-06-30
Threads merged. Please don't start more than one thread for the same or similar questions, it's confusing and it dilutes community effort.

---

### Post by Cheesemill on 2013-06-30
Just to clarify things a bit, performing a 'sudo apt-get upgrade' may not bring your system completely up to date. The command will only update packages that are already on your system, it won't install any new packages that are needed to bring your system up to date (kernels being the most obvious example).

To make sure that your system is fully up to date you should run...
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by GUZZLR on 2013-06-30
```
performing a 'sudo apt-get upgrade' may not bring your system completely up to date.
```

Got it...thanks for the help, this seems to be the alternative to opening update manger.

---

### Post by Zill on 2013-06-30
sudo apt-get dist-upgrade should, however, only be run with caution.  From "man apt-get"...
> **upgrade** is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; **[COLOR="#FF0000"]under no circumstances are currently installed packages removed[/COLOR]**, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be performed first so that apt-get knows that new versions of packages are available.
> **dist-upgrade** in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. So, **[COLOR="#FF0000"]dist-upgrade command may remove some packages.[/COLOR]** The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.
*Always* check the proposed changes when running "upgrade" and, especially, "dist-upgrade" to make sure you are totally happy about what will be upgraded and, particularly, removed.

---

