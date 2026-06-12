---
title: "anyone knows ssh terminal with expect features"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by packets21 on 2013-03-04
I just transition to Ubuntu 12.04 from Windows last week and it was great! However, most of my work rely on connecting to servers in a dmz so I need to jump in first to other server. This is where I miss SecureCRT. I just realize it can save me lots of time if I can have this feature. Currently using PAC but expect doesn't work all the time.

Any other suggestions?

---

### Post by schragge on 2013-03-04
[connect-proxy]("http://manpages.ubuntu.com/manpages/precise/en/man1/connect-proxy.1.html"), [grcm]("http://manpages.ubuntu.com/manpages/precise/en/man1/grcm.1.html"), [mussh]("http://manpages.ubuntu.com/manpages/precise/en/man1/mussh.1.html"), [python-paramiko](http://www.lag.net/paramiko/docs/), [pssh]("http://manpages.ubuntu.com/manpages/precise/man1/parallel-ssh.1.html"), [clusterssh]("http://manpages.ubuntu.com/manpages/precise/en/man1/clusterssh.1.html"), [mssh]("http://manpages.ubuntu.com/manpages/precise/en/man1/mssh.1.html"), [putty]("http://manpages.ubuntu.com/manpages/precise/en/man1/putty.1.html")?

---

### Post by vamp774 on 2013-03-04
Why not just ssh straight from Terminal?  You can get putty through the software center if you like ( a popular ssh client ) .  But you can just ssh from a terminal.  You may need to install a package or something not sure. 
 ssh < [EMAIL="username@server"]username@server[/EMAIL] >

---

