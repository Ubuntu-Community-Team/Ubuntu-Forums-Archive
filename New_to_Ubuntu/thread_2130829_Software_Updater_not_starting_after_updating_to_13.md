---
title: "Software Updater not starting after updating to 13.04"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by SamerBerjawi on 2013-03-30
Hello guys,
yesterday I upgraded my Ubuntu from 12.10 to 13.04 using 
```
sudo do-release-upgrade -d
```
during the upgrade, not everything was upgraded, so I restarted the computer, launched software updater, it told me I have to update through the terminal using 
```
sudo apt-get install -f
```
the update went on and then I had to reboot the computer, after that, the software updater doesn't start anymore, when I click on it in the launcher it glows but nothing else happen. My sound driver is also gone, probably because some updates should be pending!

I'm still new to Ubuntu, so I'm trying to teach myself out, but I need your help with this. Can you please help solve this out. 
Thank you in advance

---

### Post by Bashing-om on 2013-03-30
SamerBerjawi; Hi !
The base of this operation is in ubuntu's package manager's error reports.
Begin by cleaning up the system's config files and updating everything.
This is oldfred's methology to do so:

```

#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```
When all this is done/completed then do once again:
```
sudo apt-get update
sudo apt-get upgrade
``` and if there are any errors post the output for examination.[INDENT=4]
just try'n to help

[/INDENT]

---

### Post by grahammechanical on 2013-03-30
You can open Ubuntu Software Centre and search for Software Updater and remove (un-install) it and then re-install it.

The second command that you used was to fix broken packages. You may also need to run ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```

Regards.

---

### Post by SamerBerjawi on 2013-03-30
> **Bashing-om said:**
> SamerBerjawi; Hi !
The base of this operation is in ubuntu's package manager's error reports.
Begin by cleaning up the system's config files and updating everything.
This is oldfred's methology to do so:

```

#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```
When all this is done/completed then do once again:
```
sudo apt-get update
sudo apt-get upgrade
``` and if there are any errors post the output for examination.[INDENT=4]
just try'n to help

[/INDENT]

that did the job. thank you so much Sir

---

### Post by Bashing-om on 2013-03-30
SamerBerjawi;
Great ! Please mark the thread as solved:
interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=3]
just pass'n it on

[/INDENT]

---

