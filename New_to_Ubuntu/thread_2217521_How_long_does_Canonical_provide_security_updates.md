---
title: "How long does Canonical provide security updates?"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by sanssadness on 2014-04-17
Because I am using version 12.04 LTS, I thought security updates would be provided until 2017. But then I found a Java plugin called "Iced Tea". Even though this plugin can be installed from the Ubuntu Software Center, it says under the plugin's page that "Canonical provides critical updates for Icedtea Java Plugin until October 2013". I though Canonical would support all the software that could be installed from the Software Center (not just the operating system itself) until 2017. Does this mean if I install this plugin, I'm putting myself at risk?

---

### Post by whitesmith on 2014-04-17
Canonical allows downloading through the Software Center of certain applications that have undergone compatibility testing, but support resides with the vendor. Unless I am very mistaken, support for the product you mention ended in October, 2013 (or 2014 if the date is a typo, as seems likely).

---

### Post by oldos2er on 2014-04-17
Only software in the main repository is officially supported. See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by grahammechanical on 2014-04-17
When I go to the software centre I often see the comment "Canonical does not provide updates for ... Some updates may be provided by the Ubuntu community." For example, Chromium. 

As for IcedTea Java Plugin the 14.04 software centre says "Canonical provides critical updates for IcedTea Java Plugin until April 2019.

So, there is the reason the version in 12.04 is loosing or lost support. It is replaced by a more updated version in Ubuntu 14.04. To keep any risk factor to a minimum run the latest Ubuntu LTS.

Regards.

---

### Post by sanssadness on 2014-04-17
Can I upgrade from 12.04 to 14.04 without having to wipe the hard drive or losing my programs and data?

And how can I tell what respository a piece of software found in the Software Center comes from, aside from when it says updates have ceased already?

---

### Post by oldos2er on 2014-04-17
> **sanssadness said:**
> Can I upgrade from 12.04 to 14.04 without having to wipe the hard drive or losing my programs and data?

Of course, but I would advise making backups first if you haven't done so recently. ```
do-release-upgrade
```

> **sanssadness said:**
> And how can I tell what respository a piece of software found in the Software Center comes from, aside from when it says updates have ceased already?

I don't use Software Center, so I don't know if it can show repository information or not; however, Synaptic Package Manager can if you click the 'Origin' tab, and so can ```
apt-cache policy <package name>
``` or ```
apt-cache show <package name> | grep Section:
```

---

### Post by sanssadness on 2014-04-17
[QUOTE=oldos2er]Of course, but I would advise making backups first if you haven't done so recently[/QUOTE]

I've got backups, yes. But having to reinstall all programs would still cause me considerable headache.

Would you still expect my upgrade to be free of problems if I have a complicated partitioning scheme that involves encryption?

---

### Post by Ubi_one_2014 on 2014-04-17
download the 14.04 ISO, and burn it
to have a copy of 14.04 available

alt+ft, type:
update-manager [enter]

upgrade online to 14.04
is something goes wrong, you allways have a backup available

---

### Post by oldos2er on 2014-04-18
> **sanssadness said:**
> Would you still expect my upgrade to be free of problems if I have a complicated partitioning scheme that involves encryption?

Partitioning scheme shouldn't matter. 

I have zero experience with encryption so I can't advise you on that.

---

