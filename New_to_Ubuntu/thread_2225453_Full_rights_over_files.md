---
title: "Full rights over files"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by gijs2 on 2014-05-21
Hi,

Everytime i create a new folder i need to go to my terminal and give myself full rights over EVERYTHING in the file using:
```
chmod 777 <file name>
```

Is there a way to login into ubuntu on the root account so i always have full rights over EVERYTHING?

If not please give an alternative, thanks :)

---

### Post by deadflowr on 2014-05-21
How are you creating files?
The default permission are read/write for owner(you)
The only change you might need to make is marking it as executable.
That, though, is actually a security feature, as it prevents malware from auto-running, since it would need to be executable, which Ubuntu's file management purposely makes the user need to mark it.
If that makes sense.

---

### Post by gijs2 on 2014-05-21
> **deadflowr said:**
> How are you creating files?
The default permission are read/write for owner(you)
The only change you might need to make is marking it as executable.
That, though, is actually a security feature, as it prevents malware from auto-running, since it would need to be executable, which Ubuntu's file management purposely makes the user need to mark it.
If that makes sense.

Yeah that makes sence but I have one more question ^^
How can i give full rights to a file and everything it contains, since i sometimes get files from co-workers and i wont be able to use it with my local server since i do not have full rights over everything in the file.

---

### Post by deadflowr on 2014-05-21
What methods are you using for file-sharing?

---

### Post by gijs2 on 2014-05-21
> **deadflowr said:**
> What methods are you using for file-sharing?

Either dropbox or Smartgit.

---

### Post by grahammechanical on 2014-05-21
Have you tried copying and saving the file? Another problem with working as root/administrator is that every folder and file we create as root will only have read access for other users and that includes us when we are not working as root.

As a test I have just created a new folder on the desktop and when I use File Manager to check its permissions I see that the Owner is ME with access to create and delete files and the Group is my username with access to create and delete files but Others can only Access the folder. And I, although listed as administrator. am not working as root but as a standard user, which is the Ubuntu method. 

Now, if I was to work as root I, as standard user would only have access to the folder. I am not sure why you have a problem. Sorry.

---

### Post by gijs2 on 2014-05-21
> **grahammechanical said:**
> Have you tried copying and saving the file? Another problem with working as root/administrator is that every folder and file we create as root will only have read access for other users and that includes us when we are not working as root.

im sorry but i meant a whole map with files in it, sometimes the map contains alot of files so i dont want to go by each file and give them all rights

---

### Post by grahammechanical on 2014-05-21
When we as a standard user create a folder and copy files into it we can use File Manager to change the permissions of all the enclosed files. I have more than on installation of Ubuntu and if I copy files/folders to another installation I get this permissions problem whejn I log in to that installation. Even though I have the same password on all my installs. 

I use the file manager Change Permissions for Enclosed Files. It lets me set files for Read and Write and folders for Create and Delete files. It is a lot less bothersome than doing it one file/folder at a time.

---

### Post by gijs2 on 2014-05-21
> **grahammechanical said:**
> When we as a standard user create a folder and copy files into it we can use File Manager to change the permissions of all the enclosed files. I have more than on installation of Ubuntu and if I copy files/folders to another installation I get this permissions problem whejn I log in to that installation. Even though I have the same password on all my installs. 

I use the file manager Change Permissions for Enclosed Files. It lets me set files for Read and Write and folders for Create and Delete files. It is a lot less bothersome than doing it one file/folder at a time.

I think i downloaded the wrong one, could you pass me a link or terminal line?

---

