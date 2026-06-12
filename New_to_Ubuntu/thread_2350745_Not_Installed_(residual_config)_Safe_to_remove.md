---
title: "Not Installed (residual config): Safe to remove?"
date: 2017-01-27
forum: New to Ubuntu
---

### Post by martemarziano on 2017-01-27
Hi everyone,

Just wondered if it is safe to remove the packages listed as "residual config" in synaptic?

---

### Post by ajgreeny on 2017-01-27
Yes, it is quite safe.

If you use synaptic to do it just highlight all those packages listed and go to the Package menu and choose "Mark for complete removal".
If you use the terminal use ```
sudo apt-get purge list of package names separated with spaces
```

---

### Post by #&amp;thj^% on 2017-01-27
From man apt-get:

     >   remove
           remove is identical to install except that packages are removed instead of installed. Note
           that removing a package leaves its configuration files on the system. If a plus sign is
           appended to the package name (with no intervening space), the identified package will be
           installed instead of removed.

       purge
           purge is identical to remove except that packages are removed and purged (any configuration
           files are deleted too).


Those packages are just those  that has configuration files that hasn't been removed. Unless you are planning to reinstall the packages again, and want to keep the configuration, yes, you can remove them safely.

While there is no built in way to remove all of your configuration files or folders from your removed packages you can remove all configuration data from every removed package with the following command.

   ```
 dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge
```
Ninj'ed by ajgreeny:)

---

### Post by deadflowr on 2017-01-27
Should add a sudo to the xargs command:
```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs sudo dpkg --purge
```
also probably run a --simulate/dry-run first to double check that it isn't going to remove anything you still want or need
```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs sudo dpkg --purge --dry-run
```

---

### Post by martemarziano on 2017-01-27
Thanks everyone!
Let's purge them all away:evil:

---

### Post by #&amp;thj^% on 2017-01-27
> **deadflowr said:**
> Should add a sudo to the xargs command:
```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs sudo dpkg --purge
```
also probably run a --simulate/dry-run first to double check that it isn't going to remove anything you still want or need
```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs sudo dpkg --purge --dry-run
```

Yep I forgot that (sudo):D.
Good catch deadflowr!

---

### Post by ajgreeny on 2017-01-27
Having mentioned the simulate option, can someone tell me if there is an option to simulate actions with **apt** in the same way you can with **apt-get**?

I can not find it shown anywhere in **man apt**.

---

### Post by howefield on 2017-01-27
> **ajgreeny said:**
> can someone tell me if there is an option to simulate actions ...

Same -s switch as you would use with apt-get, eg

```
sudo apt install -s cowsay
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  cowsay-off
Suggested packages:
  filters
The following NEW packages will be installed
  cowsay cowsay-off
0 to upgrade, 2 to newly install, 0 to remove and 0 not to upgrade.
Inst cowsay (3.03+dfsg1-15 Ubuntu:16.04/xenial [all])
Inst cowsay-off (3.03+dfsg1-15 Ubuntu:16.04/xenial [all])
Conf cowsay (3.03+dfsg1-15 Ubuntu:16.04/xenial [all])
Conf cowsay-off (3.03+dfsg1-15 Ubuntu:16.04/xenial [all])
```

---

### Post by martemarziano on 2017-01-27
You are amazing guys! Looks like you communicate in a secret language. Incredible!
):P

---

### Post by ajgreeny on 2017-01-28
> **howefield said:**
> Same -s switch as you would use with apt-get.
Thanks howefield.

---

