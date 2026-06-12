---
title: "Encryption &amp; ecryptfs"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by Philip_James on 2014-02-12
Afternoon All!

I have a newbie question on encryption I hope someone can help point me in the right direction.

I have an Ubuntu server 12.04 all updated and joined to a Windows domain and all works well.

On my Ubuntu server I have created a 1TB btrfs /srv partition which can serve files and folders without issue.

I would now like to encrypt this partition and have read about eCryptfs [here]("https://help.ubuntu.com/12.04/serverguide/ecryptfs.html"). Following the instructions I install and run eCryptfs and all appears to go to plan. However, being new to this I am being honest when I say I have no idea if it has worked, what should happen when encryption is in place or what to look for to check.

Does anyone know of any idiot guides to checking/testing encryption, or any general advise please?

Many thanks in advance.

---

### Post by Dave_L on 2014-02-12
The article you referenced gives a way to test that the files are are really encrypted.

Another way is to boot in recovery mode and select the option to drop to a root shell. Then see if you can access the encrypted files without providing the password/passphrase.

Similarly, you could boot from a LiveUSB/CD and try to access the files without providing the password/passphrase.

---

