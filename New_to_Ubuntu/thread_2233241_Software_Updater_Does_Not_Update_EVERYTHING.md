---
title: "Software Updater Does Not Update EVERYTHING"
date: 2014-07-07
forum: New to Ubuntu
---

### Post by lhb1142 on 2014-07-07
For Whatever It's Worth:

I have noticed on our seven (7) computers, three running Ubuntu Studio, two running Xubuntu, and two running Lubuntu, all 14.04, that the Software Updater, which we run manually every morning (before we do anything else), does NOT update everything.

If, after we run the Software Updater, we open the Synaptic Package Manager (which must be optionally installed nowadays) and Reload & Mark All Upgrades, there wil often be many programs which were not included in the Software Updater upgrades.

I do not know why this is happening but my "solution" is to not use the Software Updater (except as a check) but update (daily) our computers using the Synaptic Package Manager.

The only problem with that is that the Synaptic Package Manager does not show when the computer needs to be restarted in order to install all of the updates (this generally occurs when new kernel firmware is installed).

So every day, my wife and I now run Synaptic Package Manager first and install all the updates and then we run the Software Updater (which will inform as to the need to restart the computer if that is necessary).

It's a bit of a "pain" but is the only solution I have been able to come up with. I hope the "powers-that-be" are able to soon correct the Software Updater so that this anomaly will no longer exist.

I hope that this has been of some help to readers.

P.S. If you are having trouble running the Software Updater or encountering the same problem I have noted above, install Synaptic Package Manager. Enter the Ubuntu Software Center, search for Synaptic, and then install the Synaptic Package Manager. (If you prefer using the Terminal, enter < sudo apt-get install synaptic >.)

P.P.S. If you have ClamAV installed, you must run (in the Terminal) < sudo freshclam > to update the signatures; neither Synaptic nor Software Updater will do this.

---

### Post by philinux on 2014-07-07
This has been the normal behaviour since version 13.04.

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

To opt out - from the blog mentioned at bottom of article.
> Who is participating?

Users of Ubuntu 13.04 who install updates with update-manager are automatically participating in this process. For every package, in -updates, update-manager will generate a random number and if that number is less than the Phased-Update-Percentage the package will be installed. One can opt out of the Phased Update process by adding ‘Update-Manager::Never-Include-Phased-Updates “True”;’ to the configuration file “/etc/apt/apt.conf”.

Rationale. [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Anyone not liking this can just use synaptic or the terminal to upgrade. Personally I'm happy to have a more stable system.

---

### Post by lhb1142 on 2014-07-08
> **philinux said:**
> This has been the normal behaviour since version 13.04.

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

To opt out - from the blog mentioned at bottom of article.


Rationale. [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Anyone not liking this can just use synaptic or the terminal to upgrade. Personally I'm happy to have a more stable system.

Thank you for writing with this information of which I was unaware.

---

### Post by pretty_whistle on 2014-07-08
> **philinux said:**
> This has been the normal behaviour since version 13.04.

[http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/08/phased-updates-to-start-rolling-out-for-ubuntu-13-04)

To opt out - from the blog mentioned at bottom of article.


Rationale. [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Anyone not liking this can just use synaptic or the terminal to upgrade. Personally I'm happy to have a more stable system.
IMO this "process" is weird.

So, technically, I should run update manager a few times a day to be sure it got everything.  That seems to be a lot of trouble so I wont.

Also IMO, synaptic and the terminal wont tell me if a restart is needed so this is weird too.

So, the whole thing is weird IMO.  :)

---

