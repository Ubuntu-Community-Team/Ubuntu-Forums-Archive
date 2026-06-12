---
title: "chromium auto start, URL and Fullscreen"
date: 2018-05-09
forum: New to Ubuntu
---

### Post by hein88 on 2018-05-09
Hi Guys.

I have something very specific I need Ubuntu to do.

Im very new to Ubuntu and Linux and I really do not know much about much when it comes down to it with Linux,

I have been given a task to complete and Im not really sure where to begin.

I need for the computer to run chromium, autostart it every time the computer restarts, it must then go to full screen, display one specific URL and refresh every 90s.

I was wondering if someone could help me with a script and or how to, that will enable me to complete the task.

I appreciate anyone help.

Thanks!

---

### Post by kerry_s on 2018-05-09
from "man chromium"
> --app=URL
              Runs URL in "app mode": with no browser toolbars.
example:
chromium --app=https://www.google.com/

once you find the right command, add it to the startup app.

---

### Post by PaulW2U on 2018-05-09
Adding to what kerry_s has said:

**--start-fullscreen ** is the switch to start Chromium in full screen mode.

Some auto refresh extensions can be found in the Chrome store - [https://chrome.google.com/webstore/search/auto%20refresh](https://chrome.google.com/webstore/search/auto%20refresh).

So now you have the tools to accomplish want you want. You just have to put it all together. :)

---

### Post by kerry_s on 2018-05-09
this better not be homework for school.

---

