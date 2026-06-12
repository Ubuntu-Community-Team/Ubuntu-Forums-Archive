---
title: "Programs not opening?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by wrtpeeps on 2008-06-27
Whenever I click to open firefox, or gedit (these are the 2 apps ive tried so far), nothing happens. I can see them using resources by looking at conky, however the windows don't appear.

Then, a few minutes later, the windows do appear, but I cannot click anything inside them (as if they are frozen).

To close them I have to use killall.

Anyone got any ideas what could be causing this? I haven't made any changes to my xorg file.

---

### Post by WRDN on 2008-06-27
Open the application using the terminal and post the output here.
This can be done easily by entering the application name e.g. "firefox" would be entered for the applicable application.

---

### Post by Xerp on 2008-06-27
Sounds like a high load? How do things look from top (terminal) or the activity monitor (gui)?

---

### Post by wrtpeeps on 2008-06-27
> **WRDN said:**
> Open the application using the terminal and post the output here.
This can be done easily by entering the application name e.g. "firefox" would be entered for the applicable application.

I tried that.

I dont get any output. It just enters the command and then waits for ages until ff loads. Then, it becomes unuseable.

Terminal has no output at all.

---

### Post by wrtpeeps on 2008-06-27
> **Xerp said:**
> Sounds like a high load? How do things look from top (terminal) or the activity monitor (gui)?

Load is low. It isn't that.

---

### Post by Xerp on 2008-06-27
Anything in syslog or messages?

---

### Post by wrtpeeps on 2008-06-27
Nope. Which is annoying.:)

---

