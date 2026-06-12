---
title: "Egrep regular expression to match a line in auth.log"
date: 2006-02-16
forum: Programming Talk
---

### Post by diebels on 2006-02-16
I'm trying to filter out lines like these:
```
Feb 15 10:22:27 localhost sshd[4676]: Invalid user massimiliano from ::ffff:83.103.27.85
Feb 15 10:22:29 localhost sshd[4680]: Invalid user mattia from ::ffff:83.103.27.85
Feb 15 10:22:29 localhost sshd[4678]: Invalid user huber from ::ffff:124.0.75.231
Feb 15 10:22:30 localhost sshd[4682]: Invalid user melchiorre from ::ffff:83.103.27.85
Feb 15 10:22:32 localhost sshd[4684]: Invalid user kaiser from ::ffff:124.0.75.231
Feb 15 10:22:34 localhost sshd[4688]: Invalid user mizio from ::ffff:83.103.27.85
Feb 15 10:22:35 localhost sshd[4686]: Invalid user kaiser from ::ffff:124.0.75.231
Feb 15 10:22:35 localhost sshd[4690]: Invalid user muzio from ::ffff:83.103.27.85
Feb 15 10:22:36 localhost sshd[4694]: Invalid user manuel from ::ffff:83.103.27.85
Feb 15 10:22:38 localhost sshd[4692]: Invalid user fuchs from ::ffff:124.0.75.231
Feb 15 10:22:38 localhost sshd[4696]: Invalid user mariano from ::ffff:83.103.27.85
Feb 15 10:22:39 localhost sshd[4699]: Invalid user maurico from ::ffff:83.103.27.85
Feb 15 10:22:40 localhost sshd[4702]: Invalid user mefisto from ::ffff:83.103.27.85
Feb 15 10:22:40 localhost sshd[4698]: Invalid user fuchs from ::ffff:124.0.75.231
Feb 15 10:22:41 localhost sshd[4704]: Invalid user mino from ::ffff:83.103.27.85
Feb 15 10:22:42 localhost sshd[4708]: Invalid user modesto from ::ffff:83.103.27.85

```from my logcheck reports.
So I've tried to make a line, looks like this(put it in /etc/logcheck/ignore.d.server/local to not interfere with automatic updates, but that's not topic of this forum section):
```
^\w{3} [ :0-9]{11} [._[:alnum:]-]+ sshd\[[0-9]+\]: Invalid user [:alnum:]+ from ::ffff:[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+$
```But It doesn't seem to match. Up to sshd\\[[0-9]\]: is a copy of other working lines, and I made up the rest myself.

It's supposed to be an egrep regular expression. Anybody know how to make one that matches?

---

