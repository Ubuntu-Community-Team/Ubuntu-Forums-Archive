---
title: "Get application under mouse cursor?"
date: 2010-01-02
forum: Programming Talk
---

### Post by r_avital on 2010-01-02
Hi all,

Is there a somewhat straightforward way to get the name or pid of the application that is under the mouse's cursor?

What I'm trying to do:  This is just a "what if" at this point, I would like to run some script that would obtain the name/pid of any application that the mouse cursor is on, and use xte to assign different functions to different mouse buttons.  For instance, assign a given button the Forward or Back function when the cursor is on a browser, but assign a scroll-left or scroll-right to the same button when it's on a spreadsheet.

Is there any way to accomplish this, say, in a script that I could run at startup as a background process?

Thanks in advance :)

---

### Post by falconindy on 2010-01-02
xprop will return some basic window information. It's a basic xorg utility.

---

### Post by r_avital on 2010-01-03
Thanks.  Fooled around with it a bit, I can do a grep on WM_NAME(STRING) or WM_CLASS(STRING) and get what I need from that in a script.

I wasn't looking for anything powerful or sophisticated, so this is a good start.

Thanks again and Happy New Year :)

---

