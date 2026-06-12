---
title: "Firefox / sqlite time issues"
date: 2009-02-20
forum: Programming Talk
---

### Post by lovinglinux on 2009-02-20
I'm not sure if this is the right place to post because it is related to programming but could be a bug in Firefox or Ubuntu. Anyways...

I'm writing a Firefox extension that display data from a sqlite database, based on the current date, so each day the values are updated accordingly.

The sql statement used is like this:

```
WHERE thetable.thedate = CURRENT_DATE
```

The date format is YYYY-MM-DD.

It works pretty fine. The only issue I'm experiencing is that when I open the extension a couple of hours before midnight, the data displayed is for the next day. It has been suggested in the Mozilla Extension Development forum that this is due to GMT difference, since I'm at GMT -3. If this is true, I guess there is a problem with Firefox, sqlite or Ubuntu. 

As far as I understand, Firefox should get the time from the system, which is correct for my location.

Any other ideas why this is happening?

---

### Post by mike_g on 2009-02-21
Looks like this might solve your problem:

[http://stackoverflow.com/questions/381371/sqlite-currenttimestamp-is-in-gmt-not-the-timezone-of-the-machine/571691](http://stackoverflow.com/questions/381371/sqlite-currenttimestamp-is-in-gmt-not-the-timezone-of-the-machine/571691)

---

### Post by lovinglinux on 2009-02-21
Thanks. 

I guess it works using the following statement:

```
WHERE thetable.thedate = date('now','localtime')
```

---

