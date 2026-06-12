---
title: "Login screen repeats &quot;Starting show Plymouth Boot screen...&quot;"
date: 2018-01-15
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-01-15
Today I shutdown the PC graciously.  I started the PC. Goes to log-in screen, I enter password and then it shows ""Starting show Plymouth Boot screen..." and comes back t**o login screen**.

Steps
1) Enter password
2) Show error dialog box. Asking to report the error to Ubuntu
3) Goes to black screen and shows 
   "Starting show Plymouth Boot screen..."
4) Comes back to log-in screen
    I enter the password and above steps repeats.


Please tell me how to debug this issue. I had no issues from 2-3 weeks, thought I had worked out all the issues. Now this comes at very bad time. Please help.

Thanks

---

### Post by ajgreeny on 2018-01-16
Did you make any changes to system files (anything not in your home) at your last successful session, or did you perhaps run a command using sudo for a GUI application?

The continuous return to the login screen is sometimes caused by wrong ownership of some of the files in your home, so it may be useful to see the output of command ```
ls -la /home/username
``` run from recovery mode (from grub menu).

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by wrongusername2 on 2018-01-17
Thanks for responding.

I ended up re-imaging the machine using DD. I keep all my data on a separate drive, that saved me.

 
**Other options for next time**
1) If it happens next time, can I go to apt-get history and uninstall the packages from reverse order? I have to do this using terminal. Do you think this will work?

2) I do see **recovery-os** in Grub-menu (see the attachment), but i do not know what they mean. Are they snapshots of the OS? Is there a date associated with them? If there is a doc on that please share the url.

Thanks

---

