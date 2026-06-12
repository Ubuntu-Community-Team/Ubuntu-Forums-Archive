---
title: "SSH and then run a command on the remote box in one terminal command"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by shubhamshukla7 on 2014-07-21
Hi,

I am supposed to ssh into a remote box and then open mysql client on that box. For that, I want to set up a terminal alias which first SSHs me into that box, and once I am in, it let's me run the command on the remote box to start mysql client. How can I set up an alias to do that? I tried something like this but that would help:

```
alias rdb='ssh -i my-pem.pem ec2-user@my-box.com && sudo mysql -uUSERNAME -pPASSWORD
```

---

### Post by Lars Noodén on 2014-07-21
Try 
```
alias rdb='ssh -i my-pem.pem ec2-user@my-box.com sudo mysql -uUSERNAME -pPASSWORD'
```

or 

```
alias rdb='ssh -i my-pem.pem ec2-user@my-box.com "sudo mysql -uUSERNAME -pPASSWORD"'
```

But why would you run the mysql client as root?  That part does not seem to be needed.  

Also, if you are using the certificate only for the mysql client, then you might be able modify the appropriate line in the server account's *authorized_keys* file to start with *command="/usr/bin/mysql -uUSERNAME -pPASSWORD" ...*  I know that works for keys, but there should also be a way for certificates, too.  See the section "authorized_keys file format" in the manual page for [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) for the authoritative description.

---

### Post by shubhamshukla7 on 2014-07-24
Thanks, Lars. But when I try either of the options, the terminal just sits and waits forever. Any clue what I might be missing? Thanks!

---

### Post by Lars Noodén on 2014-07-24
Maybe sudo needs you to force allocation of a pseudo-tty.  Does this work?

```

alias rdb='ssh -i my-pem.pem ec2-user@my-box.com "mysql -uUSERNAME -pPASSWORD"'

```

or this?

```

alias rdb='ssh **-t** -i my-pem.pem ec2-user@my-box.com "sudo mysql -uUSERNAME -pPASSWORD"'

```

Again, I'm pretty sure that running the mysql client as root is undesirable.

---

### Post by nerdtron on 2014-07-24
Running mysql -uUSERNAME -pPASSWORD on the remote machine will just log you into mysql and then what? It won't perform any queries that why is just sits there for ever. If you would like to perform a remote query to database or tables, that is the command you should put after the ssh part.

But before everything else, be you sure you can ssh on the box using the command:```
 ssh -i my-pem.pem [EMAIL="ec2-user@my-box.com"]ec2-user@my-box.com[/EMAIL]
```
Then when you are logged in the remote server, try a simple query in the bash prompt: ```
mysql -uUSERNAME -pPASSWORD -e "show databases"
```

If you have an output, now you can try joining the two commands from your computer:

Example: ```
ssh -i my-pem.pem [EMAIL="ec2-user@my-box.com"]ec2-user@my-box.com[/EMAIL] 'mysql -uUSERNAME -pPASSWORD -e "show databases"'
```

It should work but if it won't work, maybe the quotes or single quotes are wrong. At least you get the idea.

---

