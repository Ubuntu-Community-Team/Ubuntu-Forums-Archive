---
title: "Cannot run apt commands, package manager is broken"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by joomla1 on 2013-09-14
Here is the output of 
sudo dpkg --configure -a


dpkg: error processing libldap-2.4-2 (--configure):
 libldap-2.4-2:amd64 2.4.28-1.1ubuntu4.2 cannot be configured because libldap-2.4-2:i386 is in a different version (2.4.28-1.1ubuntu4.3)
dpkg: error processing libldap-2.4-2:i386 (--configure):
 libldap-2.4-2:i386 2.4.28-1.1ubuntu4.3 cannot be configured because libldap-2.4-2:amd64 is in a different version (2.4.28-1.1ubuntu4.2)
Errors were encountered while processing:
 libldap-2.4-2
 libldap-2.4-2:i386

I cannot upgrade or run any apt command.

---

### Post by oldos2er on 2013-09-14
What version of Ubuntu are you running? Do you have any PPAs enabled? If so, you might want to disable them, run ```
sudo apt-get update && sudo apt-get upgrade
``` and see if that fixes your problem.

---

### Post by Jonathan Precise on 2013-09-14
Please use code tags (shown below).

Try:

```
sudo dpkg --remove --force-remove-reinstreq libldap2.4-2:i386
```

Post any error messages with code tags:

(code)dpkg-error(/code)

Change parenthesis to brackets:

```
dpkg-error
```

Edit: what ubuntu version are you using?

---

### Post by joomla1 on 2013-09-15
I'm using Ubuntu 12.04 LTS but I use KDE

```

sudo dpkg --remove --force-remove-reinstreq libldap-2.4-2:i386
dpkg: dependency problems prevent removal of libldap-2.4-2:i386:
 libcurl3:i386 depends on libldap-2.4-2 (>= 2.4.7).
dpkg: error processing libldap-2.4-2:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libldap-2.4-2:i386

```

---

### Post by joomla1 on 2013-09-15
I disabled the f.lux and google chrome/talk ppas and ran the commands you suggested, didn't help.

---

### Post by oldos2er on 2013-09-15
Can you please post all the output from the commands?

---

### Post by CeejRab on 2013-09-15
Hello joomla,

It sounds like your essential OS components could be messed up, or maybe you need a software update? Does Update Manager show available updates for your system? (accessible via the shutdown icon at the top right of the unity desktop interface)?

Although we dont like to jump to it, if you cant get assistance that helps, i would consider a fresh install of ubuntu. You can use Deja Dup to back up your content manually to an external HD and then get a fresh install of ubuntu on the machine. Run the updates and then restore from your backup and settle in, everything should work fine after a clean install. It takes about an hour to do a fresh install and restore a simple backup, so its not too bad of an option when your system gets kahfuffled.

Hope you figure it out in a timely and satisfactory fashion. All the best,

-Christian

---

### Post by Jonathan Precise on 2013-09-17
> **joomla1 said:**
> I'm using Ubuntu 12.04 LTS but I use KDE

```

sudo dpkg --remove --force-remove-reinstreq libldap-2.4-2:i386
dpkg: dependency problems prevent removal of libldap-2.4-2:i386:
 libcurl3:i386 depends on libldap-2.4-2 (>= 2.4.7).
dpkg: error processing libldap-2.4-2:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libldap-2.4-2:i386

```

Try:

```
sudo dpkg --remove --force-remove-reinstreq libcurl3:i386
```

Post the results.

---

