---
title: "'Private' file help, please!"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by ags40 on 2013-06-28
Had the bad idea of installing Kubuntu LTS 12.04.2 with encrypted file (I suppose), in the understanding that once I entered the login password everything was going to be decrypted and ready to use until I logged out. Well, to be brief: how do I open my 'Private' file in a readable manner. Can the encryption be completely removed? Thanks

---

### Post by claracc on 2013-06-29
Here, [http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/](http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/) you have a step by step guide to unencrypt your home folder.

---

### Post by Cheesemill on 2013-06-29
> **ags40 said:**
> Had the bad idea of installing Kubuntu LTS 12.04.2 with encrypted file (I suppose), in the understanding that once I entered the login password everything was going to be decrypted and ready to use until I logged out.

This is exactly how it works. What makes you think that this isn't happening?

---

### Post by ags40 on 2013-06-29
Thanks for your answer. My puzzlement comes when I open /home/.Private and it is perfectly encrypted.

---

### Post by Cheesemill on 2013-06-29
When you are logged on the .Private file is unlocked and the contents appear as your home directory.

To test if encryption is working try booting from a Live CD and looking at your home folder, you should see that it only contains the .Private file but none of the other contents that you see when logged in.

---

### Post by ags40 on 2013-06-29
I just did what you suggested. The home folder shows the typical home dwith desktop, documents, download, etc.  When forced to show the hidden files the normal regular files the. No .Private or any of those.

---

### Post by ags40 on 2013-06-30
Thanks for your answer, but the files are already encrypted.

---

