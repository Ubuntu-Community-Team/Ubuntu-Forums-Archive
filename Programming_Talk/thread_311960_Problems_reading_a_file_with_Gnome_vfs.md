---
title: "Problems reading a file with Gnome vfs"
date: 2006-12-03
forum: Programming Talk
---

### Post by theDentist on 2006-12-03
Can someone help me,  I am learning to use gnome vfs and come across a problem I don't understand.  In a sample program, I've written a small file to disk that contains a short string as an example, it is 47 bytes in length.  When I try to read it using:
 
     result = gnome_vfs_read(fd, buffer, nbytes, &bytes_read);

where fd is the file descripter and Buffer is a gpointer, nbytes is the number of bytes to read.  Everything works fine up to 16 bytes but I get a segmentation error if I try to read more,  WHY???    ](*,)

---

### Post by theDentist on 2006-12-03
I seemed to have solved my own problem, I allocated memory to my gpointer buffer and it solved the problem       :)

---

