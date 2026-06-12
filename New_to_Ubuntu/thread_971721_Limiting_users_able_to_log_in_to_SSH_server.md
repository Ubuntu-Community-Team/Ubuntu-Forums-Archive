---
title: "Limiting users able to log in to SSH server"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by telekarlsen on 2008-11-05
I'm running some server applications on my 8.10 (Desktop version), SSH and FTP among them.
Of course my own user is able to log into my SSH server, **but so is also the FTP user**, whose username and password I have distributed to some of my friends.

Question:
How can I limit the SSH login to one single, spesific user?
(And leave the FTP user only able to log in to my FTP server?)


Thank you.

---

### Post by mister_pink on 2008-11-05
Yes you can. You need to edit /etc/ssh/sshd_config and add to the end:

AllowUsers yourusername

---

### Post by telekarlsen on 2008-11-05
Thank you, Mr. Pink

That was exactly what I was looking for

- and it works! :-D



Edit:
Remember to reload the sshd-config:
```
sudo /etc/init.d/ssh reload
```

---

### Post by jmirick on 2008-11-14
Egad, my issue too, I had tried to restrict the logins by editing the user shell to be /bin/false, however this didn't work (at least for vsftpd) as it wouldn't allow it to connect at all (I am using FileZilla as the client).  The above solution is great because it makes you specifically state which people have SSH privileges, which is what you want.

---

