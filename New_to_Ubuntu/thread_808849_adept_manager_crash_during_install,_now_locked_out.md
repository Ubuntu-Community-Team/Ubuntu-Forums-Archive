---
title: "adept_manager crash during install, now locked out"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by secondary on 2008-05-26
I attempted installing a program firestarter from Adept (kubuntu 7.10) and it crashed.  


adept_manager crashed and caused the signal 6 (SIGABRT) **_so the database is now locked and will not unlock for further activity_**.

Please help if you are able, following is more information...

--

This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

---

### Post by miesnerd on 2008-05-26
so are you locked out of the package manager or the distro itself?
If you're locked out of the package manager, you can just log out and log back in, and you should be good to go. If that doesnt work, restarting will work for sure.

If you logout and login and are worried that adept is going to suck again, you can install synaptic if you want. You can do this and avoid using adept if you'd like by typing:
"sudo apt-get install synaptic" in the command line (without quotes)

If you cant get into the distro, you can try the recovery mode, and that's commandline.

If you're locked out of the distro, let us know, and we can go from there.

---

### Post by secondary on 2008-05-26
great, i'll start trying...

---

### Post by secondary on 2008-05-26
Fellow Texan,

adept_manager opens and says 

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself. yes | no | cancel?

I click yes, and adept crashes.  KDE crash handler comes back with a dialog offering the info stated above.  

Can i kill the process without trouble, and try adept again?  Or is there a file to delete, or something else to do?

---

### Post by secondary on 2008-05-26
[I could get in the distro, yes.]

I was crashing out of the Adept Manager, but I found the Adept Installer, and it went through the same process of trying to resolve the problem, and it succeeded.

I uninstalled the package, got the same error of trying to commit changes, and I think I am back to normal again.  Apparently my system thought the installer was still running??  Whatever the case, I think I am back on track.  Both Adept Installer and Adept Manager appear to be working fine.

Thanks! (from Fort Worth),
..Patrick..

---

### Post by miesnerd on 2008-05-27
hey im from funkytown too.
Im doing my time (grad school) in TN though.
Anyways, for future reference, the deal with package managers is that sometimes if they get an error that they cant handle, they lock you out.
Also, the same applies to running two package managers at the same time. The system is built so you cant run two package managers at the same time on purpose. When the package manager crashes, its not sending a signal that its done running.

---

### Post by miesnerd on 2008-05-27
It might help you to undestsand also that things such as kpackage, synaptic, adept, apt-get, aptitude, and dkpg all do the same thing, at different levels.
They are all package managers. They are kinda at different levels. The easiest to use are graphical ones, kpackage, adept, and synaptic. They are all based off apt-get though, and apt-get off dpkg, which is debian's way of handling packages.
Different types of linux use different package managers and different package types. This is really what makes or breaks a distro.

---

