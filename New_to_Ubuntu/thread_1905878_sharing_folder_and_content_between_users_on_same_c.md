---
title: "sharing folder and content between users on same computer"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by npfa on 2012-01-07
I am a new user of Ubuntu 11.10 and over the past couple of weeks have been researching and trying to set up and share a folder with other users on the same computer. I have tried setting up a shared folder, setting user groups but each user I set up is able to access all of my  folders and files not just a single folder and file content. I want to be able to share one single folder with movies with my users. I am a new user and am looking for a step by step process on how to set this up. Thank you in advance for any assistance.

---

### Post by Blackbird_13 on 2012-01-08
I suggest you create a new group and add all relevant users to the new group. Then just change the permissions. Open a terminal and run the following command.

```
chown -vR user:NEWGRP /home/user/.../SHARE_DIR 


```Where user is your name, NEWGRP is the name of the new group created and SHARE_DIR is the name of the directory you wish to share.

---

### Post by z3nhakr on 2012-01-08
if you dont mind if all users can access the folder, you can make the folder in your home folder and then chmod 777 the directory or right-click and allow for read/write access to other users.

---

### Post by Morbius1 on 2012-01-08
Your request is actually a little bit more complicated than you might think depending on your definition of "shared".

Read / Write access which also means the ability to delete any content by everyone?
Just Read Access? 
Read / Write access but without the ability to delete someone else's content? 
The ability for one user to edit the contents of a given file created by another user?

Can you define what your requirements are in more detail?

---

### Post by npfa on 2012-01-08
I was setting up users to be able to share specific folders with other users. I have now found that each user is able to gain access to all others folders thru file system / home. I have tried changing user permissions, file sharing options, group settings, but nothing seems to prevent access. I am not very familiar with terminal commands so most of the changes I have made have been thru GUI. Any assistance is greatly appreciated, thank you in advance.

---

### Post by mörgæs on 2012-01-08
Please don't create multiple threads on the same topic. 
Threads merged.

---

### Post by Morbius1 on 2012-01-08
Misread your original post.

If you don't want userB from seeing the content of userA's home folder then change permissions so that only userA has access:
```
sudo chmod 0700 /home/userA
```If you want to create a shared directory that allows access to every user on your system then I suggest creating a directory outside of anyone's home directory:
```
sudo mkdir /home/Shared
```Then allow access to everyone:
```
sudo chmod 0777 /home/Shared
```[COLOR=Blue]Note[/COLOR]: that "chmod 0777" is only one way to share that folder. It still depends on your definition of "shared".

---

### Post by npfa on 2012-01-09
Thank to all!! I was able to fix both of my issues within in a day after spending a couple of weeks of banging my head!!

---

