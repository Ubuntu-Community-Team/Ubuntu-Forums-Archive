---
title: "User Privileges"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-11-20
Hi guys,
I'd just like to add some users for the FTP. Need remote one with no access to any directory except the home/FTP-shared directory, the user should also only be able to download and upload.
Does anyone know how to set specific folder access to a user? Is it even possible? Or must all access be determined by folder settings?
Thanks for considering :)
Rob

---

### Post by racmar on 2008-11-20
It really depends on the ftpd package you are planning to use.  For instance, vsftpd has virtual users.

See:
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/")

However, I suggest using ssh ( with scponly ) for better security than ftp.

---

### Post by hungryOrb on 2008-11-20
Oh wow, thanks racmar =)
I'm using proftpd at the moment. I'll look for some info :D
Rob

---

### Post by racmar on 2008-11-20
You are welcome.  If you're using proftpd, then see this how-to on virtual users:
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html]("http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-VirtualUsers.html")

---

### Post by hungryOrb on 2008-11-21
Thanks racmar,
At first I thought you just use normal ubuntu users to access the FTP, which worked seemingly ok. Then when I hear about virtual users, it seems like there is another layer of user control that must be used for security reasons. But then, I look through the man commands and cannot find any explicit instruction on creating a virtual user.. So conclude that I'm just assuming wrongly, and there is some significance attached to virtual users that I simply didn't grasp :(

You wouldn't be able to put it into a sentence for the less-informed would you? :(
Thanks for considering :)

---

### Post by racmar on 2008-11-21
AFAIK, there is a difference.  Regular user accounts could be used to login to the system and poke around.  Plus, they can be harder to administer and keep away from other services.  A non regular user is usually setup in a single text file and is more strictly controlled.

Also, you can ( depending on the ftp package ) use regular or virtual users, its a matter of choice.

My personal preference is to use only virtual users for safety reasons.  But your needs may be different.  YMMV.

---

