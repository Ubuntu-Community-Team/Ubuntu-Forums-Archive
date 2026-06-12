---
title: "trying to set up a git repo on my home server"
date: 2010-03-12
forum: Programming Talk
---

### Post by badperson on 2010-03-12
Hi,
I have a server on my home network with git installed. 
I want to set up a repo, and in the docs, this section:

> Adding a new project to the repository

Here is an example of the gitosis configuration file you clone before. Here it contains the default gitosis entry, and a new project entry:

[gitosis]

[group team]
writable = testproject
members = hostname.yourserver.com

[group gitosis-admin]
writable = gitosis-admin
members = keyfilename

hostname.yourserver.com or keyfilename is the name of the public key without .pub extension you copied into gitosis-admin/keydir/ directory.

After you've done editing, save the file, and commit it back to the server.

git commit -a -

doesn't specify whether I should do those commands on the client or server machine. 

the .conf file exists on both machines.
bp

---

### Post by badperson on 2010-03-15
bump...does anyone have a git repo on a setup like this?

---

### Post by sharpdust on 2010-03-15
You should make the initial commit on the server machine.
Once you're able to authenticate yourself, you can edit it using your account.

---

### Post by badperson on 2010-03-15
thanks, 
[LIST]
[*]I was able to install git, and copy my rsa key over. (this was done on the client)
[*] I was able to initialize the git repo on the server ```
sudo -H -u gitosis gitosis-init < /tmp/id_rsa.pub
Reinitialized existing Git repository in /srv/gitosis/repositories/gitosis-admin.git/
Reinitialized existing Git repository in /srv/gitosis/repositories/gitosis-admin.git/

``` (this was done on server)

[*] Then I tried to check out the admin branch to my local machine, but i got this: ```
 git clone jason@<ip address>:gitosis-admin.
Initialized empty Git repository in /tmp/gitosis-admin./.git/
fatal: 'gitosis-admin.' does not appear to be a git repository
fatal: The remote end hung up unexpectedly

```
[/LIST]


any ideas? 
thanks!
bp

---

### Post by sharpdust on 2010-03-15
> **badperson said:**
> thanks, 
[LIST]
[*]I was able to install git, and copy my rsa key over. (this was done on the client)
[*] I was able to initialize the git repo on the server ```
sudo -H -u gitosis gitosis-init < /tmp/id_rsa.pub
Reinitialized existing Git repository in /srv/gitosis/repositories/gitosis-admin.git/
Reinitialized existing Git repository in /srv/gitosis/repositories/gitosis-admin.git/

``` (this was done on server)

[*] Then I tried to check out the admin branch to my local machine, but i got this: ```
 git clone jason@<ip address>:gitosis-admin.
Initialized empty Git repository in /tmp/gitosis-admin./.git/
fatal: 'gitosis-admin.' does not appear to be a git repository
fatal: The remote end hung up unexpectedly

```
[/LIST]


any ideas? 
thanks!
bp

You need to append the .git on to the end of the git repo...

```
 git clone jason@<ip address>:gitosis-admin.git 
```

---

### Post by badperson on 2010-03-15
fixed it...
> git clone [email]gitosis@192.168.1.5:gitosis-admin.git[/email]


that worked. 
bp

---

