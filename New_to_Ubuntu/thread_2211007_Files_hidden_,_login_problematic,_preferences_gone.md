---
title: "Files hidden , login problematic, preferences gone"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by bjngchn on 2014-03-13
Installed encrypted Lubuntu 13.10 on an older computer. It had problems, but it was ok. Suddenly there are new problems making the computer useless. ..........Problem 1: Can't login to the main account graphically. Login screen refreshes instead of showing desktop (but can login to another user account, and the remaining problems are about that account)................. Problem 2: Firefox starts in its default state. Many modifications disappeared. ............Problem 3: And this is the main problem: Directories/files under home directory can't be seen, except  for newly created ones (created after this error). There are new files on home directory of this user (secondary user but became admin and sudoer) Access-Your-Private-Data.desktop and README.txt . They contain this info: On command line run: ecryptfs-mount-private . When I type this command here is the error: ERROR: Encrypted private directory is not setup properly.... Until now it was working ok. What happened to make it not work suddenly.

---

### Post by ajgreeny on 2014-03-13
It looks as if your home is now owned by root or something else, rather than by you, though the encryption may also be the reason for your problem and that is something I know nothing about.
Boot to the user you can use successfully and who has admin rights, and run ```
sudo chown -R username:username /home/username
```changing username to your problem user, of course, not the one from where you're running the command.

---

### Post by bjngchn on 2014-03-14
This is not the problem, because I tried this and it didn't work.

---

### Post by bjngchn on 2014-03-14
I use this command:     sudo ecryptfs-recover-private   .... after doing what it says, it says: INFO: Success! Private data mounted at [/tmp/ecryptfs.*] * here is a random looking extension.  When I go to that directory under /tmp/ I see those directories I can't access under /home/user ,; and maybe I can copy them somewhere (but they seem encrypted when opened with dolphin (ok , they are also encryppted when browsed with command line now (but not a few minutes ago)))... but I prefer to see them at their usual location using Dolphin..... Also the main account is not accessible except with command line at ctrl+alt+f1.

---

### Post by bjngchn on 2014-03-17
Ok. sudo ecryptfs-recover-private worked this time by luck.

---

