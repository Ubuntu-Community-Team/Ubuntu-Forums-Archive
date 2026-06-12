---
title: "Upgrading from end of life version"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by robert48 on 2014-04-23
Hello, I'm trying to get a 13.04 version up to 14.04 (through 13.10).

I can't get the system to upgrade to 13.10. The upgrade is offered by update manager, I choose upgrade and authenticate. The Update Manager window dissappears and nothing else happens.  When I run 

```
ubuntu-support-status
```

I get:-

You have 12 packages (0.6%) supported until October 2014 (9m)
You have 1677 packages (89.0%) supported until January 2014 (9m)

You have 27 packages (1.4%) that can not/no longer be downloaded
You have 168 packages (8.9%) that are unsupported

I'm thinking that the existing 13.04 install has not been completely updated and now can't be and that this some how is inhibiting upgrading.

Can you help me clear the log jam please?

---

### Post by jdeca57 on 2014-04-23
Why not a clean install? I mean, "can no longer be downloaded" isn't something you can easily cure and unsupported means just that. Advantages of LTS are that you don't have the short life cycle so that will no longer be of concern and the advantage of a clean install is that all the clutter that can accumulate is gone.

---

### Post by coffeecat on 2014-04-23
You should be able to update 13.04 to the latest packages by changing your sources to [noparse]old-releases.ubuntu.com[/noparse]. See here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If that is successful, you should then be able to upgrade to 13.10 and then to 14.04 in the normal way. Cautionary note: although that community help page was last updated in January of this year, it is full of obsolete cruft and really needs a comprehensive rewrite. In theory doing what I suggest ought to work, but no guarantees. If you want to try, good luck and don't forget to backup all important data first.

If I was in your position I would probably try the old-releases repositories first, if only out of interest and in the spirit of adventure, but in the expectation that my system might break and that I would have to make a fresh install of 14.04. Alternatively, you could simply make a fresh installation of 14.04 over your old one. It might be quicker and less stressful for you in the long run. 

Good luck!

---

