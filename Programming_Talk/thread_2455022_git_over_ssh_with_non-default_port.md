---
title: "git over ssh with non-default port"
date: 2020-12-10
forum: Programming Talk
---

### Post by spjackson on 2020-12-10
We've recently changed hosting provider and are having trouble getting git working.

ssh works with authorized_keys so:
```

$ ssh user@myhost -p NNNNN

```
works, giving me a shell (albeit a jailshell) and I can see the repos in the right place, owned by the user I am connecting as with read-write permission. git is found in the path.

However, if I try to clone the repo, I get:
```

$ git clone ssh://user@myhost:NNNNN/path/to/repo.git
Cloning into 'repo'...
ssh: connect to host myhost port NNNNN: Connection timed out
fatal: Could not read from remote repository. Please make sure you have the correct access rights
and the repository exists.

```

This isn't a temporary failure: it repeats consistently.

---

### Post by TheFu on 2020-12-10
Just setup a ~/.ssh/confg file with an alias for that connection.
I remember when I learned about that - changed my life.  All ssh-enabled programs/libraries honor those configs.

---

### Post by spjackson on 2020-12-11
> **TheFu said:**
> Just setup a ~/.ssh/confg file with an alias for that connection.
I remember when I learned about that - changed my life.  All ssh-enabled programs/libraries honor those configs.
Thanks. That's helpful so I can now do:
```

$ git clone myalias:/path/to/repo.git

```
but that still didn't work - same timeout error.

It turns out that for this server, the URL must have a trailing /, which is not the case on other servers that I've cloned from. So the following works.
```

$ git clone myalias:/path/to/repo.git/

```

---

