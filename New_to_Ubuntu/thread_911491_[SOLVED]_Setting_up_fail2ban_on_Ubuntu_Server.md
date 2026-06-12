---
title: "[SOLVED] Setting up fail2ban on Ubuntu Server"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Nxion on 2008-09-05
Hi all,

I have a server I set up for testing. I have installed SSH server and now I am getting bombarded by brute force attacks. After some research found that fail2ban sounds like a good idea, But I am having some issues... It wont ban anything.. It just seems to ignore what I set and keep allowing attempts. I set it to block after 3 fails. I'm thinking I may have  misconfiguration something. Can any one suggest a good how to on it? I have only found stuff for Debian and I know it should be the same in theory but maybe not.

Thanks in advance!,
Beau

---

### Post by StOoZ on 2008-09-05
is it even running as a daemon?

type in the terminal :
> ps ax | grep fail2ban

what do you see?

if its not running , try installing the latest version from here:
[http://packages.debian.org/unstable/net/fail2ban]("http://packages.debian.org/unstable/net/fail2ban")

I had some issues with the 8.04 repositories version

---

### Post by Nxion on 2008-09-06
> **StOoZ said:**
> is it even running as a daemon?

type in the terminal :


what do you see?

if its not running , try installing the latest version from here:
[http://packages.debian.org/unstable/net/fail2ban](http://packages.debian.org/unstable/net/fail2ban)

I had some issues with the 8.04 repositories version


It is running. and I even restarted it and no change. It installed fine. Any ideas? How do you have yours configured? I really only want it to protect ssh at the moment.

Thanks

---

### Post by Nxion on 2008-09-29
Thanks for your assistance. I have it working now.

---

