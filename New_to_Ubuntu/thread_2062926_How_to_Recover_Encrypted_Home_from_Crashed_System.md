---
title: "How to Recover Encrypted Home from Crashed System?"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by GregA on 2012-09-26
A couple days ago, I was in midst of downloading & installing some major upgrades (per prompt from upgrade manager).   My internet connection went down due to remote router issues, and not all files/dependencies were acquired.  

The partial update totally broke Kubuntu 12.4, to the point I had to reinstall the whole OS yesterday.  The reinstall went fine, but unlike the original install, I chose "not to" encrypt "home" folders, and home was installed in same partition (sda5).   Original home is still at sda7.   There were 3 users on original home, and all directories and files were readable for the two users.  My home however was not available due to encryption.

I do have the passphrase, and I have the info (from orig install) that gave the command to unwrap the passphrase (ecryptfs-unwrap-passphrase file).  I am assuming by file, it is looking for the home name (greg1).   I can't seem to figure out a command to unlock the directory using the passphrase.   The man instructions for ecryptfs are above my knowledge level.

Any info on how to "unlock" or open my home on sda7 would be great.

Attached is screenprint of error msg.

Thanks.

---

### Post by HiImTye on 2012-09-26
have a look at:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

