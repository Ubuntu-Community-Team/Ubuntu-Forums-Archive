---
title: "How to Hide Username/Passwords in shell scripts"
date: 2014-05-04
forum: Programming Talk
---

### Post by secoonder on 2014-05-04
Hello
i am using Ubuntu 12.04 Lts.
&#305; wrote script for backup.this script is executed by cron every night for file transfer
For ex:
User name:user
Pass :123
Remote ip :1.2.3.4
_**My script is : wget  [ftp://user:123@1.2.3.4/abcd.gbk.zip*](ftp://user:123@1.2.3.4/abcd.gbk.zip*)**_
How to hide Username and password in script?
&#304;s it impossible ?
Can you help me .Thank you.
Regards

---

### Post by ofnuts on 2014-05-05
Not really because at some point user/pwd will be in the clear in the wget command anyway. Your best bet is to make the script readable only by those who can run it.

Using wget to retrieve file using the ftp protocol is a bit of overkill considering that there is a ftp client on all Linux machines. This FTP client can retrieve user/password from a user-specific .netrc file which may be a bit easier to control access to.

---

### Post by Habitual on 2014-05-07
sftp protocol with ssh-key?

---

### Post by secoonder on 2014-12-25
Habitual Thanks.
 i tried sftp user@1.2.3.4 command , and solved it
Thanks a lot

---

### Post by Habitual on 2015-01-13
You are very welcome.

---

