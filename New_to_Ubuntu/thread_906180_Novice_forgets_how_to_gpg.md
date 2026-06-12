---
title: "Novice forgets how to gpg"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by darkworld on 2008-08-31
I used gpg to secure a folder/files on my usb key when I was on fiesty, Im now on hardy. I can remember my gpg key but I cant remember what I did over a year ago. Please help.

If I look at my usb stick contents I have a folder called secure. In the deskstop folder icon it has a padlock top right and a close box bottom right on the icon.

Now I cant remember how I did it, I think I secured the folder with gpg. Cant remember the commands to unlock in terminal then copy content onto desktop. I remember the gpg key and thats all.

---

### Post by Pro-reason on 2008-08-31
If you have all the right GPG stuff installed, you can encrypt and decrypt by right-clicking on the file in Nautilus.

---

### Post by unutbu on 2008-08-31
To encrypt:```

gpg --recipient NAME --encrypt FILE
```
yields FILE.gpg

To decrypt FILE.gpg:
```
gpg FILE.gpg
```

---

