---
title: "&quot;Update&quot; vs &quot;Upgrade&quot;?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by TNFrank on 2013-06-06
Ok, so I've used "sudo apt-get update" to keep my OS updated but what would "sudo apt-get upgrade" do?  Would it upgrade me from 12.04 to 13.04 or does it do about the same as update? Thanks.

---

### Post by Shrek01 on 2013-06-06
In simple:
Update is to get the list of the latest software available, which you can then search and show descriptions (apt-cache search <key words>, and apt-cache show <package>)
Upgrade is to **install** the latest versions of the software already installed.

---

### Post by matt_symes on 2013-06-06
Hi

> **TNFrank said:**
> Ok, so I've used "sudo apt-get update" to keep my OS updated but what would "sudo apt-get upgrade" do? .

That's not quite right. Explained below

> Would it upgrade me from 12.04 to 13.04 or does it do about the same as update? Thanks

No.

```
sudo apt-get update 
```

will update the package list so that the package manager knows which packages are out of date/missing or need upgrading.

```
sudo apt-get upgrade
```

will actually upgrade the packages that the update command has found to be out of date.

To throw confusion into the mix, there is also 

```
sudo apt-get dist-upgrade
```

That will also upgrade the packages, taking into account dependencies. It will remove packages if they conflict etc.

To upgrade 12.04->12.10 and from one version to another your looking at

```
sudo do-release-upgrade
```

You can upgrade from lts (lts = long term support) release to lts release (8.04 -> 10.04 -> 12.04->14.04 (when it comes out)), otherwise it's release to release...

12.04->12.10->13.04->13.10->14.04.

Kind regards

---

### Post by TNFrank on 2013-06-06
Ahh, so upgrade is the more powerful command that'll get things updated and all shinny new, thanks.   I just want to keep my system set up with all the newest updates, upgrades and patches so it'll run well. Thanks for the quick respons guys. ;)

---

### Post by coffeecat on 2013-06-06
> **TNFrank said:**
> Ahh, so upgrade is the more powerful command

No, not more powerful - different. Upgrade won't do anything unless you run update first.

---

### Post by TNFrank on 2013-06-06
Ok, so I just did a "sudo apt-get update; sudo apt-get dist-upgrade" to get the latest/greatest and it seemed to work fine. Since 12.04 is Long Term Support I figure they'll be coming out with all kinds of updates and upgrades for bugs that are found, ect. and I just want to keep up to date on it.

---

### Post by dejavue on 2013-06-06
> **TNFrank said:**
> Ok, so I just did a "sudo apt-get update; sudo apt-get dist-upgrade" to get the latest/greatest and it seemed to work fine. Since 12.04 is Long Term Support I figure they'll be coming out with all kinds of updates and upgrades for bugs that are found, ect. and I just want to keep up to date on it.

Just enter 

> sudo apt-get update && apt-get upgrade

and it updates first then upgrades right after that.

---

### Post by deadflowr on 2013-06-06
It's important to note there is a difference between upgrade and dist-upgrade.
Upgrade will only install packages deemed safe to install, and most likely will hold back packages regarded as potentially dangerous.
Where as dist-upgrade ignores this safety measure and throws caution to the wind and installs everything.
So if you want to be safe, use upgrade over dist-upgrade.

---

### Post by oldos2er on 2013-06-06
```
man apt-get
``` has a lot of info.

---

### Post by oldos2er on 2013-06-06
> **dejavue said:**
> Just enter ```
sudo apt-get update && apt-get upgrade
``` 

Should be ```
sudo apt-get update && [COLOR=#ff0000]sudo[/COLOR] apt-get upgrade
```

---

### Post by Zill on 2013-06-06
> **TNFrank said:**
> Ok, so I just did a "sudo apt-get update; sudo apt-get dist-upgrade" to get the latest/greatest and it seemed to work fine. Since 12.04 is Long Term Support I figure they'll be coming out with all kinds of updates and upgrades for bugs that are found, ect. and I just want to keep up to date on it.
Sorry, almost but not *quite*, right. ;-)

All Ubuntu releases are "fixed" with the packages specified when it was originally released.  i.e.  Ubuntu 12.04 has packages that were current in April 2012.  The only updates/upgrades any release will *ever* receive will generally be related to security or important bug fixes.  There may be upgrades for Firefox and Thunderbird but these are the exceptions, rather than the rule.  *Most* packages will remain unchanged for the life of the release, other than as mentioned earlier.

However, it is always best to regularly update/upgrade as you have done, ensuring that your release is up-to-date and secure.

If you really do want (or even need!) the "latest/greatest" then you will have to regularly upgrade Ubuntu to the latest release.

---

### Post by monkeybrain2012 on 2013-06-06
> **matt_symes said:**
> Hi


