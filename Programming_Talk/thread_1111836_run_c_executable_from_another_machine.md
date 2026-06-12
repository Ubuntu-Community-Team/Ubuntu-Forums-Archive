---
title: "run c executable from another machine"
date: 2009-03-31
forum: Programming Talk
---

### Post by bilol on 2009-03-31
Hi friends,
I have two machines X and Y connected via LAN in ubuntu 8.04.I have a C executable (say, a.out) in machine X. I want to run that a.out from machine Y via a C application (say, myApp.c ). 
I want the following:
Whenever the user , sitting in Y,runs myapp.c the control goes to machine X, execute a.out there and show the result in Y.

Please tell me the steps Or give links to some tutorials.
Thanks in anticipation......

---

### Post by dwhitney67 on 2009-03-31
Try using:
```

ssh remoteIP command

```

For example:
```

ssh acme.com /usr/local/bin/complete-sale

```

If you do not want to be prompted for an SSH password, then setup your systems so that they share public keys.

---

