---
title: "recovery data from encryptfs"
date: 2014-12-08
forum: New to Ubuntu
---

### Post by deniska2b41 on 2014-12-08
I have a problem with data recovery. My computer with Ubuntu 14.04 LTS no longer run after a few experiments. I decided to install a new operating system Opensuse 13.2. I forgot that my drive was encrypted. I installed Opensuse on the same drive where it was installed Ubuntu 14.04 LTS and connected / home partition from it. Now in the / home folder has .Private and encryptfs. I tried to recover the data on the instructions [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically)
 After restoring my files remain encrypted. What should I do?

---

### Post by deniska2b41 on 2014-12-08
Solved this problem. I booted from live usb. Then I mount the HDD with the encrypted directory.
 In the terminal I typed sudo ecryptfs-unwrap-passphrase name of mounted HDD/home/.ecryptfs/$USER/.ecryptfs and received a passphrase.
 Then I typed sudo ecryptfs-recover-private. A request for a password answered no. Then I was asked to passphrase. I brought her, and data were transcribed and unmounted in the directory /tmp. Sorry for my English

---

