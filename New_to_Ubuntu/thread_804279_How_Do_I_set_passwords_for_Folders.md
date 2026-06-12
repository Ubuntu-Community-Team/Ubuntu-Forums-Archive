---
title: "How Do I set passwords for Folders"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Foxfire on 2008-05-23
What I am trying to say is How do I set a password on a folder so that you cant even open it unless type the password in. The folder would be on the desktop or where ever.  I have no network?

---

### Post by Bodsda on 2008-05-23
make the folder owned by root not you.

im not on my Ubuntu machine atm so i cant give you an exact command but in a terminal type

```
 man chowner 
```

that will give you a big document about the command 'chowner'

---

### Post by Steve413z on 2008-05-23
chowner doesn't password protect a folder

if you are trying to keep confidential files safe incase your computer gets stolen, you need to encrypt the files

Linux has a bunch of utilities for doing this,

GnuPG
TrueCrypt
dm-crypt

are 3 of the most common linux encryption tools

---

### Post by Steve413z on 2008-05-23
[http://ubuntufs.wordpress.com/2007/05/22/encryptingdecrypting-with-gnome/](http://ubuntufs.wordpress.com/2007/05/22/encryptingdecrypting-with-gnome/)

---

### Post by Foxfire on 2008-05-23
Thank you

---

