---
title: "dm-crypt + pam_mount: one login necessary"
date: 2005-09-08
forum: Outdated Tutorials &amp; Tips
---

### Post by MrMinute on 2005-09-08
Hello,
I use dm-crypt to encrypt my home directory successfully. Now I would like to configure Ubuntu that I need to enter my password one time only. I used pam_mount on a Debian system successfully for this job but did not managed to configure it in the right way with Ubunut. 
Thank you!

PS: My password for user and home directory is the same.

---

### Post by fyrefly on 2005-09-10
I had the opposite problem -- I wanted a separate partition encrypted and didn't want it connected to my user password - I wanted to manually mount it..

When I was first setting up encryption on Ubuntu, I followed the instructions here - [https://wiki.ubuntu.com/EncryptedFilesystemHowto?highlight=%28crypt%29](https://wiki.ubuntu.com/EncryptedFilesystemHowto?highlight=%28crypt%29) [scroll down to examples] 

My encrypted partition would mount and decrypt on boot up after I put in my user password.

Hope that helps.

---

