---
title: "Pidgin passwords"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by saintiria on 2008-06-05
Can anybody please tell me where pidgin stores the passwords or does it just check them through the internet?

---

### Post by drs305 on 2008-06-05
The pidgin files are stored in ~/.purple 
The passwords are stored in accounts.xml file and are NOT encrypted. 
/home/username/.pidgin/accounts.xml

---

### Post by drs305 on 2008-06-05
After posting the answer, I was a bit disturbed by the lack of password security. I just started using pidin last week. I did a search and learned there is a patch to fix this. Ubuntu Geeks offers a solution at: [http://www.ubuntugeek.com/fix-for-master-password-expose-for-pidgin.html]("http://www.ubuntugeek.com/fix-for-master-password-expose-for-pidgin.html")

Just saw the patch is for versions earlier than the current version (2.4.1). I was unable to get the patch to take and cannot find a patch for the current version.

---

