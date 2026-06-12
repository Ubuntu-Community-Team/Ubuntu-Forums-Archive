---
title: "md5 sha1 ripemd &quot;linux hash tool&quot;"
date: 2006-12-24
forum: Programming Talk
---

### Post by saphil on 2006-12-24
Is there an app to verify checksums or would I have to write the application?

I was looking at wireshark's checksums, which are:
                                         [LIST=1]
[*][LIST=1]
[*]MD5(wireshark-setup-0.99.4.exe)=44edc28501c52c5a38e7351ea57d7873
[*]SHA1(wireshark-setup-0.99.4.exe)=b245151b0dca0a88c65e7900ce7558ea89d29bc2
[*]RIPEMD160(wireshark-setup-0.99.4.exe)=32710d62eed42bb8237de688736c7c688f2b8d03[/LIST] [/LIST]The containing file is signed with [key id 0x21F2949A]("http://www.wireshark.org/download/gerald_at_wireshark_dot_org.gpg")which is tied to a pgp key key belonging to gerald at wireshark dot org

I can look up how these were done, and code something to run a comparison or I can look for a rainbow table, or I could probably use a password cracker to come up with something, but I think there must be something extant that could let me do all of these checksum processes.  
Note: my constraints are "linux-based and no-cost"  I have found several apps for Windows.  I would rather use my ubuntu box for everything.

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.3 (Darwin)

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
=EAj0
-----END PGP PUBLIC KEY BLOCK-----
```

---

### Post by ghostdog74 on 2006-12-24
you can use md5sum

---

### Post by saphil on 2006-12-25
Thanks GhostDog.  
It doesn't seem to work on SHA-1 or RIPEMD-160, but it tears heck out of MD5.

Once I spent the 2 or 3 hours finding somebody who knew how to use it. :-)

Merry Christmas!
Joyeous Yule!
Happy Hanukkah!
Good Kwanzaa!

If you have a holiday, let's celebrate!

---

### Post by Ted_Smith on 2012-01-31
For the benefit of others finding this, I wrote a GUI for hashing in Linux called QuickHash. You can hash strings, files, or recursively hash directories of files. 

If ran as sudo, you can also physically hash disks by using the file hashing and choosing /dev/hdX

You can choose between MD5, SHA1, SHA256 & SHA512

[http://sourceforge.net/projects/quickhash/](http://sourceforge.net/projects/quickhash/)

Ted

---

### Post by oldos2er on 2012-01-31
Closed, necromancy.

---

