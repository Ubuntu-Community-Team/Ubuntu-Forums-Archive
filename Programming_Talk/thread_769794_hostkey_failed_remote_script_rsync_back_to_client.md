---
title: "hostkey failed: remote script rsync back to client"
date: 2008-04-26
forum: Programming Talk
---

### Post by a_posse_ad_esse on 2008-04-26
I am working on a project, and for it a client machine triggers a script on a server through ssh.  The server script then must send back data to the client through rsync.  The command that gives the hostkey failure message (below) is, as far as the client is concerned:

```

ssh user@IP /script rsync --options /directory user@IP:/directory

```

This command returns:
```

Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).

```

Is there a better way to do this?  Thanks.

---

### Post by a_posse_ad_esse on 2008-04-29
The answer is adding to -t flag to ssh, telling the program that you are dealing with a remote host.  In this case, it allows rsync to prompt for the password.

---

