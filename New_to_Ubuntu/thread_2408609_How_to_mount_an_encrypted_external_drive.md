---
title: "How to mount an encrypted external drive"
date: 2018-12-20
forum: New to Ubuntu
---

### Post by jaikishanl on 2018-12-20
I have an external hard drive that I encrypted using DiskCryptor tool ([https://diskcryptor.net/](https://diskcryptor.net/)) in Windows. 
Cipher - AES
Encryption mode - XTS
pkcs5.2 prf - HMAC-SHA-512

I did quite a bit of research but haven't succeeded yet mounting the drive. I used cryptsetup and went through the process defining the mount point and entering the paraphrase. However, I get different errors depending on how I mount. For instance using [COLOR=#242729][FONT=Consolas]sudo ntfs-3g /dev/device /media/hdd

[/FONT][/COLOR]I would like to know the steps for mounting. Any help will be much appreciated. 

Thank you!

---

### Post by TheFu on 2018-12-20
Never heard of that tool.  Are you certain the method of encrypt it uses is even supported by any other OS?

Most people who need cross-platform encryption use something like VeraCrypt or just use the native encryption and share the files over a network sharing method like CIFS or NFS or sshfs or sftp or ... one of the 500 other methods available.

---

### Post by jaikishanl on 2018-12-21
It uses standard aes-256 encryption

---

