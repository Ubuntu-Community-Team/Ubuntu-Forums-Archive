---
title: "problems with Intel NIC"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by oklop on 2011-12-16
I have Intel MB DZ68DB ([http://www.intel.com/Products/Desktop/Motherboards/db-dz68db/DZ68DB-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/db-dz68db/DZ68DB-overview.htm)) with integrated 82579V Gigabit Ethernet Controller (that one makes a problem). Ubuntu 10.04 64 does not see this card. I have tried with install e1000e (found some links at fedora forums), but have failed to enable it. I was thinking to buy TP-Link TG-3269 NIC, that is cheap and has Realtek RTL8169SC chipset. Should this card work with Ubuntu?

---

### Post by anewguy on 2011-12-16
If you do a Google search with:

ubuntu RTL8169SC

in the search string, you'll find a lot of information, including information on getting it working in Ubuntu.  I may be remembering incorrectly, and someone will correct me if I am, but it sticks in my mind that the last time I help someone with that we ended up having to use ndiswrapper.  It's sort of a last resort, so please search first for a native solution.

Post back with ANY questions after you've tried the search.  Not trying to brush you off, but rather educate new users who may be reading this on using a search engine to search for their problem and possible solution.  Often times that's what we do to find the answers to someones problem.

Remember - post back with ANY questions!  ;)

Dave ;)

---

### Post by Vpc on 2012-03-26
> **oklop said:**
> I have Intel MB DZ68DB ([http://www.intel.com/Products/Desktop/Motherboards/db-dz68db/DZ68DB-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/db-dz68db/DZ68DB-overview.htm)) with integrated 82579V Gigabit Ethernet Controller (that one makes a problem). Ubuntu 10.04 64 does not see this card. I have tried with install e1000e (found some links at fedora forums), but have failed to enable it. I was thinking to buy TP-Link TG-3269 NIC, that is cheap and has Realtek RTL8169SC chipset. Should this card work with Ubuntu?

I had the same problem with Ubuntu 10.04 (32 bit) and the 82579V Gigabit Ethernet Controller on the Intel DP67DE motherboard. Installing Ubuntu 11.10 solved the problem.

---

