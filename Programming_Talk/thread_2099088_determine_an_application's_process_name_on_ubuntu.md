---
title: "determine an application's process name on ubuntu"
date: 2012-12-28
forum: Programming Talk
---

### Post by Jacobonbuntu on 2012-12-28
This is the situation: 



Working on (the next version of) a Unity quicklist editor, I would  like to add a reliable way of "restarting" launcher icons. To do so, the editor  needs to remove the icon (editing gsettings) and replace it on the same  position. So far no problem. However, if the application in question is  running, user will possibly lose data, as the application will quit when  it's icon is removed from the launcher. What I need is a reliable way  to find an application's process name, to let the editor check in the  list of running processes if the application is running, and send a  warning message to the user that the icon can not be restarted *if* the application is running.
  What I did so far is make the editor look into the desktop file, to  read the command, also read the command, stripped from the directory  section, and furthermore look into possible remote (launch-) scripts the desktop  file command might refer to, looking for strings starting with "./"
  Although the method seems to work well with all applications I tested  it on, I have the feeling there must be an easier way to cover the  problem in an "all in one" way...
  Is there?
  Also suggestions to catch more exceptional situations are welcome!

---

### Post by Jacobonbuntu on 2013-01-02
-bump-
I would appreciate if someone let me know if my question is not clear (English is not my native language), or there simply is no answer?
thanks in advance!

> **Jacobonbuntu said:**
> This is the situation: 



Working on (the next version of) a Unity quicklist editor, I would  like to add a reliable way of "restarting" launcher icons. To do so, the editor  needs to remove the icon (editing gsettings) and replace it on the same  position. So far no problem. However, if the application in question is  running, user will possibly lose data, as the application will quit when  it's icon is removed from the launcher. What I need is a reliable way  to find an application's process name, to let the editor check in the  list of running processes if the application is running, and send a  warning message to the user that the icon can not be restarted *if* the application is running.
  What I did so far is make the editor look into the desktop file, to  read the command, also read the command, stripped from the directory  section, and furthermore look into possible remote (launch-) scripts the desktop  file command might refer to, looking for strings starting with "./"
  Although the method seems to work well with all applications I tested  it on, I have the feeling there must be an easier way to cover the  problem in an "all in one" way...
  Is there?
  Also suggestions to catch more exceptional situations are welcome!

---

