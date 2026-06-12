---
title: "disable compiz-fusion at boot?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-29
So on my laptop compiz fusion basically locks up the computer when it tries to run at boot. I can start in the failsafe GNOME session and go about my buisness, but I can't find a way to stop compiz from running without uninstalling it. It still works fine if I start it after the computer has loaded so I dont wanna just kill it off.

---

### Post by Amarsingh0793 on 2008-10-29
Go to System > Preferences > Session. Then click add and put this command in the command field:

"metacity --replace"
(without the quotes)

Name the command whatever you want to name it. Then test and see if it works - log out and try logging in again.

Hope this helps :)

---

### Post by medic2000 on 2008-10-29
Also go look for the `Sessions` if there is a compiz ticked to start at boot cancel it.

---

### Post by DoubleMcLovin on 2008-10-29
EDIT:

After a reboot this command worked =D tyvm

---

