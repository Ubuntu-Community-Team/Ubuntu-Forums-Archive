---
title: "Command for file uploading to web server"
date: 2015-09-28
forum: New to Ubuntu
---

### Post by Danial_Rana on 2015-09-28
Is there any command in LINUX that will allow me to upload any file type to a dedicated we server?

---

### Post by Bucky Ball on 2015-09-28
Without more detail it is virtually impossible to give you much/any help. 

What you are trying to do and what file type you are talking about would be a good start. Also, Ubuntu flavour and release. :)

Please read the third link in my signature.

You can upload any file you like to a webserver using Filezilla or something like it. Never heard of specific commands for uploading filetypes, but then, I have no idea what you're doing.

---

### Post by Lars Noodén on 2015-09-28
Your server is probably running SSH which means you can use SFTP to transfer the files.  As mentioned above, FileZilla can do that graphically.  So can [Nautilus](https://www.youtube.com/watch?v=9S4DV1PluzA) with comes with Ubuntu out of the box.

But if you are looking for a way to do it via the shell, then you can use [sftp](http://manpages.ubuntu.com/manpages/trusty/en/man1/sftp.1.html):

```

sftp *user*@*server.example.com*

```

Substitute your own remote user's name and the name or ip address of your remote machine.

(PS.  If you haven't done so already, it is considered a good idea to enable key-based authentication and disable password login on the remote machine.)

---

### Post by Danial_Rana on 2015-09-29
Actually i want to implement post command in curl library to upload text files to a remote server.

---

### Post by Lars Noodén on 2015-09-29
It looks like curl does support SFTP, but you can use the regular SFTP client in [batch mode](http://manpages.ubuntu.com/manpages/trusty/en/man1/sftp.1.html) which would give your script more options.  You would also need keys for that arrangement.

---

