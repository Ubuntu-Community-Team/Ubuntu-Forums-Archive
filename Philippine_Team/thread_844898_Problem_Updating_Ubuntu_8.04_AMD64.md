---
title: "Problem Updating Ubuntu 8.04 AMD64"
date: 2008-06-30
forum: Philippine Team
---

### Post by kaola_linux on 2008-06-30
Mga tol help nmn plz sa prob k...

(using update manager, i get the following error message when i press on check:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...curity/Release](http://security.ubuntu.com/ubuntu/di...curity/Release)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...pdates/Release](http://us.archive.ubuntu.com/ubuntu/...pdates/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.)



na copy k lng to sa ubuntu forums general help d same kc kming error.  Isa pa wla roon ung solusyon..Help me plz..Hirap kc mg update pg my gnito..Thanks in advance...:(

---

### Post by loell on 2008-06-30
can you copy/paste your sources.list?

type this in the terminal/console

```
gedit /etc/apt/sources.list
```


the copy paste the text here.

---

