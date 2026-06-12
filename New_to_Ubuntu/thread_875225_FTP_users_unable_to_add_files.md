---
title: "FTP users unable to add files"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by richiewrt on 2008-07-30
I have a ftp server set up, and the user can log in and see and download files just fine, but for some reason it won't allow them to add files to the directory. The directory is the users home directory so they should have permissions, so I don't know what the problem is. Could someone point me toward a solution.

Thanks

---

### Post by f37u5g0d on 2008-07-30
Just cause the FTP folder is in the home folder doesn't mean the permissions are set right.  You should double check them.

---

### Post by RbikeRider on 2008-07-30
I am actually about to start setting up an FTP server here in a few minutes as well.  I will go through my mental notes from a class a year or so ago and let you know when I have something for you to try.

---

### Post by richiewrt on 2008-07-30
Ok, the user that is login in via ftp is the owner of the directory, and has all privileges for that directory. I can ssh into the server and create files with that user, just can't add them through ftp.

---

### Post by richiewrt on 2008-07-30
Ok, I just though to double check this, If i FTP into the server on my ubuntu laptop, or in win xp, I can create files just fine with this user. It appears that this is only a problem on a MAC. I can connect on the mac, but am unable to create files?
Since I am not a mac person, i didn't realize that the connect to server didn't give write access to ftp, problem solved by installing cyberduck.

---

