---
title: "[SOLVED] Problem with terminal and /dev/null error"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-19
When I start up terminal I get a error for about 5 seconds before it lets me run anything.  I have included a picture of the error.  Any help would be appreciated.

---

### Post by sdennie on 2008-05-19
What are the permissions on /dev/null?

```

ls -l /dev/null

```

---

### Post by alienexplorers on 2008-05-19
crw-rw-rw- 1 terminator terminator 2, 2 2008-05-19 02:58 /dev/null

have also tried root root and that caused the error too.

---

### Post by sdennie on 2008-05-19
I have no idea how the permissions got changed but, you could try the following:

```

sudo chown root:root /dev/null

```

---

### Post by alienexplorers on 2008-05-19
crw-rw-rw- 1 root root 2, 2 2008-05-19 02:58 /dev/null

Still getting the same error about bash and /dev/null

---

### Post by sdennie on 2008-05-19
I would try the following (it looks scary but, check "man null"):

```

sudo rm /dev/null
sudo mknod -m 666 /dev/null c 1 3
sudo chown root:root /dev/null

```

---

### Post by alienexplorers on 2008-05-19
Well that fixed the problem.  Many, many thanks.

---

### Post by sdennie on 2008-05-19
Glad it worked.  I'm still not sure how your /dev/null got into that state so it may revert.  It's possible that you have some errant udev rule that's making it do that.  You could check with:

```

grep terminator /etc/udev/rules.d/*
grep null /etc/udev/rules.d/*

```

The last command should return one line in 40-basic-permissions.rules

---

### Post by alienexplorers on 2008-05-19
grep null /etc/udev/rules.d* gives the following output:
> /etc/udev/rules.d/40-basic-permissions.rules:KERNEL=="null",			MODE="0666"
grep terminator /etc/udev/rules.d* gives no output.

---

### Post by sdennie on 2008-05-19
That looks correct.  If upon reboot or starting an app, you start to get the /dev/null errors again, it would be interesting to know what happened to get /dev/null in that state.

---

### Post by alienexplorers on 2008-05-19
I wish I knew what got /dev/null in that state to start with.  All I was doing is scanning threw the Ubuntu forums and went to try something in terminal and got that error before typing anything.

---

