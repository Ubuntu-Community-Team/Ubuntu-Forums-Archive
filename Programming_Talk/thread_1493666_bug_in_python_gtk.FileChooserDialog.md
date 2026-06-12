---
title: "bug in python gtk.FileChooserDialog"
date: 2010-05-26
forum: Programming Talk
---

### Post by alterpinguin on 2010-05-26
bug in python gtk.FileChooserDialog
-
I wonder if i am the only one to notice this:

gtk.FileChooserDialog returns not the selected item
in an directory with some changing the data of a file.

Example to test uses the default example python from:
python /usr/share/doc/python-gtk2-doc/examples/gtk/filechooser.py

create a slowly growing dummy-file in the current directory, like
this one-liner in a terminal:
while true; do echo "newline"; echo "11111111">>dummy.txt; sleep 1; done

while this file is slowly growing, try the default example filechooser
and select an file from the directory where this "dummy.txt" is growing.
gtk.FileChooserDialog will return a wrong selection!

and if one try the old version:
python /usr/share/doc/python-gtk2-tutorial/html/examples/filesel.py
this will return the selected file and will not get confused by the running growth of one file in the directory.

It looks like the running update of the directory content in gtk.FileChooserDialog changes the content of the listdata without taking the changes in respect for the display - next, sometimes the fileselect-box seems to freeze at such moments and only abort works.

Anyone noticed this too? I will use the old fileselect method, because i often have a python script running and other programs changing some directory-content and getting the wrong file from the selection happens then.

---

