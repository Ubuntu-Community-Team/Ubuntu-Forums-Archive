---
title: "[SOLVED] No Firefox in Hardy"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by captgadget on 2008-05-31
I did a clean install and had Firefox. Then I told Hardy where my Home folder was located and now when I start Firefox I get a message that says FF is already running but it isn't. I've restarted and it won't run. Any here able to help me get FF running again?

---

### Post by robertchahine on 2008-05-31
go to the system panel>administration>system monitor
then go to the process tab and search if there a firefox process, end it.
then run mozilla.
if there still problem, try to move your FF profile to the trash, and then run it(it will make a new profile)

---

### Post by aysiu on 2008-05-31
Press Alt-F2 and paste in the command ```
killall firefox-bin
```

---

### Post by captgadget on 2008-05-31
it comes back firefox-bin: no process killed

---

### Post by captgadget on 2008-05-31
sorry, I don't understand FF profile. Where would I find that?

---

### Post by shifty_powers on 2008-05-31
go to your home folder and press control-h. this will show your hidden files.

then find the .mozilla folder and go into firefox

see screenshot

---

### Post by sayakb on 2008-05-31
Do:
```
rm ~/.mozilla/firefox/profiles.ini
```
to remove the profile.

---

