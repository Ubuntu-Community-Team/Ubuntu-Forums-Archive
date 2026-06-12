---
title: "[mono]Working with special characters, problem on ubuntu"
date: 2010-02-23
forum: Programming Talk
---

### Post by popopop on 2010-02-23
Hi all
I'm working with  special characters in filename 

my project is a Drag n Drop app, just drop a illegal filename and covert it legal
it's worked fine on windows but not on ubuntu

[solution 1]
using winform and System.Windows.Forms.DragEventArgs
with this line to receive file drop 
```
 string[] photo = (string[])e.Data.GetData(DataFormats.FileDrop, false);
```
sample, if filename is " $@#%^&.jpg "
on windows it return photo[0] =  " $@#%^&.jpg "    **it's right**
but in the same code on ubuntu, it  return  photo[0] =  " /@ %$#.jpg "   **??**
ubuntu gives the wrong filename, _why..ubuntu? nautilus?_

so.. 
[solution 2]
using Gtk# and Gtk.DragDataReceivedArgs
with this line to receive file drop 
 ```
string data = System.Text.Encoding.UTF8.GetString(args.SelectionData.Data);
```
gtk return a uri but system.io.file class doesn't suppprt uri, so i can't copy it with file.copy method
_is there another solution?_ :confused:

Thank you so much
and sorry for my english

Giggs, popopop

---

