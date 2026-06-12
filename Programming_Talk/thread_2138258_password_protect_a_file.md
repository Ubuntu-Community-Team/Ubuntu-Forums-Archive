---
title: "password protect a file"
date: 2013-04-23
forum: Programming Talk
---

### Post by krool89 on 2013-04-23
Is it possible to password protect a file in c language..?? it is not encyrpt data

By this I mean that when anybody is going to view the file (whatever be  the way he choose) it will ask for a password and if valid password is  entered it will allow.
If any body found any hints or any suitable link just help me.

---

### Post by schragge on 2013-04-24
This has nothing to do with C per se. Make the file owned by specific user or group, restrict read permissions on it to that user/group, protect the user/group with a password, then use su/sg to access the file. I'd recommend making the file owned by root, creating an appropriate group, and using *sg* or *newgrp* for this.

See manpages for [addgroup]("http://manpages.ubuntu.com/manpages/quantal/en/man8/addgroup.8.html"), [gpasswd]("http://manpages.ubuntu.com/manpages/quantal/en/man1/gpasswd.1.html"), [chown]("http://manpages.ubuntu.com/manpages/quantal/en/man1/chown.1.html"), [chgrp]("http://manpages.ubuntu.com/manpages/quantal/en/man1/chgrp.1.html"), [chmod]("http://manpages.ubuntu.com/manpages/quantal/en/man1/chmod.1.html"), [sg]("http://manpages.ubuntu.com/manpages/quantal/en/man1/sg.1.html"), [newgrp]("http://manpages.ubuntu.com/manpages/quantal/en/man1/newgrp.1.html").

---

### Post by nvteighen on 2013-04-25
schragge's solution is a good one, but system-dependent and it doesn't really give you password-protection as you might know it from, e.g. OpenOffice.

If you want to write a program that password protects some file, then you do want encryption: your password will be the key needed to decrypt the file into some human-readable format. The GNU crypt library supports DES encryption and there are other libraries that might be useful to you. If you want to encrypt a whole directory hierarchy, there's EncFS (although I'm not sure if there's a library for it... of not, call it from shell).

---

### Post by wolfgentleman on 2013-04-25
If the file is not an executable, what you want is not possible - at least not OS independent. You would have to encrypt it. If you do decide to encrypt, my suggestion is PGP keys.

---

