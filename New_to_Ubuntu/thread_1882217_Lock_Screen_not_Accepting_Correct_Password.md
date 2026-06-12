---
title: "Lock Screen not Accepting Correct Password"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by flyingscotsman74656 on 2011-11-16
I am having an issue with my Ubuntu 11.10 installation that started after my password expired on my only account (this was due to my setting the Gnome security settings incorrectly). After unlocking the account I was able to change the password without issue. My problem is that whenever I lock my screen, the correct user password is not accepted at all. In order to regain the use of my system I need to switch the user, and then relogin to my user, which strangely enough works without a problem with the exact same password that the lock screen rejects. I have found this forum ([http://ubuntuforums.org/archive/index.php/t-804647.html](http://ubuntuforums.org/archive/index.php/t-804647.html)) that details some solutions, but even after trying to reset ownership and permissions of /etc/shadow and /sbin/unix_chkpwd (which I later determined weren't broken in the first place) I cannot use my lock screen to log back in. I have no idea where else to look, would my password expiring have set some obscure settings that only the lock screen looks at? Shouldn't all login dialogs use the same means to look up my password? Thanks for any help, I do appreciate it!

---

### Post by flyingscotsman74656 on 2012-02-05
I ended up simply reinstalling the system, I am not well-versed enough in the ways of Ubuntu to guess why that occurred. If anyone does have some idea I would be extremely grateful in case it occurs again.

---

### Post by taekker on 2012-02-05
I have a same kind of problem. while trying to install a printerdriver i'm asked for a password and it doesn't accept the right password. What can I do?

---

