---
title: "Using SSH"
date: 2019-11-10
forum: New to Ubuntu
---

### Post by jeremycollins2 on 2019-11-10
[B]SOLVED: I didn't enter the full path in the IdentityFile line: ~/.ssh/siteground
[/B]
Hello, I am trying to setup SSH on Ubuntu 18.04 but I'm having some issues. I created a config file located at ~/.ssh/config and in the file I have this:

```

Host siteground
        HostName mydomain.com
        User myusername
        Port 18765
        IdentityFile siteground

```

When I try to ssh into my Siteground server, I get this error:

```
*no such identity: siteground: No such file or directory*
*myusername@mydomain.com: Permission denied (publickey).*

```

However, if I am inside of the .ssh folder and try to login, it works as expected.

How can I make it so I can login anywhere using the Host in my Identity File?

---

### Post by Holger_Gehrke on 2019-11-10
By giving a **path** and filename to the IdentityFile directive.
```

Host siteground
        HostName mydomain.com
        User myusername
        Port 18765
        IdentityFile **~/.ssh/**siteground

```

Holger

---

### Post by jeremycollins2 on 2019-11-10
Thank you!!

> **Holger_Gehrke said:**
> By giving a **path** and filename to the IdentityFile directive.
```

Host siteground
        HostName mydomain.com
        User myusername
        Port 18765
        IdentityFile **~/.ssh/**siteground

```

Holger

---

