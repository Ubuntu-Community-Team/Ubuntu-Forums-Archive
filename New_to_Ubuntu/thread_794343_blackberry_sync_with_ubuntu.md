---
title: "blackberry sync with ubuntu"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by bmann11 on 2008-05-14
Is there a program out there that will sync my blackberry with evolution running on Hardy?

---

### Post by tavella on 2008-05-17
There is, but I have not been able to get it working properly. 

[http://wiki.colar.net/tethering_with...pearl_on_linux]("http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux")

You're going to run in to problem most likely while trying to compile some of the programs. Just let me know the errors are and I'll try to help you resolve them. I know that I was missing quite a few libraries, opensync was a pain to get working.

---

### Post by chipbennett on 2008-06-01
> **bmann11 said:**
> Is there a program out there that will sync my blackberry with evolution running on Hardy?

I have my BlackBerry 8310 synchronizing with KDE-PIM in Kubuntu Hardy. You need to use Barry and OpenSync. Here are [step-by-step instructions]("http://www.chipbennett.net/wordpress/index.php/2008/05/synchronizing-a-blackberry-in-linux/").

Let me know if they are helpful, or if you have any questions.

Note, if you are synchronizing with Evolution, you will need to install the "oopensync-plugin-evolution" package rather than the "opensync-plugin-kdepim" package. Also, when configuring the synchronization group and members, you will need to use "sync-evo2" rather than "sync-kdepim". All else should work pretty much the same.

---

