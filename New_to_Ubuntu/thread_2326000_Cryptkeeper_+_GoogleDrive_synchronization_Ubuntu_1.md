---
title: "Cryptkeeper + GoogleDrive synchronization Ubuntu 16"
date: 2016-05-27
forum: New to Ubuntu
---

### Post by whois2 on 2016-05-27
Hi. I want to create encoded folder or drive, and i want this folder or drive synchronized with google drive. I install Cryptkeeper and mount in /home/user/gdrive. It works ok. Then, i install google-drive-ocamlfuse, and i point /home/user/gdrive folder for google-drive-ocamlfuse this command:
```
google-drive-ocamlfuse /home/user/gdrive
```
and I get this error:
fusermount: failed to access mountpoint /home/user/gdrive: Permission denied

then i type this:
```
sudo google-drive-ocamlfuse ~/gdrive
```
error:
Error: Mountpoint /home/whois/gdrive should be an existing directory
help guys. 
Also, I listen to tips for using other encoded and synchronize apps for ubuntu 16. tnx

---

