---
title: "how to put /var/cache/apt/ as a repository server"
date: 2005-02-04
forum: Repositories &amp; Backports
---

### Post by Razvan on 2005-02-04
Hey Guys,

i want to put the files that synaptic already downloaded to sit in my apache as a local (incomplete) mirror of the "real world" ubuntu repository so all the other ubuntu machines in my network can load them from my machine and dont have to use internet bandwith (wich costs money in some contries :-) )

i found mini-dinstall to do that for me.

here is what i did:

i wrote that 

```
[DEFAULT]
archivedir = /var/www/ubuntu
incoming = /var/www/ubuntu/incoming
archive_style = simple-subdir
```

into my config file

and get the following output

```
root@razvan:~ # mini-dinstall -c .mini-dinstall.conf -r -v /var/cache/apt/archives
Traceback (most recent call last):
  File "/usr/bin/mini-dinstall", line 256, in ?
    sock.connect(socket_name)
  File "<string>", line 1, in connect
socket.error: (111, 'Connection refused')
```

what should i do? how do i get dinstall to load the archives into my apache?

thanks, Martin

ps: sorry for my english, i hope you can understand me

---

