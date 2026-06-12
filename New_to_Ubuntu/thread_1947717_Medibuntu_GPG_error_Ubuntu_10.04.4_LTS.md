---
title: "Medibuntu GPG error Ubuntu 10.04.4 LTS"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by candtalan on 2012-03-27
I am getting an error which appears to say that the medibuntu gpg is invalid.
When checking for updates an error is shown:

```

W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

```

What needs to be done please?

tia

---

### Post by plucky on 2012-03-27
> **candtalan said:**
> I am getting an error which appears to say that the medibuntu gpg is invalid.
When checking for updates an error is shown:

```

W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

```

What needs to be done please?

tia

Try ```
sudo apt-get install medibuntu-keyring
```

OR

Run from a terminal ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
```


Good Luck

---

### Post by candtalan on 2012-03-27
Thanks
 I tried this

```

user@novatech1:~$ sudo apt-get install medibuntu-keyring
[sudo] password for candt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@novatech1:~$ 
user@novatech1:~$ 
user@novatech1:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" 11 new signatures
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:         new signatures: 11
user@novatech1:~$ 

```
but still not working, and with the same error message

---

### Post by oldos2er on 2012-03-27
Try [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by candtalan on 2012-03-27
> **oldos2er said:**
> Try [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Yay!
Thank you kindly!
Method 2 - I tried this first :-) did not work for me.

Method 1 worked!
FWIW I used each command string separately one after another, with a return key after each  one.

---

### Post by oldos2er on 2012-03-27
Glad it worked. Would you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

### Post by candtalan on 2012-03-28
> **oldos2er said:**
> Glad it worked. Would you please mark the thread as 'Solved' under Thread Tools? Thanks. Whoops, oh yes, sorry, I forgot in the excitement!
And thanks again

---

### Post by smilingfrog on 2012-04-02
> **oldos2er said:**
> Try [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

Same problem, and this does the trick.

---

