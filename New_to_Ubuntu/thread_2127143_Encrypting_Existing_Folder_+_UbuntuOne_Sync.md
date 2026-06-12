---
title: "Encrypting Existing Folder + UbuntuOne Sync"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by krustenBrot on 2013-03-19
Hi there,

I want to encrypt an existing Folder while still be able to sync it with UbuntuOne. After digging around a bit i found 2 methods of doing so:

1. **Truecrypt**: Creating a Container pack everything in there and upload it. This is quite inconvenient as soon as you change just a tiny bit you have to upload the whole container. And also it doesn't as nicely as method 2.

2. **Cryptkeeper:** Create a Folder, encrypt it, and only mount it if you use it. Automatically unmounting is really nice btw. But: is there a method to apply this to* existing* Folders? Lets say i want to encrypt my *Documents* Folder in */home/xx/* if i delete it, create a new Folder using Cryptkeeper called Documents will i be able to access it through the shortcuts in Nautilus & Unity?
How is Cryptkeeper managing the Files? How will they be uploaded to UbuntuOne? Anyone has experiences with it? Is my Cloud drive encrypted?

I know - a lot of questions. Thanks in advance to whoever takes the time to answer them. :)

---

### Post by jonnyboysmithy on 2013-03-19
An encrypted private directory would do that. You would have to make a new directory a put all the data in there.
See: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

