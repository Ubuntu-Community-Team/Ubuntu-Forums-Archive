---
title: "ssh on Ubuntu 10.04 with encrypted home directory"
date: 2010-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by clegends on 2010-10-21
Hi folks, just spent the past 2 hours trying to work out why I couldn't ssh into my server after reinstalling with an encrypted home partition. The problem was my encrypted home partition, so I thought I'd post this workaround. This is for 10.04.1 & before, no idea if this has been fixed in Maverick or not.

The issue is that by default your authorized_keys file is stored in /home/user/.ssh . Not much good if when your machine boots up your /home partition is encrypted! To solve this, and keep your partitions encrypted, you need to edit your /etc/ssh/sshd_config file. 
```

sudo nano /etc/ssh/sshd_config

```
Fine the line beginning with:
```

#AuthorizedKeysFile

```
And change it to: 
```

AuthorizedKeysFile      /etc/ssh/keys/%u/authorized_keys

```
Now create the directories for your key files. Replace 'user' below with the name of each user you want to have ssh access for:
```

sudo mkdir /etc/ssh/keys
sudo mkdir /etc/ssh/keys/user

```
Now move your authorised_keys file for each user into their /etc/ssh/keys/user/ directory.
```

sudo mv /home/user/.ssh/authorized_keys /etc/ssh/keys/user

```

Good luck!

---

### Post by darknighte on 2010-10-31
Great post.  Thanks for the info.
One comment that may be obvious to some, but the default permissions on the directories need to allow the directory to be read by the user id in question, or else it won't work.

---

### Post by rts on 2011-03-10
This technique doesn't work for me on Meerkat; nor does this workaround: [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/362427/comments/12)

I can log in, but the encrypted home directory is not mounted unless I log in with a password.  When I log in using the key and try "ecyprtfs-mount-private", it prompts for the login password before mounting.

Any other ideas?

---

