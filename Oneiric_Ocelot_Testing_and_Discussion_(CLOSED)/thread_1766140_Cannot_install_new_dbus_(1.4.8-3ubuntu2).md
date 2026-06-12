---
title: "Cannot install new dbus (1.4.8-3ubuntu2)"
date: 2011-05-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-24
The new dbus package set cannot be installed due to an error in its dependencies.
Package dbus (1.4.8-3ubuntu2) depends on netbase (4.45ubuntu3).

However, new netbase version (4.45ubuntu2) was just uploaded into repos, but it is not a correct version, it should be 4.45ubuntu3.

New dbus is here:
[https://launchpad.net/ubuntu/oneiric/+source/dbus/1.4.8-3ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/dbus/1.4.8-3ubuntu2)

New netbase is here:
[https://launchpad.net/ubuntu/oneiric/+source/netbase/4.45ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/netbase/4.45ubuntu2)

---

### Post by Quackers on 2011-05-24
I just found that out :-)

---

### Post by dino99 on 2011-05-24
what i'm seeing is:

dbus depend on upstart-job
but now upstart have replaced upstart-job (this package is no more into repo)

---

### Post by Quackers on 2011-05-24
It shows as a broken package for me, with unresolvable dependencies.

---

### Post by dino99 on 2011-05-24
bug report:

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/787360](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/787360)

---

### Post by JMB74 on 2011-05-24
> **Quackers said:**
> It shows as a broken package for me, with unresolvable dependencies.

Yep. A broken dependency on netbase 4.45ubuntu3.

[COLOR=Navy][I]The following packages have unmet dependencies.
 dbus : Depends: netbase (>= 4.45ubuntu3) but 4.45ubuntu2 is to be installed
E: Broken packages[/I][/COLOR]

---

### Post by dino99 on 2011-05-24
> **JMB74 said:**
> Yep. A broken dependency on netbase 4.45ubuntu3.

[COLOR=Navy][I]The following packages have unmet dependencies.
 dbus : Depends: netbase (>= 4.45ubuntu3) but 4.45ubuntu2 is to be installed
E: Broken packages[/I][/COLOR]

the problem is : upstart-job replaced by upstart (see post above with bug)

---

### Post by JMB74 on 2011-05-24
> **dino99 said:**
> the problem is : upstart-job replaced by upstart (see post above with bug)

Not here.

Here dbus wants netbase (>= 4.45ubuntu3) but only netbase 4.45ubuntu2 is available in the repos.

If I bump the netbase version myself to 4.45ubuntu3, the dependancy problem goes away.

[I]The following packages will be upgraded:
   dbus (1.4.8-3ubuntu1 => 1.4.8-3ubuntu2)
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 226 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main dbus i386 1.4.8-3ubuntu2 [226 kB]
Fetched 226 kB in 0s (408 kB/s)
(Reading database ... 174674 files and directories currently installed.)
Preparing to replace dbus 1.4.8-3ubuntu1 (using .../dbus_1.4.8-3ubuntu2_i386.deb) ...
Unpacking replacement dbus ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up dbus (1.4.8-3ubuntu2) ...
Installing new version of config file /etc/init/dbus.conf ...[/I]

---

### Post by JMB74 on 2011-05-24
> **Harry33 said:**
> The new dbus package set cannot be installed due to an error in its dependencies.
Package dbus (1.4.8-3ubuntu2) depends on netbase (4.45ubuntu3).[]("https://launchpad.net/ubuntu/oneiric/+source/netbase/4.45ubuntu2")

Now fixed.

[https://launchpad.net/ubuntu/oneiric/+source/dbus/1.4.8-3ubuntu3](https://launchpad.net/ubuntu/oneiric/+source/dbus/1.4.8-3ubuntu3)

** debian/control: Fix versioned dependency to netbase to make package     installable again.*

---

### Post by Harry33 on 2011-05-24
Confirmed, the dependency (dbus => netbase) is correct now.
Not related to upstart.

---

