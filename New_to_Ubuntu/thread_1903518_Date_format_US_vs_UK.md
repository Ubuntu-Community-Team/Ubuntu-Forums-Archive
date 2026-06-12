---
title: "Date format US vs UK"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by jermza on 2012-01-02
I've given up trying to change the locale so that Monday appears as the first day of the week (instead of Sunday).

What I'm trying to do now is to move the day of the week to the front of the month.

[IMG]http://i.imgur.com/GLhQf.png[/IMG]

Instead of "Jan 3", I want it as "3 Jan". I managed to get it right in 10.10 but can't get it right in 11.10.

Is this possible?

---

### Post by lechien73 on 2012-01-02
I believe you need to do this through dconf-editor. When you've opened it, navigate to: **com -> canonical -> indicator -> datetime**

Change the **custom-time-format** string to read (for your case):

```
%a %e %b %k:%M
```

Then change the **time-format** dropdown to **custom**

---

### Post by jermza on 2012-01-03
It won't let me edit those settings. (Never mind the fact that the screenshot button seems to include the highlighted area IN THE actual screenshot, for some reason.)

[IMG]http://i.imgur.com/S6wc2.png[/IMG]

Every time I click on the setting you recommended, the white text field vanishes. Is this expected behaviour?

---

### Post by jermza on 2012-01-03
And amid the dconf weirdness, I managed to change the setting to "custom" but despite what I entered into the custom date format, it defaults back to the original. I simply refuses to accept my edit.

---

### Post by jermza on 2012-01-03
Found a solution here: [http://askubuntu.com/questions/43999/how-to-change-the-date-format](http://askubuntu.com/questions/43999/how-to-change-the-date-format)

Terminal worked better than dconf.

---

