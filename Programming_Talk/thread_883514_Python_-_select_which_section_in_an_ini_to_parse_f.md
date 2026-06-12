---
title: "Python - select which section in an ini to parse first"
date: 2008-08-08
forum: Programming Talk
---

### Post by Reactor5 on 2008-08-08
I'm coding an automatic file organizer, which I'm calling osmium (just for kicks.)  I've run into a problem though, parsing the ini.  By my logic, ConfigParser should parse sections according to what order they are in the ini, but it seems to parse them according to size.  Anyone know a way to change this?

By the way, the code is at [https://code.launchpad.net/~brianhicks/+junk/Osmium](https://code.launchpad.net/~brianhicks/+junk/Osmium) if you'd like to take a look.  I'm really open to suggestions on how to improve this!

---

### Post by geirha on 2008-08-08
The order of the entries in an ini file should be irrelevant. Why do you need them to be parsed in order?

---

### Post by Reactor5 on 2008-08-08
Because if files have two or more positives in the rules, it should apply the first one first, but if I can't control that, files are getting deleted before they can be moved.

---

### Post by geirha on 2008-08-08
How about adding a priority field then?

---

