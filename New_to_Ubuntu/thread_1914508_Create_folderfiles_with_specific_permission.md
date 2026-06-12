---
title: "Create folder/files with specific permission"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-01-24
How do you specify what user, group and permission files and folder should get? I got folder where I want all files and folders created to be owned by root:sftpgroup and where the folder permission is 770 and files are 660. As it's now will the file/folder be owned by the creator:sftpgroup and permission are 644/755

---

### Post by searchfgold6789 on 2012-01-24
Normally you would login as a user who has write permissions to he folder. As I understand it is rather difficult to be logged in as one user, and create a file or folder which is owned by another user, without first creating the file or folder and then forcing it to be owned by someone else. The exception to this is creating files or folders owned by root.

---

### Post by Frozen Forest on 2012-01-24
> **searchfgold6789 said:**
> Normally you would login as a user who has write permissions to he folder. As I understand it is rather difficult to be logged in as one user, and create a file or folder which is owned by another user, without first creating the file or folder and then forcing it to be owned by someone else. The exception to this is creating files or folders owned by root.
The sftp server is chrooted if it would make any diffrence.

---

