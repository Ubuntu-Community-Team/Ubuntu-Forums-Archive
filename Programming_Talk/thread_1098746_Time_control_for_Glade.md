---
title: "Time control for Glade"
date: 2009-03-17
forum: Programming Talk
---

### Post by thornmastr on 2009-03-17
Hi,

I am using Python 2.5 under Ubuntu 8.10 and Glade 3.4.5.There is not, using Glade, a readily available time control. If I need to capture a date and time parameter, I can use the calendar control to capture a date, but the time is not so readily apparent. I thought two spin buttons; one for hour (say 00-23) and one for minutes (00-59) would do the trick but somehow that seems to not be quite the correct solution.

So, is there a time control available for Glade?

If not, what is the general most used approach to handling time values. 

Thanks very much,


Robert Berman

---

### Post by woodenbrick on 2009-03-17
Maybe someone has a better solution, but I would just use a single ComboBoxEntry widget with the entire time in it, default values of every half hour. It's editable so the user can enter any times that aren't listed.

---

### Post by thornmastr on 2009-03-17
> **woodenbrick said:**
> Maybe someone has a better solution, but I would just use a single ComboBoxEntry widget with the entire time in it, default values of every half hour. It's editable so the user can enter any times that aren't listed.

That will certainly do it.

Thank you,:D:D

Robert

---

