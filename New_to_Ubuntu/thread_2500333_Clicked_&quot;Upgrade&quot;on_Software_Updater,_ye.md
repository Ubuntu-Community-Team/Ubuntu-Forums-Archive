---
title: "Clicked &quot;Upgrade&quot;on Software Updater, yet button does nothing..."
date: 2024-08-30
forum: New to Ubuntu
---

### Post by yatski on 2024-08-30
Software Updater prompted me that there is new LTS version available...(from 22.04 to 24.04.1)
Yet when I click "Upgrade"-button, nothing happens.

This is old Sony Vaio that has noveau driver. (used to have nvidia but there was compatibility problems)

Already tried "sudo apt upgrade" without real results.
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libargon2-1:i386 libcryptsetup12:i386 libdevmapper1.02.1:i386 libflashrom1
  libftdi1-2 libip4tc2:i386 libjson-c5:i386 libkmod2:i386 libllvm13
  libllvm13:i386 libseccomp2:i386 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  pepperflashplugin-nonfree
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  gcc-10-base gcc-10-base:i386 python3-update-manager shim-signed
  ubuntu-advantage-tools ubuntu-pro-client ubuntu-pro-client-l10n
  update-manager update-manager-core
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```


(Problem in this is it prevents me updating anything else...)

---

### Post by ajgreeny on 2024-08-30
I do not use software-updater but I think it simply updates any packages installed to the most recent version of that package for the OS version running, in your case 22.04.  It does not update from one OS version to the next which is carried out differently.

I have never updated my OS version but always clean installed tyh enew version so will leave it to others to tell you what is the best method to use.

---

### Post by Dennis N on 2024-08-30
Failure to start the upgrade can be caused by held packages. I would check for any held packages by running:
```
apt-mark showhold
``` 
in the terminal. If there is any output, you have to remove the hold on each package shown:
```
sudo apt-mark unhold package-name
```
and then run: 
```
sudo apt upgrade
``` 
again.
Also, to clean things up, I would also remove the packages that are no longer required on your system with:
```
sudo apt autoremove
```

Then start Software Updater and try the upgrade button again.

---

### Post by yatski on 2024-08-30
Command
```
apt-mark showhold
```
produces no results. Is this intended?

---

### Post by Dennis N on 2024-08-30
> **yatski said:**
> Command
```
apt-mark showhold
```
produces no results. Is this intended?
if there is no output, there are no held packages. So held packages are not the problem.
Were you shown a message like one of the attached images after updating? If so, and the Upgrade button still doesn't work, I am not sure of the cause, but I suspect there is some issue with one or more of the packages that have been held back.

You may get more information by running:
```
sudo do-release-upgrade
```
in the terminal. Try that.

---

### Post by yatski on 2024-08-30
I tried

```
heta@heta-vaio:~$ sudo do-release-upgrade
[sudo] password for heta: 
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
heta@heta-vaio:~$ 
```

I was shown message similar to the first picture, but there wasn't message similar to second picture. (There was no second dialog box at all.)

---

### Post by Dennis N on 2024-08-30
Ok, Instead of upgrading 22.04 with sudo apt upgrade, I would try updating with:
```
sudo apt full-upgrade
```

The difference between 'upgrade' and 'full-upgrade' options is that the latter can remove packages if needed to upgrade the system:

here is the description of this option from manpage of apt:
> full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.


---

### Post by yatski on 2024-08-30
> **Dennis N said:**
> Ok, Instead of upgrading 22.04 with sudo apt upgrade, I would try updating with:
```
sudo apt full-upgrade
```

Ran command, updated packages and tried Software Updater.... Still no second dialog box.

Maybe my laptop is too old?

---

### Post by Dennis N on 2024-08-30
After running **sudo apt full-upgrade**, did you try
```
sudo do-release-upgrade
```
again?

---

### Post by yatski on 2024-08-30
Got this:

```
heta@heta-vaio:~$ sudo apt full-upgrade
[sudo] password for heta: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libargon2-1:i386 libcryptsetup12:i386 libdevmapper1.02.1:i386 libflashrom1
  libftdi1-2 libip4tc2:i386 libjson-c5:i386 libkmod2:i386 libllvm13
  libllvm13:i386 libseccomp2:i386 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  pepperflashplugin-nonfree
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  gcc-10-base gcc-10-base:i386 python3-update-manager shim-signed
  update-manager update-manager-core
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
heta@heta-vaio:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
heta@heta-vaio:~$ 
```

---

### Post by Dennis N on 2024-08-30
Now it shows 6 not upgraded, while before there were 9 not upgraded. I would run **sudo apt autoremove** just to clean things up a bit. Then try **sudo do-release-upgrade** once more.

---

### Post by yatski on 2024-08-30
Ran commands and got:

```
heta@heta-vaio:~$ sudo apt autoremove
[sudo] password for heta: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  libargon2-1:i386 libcryptsetup12:i386 libdevmapper1.02.1:i386 libflashrom1
  libftdi1-2 libip4tc2:i386 libjson-c5:i386 libkmod2:i386 libllvm13
  libllvm13:i386 libseccomp2:i386 libwpe-1.0-1 libwpebackend-fdo-1.0-1
  pepperflashplugin-nonfree
