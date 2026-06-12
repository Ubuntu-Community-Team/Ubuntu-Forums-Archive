---
title: "Logon information at console"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by crashcoredump on 2008-05-22
In Fedora and Redhat the console info is stored in a file /etc/issue that will be seen when you login.

In Ubuntu when I *alt+ctrl+F7* over to a VTY I see this long text disclaimer. How do you edit that output?

Thanks in advance,

-Jayzao

---

### Post by PinkFloyd102489 on 2008-05-22
I thought it was stored in /etc/issue also? Check /etc/issue.net

This is the disclaimer I put in my server's /etc/issue:

```

***************************************************************************
                            NOTICE TO USERS


This computer system is the private property of its owner, whether
individual, corporate or government.  It is for authorized use only.
Users (authorized or unauthorized) have no explicit or implicit
expectation of privacy.

Any or all uses of this system and all files on this system may be
intercepted, monitored, recorded, copied, audited, inspected, and
disclosed to your employer, to authorized site, government, and law
enforcement personnel, as well as authorized officials of government
agencies, both domestic and foreign.

By using this system, the user consents to such interception, monitoring,
recording, copying, auditing, inspection, and disclosure at the
discretion of such personnel or officials.  Unauthorized or improper use
of this system may result in civil and criminal penalties and
administrative or disciplinary action, as appropriate. By continuing to
use this system you indicate your awareness of and consent to these terms
and conditions of use. LOG OFF IMMEDIATELY if you do not agree to the
conditions stated in this warning.

****************************************************************************

```

---

### Post by crashcoredump on 2008-05-23
Mine look like this.
I wonder if this the login message I see is specified by some logon variable in my bash_profile or bash.rc?

```
jayzao@Penguin:~$ cat /etc/issue.net 
Ubuntu 8.04
jayzao@Penguin:~$ cat /etc/issue
Ubuntu 8.04 \n \l

```

---

