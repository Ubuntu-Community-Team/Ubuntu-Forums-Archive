---
title: "FTP using FileZilla"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by geomcd1949 on 2012-03-02
Hi, I'm trying diligently and valiantly to transition from Windows to GNU/Linux (Ubuntu 11.10). I want to FTP files from my new Linux machine to a remote server. Using FileZilla, I can send files from my machine to the server. When I try to get files from the server, I get a FileZilla error message saying "Failed to open /var/www/index.php" "File transfer failed."

Advice is greatly appreciated.

~George

---

### Post by Jon Monreal on 2012-03-08
Sounds quite odd. Can you try transferring all of the files except the index.php file and seeing if the transfer works then?

---

### Post by papibe on 2012-03-08
Hi geomcd1949.

If I were you, I would forget about ftp, and instead..

I would recommend installing openssh-server, and use sftp. It requires little to none configuration, and connect you directly to your home directory.

Filezilla can hadle sftp just fine. Use your Ubuntu user and password to connect (port 22).

Just some thoughts.
Regards.

---

