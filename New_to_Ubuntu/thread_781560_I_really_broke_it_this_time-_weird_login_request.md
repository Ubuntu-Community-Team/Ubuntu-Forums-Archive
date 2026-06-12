---
title: "I really broke it this time- weird login request??"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by friendofpugs on 2008-05-04
Hi all,

I've been running Hardy w/o any problems until last night. I must've done something wrong because when I login, at the desktop I immediately get "Enter password for default keyring to unlock. The app nm-applet (usr/bin/nm-applet) wants access to the keyring but it is locked." I enter my password and proceed to the desktop, but my system is so slow; through the system monitor I see that my processor is tanking, RAM is through the roof. I also have Screenlets enable, but my system sensor ringlets are duplicated and going wacky. Anyway, when I try to use my touchpad to move the cursor, the screen flickers and kicks me out to the login screen. What's going on?

---

### Post by luckyuser on 2008-08-31
This might work:

 Re: [SOLVED] Keyring trouble
I found a solution in the archives from May.

"To get rid of the keyring prompt after automatic login in Hardy 8.04 you can:

System>Preferences>Encryption and Keyrings
Under Password Keyrings click o 'login Automatically unlocked when user logs in.'
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank."
Click OK

This did it for me.

The downside of this workaround is that it leaves your password exposed to anybody who has access to your files.

from thread: [http://ubuntuforums.org/showthread.php?p=5698832#post5698832]("http://ubuntuforums.org/showthread.php?p=5698832#post5698832")

---

### Post by billgoldberg on 2008-08-31
You must have done something, this won't happen by itself.

I don't know what would cause that, so unless you remember what you did I doubt we will be able to help you.

--

If you can't fix it, back up your data, do a fresh reinstall.

---

### Post by Line on 2008-09-13
Hi! I had the same problem after i selected automatic login in my newly insalled 8.04.1. If i clicked "deny" i had to write the wireless WPA password manually, sounds like a bug to me :)

---

