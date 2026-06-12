---
title: "Reminder oddity"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by gladgrind on 2012-12-29
I am running 12.04. I have a small script which pops up reminders. The syntax is:

export DISPLAY=:0 && notify-send -t 10800000 'some message'

The -t 10800000 is supposed to allow the popup to remain for three hours or until I click on it.

When I run this in ubuntu mint, it works properly.

When I run it in ubuntu 12.04, the popup remains for 10 seconds and disappears.

Interestingly, if I move the cursor over it, the
popup disappears until I move the cursor away, and
it remains an extra time beyond the 10 seconds,
that is equal to the time the cursor was over it.

Any idea how to get it to work properly?

---

