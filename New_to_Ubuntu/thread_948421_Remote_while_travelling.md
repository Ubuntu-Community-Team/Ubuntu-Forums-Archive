---
title: "Remote while travelling"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by donnyc on 2008-10-15
Hi there, I am a newbie to Ubuntu. I have a client that is traveling out of the country. He is using a Windows laptop and wishes to access his Samba files. Although I can use VNC to get him to connect, How do I configure to allow him to connect in a GUI way as he is fairly computer illiterate and wants to open windows files through a Windows interface?

Thanks

---

### Post by Orange_and_Green on 2008-10-15
How about a desktop shortcut that points to \\server_name\path\subpath\etc ?

(edit)I guess I am still a little confused over this post even after giving it more thought... What we do at the place where I work is to have the client connect to our network with OpenVPN and then have them connect directly to the server.

---

### Post by low-res on 2008-10-15
Don't use plain VNC cause it's unencrypted.
You could try something like "fish".
It's filebrowsing over ssh.

---

### Post by superprash2003 on 2008-10-15
how about ftp.. thats pretty ok.. good GUI.. etc..

---

