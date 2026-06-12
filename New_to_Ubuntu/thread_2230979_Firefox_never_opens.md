---
title: "Firefox never opens"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by zognorp-yahoo on 2014-06-22
Trying to use Firefox on ethernet or wifi.  It takes a long time to open and then it opens with unresponsive script box.  Even if I close that box Firefox still does not work and i can't move the mouse at all.

---

### Post by zognorp-yahoo on 2014-06-22
Also, How do I close previous threads that are finished?

---

### Post by zognorp-yahoo on 2014-06-22
I closed everything with alt-F4 but the mouse is still stuck.  Hard drive is silent at this point

---

### Post by deadflowr on 2014-06-22
> **zognorp-yahoo said:**
> Also, How do I close previous threads that are finished?

You don't.
You can either simply mark a thread as solved, or click on the report post button in the bottom left corner of any post(preferably the first post) and request the thread be closed. Then it is staff discretion as to whether or not to close it.

Per this thread, what happens if you try launching firefox from a terminal
(ctrl+ alt + t)or search the dash, or menu for terminal then try
```
firefox
```
ctrl + c will cancel it.
Perhaps you can post what the output says.
(As long as it isn't super long)

---

### Post by zognorp-yahoo on 2014-06-22
First off, I could not get the mouse to work or any keyboard commands to work.  I finally was able to shut down by hitting the power button. After rebooting it takes about 4 minutes for the terminal window to open or any other keyboard command for that matter.  Even when the window is open it will not let me use the terminal for about another 5 minutes. None of this seems normal to me.

I typed the command "firefox" into the terminal window and it says: 
(process:2730): GLib-CRITICAL **:g_slice_set_config: assertion 'sys_page_size == 0'' failed

There is a whole bunch more if you want it all pertaining to 'Attempt to add GnomeProgram........'

---

### Post by zognorp-yahoo on 2014-06-22
Now, 20 minutes later a partially complete firefox window has opened with the unresponsive script warning box.  The mouse is not frozen this time though

---

### Post by zognorp-yahoo on 2014-06-22
Turns out the Ubuntu install is working just fine and the internal fan on the laptop has all the blades broken off.  It was simply overheating and freezing up.  Thanks for all your help.

---

