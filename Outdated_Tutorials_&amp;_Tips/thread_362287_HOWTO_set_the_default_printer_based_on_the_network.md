---
title: "HOWTO: set the default printer based on the network your laptop is connected to"
date: 2007-02-15
forum: Outdated Tutorials &amp; Tips
---

### Post by rrwo on 2007-02-15
Using the 'whereami' package, described in
[http://ubuntuforums.org/showthread.php?t=24994]("http://ubuntuforums.org/showthread.php?t=24994").

Then in your whereami.conf file, use the following lines for each network:
```

=networkname sudo -H -u user lpoptions -d printername > /dev/null

```
substituting the appropriate user and printer names. (Since it runs as root, you'll have to use the sudo -u username, and do this for each user.)

---

