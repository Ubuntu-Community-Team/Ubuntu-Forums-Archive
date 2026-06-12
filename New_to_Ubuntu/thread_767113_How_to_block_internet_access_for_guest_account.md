---
title: "How to block internet access for guest account?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Odd-rationale on 2008-04-25
Hello!

Does anyone know of any good way to block internet access for a guest account?

Thanks!

---

### Post by Bentai on 2008-04-25
[http://ubuntuforums.org/showthread.php?t=407724](http://ubuntuforums.org/showthread.php?t=407724)
Post #3 might give your best option, which is to create a script to be run that turns off eth0 or whatever network adapter is used to allow internet access. The script would trigger after the guest logs into the system, and should not affect other users, I think.

---

