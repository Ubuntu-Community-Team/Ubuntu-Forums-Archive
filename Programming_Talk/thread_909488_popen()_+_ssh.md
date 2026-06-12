---
title: "popen() + ssh"
date: 2008-09-03
forum: Programming Talk
---

### Post by alxlabs on 2008-09-03
I need to establish an ssh connecion from C program to another machine then run some commands thru ssh then close the ssh connection. So I did 

```

fp=popen("ssh -l username host");
if (fp)
{
    fprintf (fp, "userpassword\n");
    fprintf (fp, "somecommand\n"); 
}

```

 ...but it didn't work 'cause ssh stopped and asked for password. I did some googling and found that "For security reasons, ssh opens /dev/tty for reading user input". 

How can I code for ssh then?

---

### Post by sq377 on 2008-09-03
You could use a library instead of wrapping the binary.
[http://0xbadc0de.be/wiki/libssh:libssh](http://0xbadc0de.be/wiki/libssh:libssh)

---

### Post by el.pescado on 2008-09-03
You could set up public key authentication in ssh instead of password, so that you don't have to type your pw every time.

Link:
[http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

---

