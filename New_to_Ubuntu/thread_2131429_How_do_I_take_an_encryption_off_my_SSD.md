---
title: "How do I take an encryption off my SSD"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by thri11house on 2013-04-01
During the Xubuntu install it asked if I wanted to encrypt the SSD and I picked yes.

I wan to take it off now. How?

I have Xubuntu installed on my HDD and there is nothing on the SSD so there's no need to worry about deleting important files.

---

### Post by save2 on 2013-04-22
encrypting an SSD disk using the install option is  VERY bad in terms of SSD performance. the write performance will drop to ~12MB/s.

basically if you don't care about your encrypted content: you delete the  ~/Private ~/.Private ~/.ecryptfs  folders. 

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How_to_Remove_an_Encrypted_Private_Directory_Setup)

---

### Post by dodo3773 on 2013-04-22
If there's nothing on the ssd then just reformat it. Just fire up gparted or anything else. If you want to automount it you may need to change your fstab to point to the new UUID but other than that shouldn't be too complicated.

---

