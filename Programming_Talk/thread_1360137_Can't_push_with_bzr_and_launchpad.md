---
title: "Can't push with bzr and launchpad"
date: 2009-12-20
forum: Programming Talk
---

### Post by finer recliner on 2009-12-20
Hey, I'm a n00b just getting started with bzr + launchpad hosting. I'm trying to push a test project using the following command: 

```
bzr push lp:~finerrecliner/+junk/test
```

but I always get the following error:
> Permission denied (publickey).
bzr: ERROR: Connection closed: Unexpected end of message. Please check connectivity and permissions, and report a bug if problems persist. 


I've been following the directions from here: [http://doc.bazaar.canonical.com/bzr.dev/en/mini-tutorial/index.html](http://doc.bazaar.canonical.com/bzr.dev/en/mini-tutorial/index.html)

I tried making an ssh key as recommended on another site, and submitted it to Launchpad, but it still won't work.

What am I missing??

---

### Post by davidboy on 2009-12-20
Nothing.  It's a bug.  Run 'unset SSH_AUTH_SOCK' and then it should work.  See [here]("http://www.launchpad.net/ubuntu/+source/gnome-keyring/+bug/328127") for the bug report on launchpad.

---

### Post by finer recliner on 2009-12-20
That bug seems to have been fixed in 9.10 (which I'm running). I tried to unset $SSH_AUTH_SOCK anyways, but it didn't help. Any other ideas?

---

### Post by nvteighen on 2009-12-21
I recall having problems using RSA keys in Launchpad even though they recommend them... Try using DSA/DSS by using:
```

ssh-keygen -t dsa

```

You can take a look on DSA at: [http://en.wikipedia.org/wiki/Digital_Signature_Algorithm](http://en.wikipedia.org/wiki/Digital_Signature_Algorithm) if you feel curious :)

---

