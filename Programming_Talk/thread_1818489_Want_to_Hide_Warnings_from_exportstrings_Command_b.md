---
title: "Want to Hide Warnings from export/strings Command but Can't"
date: 2011-08-04
forum: Programming Talk
---

### Post by jamesisin on 2011-08-04
I am using a novel (to me) command which combines export, strings, grep, and tail to set the correct dbus channel for a script to remotely control Banshee:

```
export $(strings /proc/*/environ | grep DBUS_SESSION | tail -1)
```

I tried redirecting output to /dev/null but that either didn't send what I wanted sent to /dev/null or else it made the export command fail to do what it needs to do to make the commands work.

Can someone help me hide those warnings from the user?

It's important to remember that this script is meant to be used remotely (over ssh) because some of the commands behave differently when called remotely.

You can see the full script here:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/](http://jamesisin.com/a_high-tech_blech/index.php/2011/08/a-new-script-for-skipping-tracks/)

---

### Post by Bachstelze on 2011-08-04
```
strings /proc/*/environ 2> /dev/null | grep DBUS_SESSION | tail -1
```

The warnings appear on the standard error stream (stderr), so they are not affected by > or |, since those work on the standard output (stdout). You must use 2> to redirect only stderr, or you can use &> to redirect both stdout and stderr.

---

### Post by jamesisin on 2011-08-04
Odd.  I thought I tried redirecting out and err (at strings) to null but it failed when run remotely.  Now it works through redirecting err (as per your suggestion).  Good enough I guess.  Thanks.

---

