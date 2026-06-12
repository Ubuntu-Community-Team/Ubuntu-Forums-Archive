---
title: "help with ssh"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by a_weasel on 2008-10-12
I want to remotely connect to my school server, using X11 tunneling and to transfer files. I'm able to get in, but I can't get X11 enabled, nor can I figure out how to transfer.

Here's what i'm gettin for X11 (supposedly the commands -X and -Y should enable it, but I guess i'm having a usage issue).

```

daren@daren-laptop:~$ ssh -X
usage: ssh [-1246AaCfgKkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]yadayada

```


and for file transfer: (In this exaple, i've already logged in)

```

cory [6] ~/projdump/proj1 > scp draw.java daren@daren-laptop:~/Documents/draw.java
ssh: daren-laptop: node name or service name not known
lost connection

```

---

### Post by iponeverything on 2008-10-12
> **a_weasel said:**
> I want to remotely connect to my school server, using X11 tunneling and to transfer files. I'm able to get in, but I can't get X11 enabled, nor can I figure out how to transfer.

Here's what i'm gettin for X11 (supposedly the commands -X and -Y should enable it, but I guess i'm having a usage issue).

```

daren@daren-laptop:~$ ssh -X
usage: ssh [-1246AaCfgKkMNnqsTtVvXxY] [-b bind_address] [-c cipher_spec]yadayada

```


and for file transfer: (In this exaple, i've already logged in)

```

cory [6] ~/projdump/proj1 > scp draw.java daren@daren-laptop:~/Documents/draw.java
ssh: daren-laptop: node name or service name not known
lost connection

```

Try "ssh -X some.school.server.net"

Where some.school.server.net is your school server.

scp:

```
scp draw.java daren@IP-of-your-home-machine:~/Documents/draw.java
```

---

