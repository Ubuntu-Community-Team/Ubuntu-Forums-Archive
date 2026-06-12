---
title: "Rebuilding OpenSSH-client with different options"
date: 2008-02-14
forum: Packaging and Compiling Programs
---

### Post by bismark on 2008-02-14
I am looking to use opensc with ssh.  The installed version of openssh-client doesn't have the opensc option enabled.  What would be the best way to go about enabling this option.  I know I could download the tarball source, configure and install in /usr/local/ beside the version installed by default.  However this to me seems like asking for trouble.

Can I download the ubuntu source for openssh-client reconfigure\compile and repackage the deb, without affecting it's dependencies\dependents?

---

### Post by Dr Small on 2008-02-15
Why not just apt-get remove openssh-client, download the source and compile it?
If something doesn't work, you can always install the one from the repositories again.

Dr Small

---

### Post by bismark on 2008-02-15
because if I try to remove openssh-client it askes to remove keychain openssh-client openssh-server ssh-askpass-gnome sshfs ubuntu-standard.

---

### Post by bismark on 2008-02-15
Well I found vague instructions here [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/16918/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/16918/+viewstatus)

and was able to get it to work.  The only thing I had to do was then
```

echo "openssh-client hold" | sudo dpkg --set-selections

```

to freeze my version in place.

---

