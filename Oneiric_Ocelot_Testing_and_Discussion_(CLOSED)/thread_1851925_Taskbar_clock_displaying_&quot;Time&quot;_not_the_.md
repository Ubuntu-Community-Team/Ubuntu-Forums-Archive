---
title: "Taskbar clock displaying &quot;Time&quot; not the time"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nick_stokie on 2011-09-29
At some point during updates, indicator-datetime got uninstalled. I reinstalled it and now get the text "Time" on the taskbar instead of the actual time. Clicking it brings up the correct calendar and in the date and time settings it has the correct date and time.

Any thoughts on how to get the time display back, please? Unity-2d.

---

### Post by dino99 on 2011-09-29
try in a terminal:

  unity --reset

sudo dpkg-reconfigure -phigh -a

---

### Post by nick_stokie on 2011-09-29
Thanks for the suggestions.

unity --reset
doesn't do anything as I don't have unity installed, only unity-2d. Maybe this is part of the problem, although everything else in unity-2d works fine.

sudo dpkg-reconfigure -phigh -a
seemed to restart most of my services but I didn't see one that looked applicable to the indicator time. Either way, it hasn't resolved it.

Maybe I need to try installing unity?

---

### Post by cariboo on 2011-09-29
When clicking on the clock, do you get the option for Time & Date settings?

---

### Post by nick_stokie on 2011-09-30
If I right-click on the "Time" text in the taskbar then I get the calendar (correct date shown) and the 'Time & Date Settings' option. This brings up the settings but toggling the various 'show seconds', 'date and month' has no effect.

---

