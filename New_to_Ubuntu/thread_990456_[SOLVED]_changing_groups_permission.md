---
title: "[SOLVED] changing groups permission"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-22
I just added a file to change my styles on phpbb3 board. I change the ownership of the file too root. Now I need to change the group folder access currently set too none. To a group folder access: access files. The file is located in /usr/share/phpbb3/styles/ file name is reGrey.

---

### Post by MuH4hA on 2008-11-22
You can change the permissions of a file or directory with the command 
```
chmod XYZ /your/directory/or/file
```

where XYZ are octal numbers, X representing the permissions of the owner, Y of the group and Z of all the others.

for example:

```
chmod 755 /usr/share/phpbb3/styles/
```

07 = 0b111 [read=true][write=true][execute=true]
05 = 0b101 [read=true][write=false][execute=true]

if it is a directory, 7 is r/w access. 5 would be your desired 'access files'. 

For more information look at ```
man chmod
```

---

### Post by shanep-server on 2008-11-22
thank you I figured it out though.

You were right. I was setting the folder down in etc/phpbb3/styles instead of /usr/share/phpbb3/styles however I had to go in using nautilus to change the folders permissions. And i had to change the owner of the file too root.

Owner: root
Folder access: create and delete files

Group: root
Folder access: access folder

Others: None
Folder access: access folder

Then the folder showed up like prosilver and subsilver2. Then I was able to log into phpbb3 as admin > administration > styles and install like normal.

---