0 upgraded, 0 newly installed, 14 to remove and 6 not upgraded.
After this operation, 197 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 326427 files and directories currently installed.)
Removing libcryptsetup12:i386 (2:2.4.3-1ubuntu1.2) ...
Removing libargon2-1:i386 (0~20171227-0.3) ...
Removing libdevmapper1.02.1:i386 (2:1.02.175-2.1ubuntu4) ...
Removing libflashrom1:amd64 (1.2-5build1) ...
Removing libftdi1-2:amd64 (1.5-5build3) ...
Removing libip4tc2:i386 (1.8.7-1ubuntu5.2) ...
Removing libjson-c5:i386 (0.15-3~ubuntu1.22.04.2) ...
Removing libkmod2:i386 (29-1ubuntu1) ...
Removing libllvm13:amd64 (1:13.0.1-2ubuntu2.2) ...
Removing libllvm13:i386 (1:13.0.1-2ubuntu2.2) ...
Removing libseccomp2:i386 (2.5.3-2ubuntu2) ...
Removing libwpebackend-fdo-1.0-1:amd64 (1.14.2-0ubuntu0.22.04.1) ...
Removing libwpe-1.0-1:amd64 (1.14.0-0ubuntu0.22.04.1) ...
Removing pepperflashplugin-nonfree (1.8.8~ubuntu20.04.1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.8) ...
heta@heta-vaio:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.
heta@heta-vaio:~$ 
```

....Maybe upgrade and packages are phased and isn't my turn yet?

---

### Post by Dennis N on 2024-08-30
I think (but don't know for sure) that one of the "held back" packages is preventing the upgrade. Once I had one "held back" package stopping an upgrade to the next version. I just removed it, upgraded, and reinstalled it again after the upgrade. 

The only things in your list of 6 that to me look safe to remove are **gcc-10-base** and **gcc-10-base:i386**. Those are compiler related, and are not installed in my Ubuntu 22.04, so they are optional. If it were me, I would remove them, then run **sudo apt full-upgrade** and **sudo do-release-upgrade** again. The other 4 kept-back files are important system files - do not remove those. 

Also, I would definitely be sure all my important files are backed up before doing the above suggestion or anything more. You might have to do a new install if all else fails.

---

### Post by yatski on 2024-08-30
> **Dennis N said:**
> 
Also, I would definitely be sure all my important files are backed up before doing the above suggestion or anything more. You might have to do a new install if all else fails.

I'm currently downloading newest version Ubuntu and plan to create bootable USB stick, just to be sure.
I will follow your instructions and see what happens.

---

### Post by yatski on 2024-08-30
It was "gcc-10-base:i386" that held whole thing back!

```

heta@heta-vaio:~$ sudo do-release-upgrade
Checking for a new Ubuntu release

= Welcome to Ubuntu 24.04 LTS 'Noble Numbat' =

The Ubuntu team is proud to announce Ubuntu 24.04 LTS 'Noble Numbat'.

To see what's new in this release, visit:
  https://wiki.ubuntu.com/NobleNumbat/ReleaseNotes

Ubuntu is a Linux distribution for your desktop or server, with a fast
and easy install, regular releases, a tight selection of excellent
applications installed by default, and almost any other software you
can imagine available through the network.

We hope you enjoy Ubuntu.

== Feedback and Helping ==

If you would like to help shape Ubuntu, take a look at the list of
ways you can participate at

  http://www.ubuntu.com/community/participate/

Your comments, bug reports, patches and suggestions will help ensure
that our next release is the best release of Ubuntu ever.  If you feel
that you have found a bug please read:

  http://help.ubuntu.com/community/ReportingBugs

Then report bugs using apport in Ubuntu.  For example:

  ubuntu-bug linux

will open a bug report in Launchpad regarding the linux package.

If you have a question, or if you think you may have found a bug but
aren't sure, first try asking on the #ubuntu or #ubuntu-bugs IRC
channels on Libera.Chat, on the Ubuntu Users mailing list, or on the
Ubuntu forums:

  http://help.ubuntu.com/community/InternetRelayChat
  http://lists.ubuntu.com/mailman/listinfo/ubuntu-users
  http://www.ubuntuforums.org/


== More Information ==

You can find out more about Ubuntu on our website, IRC channel and wiki.
If you're new to Ubuntu, please visit:

  http://www.ubuntu.com/


To sign up for future Ubuntu announcements, please subscribe to Ubuntu's
very low volume announcement list at:

  http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce
```

---

### Post by Dennis N on 2024-08-30
That must be a relief. You should now be able to upgrade to 24.04 either with Software Updater OR use do-release-upgrade in the terminal. Post again if it is successful. Upgrading in place saves time versus a new install with all the setup and personalizing you have to do afterwards.

---

### Post by yatski on 2024-08-30
Well, after much fighting and blundering(I won't even start to explain) I... I think my system is okay.(meh, I was wrong. Can't start LibreOffice... See [https://ubuntuforums.org/showthread.php?t=2500350](https://ubuntuforums.org/showthread.php?t=2500350))


I'm so grateful for your patience.

(I will mark this thread as solved.)

---

