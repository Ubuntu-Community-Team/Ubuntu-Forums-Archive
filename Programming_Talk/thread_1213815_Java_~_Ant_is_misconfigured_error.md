---
title: "Java ~ Ant is misconfigured error"
date: 2009-07-15
forum: Programming Talk
---

### Post by theDaveTheRave on 2009-07-15
Hello all.

Recently after performing an "upgrade" of my current instalation of Netbeans 6.5 (running on an Ubuntu 8.10 instalation) I received errors relating to the ANT instalation being misconfigured.

I'm affraid that I no longer have the full text of the error message.

Essentially it was a

java.lang.ClassNotFoundException.....

After a not incosiderable amount of hunting I found that the default location could be used from within the <Tools | Options | Miscellaneous > dialogue by simply pressing the "Default" button on the relevant place of the Ant tab.

However, my default location was blank!

there may have been an issue of using NetBeans 6.7 beta, and that upsetting the path to the ant .jar file?

Simply I needed to point the path to the new location (or in fact the default Ant location).

On my Linux setup this was simply < usr/share/ant > 

However it took a while of hunting to find it!

I hope other find this information usefull.

An interesting point in this is, the beta version of NetBeans 6.7 was pointing too < /usr/local/netbeans-6.7/java2/ant >, I couldn't find a similar locaiton for NetBeans 6.5 hence the use of the <usr/share/ant > location.

I would like to know why doing the updates from NetBeans seemingly broke this link. Particularly as I was unable to perform the updates for some time as I was not in my usual location and hence internet was not available to download the update.

I was at least 2 weeks behind, but I haven't seen any other notices of others having a similar problem? what made my setup so different / unusual ?

Suffice to say that everything is now working as it should

David.

---

