---
title: "Making a folder read/writeable for www-data and another user"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by aktiwers on 2012-05-24
I have a custom created ftp-user that I want to be able to read/write to a specific location. He also will be uploading files where the user www-data should be able to read/write.

So basicly the folder and all folders/files created in this folder, should have 777 permissions for these two users.

www-data user should be able to read/write to files that ftp-user has created.

I guess I need to create a group and include the 2 users in this group?  I'm in doubt how to do this in best practise way. I hope someone can explain it to me.

Thanks a lot

---

### Post by aktiwers on 2012-05-25
No one? :)

---

### Post by kc1di on 2012-05-25
> **aktiwers said:**
> I have a custom created ftp-user that I want to be able to read/write to a specific location. He also will be uploading files where the user www-data should be able to read/write.

So basicly the folder and all folders/files created in this folder, should have 777 permissions for these two users.

www-data user should be able to read/write to files that ftp-user has created.

I guess I need to create a group and include the 2 users in this group?  I'm in doubt how to do this in best practise way. I hope someone can explain it to me.

Thanks a lot

Ok if I understand it right you will have a folder someplace on your system that you want both users to be able to use.  and have permission to write and modify them as they choose?

if that is correct you will make the folder: the onwer would be say www-data  and ftp-user would be given permission to read write to that file.  I don't see any promblem with that if you don't want others to be able use the folders.  
think what you might need is to make www-data user and ftp-user members of the group and exclude all others.  Now the ftp-user would have to make sure he gives the files he uploads the right permissions so that www-data usr would be albe toopen them. He would be the owner of his files so it will be up to him to give permissions. 

here a web page that will give you some help I think in doing what you want.
[http://www.tuxfiles.org/linuxhelp/filepermissions.html]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")

---

