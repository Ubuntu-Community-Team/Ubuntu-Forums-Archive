---
title: "Encrypted home folder"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Aladrac on 2013-07-11
Hello. I'm wondering if anybody could give me some guidance in this. When I first installed Kubuntu, I ticked the ''Encrypted home folder'' option. After noticing some issues I couldn't get past, I decided to re-install the OS, leaving the first install in a separate partition. After logging into my new account on the second install, I tried to access the ''Home'' folder to move the files from one partition to another,  but it says it has been unmounted to protect my data. When clicking the Access-Your-Private-Data.desktop file, a console window briefly appears and then closes itself. I tried using the ''ecryptfs-mount-private'' command, but nothing happens. Am I doing something wrong? I'm a newbie in this, and I'm completely lost.

---

### Post by Traxster on 2013-07-11
> **Aladrac said:**
> Hello. I'm wondering if anybody could give me some guidance in this. When I first installed Kubuntu, I ticked the ''Encrypted home folder'' option. After noticing some issues I couldn't get past, I decided to re-install the OS, leaving the first install in a separate partition. After logging into my new account on the second install, I tried to access the ''Home'' folder to move the files from one partition to another,  but it says it has been unmounted to protect my data. When clicking the Access-Your-Private-Data.desktop file, a console window briefly appears and then closes itself. I tried using the ''ecryptfs-mount-private'' command, but nothing happens. Am I doing something wrong? I'm a newbie in this, and I'm completely lost.


lol,

I just had the same problem. If you did not write down your wrapped password (not your login password) that was generated and displayed on the screen for you to write down after you checked the box for 'encrypt home folder.' You might be screwed, however, there may be an opportunity to recover it. See [this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") and you can also do a search for recovering wrapped passphrase from live cd. There are plenty of threads on the internet about this topic.

Best of luck.

Traxster

---

### Post by Aladrac on 2013-07-11
I recovered the passphrase, though I didn't know what to do after. So, I just tried to do what I thought was logical. After replacing the paths in the commands, I was able to access the Home folder from the first install. Thank you very much, Traxster!

---