```
sudo apt-get dist-upgrade
```

That will also upgrade the packages, taking into account dependencies. It will remove packages if they conflict etc.




See I don't understand this part because  "sudo apt-get upgrade" already automatically pulls in dependencies and removes conflicting packages etc.

---

### Post by monkeybrain2012 on 2013-06-06
> **Zill said:**
> 


If you really do want (or even need!) the "latest/greatest" then you will have to regularly upgrade Ubuntu to the latest release.

No, you can also use ppas or compile yourself. Many of my software packages in 12.04 are more up to date than 13.04.

---

### Post by matt_symes on 2013-06-06
Hi

> **monkeybrain2012 said:**
> See I don't understand this part because  "sudo apt-get upgrade" already automatically pulls in dependencies and removes conflicting packages etc.

I think the best thing is to check the man pages.> 

upgrade

           upgrade is used to install the newest versions of all packages currently installed on the system from the sources
           enumerated in /etc/apt/sources.list. [B]Packages currently installed with new versions available are retrieved and
           upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved
           and installed.[/B] New versions of currently installed packages that cannot be upgraded without changing the install status
           of another package will be left at their current version. An update must be performed first so that apt-get knows that
           new versions of packages are available.

       dist-upgrade

           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with
           new versions of packages; apt-get has a "smart" conflict resolution system, [B]and it will attempt to upgrade the most
           important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove
           some packages.[/B] The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

Kind regards

---

### Post by monkeybrain2012 on 2013-06-06
Hi,

> 
[B]Packages currently installed with new versions available are retrieved and
           upgraded; under no circumstances are currently installed  packages removed, or packages not already installed retrieved
           and installed.[/B]


I don't think that is true. I have definitely done "sudo apt-get upgrade" and it tells me package x will be removed and package Y will be installed and asks if I want to continue.

maybe the man page is outdated?

---

### Post by matt_symes on 2013-06-06
> **monkeybrain2012 said:**
> Hi,

I don't think that is true. I have definitely done "sudo apt-get upgrade" and it tells me package x will be removed and package Y will be installed and asks if I want to continue.

If you have then you have discovered a bug in apt as it should not be doing that. Next time it happens raise a bug report.

I have never seen this. The times i use it, it behaves the as the man pages describe.

> maybe the man page is outdated?

Not impossible however on my system the man pages were packaged in a new apt deb file. When they were last updated is another issue though.

The other thing to bear in mind is that dist-upgrade was added for intelligent dependency handling so that upgrade should not need to do it.

EDIT:

Next time you see it post it here. 

EDIT 2:

> I don't think that is true. I have definitely done "sudo apt-get  upgrade" and it tells me package x will be removed and package Y will be  installed and asks if I want to continue.

Are you sure this is not configuration files ?

Kind regards

---

### Post by monkeybrain2012 on 2013-06-06
> **matt_symes said:**
> 



Are you sure this is not configuration files ?

Kind regards

I am sure.

See, this is the output format
 ```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  grub-common grub-pc grub-pc-bin grub2-common
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

Right now I have no upgrade  so all the three entries in the last line are 0 (4 packages are pinned) , but they can and have had other values when new packages are installed as dependencies and old ones removed because of conflicts.

---

### Post by Zill on 2013-06-06
> **monkeybrain2012 said:**
> No, you can also use ppas or compile yourself. Many of my software packages in 12.04 are more up to date than 13.04.
This is a "pick'n'mix" approach though!  It would be *very* difficult, if not impossible, to upgrade *all* packages in a release this way. ;-)

---

### Post by monkeybrain2012 on 2013-06-06
> **Zill said:**
> This is a "pick'n'mix" approach though!  It would be *very* difficult, if not impossible, to upgrade *all* packages in a release this way. ;-)

Yeah, but you may not want to upgrade all your packages. This is the flexibility of the Ubuntu ecosystem, ppas allow you to selectively upgrade what you want to upgrade while leaving the core parts alone (unless you install a ppa that pulls in a lot of dependencies, I would be very cautious about those), whereas something like Arch would upgrade everything and Debian doesn't upgrade anything (apart from security and backports, which are only "less old")

 I am bringing this up because there is no reason why you would have to upgrade the whole OS every x months just to get newer applications even if you are perfectly happy with the core OS and it is supported. Some people warn new users against ppas but they are far less risky than upgrading your whole OS (the recommended route to get updated software). Even if you get a rare  bad upgrade from ppas, they are easily reversible with ppa-purge.

---

### Post by matt_symes on 2013-06-06
Hi

> **monkeybrain2012 said:**
> n the last line are 0 (4 packages are pinned) , but they can and have had other values when new packages are installed as dependencies and old ones removed because of conflicts.

When youu next see that situation then post it here and we'll investigate just what is happening.

Kind regards

---

