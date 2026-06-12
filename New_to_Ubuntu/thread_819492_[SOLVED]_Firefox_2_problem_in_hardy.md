---
title: "[SOLVED] Firefox 2 problem in hardy"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by A$h X on 2008-06-05
I've replaced firefox 3 beta 5 with firefox 2 in hardy. It's working okay, but with a small problem. Firefox is no longer "integrated" with hardy. If I click a link or button or control etc in an external program which should open a link nothing happens. 

For example, in deluge there is a "test active port" button. This should open a page in firefox which tests whether the active port is open or not. This works in FF3, but not in FF2. I'm sure there is some command which will remedy this, but I don't know what it is.

Any ideas?

---

### Post by Nepherte on 2008-06-05
You should look under system > preferences > default programs that for www, you have firefox-2. Most likely it will say firefox but that is a symbolic link refering to Firefox 3 Beta 5.

---

### Post by A$h X on 2008-06-05
Thanks Nepherte! Your advice worked perfectly! :KS

In case anyone has the same problem just goto to system > preferences > preferred application and where it says "web browser" change the command to:
> firefox-2 %s

Close the dialog and it should work as before. :)

---

