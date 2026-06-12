---
title: "Not updating the system"
date: 2021-07-20
forum: New to Ubuntu
---

### Post by amirabbasjadidi on 2021-07-20
Hello with the following command
```
[COLOR=#000000][FONT=&quot]sudo apt full-upgrade[/FONT][/COLOR]
```
I was trying to update the system, but I get the following error:
```
[COLOR=#000000][FONT=&quot]E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).[/FONT][/COLOR]
```
please guide me.Thank

---

### Post by ActionParsnip on 2021-07-20
What is the output of
```

sudo apt-get -f install
lsb_release -a
uname -a

```
Thanks

---

### Post by TheFu on 2021-07-20
Well, the error provides the possible solution.  Did you try it?
> E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

If not, try it.

If you haven't run **sudo apt update** today, try that before the next commands.
If you have ever installed any .deb packages manually, those are probably the issue.  Remove those. Do the full-upgrade, the find newer versions of the manually installed .deb files and install them again.  Plan to do this at least monthly.
If neither of the above things apply, then it is possible that someone marked a few packages to "hold" inside APT.  Figure out which packages are marked to be held. I'd use apt-mark to get a list of held packages, then remove the "holds" and start over with the update/full-upgrade effort again.

---

### Post by grahammechanical on 2021-07-20
I would like to quote the apt man page

> **upgrade** (apt-get(8))
           upgrade is used to install available upgrades of all packages currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to satisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the removal of an installed package the upgrade for this package isn't performed.

       **full-upgrade** (apt-get(8))
           full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the
           system as a whole. 

The removal of currently installed packages by apt full-upgrade could be the reason for other packages having dependency issues. For myself, I never run full-upgrade. As for those who think that dist-upgrade will upgrade one version of Ubuntu to a newer version, please note what the apt-get man page says:

> [B]dist-upgrade
[/B]           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

The command dist-upgrade has been know to break the OS. Especially on the development version of Ubuntu. Update manager calls it Partial Upgrade.

Regards

---

### Post by TheFu on 2021-07-20
The confusion about dist-upgrade is because that is how Debian does their upgrades, but manual changes to the APT files are necessary to move from release to release in Debian.  Ubuntu and Debian are slightly different in the package management and Ubuntu has been pushing snaps (too hard) to completely diverge from the APT management system that many people count on and love.

If you don't plan to migrate from 20.04 --> 22.04, then there is little reason to use full-upgrade.  Last time I looked, full-upgrade == dist-upgrade in the apt-get manpage with the default APT settings.  There are all sorts of preferences for APT that most people never touch, but which can have profound impacts.

I cannot recall a full-upgrade breaking my system. Perhaps I'm just lucky.

From scripts, apt-get is preferred.
From a shell, manually, apt is preferred.  The verbs for each usually are the same and apt-get options can be passed to apt and will passed into apt-get - iff that verb is handled by apt-get. Most are.  But apt will do some extra stuff like removing older kernels.

I've been using full-upgrade for at least 5 yrs, perhaps 10 yrs.  My systems try to use Canonical Repos only, with just a few exception.  About a year before I plan a distro upgrade, I'll install the HWE to learn about any kernel issues BEFORE moving to the next release.  This isn't strictly necessary, but I prefer for problems to be small, a little at a time, not huge all at once.  So, my 18.04 servers are running the HWE kernel (20.04 kernel).  But my 20.04 system are on the original kernel and probably will be until 24.04 is released.

BTW, in the late 1990s, I was running RHAT systems and frequently got into "RPM-hell" where a system couldn't be patched.  Back then, there was lots of software that didn't exist in the repos so we were always building important programs. Those programs required manual dependency solutions, often which conflicted with the OS version of different libraries.  It was a pain, but we'd usually create a startup-script for each of those programs to restrict any interactions of libraries to only the program involved and not the wider OS by controlling the LD_LIBRARY_PATH and other environment variables just for that program. 

All of those things taught me to be cautious about mixing dependencies.  There is a thing called "APT-hell". It is exactly the same as RPM-hell.  I've never been in APT-hell that couldn't be corrected.  It is best to avoid it completely by using the distro repositories only, especially for non-experts.  Of course, that isn't always possible.

---

### Post by rsteinmetz70112 on 2021-07-20
If this were my computer I'd run the following commands and see what they report; 

Open a terminal <cntrl alt T>
```
sudo apt install -f
sudo dpkg --configure -a
```

apt is a newer command than apt-get but does pretty much everything apt-get does and a few more things but there are some differences (for example apt uses full-upgrade vs. apt-get dist-upgrade - that one always confused me).
If the two commands above produce errors deal with those. Feel free tp post the output. Please cut and past the text and use code tags.

When they run without error run this commands;

```
sudo apt update
sudo apt upgrade
sudo autoremove
```

If you make it through them without errors you're good.

---

