---
title: "indicator-cpufreq"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-01-16
I'm having trouble with my Dell Inspiron 1520 getting really hot running Ubuntu 12.04.
A Google search led me to believe that perhpas the utility indicator-cpufreq could help with the excess heat.
The jury is still out on if it helps or not, but after installing indicator-cpufreq from the Ubuntu repository I found that I can only launch it as root.
As a regular user it gives an error in /xsession-errors:
```
** Message: applet now embedded in the notification area

(dropbox:2169): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
/usr/bin/indicator-cpufreq:82: GtkWarning: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()

```

I can get around this and have it launch as a start up program by using 
```
echo password | sudo -S 
```
in a script to launch indicator-cpufreq.

I'm wondering why am I forced to do this?  It doesn't seem that this program should be run as root.
Does anyone know how I can fix this problem?

---

