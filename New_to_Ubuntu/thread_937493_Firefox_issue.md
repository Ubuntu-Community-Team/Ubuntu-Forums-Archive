---
title: "Firefox issue???"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by timstone on 2008-10-03
I downloaded and installed Avant Window Manager to take the place of my lower panel and added some applications there on it as launchers.

Everything works fine except for firefox.

When I click to open it, it first opens a terminal window and then the firefox app.

After firefox is opened for a minute or two the terminal window starts spitting out this error

```

(firefox:6556): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

I searched with google to see if i could find a solution and did find one forum where a guy said to change the fonts in firefox back to serif.  Well I did that and it still happens.

I should also mention that none of the other programs on the window manager open up this way or give errors like this.

---

### Post by Frak on 2008-10-03
When disabling AWN does it continue the errors?

---

### Post by Cato2 on 2008-10-04
AWN seems to be opening Firefox in a terminal window for some reason - it should simply point to /usr/bin/firefox in its launcher icon for Firefox.

The errors you see from Firefox can be ignored.  You will get the same errors if you open a terminal and type 'firefox &'.

---

### Post by Lord DarkPat on 2008-10-04
Run firefox in terminal and post the output.

---

