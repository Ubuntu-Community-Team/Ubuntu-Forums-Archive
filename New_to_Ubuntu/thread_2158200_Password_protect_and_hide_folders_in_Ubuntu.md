---
title: "Password protect and hide folders in Ubuntu?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by chemical1608 on 2013-06-28
Hello all,

I am pretty new to Linux and I just want to know if there are any applications/programs which would let me password protect and hide folders in Ubuntu?

thanks in advance
Chemical

---

### Post by mastablasta on 2013-06-28
have you tried right clicking the folder and selecting properties?

otherwise a dot "." before the folder name will hide it.

chown command sets user's privileges.

---

### Post by dino99 on 2013-06-28
There are already some hidden folders inside your /home: those one started with a dot (.folder); they can be unhided with ctrl+h
Changing the attribute of a folder (with chattr) can protect your data, and chown can change the owner (but be carefull to not doing that with the system folders, only do it with your  /home file/folder)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[http://www.ossdoc.com/2013/01/how-to-protect-your-folder-or-files.html](http://www.ossdoc.com/2013/01/how-to-protect-your-folder-or-files.html)

---

### Post by chemical1608 on 2013-06-28
Hello Dino & MastaBlasta,

 Thank you for your valuable reply. But I do have confidential files to protect in my system. I believe if someone inserts a live cd and login as a root user, permissions can be revoked? Correct me if I am wrong. I was looking for a more secure software with which I can encrypt the whole folder with a password and hide it or something like folder lock available for windows?

Chemical

---

### Post by Kujua on 2013-06-28
chemical1608,

I use encrypted disk images to store confidential data. Basically an encrypted filesystem is created in a file. This image file is then mounted to a directory. Then whatever you copy into that directory goes to the image file as encrypted data. This link explains it better: [http://www.techrepublic.com/blog/opensource/create-encrypted-loopback-filesystems-on-linux/67](http://www.techrepublic.com/blog/opensource/create-encrypted-loopback-filesystems-on-linux/67)

The reason why I use this method is that it does not require installing additional applications on multiple machines from which I access the data. It uses only common tools that are there on all standard distros. But security-wise I am not sure how it compares with other solutions.

Truecrypt is a popular choice I guess, though I have never used it.

---

### Post by chemical1608 on 2013-06-28
Hello Kujua,

Thats just brilliant. Just hoping I can understand it all. :) :) what's written on the link. If that works, a million thanks to you !! Gonna try it now .!!

---

