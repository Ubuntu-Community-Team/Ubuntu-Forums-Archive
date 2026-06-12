---
title: "&quot;emulate&quot; dpkg-reconfigure via manual commands?"
date: 2010-01-26
forum: Packaging and Compiling Programs
---

### Post by florin on 2010-01-26
I'm having a very hard time trying to install MythTV from the Mythbuntu repos on a clean Ubuntu 9.04 system:

[http://ubuntuforums.org/showthread.php?t=1391334](http://ubuntuforums.org/showthread.php?t=1391334)

So, here's the thing: Instead of blindly poking around, I'd rather just have it done, no matter what. The problem is, I don't know what does dpkg-reconfigure do. So here's my question:

Given a package, how do I know what exactly "dpkg-reconfigure <package-name>" is doing, and how I can emulate all those actions manually? Basically, I suspect it's a bunch of scripts, so conceivably I could just run those manually in a terminal, no?

(If this was an RPM-based system, I would know what to do, but I'm fairly new to .deb so I need some directions.)

---

### Post by SevenMachines on 2010-01-27
i probably wouldnt recommend 'emulating' dpkg, nothing worse than a broken packaging system. that being said though!,

dpkg uses pre and post install/removal scripts found in /var/lib/dpkg/info (and sometimes some others too), for example <packagename>.postinst would be run after the package installs to configure it.
theres an [excellent explanation here]("http://women.debian.org/wiki/English/MaintainerScripts")

Best thing though is too see why dpkg installation is failing, its doing that because its meant to if it finds something out of place, it really is to protect you against having a package installed in a broken state, for your own protection, honest! You can get more information on whats going wrong by passing the debug option, run this command for more details on debug levels.
$ dpkg --debug help

If the scripts used by the package in /var/lib/dpkg/info are shell scripts (they usually are) you can also see the commands being run by dpkg by adding the set -x option to the top of the script

---

### Post by EliasKesh on 2010-11-11
Is there anyway to see the errors that dpkg-reconfigure generated ?
dpkg has a --debug option but not a reconfigure option and dpkg-reconfigure does not have a --debug option .

---

