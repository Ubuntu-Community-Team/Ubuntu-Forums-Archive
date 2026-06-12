---
title: "[SOLVED] Cannot set Launchpad username in Bazaar"
date: 2008-10-05
forum: Programming Talk
---

### Post by snova on 2008-10-05
I recently created an account on Launchpad (no idea what I'm going to do with it), and everything is set up correctly, but I'm getting an error when trying to use it with Bazaar.

```

xxxx@xxxxxxxx[02:56]:~$ bzr lp-login snova
bzr: ERROR: Connection error: curl connection error (Problem with the SSL CA cert (path? access rights?))
on https://launchpad.net/%7Esnova/%2Bsshkeys
xxxx@xxxxxxxx[02:57]:~$

```

I can access the page from a web browser, and it looks like the SSH key I uploaded earlier today.

This is bazaar 1.7.1 as obtained from the PPA repository a few hours ago. 1.6 does not work either, I already tried.

On the off chance that logging in first might have helped, I just tried, and there was no difference. Oh well.

Oddly enough, I can push and checkout branches without any problems. I wonder if setting the username is even useful, since it seemed to be irrelevant to normal usage.

Has anybody else had this problem? How can I fix this? Why bother?

---

### Post by mssever on 2008-10-05
> **snova said:**
> ```

xxxx@xxxxxxxx[02:56]:~$ bzr lp-login snova
bzr: ERROR: Connection error: curl connection error (Problem with the SSL CA cert (path? access rights?))
on https://launchpad.net/%7Esnova/%2Bsshkeys
xxxx@xxxxxxxx[02:57]:~$

```
Looks to me like a problem with your SSH key. Presumably something will eventually fail if you can't log in to Launchpad. I'm surprised you're able to push. That shouldn't work.

---

### Post by snova on 2008-10-05
Yes, but what? I checked again, and the SSH key looks exactly like the one in ~/.ssh/id_rsa.pub.

It gives me the same error when I try to run the command with other, invalid usernames.

I think it's a connection problem rather than an SSH problem, possibly something to do with certificates. But that doesn't make any more sense, because it lets me push branches.

Specifically, if I register a branch 'test' in Launchpad:

```

xxxx@xxxxxxxx[06:31]:~/Desktop$ mkcd test
xxxx@xxxxxxxx[06:32]:~/Desktop/test$ bzr init
Standalone tree (format: pack-0.92)
Location:
  branch root: .
xxxx@xxxxxxxx[06:32]:~/Desktop/test$ touch silly-file
xxxx@xxxxxxxx[06:32]:~/Desktop/test$ bzr add
added silly-file
xxxx@xxxxxxxx[06:32]:~/Desktop/test$ bzr commit
Committing to: /home/xxxx/Desktop/test/
added silly-file
Committed revision 1.
xxxx@xxxxxxxx[06:32]:~/Desktop/test$ bzr push lp:~snova/+junk/test
Enter passphrase for key '/home/xxxx/.ssh/id_rsa':
bzr: ERROR: Target directory lp:~snova/+junk/test already exists, but does not have a valid .bzr directory. Supply --use-existing-dir to push there anyway.
xxxx@xxxxxxxx[06:32]:~/Desktop/test$ bzr push lp:~snova/+junk/test --use-existing-dir
Enter passphrase for key '/home/xxxx/.ssh/id_rsa':
Created new branch.
xxxx@xxxxxxxx[06:33]:~/Desktop/test$

```

And Launchpad recognizes the revision and file when browsing it online.

Similarly:

```

xxxx@xxxxxxxx[06:36]:~/Desktop$ mkcd test2
xxxx@xxxxxxxx[06:36]:~/Desktop/test2$ bzr co lp:~snova/+junk/test
Enter passphrase for key '/home/xxxx/.ssh/id_rsa':
xxxx@xxxxxxxx[06:37]:~/Desktop/test2$ cd test
xxxx@xxxxxxxx[06:37]:~/Desktop/test2/test$ ls
silly-file
xxxx@xxxxxxxx[06:37]:~/Desktop/test2/test$

```

---

### Post by snova on 2008-10-05
The nice people on #bzr were able to solve this for me. Apparently it's a Curl thing, so I simply removed the package. One other package depended on it, but since I don't remember how it got there in the first place, that went too.

---

