---
title: "No Permissions to extract zip files"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by Joseph_Smytth on 2014-01-23
Never used ubuntu before. I want to install bolehvpn on a VM with ubuntu. I can download file. When I try to extract zip files to etc/openvpn I get access denied. you do not have permissions. When I try and create new folders inside openvpn folder I get access denied, you do not have permission. I tried sudo nautilus but this does not give me access to file system where I need to extract and add files. I am not a novice to windows but I am to ubuntu so I hope this is not my one and only try with linux:(

---

### Post by Dave_L on 2014-01-24
If you run unzip from the command line, you can use sudo with it, and extract the files wherever you want.
```
sudo unzip ...
```

"sudo nautilus" should give you access to everything. Could you provide more detail on why that's not working?

---

### Post by coldraven on 2014-01-24
Try this for root permission in the file browser. Warning! With nautilus in root mode you can delete critical files and break your system. 
```
gksu nautilus
```

---

### Post by Joseph_Smytth on 2014-01-24
when I run sudo nautilus in a terminal I get my home directory. I need access to the file system where I can extract zip files to the folder ect/openvpn. All I get in nautilus is a home directory.

---

### Post by Joseph_Smytth on 2014-01-24
okay I did it. Thanks.

---

### Post by ubudog on 2014-01-24
> **Joseph_Smytth said:**
> when I run sudo nautilus in a terminal I get my home directory. I need access to the file system where I can extract zip files to the folder ect/openvpn. All I get in nautilus is a home directory.

You should be able to navigate through the File System in nautilus.

But, you can always just open /etc/openvpn:
```
gksu nautilus /etc/openvpn
```

---

