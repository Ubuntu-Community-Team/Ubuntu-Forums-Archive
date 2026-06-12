---
title: "Nightmare - booted up with encrypted filesystem"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by streetbusker on 2012-05-12
As the title states, I have an encrypted filesystem - I never set up such a thing I don't believe. I have no  I did not (at least wittingly) ever do such a thing. I was running 10.04 lts,and this morning I booted up to a encrypted home dir, can't access anytthing except my unencrypted root dir. What the ??? I'm just lost here on this, how could this have happened? Is this some sort of malicious action I've fallen victim of?

---

### Post by streetbusker on 2012-05-12
[B]After reading the following below I guess I'm just hosed. How could this have happened!!!! WTF! ubuntu!f arrrgghh!!
[/B]

[B]
[/B]

**Recovering Your Mount Passphrase**

 In the event that you did not write down your mount passphrase, you may be able to recover it by decrypting the file  /home/username/.ecryptfs/wrapped-passphrase  using your login passphrase. 

[LIST]
[*] ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase 
[*]Type your login passphrase to reveal the mount passphrase  
[/LIST]
If your login passphrase matches the passphrase used to encrypt the wrapped-passphrase file, your mount passphrase will be written to screen.  Record and protect this data accordingly. 
If you have lost your wrapped-passphrase file, and you did not record your mount passphrase, it is impossible to access your encrypted data.

---

### Post by streetbusker on 2012-05-12
people should know that UBUNTU can be dangerous to use, this really sucks! I can't believe this freaking system is suddenly encrypted. I've backed up but how in the world did this happen!!

---

### Post by codingman on 2012-05-12
Did you play with root???

If so, you probably locked the system by switching out the sudo setup, like by removing files.

ITS LOCKED. IF A MOD CAME HERE MAYBE THEY COULD GET THE SUDO LOCK OUT VIA TERMINAL.

---

### Post by Hadaka on 2012-05-13
This thread may help your problem

 [http://ubuntuforums.org/showthread.php?t=186254](http://ubuntuforums.org/showthread.php?t=186254)

---

### Post by Utkarsh Ray on 2012-05-13
> **streetbusker said:**
> people should know that UBUNTU can be dangerous to use, this really sucks! I can't believe this freaking system is suddenly encrypted. I've backed up but how in the world did this happen!!

If one chooses to use encryption, one should remember and safekeep the method to access the data similar as one would as with a bank locker.

The text you have provided in #4 is too true
'If you have lost your wrapped-
passphrase file, and you did not
record your mount passphrase, it is
impossible to access your encrypted
data.'

This is not Ubuntu's problem this is inherent risk in encryption.
I lost access to about a quarter of a large chunk of not-that-important data saved in Windows 7 when I reinstalled W7 and forgot the passphrase to the .pfx file (container to PKCS#12 certificates)
However unlike you that data was not completely backed-up.
I keep guessing the passphrase even now (after 3 years)

---

### Post by jtarin on 2012-05-13
In a terminal issue the command (as root) ```
lsmod
```
"Look for something with aes in it - aes, aes-i586, aes-i386, and so forth.
If you find it post the output of lsmod here.

---

