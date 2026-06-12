---
title: "HOWTO: Disable Fade Effect on Password and Quit Dialogs"
date: 2006-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by 23meg on 2006-12-26
This is very simple and may be obvious, but I've missed it for a very long time, and I feel others may be as well.

**Problem:** The fade effect that darkens the area outside the windows in the password dialogs when running an administrative app and the window that comes up when you hit System / Quit may be disturbing. The animation is quite choppy with certain (most?) video configurations, especially when using a compositing manager, it's quite possible not to like it as a matter of preference. 

**Solution: ** Go to System / Preferences / Assistive Technology Preferences and check the "Enable assistive technologies" and "Password dialogs as floating windows" checkboxes. That's it. It's a good workaround, and is easy to miss if you've never thought this is where the option would be and don't need assistive technologies.

[COLOR=Red]**Caution:**[/COLOR] Be aware that with this behavior, the dialogs will be regular windows and be treated as such by your window manager, and input outside them won't be blocked. **This may bring security and usability concerns or block functionality **in certain cases.

---

### Post by 23meg on 2007-01-16
I noticed that the "Switch User" feature stopped working after applying this. Can anyone confirm that?

---

### Post by palehorse1 on 2009-08-18
*BUMP*
Is this the only way anyone has found to fix this?

I am using an XDMCP over a 100bT network connection (clearly I have just enough knowledge to be dangerous) and every time I try to perform an administrative task the fade takes an unbearable 15 seconds, or so, before it prompts me for a password.
I would prefer not to use a hack like this if it can be avoided but I would also like to improve the responsiveness of these tasks.

Thanks.
-E

---

