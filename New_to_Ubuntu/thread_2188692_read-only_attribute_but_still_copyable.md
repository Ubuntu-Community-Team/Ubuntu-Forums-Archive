---
title: "read-only attribute but still copyable"
date: 2013-11-18
forum: New to Ubuntu
---

### Post by Kanefa on 2013-11-18
I have been using the following command to make sure students do not delete certain files.

```
chattr +i -R  /home/student/Books
```

However, this command makes the file uncopyable.  I would still like the students to be able to copy the file, but not delete or move it.  Any suggestions?

---

### Post by deadflowr on 2013-11-18
You should look into permissions instead of attributes.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

The gist of it would be to set all the users into a certain group and then set the files you want to share with read-only permissions.
of course it is all for moot if the users have admin rights, as they can then change both the attributes and file ownership/permissions.

---

### Post by bab1 on 2013-11-18
> **Kanefa said:**
> I have been using the following command to make sure students do not delete certain files.

```
chattr +i -R  /home/student/Books
```

However, this command makes the file uncopyable.  I would still like the students to be able to copy the file, but not delete or move it.  Any suggestions?

For what you want to do you should set the "sticky bit" on the directory /home/student/Books.  This will make the files readable but the user can't delete them.  If you want the user to be able to copy the file you would use this command```
sudo chmod 1777 /home/student/Books
```...If you want to have a directory the the student can read the file but not be able to copy it you would use this command```
sudo chmod 1775 /home/student/Books
```.

No recursion is needed.  The sticky bit is set on the root directory (Books) and anything created in it.

---

### Post by Ghost_Mazal on 2013-11-19
Forgive my ignorance , but what is the nr 1 for at the beginning of both commands ?

---

### Post by heir4c on 2013-11-19
That is the 'Sticky bit' like bab1 write in his post.
When the sticky bit is enabled than only the owner of the folder/file can remove the folder/file and nobody else (except root). So if you are the owner of a folder and you share it with other users, they can't delete your files, just read and/or executed the file. When you do ls -l  in the terminal (and you have a file with the sticky bit) than you see a t where normally stand a x  or a - under the permissions of "others" (the last one) . So when the sticky bit is activated than you see this (example): drwxrwxrw[COLOR="#FF0000"]t[/COLOR] instead of: drwxrwxrw[COLOR="#FF0000"]x[/COLOR]


[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)
[http://en.wikipedia.org/wiki/SUID](http://en.wikipedia.org/wiki/SUID)


Edit: I changed my post because of a misinterpretation where the t stands. It's not at the front but at the end of the line with the permissions.

---

### Post by Impavidus on 2013-11-19
I don't really follow the case for the sticky bit. The sticky bit is meant so that files can ony be deleted by the owner of the file and root, not by every user with write access to the directory. So you could indeed give the directory permissions 1777 and the files permission 0644. With permission 666 on the files the students cannot delete them, but can truncate them to zero length. This is the way to go if all students have permission to add books to the directory, but are only allowed to delete or move the files they added themselves.

If the students don't have permission to add files themselves, you can just put them in a directory owned by the teacher and make the files teacher-owned. Give the students read permission to the files and read and execute permission to the directory, but no write permission.

If you want to do it the really neat way, try this approach:```

sudo mkdir -p /data/course_material/particular_course/ #Or substitute any convenient directory
sudo chown teacher_of_particular_course:students_of_particular_course /data/course_material/particular_course/
sudo chmod 2750 /data/course_material/particular_course #2750: see below

#Following commands can be executed by the teacher
cp particular_file /data/course_material/particular_course/
chmod 640 /data/course_material/particular_course/particular_file #Or just make sure the umask has been set to 0022
```
This way any student who is member of the group "students_of_particular_course" has read access (but no write or delete access) to all files placed in the directory belonging to that course, the teacher of that course has write access to that directory and other people have no access.

The chmod 2750 sets access to the directory to full access for the owner, read and execute access for the group and no access for others. The "2" sets the set group ID (sgid) bit on the directory, which causes new files and directories to belong to the same group as the top directory and causes all subdirectories to inherit the sgid bit. The umask can be used to give all new files automatically the right permissions. By default the umask on Ubuntu is 0002. Change it to 0022 to give the students no write access to the files.

(Stricktly speaking, to give others no access at all the umask should be set to 0027, but without read access on the directory others have to know the file's inode number to gain access, which they can only get from somebody with legitimate access, which means they can get access anyway.)

---

### Post by Kanefa on 2013-11-23
I may need to give more info.  These files all exist in the student's home directory.  I have a simple script that needs to be able to perform a move on them (admin account). The files reside in the students home directory, but I don't want them to be able to delete them.  I do want them to be able to copy them if they want to take them home.  

I read the file permission link deadflowr posted and tried the following.  

```

sudo chown administrator:administrator readme.txt
sudo chmod 644 readme.txt

```

The administrator account takes ownership from the student's account.  Then as I understand it the owner should have read and write permissions and everyone else can only read it.  However, after setting it I log to the student's user account and delete the file without issue.

---

### Post by The Cog on 2013-11-23
Your problem there is that you don't need write permission to a file in order to be able to delete it - you need write permissions to the directory the file is in. 
And the students do have write permissions to their home folder. 

You could add the sticky bit to their home directories so that they can't delete root-owned files in there.

Or you could create a root-owned directory inside their home directory, and put the files in there. They will not be able to delete the folder because it's not empty, and if don't have write permissions to the directory they won't be able to delete the files. 
E.g. as root, do:
```
mkdir "/home/studentName/Course Material"
cp Books "/home/studentName/Course Material/"
```
Or even easier, make up a directory full of all the material that they need and copy the whole directory
```
for student in $(ls /home)
    cp -r "Course Material" /home/$student/
done
```

Edit: 
As an afterthought, I would probably not copy the files to each student's home directory but instead put links to the files into their homes. So the directory that you copy into their home directories would be a directory full of symlinks to the real file locations. This would save a lot of disk space.

---

### Post by heir4c on 2013-11-23
FYI: I make a change in my post above because the t for the sticky bit will not be seeing at the beginning of the line but at the end of the line of the permissions. Sorry about that.
[http://ubuntuforums.org/showthread.php?t=2188692&p=12851804#post12851804](http://ubuntuforums.org/showthread.php?t=2188692&p=12851804#post12851804)

---

### Post by Impavidus on 2013-11-23
I'm not sure the sticky bit trick would work. The students own their home directory, so they can remove the sticky bit and then remove the files. The root-owned directory will probably work, but still not very neat. Why not put the files in a directory they don't own and maybe put a symlink to that in their home directories? I'm used to teachers who say: `You can find the material in my home directory.' But then, I don't know what kind of material you're talking about.

---

