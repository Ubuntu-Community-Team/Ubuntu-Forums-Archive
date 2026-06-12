---
title: "Is Python 2.5+ backward compatible with 2.4?"
date: 2011-12-10
forum: Programming Talk
---

### Post by donsy on 2011-12-10
I'm trying to get my hosting site to upgrade from Python 2.4.3 to, at a minimum, 2.5 but they're resisting, citing fears of breaking existing Python scripts. Is that correct? Will an upgrade to 2.5 break existing code? If not, how far up the 2.x branch can they upgrade before backward compatibility becomes an issue?

---

### Post by bluexrider on 2011-12-10
> **donsy said:**
> I'm trying to get my hosting site to upgrade from Python 2.4.3 to, at a minimum, 2.5 but they're resisting, citing fears of breaking existing Python scripts. Is that correct? Will an upgrade to 2.5 break existing code? If not, how far up the 2.x branch can they upgrade before backward compatibility becomes an issue?

According to what I found was YES it is and shouldn't have to be ported over. With questions using other OS and the like Stack overflow recommends a program something like [buildbot ]("http://buildbot.net/trac")to automate the test running on all the other platforms, and collecting the results.

also reading this [http://regebro.wordpress.com/2010/02/12/yes-python-2-6-is-backwards-compatible/](http://regebro.wordpress.com/2010/02/12/yes-python-2-6-is-backwards-compatible/)

Hope this helps

---

### Post by r.darwish on 2011-12-11
Maybe they can use [virtualenv]("http://pypi.python.org/pypi/virtualenv/1.7") to create additional Python environments containing different Python versions. I agree with [bluexrider]("http://ubuntuforums.org/member.php?u=1456072"): Moving to 2.5 Shouldn't case harm, but they may see deprecation warnings however. If they do, then they should change their scripts to stop using deprecated API, and then they can upgrade to the next version. Like [bluexrider]("http://ubuntuforums.org/member.php?u=1456072"), I also suggest writing automated test. They will have to upgrade eventually

---

