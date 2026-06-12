---
title: "Glade/Python question about file chooser"
date: 2008-08-15
forum: Programming Talk
---

### Post by realitybites on 2008-08-15
i have written my first python program which is a simple front end for sftp.
i added the file choosers for remote and local paths but i have two questions.

1-what is the name of the attribute that contains the path information so i can get it after submitting?

2-how do i make file chooser work for the remote path? or can i do that at all?

i am using glade2. although i am new to python, i am an experienced programmer, so do not hesitate to give non-trivial solutions:)

best regards.

---

### Post by red_Marvin on 2008-08-15
1 You can get the file(s) with gtk.FileChooser.get_filename() and gtk.FileChooser.get_filenames().
For more information, see [here]("http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html#method-gtkfilechooser--get-filename").
(I at least think that you should be able to use the same member functions)

2 Dunno, sorry.

---

### Post by realitybites on 2008-08-15
thanks, i did it with get_current_folder_uri() function instead of yours.i think they both lead to same door. 
but i still couldn't find how to do the remote thing. i'm now gonna try if i can do it with set_current_folder_uri() function. if only i knew what to set as remote path

---

