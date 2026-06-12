---
title: "&quot;ssh localhost git pull&quot; fails immediately"
date: 2016-10-31
forum: Programming Talk
---

### Post by azzamite on 2016-10-31
Hello guys

I'm working with a script that enters some build servers and updates
the git repositories before building on each of them... for security
reasons we can't use password-less login.

The problem is that *git pull* isn't waiting for the user to provide the
password, instead it fails immediately, here is an example:

```
$ ssh localhost 'cd repo; git pull'
user@localhost's password: 
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,gssapi-keyex,gssapi-with-mic,password).
fatal: The remote end hung up unexpectedly
```

Any ideas?

---

### Post by reegz on 2016-10-31
How have you set up the repo URL? Run ```
git remote -v
``` to see what the URL looks like. I have a sneaky suspicion that your URL looks as follows:-

```
https://<username>:<password>@host
```

If it is the case that the password is included in the URL then it's a simple case of updating the URL to exclude the password. That should solve it.

If that still doesn't work, try resetting the git config.

```
 git config --global core.askPass ""
```

---

### Post by azzamite on 2016-10-31
> **reegz said:**
> 
```
 git config --global core.askPass ""
```

I saw that suggestion, but the thing is that I don't want to mess with other people's git configuration.

The solution I found was to add -xt while ssh'ing

```
ssh -xt localhost 'cd repo; git pull'
```

Now it works : )

---

### Post by reegz on 2016-10-31
Cool. You can also run that git command without the ***--global*** and in so doing only affect the changes on the project you're in.

---

