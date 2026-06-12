---
title: "Packages are not updated by APT upgrade"
date: 2024-11-09
forum: New to Ubuntu
---

### Post by joepesci2 on 2024-11-09
Hello everyone.
Im doing an apt update and it finds 9 upgradeable packages.
When i do apt upgrade to upgrade them, i get the following:

five of these packages appear as "***not upgrading yet due to phasing***".
I understand that this is because they are being updated in phases and its not my turn yet.

The other four appear as "***not upgrading***", but it doesnt show any other message.
Among them is Dolphin.

However, in the Discover updates app, another four packages do appear to be upgraded, including Dolphin again.

Can anyone give me information about this?

Thanks for your help.

---

### Post by Holger_Gehrke on 2024-11-09
One situation where 'apt update' will not update is a change in a package that introduces a new dependency or reflects a newly discovered incompatibility ('apt show' would display something like 'breaks '+package name) and therefore asks for the removal of the incompatible package. 'update' will not install new packages or remove conflicting packages. To do the update and install the needed new package or remove the conflicting one there is 'apt dist-upgrade'. I can only assume that discover does that by default (or you set it to do that).

Holger

---

### Post by joepesci2 on 2024-11-10
> **Holger_Gehrke said:**
> One situation where 'apt update' will not update is a change in a package that introduces a new dependency or reflects a newly discovered incompatibility ('apt show' would display something like 'breaks '+package name) and therefore asks for the removal of the incompatible package. 'update' will not install new packages or remove conflicting packages. To do the update and install the needed new package or remove the conflicting one there is 'apt dist-upgrade'. I can only assume that discover does that by default (or you set it to do that).

Holger

Hi Holger_Gehrke, how are you?

I did an apt dist-upgrade and then an apt uptade-upgrade.
After that, i no longer see any available updates in Discover, so some have been successfully done now.

Right now when i do an apt update-upgrade, i only see 6 packages that could not be updated.
They are all related to GRUB.
[B]5 of 6 packages could not be updated because of "not upgrading yet due to phasing"

1 of the packages simply says "not upgrading".[/B]

As i said before, all 6/6 packages are related to grub.

**I did an apt show as you told me, but it didnt show any extra information.**

Thank you very much for your help and kindness.

---

### Post by Holger_Gehrke on 2024-11-10
'apt show' needs the name of the package to show additional information on, e.g 'apt show grub-efi-amd64-bin'. Might be the case that the package not being updated is not phased but depends on a package that is.

Holger

---

### Post by grahammechanical on 2024-11-10
For anyone who doesn't know but wants to know this is what happens when we run either apt dis-upgrade or apt full-upgrade:

> **dist-upgrade**
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages; apt-get has a "smart" conflict
           resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. [COLOR=#ff0000]The dist-upgrade command may therefore
           remove some packages[/COLOR]. The /etc/apt/sources.list file contains a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism
           for overriding the general settings for individual packages.

> **full-upgrade** (apt-get(8))
           full-upgrade performs the function of upgrade [COLOR=#ff0000]but will remove
           currently installed packages[/COLOR] if this is needed to upgrade the
           system as a whole.

Regards


Stuff gets removed. This is why packages held back get upgraded. Don not be surprised if using either of those commands breaks something of removes something.

---

### Post by joepesci2 on 2024-11-11
> **Holger_Gehrke said:**
> 'apt show' needs the name of the package to show additional information on, e.g 'apt show grub-efi-amd64-bin'. Might be the case that the package not being updated is not phased but depends on a package that is.

Holger

> **grahammechanical said:**
> For anyone who doesn't know but wants to know this is what happens when we run either apt dis-upgrade or apt full-upgrade:





Regards


Stuff gets removed. This is why packages held back get upgraded. Don not be surprised if using either of those commands breaks something of removes something.

I get the idea of &#8203;&#8203;what you mean.
Thank you very much for your help and time.

---

