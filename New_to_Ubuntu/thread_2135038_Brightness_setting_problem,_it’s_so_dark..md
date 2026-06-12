---
title: "Brightness setting problem, it’s so dark."
date: 2013-04-13
forum: New to Ubuntu
---

### Post by Context Sensitive on 2013-04-13
I installed Ubuntu 12.10 on my ASUS netbook laptop
The model is Eee PC X101CH

The problem is that the brightness function seems to be stuck on its lowest setting.

The brightness up and down commands &#8220;Fn + F5/F6&#8221; as well as trying to change it manually on the brightness settings does nothing.  I can move the brightness bar but it does not change anything.


This is my first try with the Ubuntu Operating system and I am at a bit of a loss.  If anyone can help me with this problem I will be thankful.

---

### Post by prismctg on 2013-04-13
I m also using this netbook with ubuntu 12.10 , but i dont face this problem , maybe its a bug ...

---

### Post by Toz on 2013-04-13
> **prismctg said:**
> I m also using this netbook with ubuntu 12.10 , but i dont face this problem , maybe its a bug ...

@Context Sensitive, make sure you have fully updated your system (especially kernel updates). If @prismctg is not having the issue, perhaps it has been fixed in a recent update.

Otherwise.....
Bug reports here:
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132261]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1132261")
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140581]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140581")

Forum thread describing manual workaround here: 
- [http://ubuntuforums.org/showthread.php?t=2128908]("http://ubuntuforums.org/showthread.php?t=2128908")

Patch from bug #1132261 that apparently fixes the function keys and makes them control brightness again. Note, you need to create those files in /etc/acpi and /etc/acpi/events:
- [https://launchpadlibrarian.net/132241542/asus-display-brightness.patch]("https://launchpadlibrarian.net/132241542/asus-display-brightness.patch")

---

### Post by Context Sensitive on 2013-04-13
ok gabriolastyle&#8217;s solution worked.  need to find a "coding 101" thing  to understand what I did but that something I can look up at another  time.

Thanks for all the help.

---

