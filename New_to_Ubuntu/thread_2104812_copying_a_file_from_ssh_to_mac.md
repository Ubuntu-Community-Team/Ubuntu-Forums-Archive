---
title: "copying a file from ssh to mac"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by jhuuht9 on 2013-01-14
Hello,

I'm using a ssh linux server and I'm trying to copy a file from that server to my mac:

scp jhuuhtan @linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf /Users/juliahuuhtanen/Documents
jhuuhtan @linappserv0.pp.rhul.ac.uk's password: 
/Users/juliahuuhtanen/Documents: No such file or directory

What am I doing wrong, if I want to copy that file to my computer?

---

### Post by jhuuht9 on 2013-01-14
[QUOTE=jhuuht9;12454603]Hello,

I'm using a ssh linux server and I'm trying to copy a file from that server to my mac:

scp jhuuhtan @linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf /Users/juliahuuhtanen/Documents
jhuuhtan @linappserv0.pp.rhul.ac.uk's password: 
/Users/juliahuuhtanen/Documents: No such file or directory

What am I doing wrong, if I want to copy that file to my computer?

I left a gap in jhuuht @ on purpose because it starts assuming its e-mail here and does something weird to the text on the forum.

---

### Post by SlugSlug on 2013-01-14
try

```
scp jhuuhtan@linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf .
```

the '.' will use your current directory

---

### Post by jhuuht9 on 2013-01-14
> **SlugSlug said:**
> try

```
scp jhuuhtan@linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf .
```

the '.' will use your current directory

It gives me this

scp [email]jhuuhtan@linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf[/email]
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2
[linappserv0]%~>

---

### Post by steeldriver on 2013-01-14
I think maybe you need full path to the remote file

```
scp user@remotehost:/path/to/file .
```e.g.

```
$ scp steeldriver@192.168.1.102:/home/steeldriver/file .
steeldriver@192.168.1.2's password: 
file
$ ls -l file
-rw-rw-r-- 1 steeldriver steeldriver 9 Jan 14 09:38 file               

```

---

### Post by SlugSlug on 2013-01-14
> **jhuuht9 said:**
> It gives me this

scp [EMAIL="jhuuhtan@linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf"]jhuuhtan@linappserv0.pp.rhul.ac.uk:~/MCFM/Bin/LOdeltasigbkg.pdf[/EMAIL]
usage: scp [-1246BCpqrv] [-c cipher] [-F ssh_config] [-i identity_file]
           [-l limit] [-o ssh_option] [-P port] [-S program]
           [[user@]host1:]file1 [...] [[user@]host2:]file2
[linappserv0]%~>


looks like you missed the . out ?

---

### Post by jhuuht9 on 2013-01-14
> **SlugSlug said:**
> looks like you missed the . out ?

Where exactly did I miss ".out"?

---

### Post by dannyboy79 on 2013-01-14
at the very end of the command, the . (dot) represents the current working directory as he stated.

---

