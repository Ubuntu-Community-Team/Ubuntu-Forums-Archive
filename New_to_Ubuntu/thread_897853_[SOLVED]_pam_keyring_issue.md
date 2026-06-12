---
title: "[SOLVED] pam keyring issue"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by Lorelei- on 2008-08-22
So to solve the problem of constantly being asked to unlock the default keyring I installed libpam-keyring. However when I try to edit the file (as recommended) to allow for a common password at login, I get this:

> kimmii@dell-desktop:~$ /etc/pam.d/gdm @include common-pamkeyring
bash: /etc/pam.d/gdm: Permission denied

how do I resolve this? so that I can have a common pam keyring as a default?

---

### Post by Lorelei- on 2008-08-22
Resolved the above but now I have another issue!

I rebooted my system after resolving the above and now it won't let me log in or anything. It just comes up with a GUI interface saying "Authentication failed" and won't let me do anything beyond that point.

How do I resolve this so that I can access my system again?

---

### Post by HalPomeranz on 2008-08-22
The command you posted does not edit the /etc/pam.d/gdm file-- what you're trying to do there is execute /etc/pam.d/gdm as a program, which is obviously not what you want to do.

You'll want to edit the file with a command like "sudo gedit /etc/pam.d/gdm" and add the line "@include common-pamkeyring" in the appropriate place.  Do your instructions specify whether you need to add the line at the beginning or the end of the file, or someplace in the middle?  Order is important in these files-- if you're not sure, make it the last line of the file.

---

### Post by Lorelei- on 2008-08-22
> **HalPomeranz said:**
> The command you posted does not edit the /etc/pam.d/gdm file-- what you're trying to do there is execute /etc/pam.d/gdm as a program, which is obviously not what you want to do.

You'll want to edit the file with a command like "sudo gedit /etc/pam.d/gdm" and add the line "@include common-pamkeyring" in the appropriate place.  Do your instructions specify whether you need to add the line at the beginning or the end of the file, or someplace in the middle?  Order is important in these files-- if you're not sure, make it the last line of the file.

hello, I did this bit and added it as the last line of the file. Then I rebooted my system and now it won't let me log in or anything as it just comes up with a box saying: "Authentication failed".

Help?

---

### Post by HalPomeranz on 2008-08-22
> **Lorelei- said:**
> 
I rebooted my system after resolving the above and now it won't let me log in or anything. It just comes up with a GUI interface saying "Authentication failed" and won't let me do anything beyond that point.

How do I resolve this so that I can access my system again?

Sounds like your change broke your PAM configuration, at least for the gdm GUI.  You'll need to log in and reverse the change you made /etc/pam.d/gdm.  There are two ways you can get into the system at this point:

1) Via the text-mode console, which you can access by typing Ctrl-Alt-F1 (Ctrl-Alt-F7 will take you back to the GUI login interface)

2) By booting off of an Ubuntu LiveCD (or other LiveCD distro)

The first is easier in that it doesn't require a reboot, but means you'll have to work with the command-line, which you may not be comfortable with.

---

### Post by Lorelei- on 2008-08-22
will try command line and see where i get to

---

### Post by Lorelei- on 2008-08-22
well the command line works up to a point, but i can't figure out how to access the gdm file to edit it as when i type in the gedit command (sudo gedit /etc/pam.d/gdm) it says:

cannot open display

so how do I get to it from here?

---

### Post by HalPomeranz on 2008-08-22
Graphical programs like gedit won't work in text mode.  Try "sudo nano /etc/pam.d/gdm"-- nano is a pretty simple text-mode editor.

---

### Post by HalPomeranz on 2008-08-22
By the way, once you fix the problem that's preventing you from logging in, you might check out this thread:

[http://ubuntuforums.org/showthread.php?t=796410](http://ubuntuforums.org/showthread.php?t=796410)

It talks about a (perhaps simpler) method for disabling the annoying gnome-keyring prompts.

---

### Post by Lorelei- on 2008-08-22
ended up just removing the file and now that I'm back on my system will uninstall pam keyring and then try again I think.

any ideas why it would've done that in the first place? don't want to make the same mistake twice but desperately want to make it so that it stops asking me for a password for the default keyring!

on the plus side, I've learnt some new bits of command line which is always helpful. I prefer doing stuff through command line if I can so that I can learn :)

---

### Post by HalPomeranz on 2008-08-22
> **Lorelei- said:**
> ended up just removing the file and now that I'm back on my system will uninstall pam keyring and then try again I think.


Removing the file is probably a bad idea in the long run.  You should probably re-create the original file.  Here's the default version:

```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password

```

> **Lorelei- said:**
> any ideas why it would've done that in the first place?


PAM configuration is a fiddly thing.  If you put the "@include" statement into the file in the wrong place, or if the common-pamkeyring file wasn't installed properly or contained an error, then you wouldn't be able to log in.

> **Lorelei- said:**
> don't want to make the same mistake twice but desperately want to make it so that it stops asking me for a password for the default keyring!

Again, per my post above, the solution you're looking for may be here:

[http://ubuntuforums.org/showthread.php?t=796410](http://ubuntuforums.org/showthread.php?t=796410)

> **Lorelei- said:**
> on the plus side, I've learnt some new bits of command line which is always helpful. I prefer doing stuff through command line if I can so that I can learn :)

That's it, stay positive!  :)

---

### Post by Lorelei- on 2008-08-22
think I'll just uninstall pam altogether and see how well the solution you posted works

---

### Post by Lorelei- on 2008-08-22
hmm it seems it won't uninstall it properly :-S

when I run the command: sudo apt-get remove libpam-keyring

It comes up with this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libpam-keyring is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so how can I uninstall this from my system?

---

### Post by HalPomeranz on 2008-08-22
Are you sure the package was successfully installed in the first place?  What results do you get if you run "dkpg --list | grep libpam-keyring"?

---

### Post by egalvan on 2008-08-22
> **HalPomeranz said:**
> Graphical programs like gedit won't work in text mode.  Try "sudo nano /etc/pam.d/gdm"-- nano is a pretty simple text-mode editor.

Under 8.04.1

```

 sudo gedit /etc/pam.d/gdm
```

works for me,

but I would still rather use

```

 gksudo gedit /etc/pam.d/gdm

```

:popcorn:

---

### Post by Lorelei- on 2008-08-22
*sigh* ended up having to reinstall my system to stop it having an almighty fit with itself.

---

