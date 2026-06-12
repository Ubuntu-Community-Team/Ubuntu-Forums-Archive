---
title: "addroup: No GID is available..."
date: 2012-02-03
forum: New to Ubuntu
---

### Post by goishin on 2012-02-03
Hi all,
I'm a newbie ubuntu user. We're using it at work. I'm trying to set up a cron job to run some tests, and I'd like the bash script I wrote to email me the results of the tests when it's done. So, I'm trying to install sendmail by using the command:
sudo apt-get install sendmail

But somewhere during the installation, I'm getting the error:
addgroup: No GID is available in the range 100-999 (FIRST_SYS_GID - LAST_SYS_GID).

When I try to figure out what FIRST_SYS_GID and LAST_SYS_GID are (I'm assuming they're environment variables), they're empty. To try and see what they are, I typed:
echo $FIRST_SYS_GID

I'm running Ubuntu 10.04.

Any advice for me?

---

