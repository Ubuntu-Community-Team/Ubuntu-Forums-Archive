---
title: "Ubuntu file permissions"
date: 2017-01-03
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2017-01-03
Hey everyone,

I am having a problem with file permissions. even i execute the chmod with correct locations.

I am using lampp, where first I give permissions to /opt/lampp/ with chmod 744.

after that I start lampp server.

but in past two days I couldnt install a wordpress plugin in wordpress locahost. 

also with that i am not able to save the codes on lampp location. the editor i use is brackets.

UPDATED: NOW THE WHOLE WORDPRESS DIRECTORY IS NOT ACCESSIBLE AFTER BECOMING ROOT AND CHANGING CHMOD'S

before weeks i havent give permissions stuffs like these. i just open the app and code and exit.

Note: I also gave FS Direct on wordpress config for connection. still it saying cannot create directory.

can anyone tell me what is the problem here?

UPDATED: AFTER BECOMING ROOT AND EXECUTING CHMOD ON LAMPP LOCATION, THE WHOLE WORDPRESS DIRECTORY IS NOT ACCESSIBLE.

---

### Post by Keith_Helms on 2017-01-03
First of all, don't give "4" (read only) permission to a directory.  You need to give "5" (read + execute).  Execute means can run as a command for a file, but it means can change directory into for a directory.  A directory with permission 4 is one you can't use.

I would recommend doing a little reading about permissions before using chmod.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by weirdygeekpsych on 2017-01-03
When I installed ubuntu , there was no problem for permissions like this. I just access file normally. but the scenario is changed now. whenever i have to use those apps. i have to open separate terminal windows and start the app. is there any solution to solve all in one thing ???


My question is why permissions are keep changing even I have given permissions to the files eariler.

---

