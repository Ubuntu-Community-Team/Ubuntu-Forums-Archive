---
title: "sftp automation and cronjob"
date: 2012-11-14
forum: Programming Talk
---

### Post by yma981 on 2012-11-14
Hello 

I need to upload a txt file to a server once per day on a specific time. Is the a way to use sftp and cronjob to do the task?

10x

---

### Post by Lars Noodén on 2012-11-14
[sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html) can use keys for authentication, use the -i option.  That is the best way to do it.  

You can even put the keys in an agent and use that in cron, though that takes a little planning.

You can also make the key single purpose and lock it to using sftp by prepending the key with a forced command.  

```

[s]command="/usr/libexec/sftp-server" ssh-rsa AAAAB3NzaC1yc2EAA...[/s]
command="/usr/lib/openssh/sftp-server" ssh-rsa AAAAB3NzaC1yc2EAA...

```

Edit: Once you have keys working, you can use batch mode (-b) to do the upload.

---

### Post by Bachstelze on 2012-11-14
For a single file, scp would probably be better (but the same things apply for authentication, of course).

---

