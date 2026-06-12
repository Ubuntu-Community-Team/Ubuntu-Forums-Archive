---
title: "trash won't trash"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by sandskev on 2008-08-25
hi, I moved some mac made files from a dvd over to my freshly installed 8.04 desktop, kept some, and trashed others, but the files in the trash won't go! i get an error message saying permission denied, but when i try to alter permissions, it says, ' not supported by the backend' whatever that means! the files have no lock emblem on them, but if i move them to the desktop they do........i'm confused, so any tips and tricks will be appreciated.

---

### Post by Ryadt on 2008-08-25
Try ```
gksu nautilus
```
This will give you temporary root privileges and delete them from there.

---

### Post by SunnyRabbiera on 2008-08-25
are the files locked by any chance?
go into a terminal and try the command above and make your way to /home/(your user name here)/.local/share/Trash/files
This is a hidden directory in your home folder, to unhide it hit ctrl+h

---

### Post by sandskev on 2008-08-26
Thanks all the very quick replies, I followed the instructions, and it worked a treat!

---

### Post by firedevilbg on 2008-08-29
I have the same problem and with you help I solved it! 10x  :guitar:

---

### Post by Crafty Kisses on 2008-08-29
-Do Alt+F2
-Type gksudo nautilus and enter your password
-You should now be in your root folder
-Navigate to your home folder and enter the hidden folder .Trash (To view hidden files and folders do Ctrl+H)
-Delete the files
-Go back to the Root folder
-There is a .Trash in there as well if it doesn't show try Ctrl+H again
-Now delete the files from there as well
-They should be gone for good at this point

---

