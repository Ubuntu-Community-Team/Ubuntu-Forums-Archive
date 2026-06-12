---
title: "GPG Error"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by maddot on 2008-05-23
i just did a fresh install of hardy heron and everytime i reload synaptic, i get an error at the very end. similarly i tried apt-get update, and i still get the same error at the end.

```

W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

any ideas?

---

### Post by Maestro23 on 2008-05-23
Need to add the key. Medibuntu link: [https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu))

---

### Post by maddot on 2008-05-23
i tried that but i still get errors:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---

### Post by plucky on 2008-05-24
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems 


Try this instead to add the key for Medibuntu from a terminal window.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```



Good Luck

---

### Post by maddot on 2008-05-24
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

that's the error i get now...

---

### Post by plucky on 2008-05-25
> W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



Try **System > Administration > Software Sources > Authentication**

and click on **Restore Defaults**.

Then open a terminal and ```
sudo apt-get update
```.

If this doesn't work,in Software Sources,Change the Server to the Main Server and try again.

You might have to restore the Medibuntu repository after this.


Good Luck

---

### Post by maddot on 2008-05-25
no go.... still same problem. even after i did what you said....does the archive.ubuntu.com need a gpg as well?

---

### Post by plucky on 2008-05-26
This [link](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24234) is all I can find for your problem.If you scroll to the end ,it seems others on Hardy are having your problem.There is no fix for it at present.

I can only suggest you try other servers.


Sorry.

---

