---
title: "power management events"
date: 2010-06-10
forum: Programming Talk
---

### Post by sammy_aus on 2010-06-10
Hello,

Is it possible to catch the power management events(hibarnate/standby/sleep) into the code(c++)?

As far as i understand i need to use acpi daemon.
But it is not clear how can i subscript to events?

Thanks in advance.

---

### Post by Zugzwang on 2010-06-10
Have a look at the D-Bus:

[http://software.intel.com/en-us/articles/developing-power-aware-applications-using-d-bus/](http://software.intel.com/en-us/articles/developing-power-aware-applications-using-d-bus/)

The article does not cover precisely what you want but might be a good start.

---

