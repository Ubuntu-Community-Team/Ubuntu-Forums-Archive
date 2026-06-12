---
title: "Backup my installed packages"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by DaveDeviant on 2012-04-17
Hello, can you please tell me what's the best method to save a list with my installed packages and use it for a later Ubuntu re installation?

Thank you.

---

### Post by anejo on 2012-04-18
Install and use 'aptoncd'

This will take whatever you have in /var/cache/apt/archives and create a media (CD-DVD) to use to install software via apt.  You can the upgrade and install the same set of softwares in several machines with no need to re-download those packages again.

---

