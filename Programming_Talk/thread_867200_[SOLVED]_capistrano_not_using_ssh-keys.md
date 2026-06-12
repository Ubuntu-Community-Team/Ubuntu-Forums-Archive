---
title: "[SOLVED] capistrano not using ssh-keys"
date: 2008-07-22
forum: Programming Talk
---

### Post by qiepenguin on 2008-07-22
I upgraded from Gutsy to Hardy yesterday.  I do work on rails applications and use Capistrano for auto-deployment.  After the upgrade, Capistrano has started prompting for a passphrase rather than using my ssh keys.  Since the server is key access only, there is no passphrase, and it is impossible to connect.  My keys are working (I can connect directly through ssh) but are not working for Capistrano.  Can anyone help?

Thanks,
David

---

### Post by qiepenguin on 2008-07-24
Problem solved by updating capistrano from version 1.4.1 to 1.4.2, which uses a different version of net-ssh.

---

