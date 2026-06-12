---
title: "Folder children"
date: 2007-01-02
forum: Programming Talk
---

### Post by Hairy_Palms on 2007-01-02
, i was wondering , how do i use a gtk dialog via pyGTK to let me select a folder and it return all the files in that folder?
 ive got some code that works to select multiple files but i cant seem to do the above.

just ask for any more details

---

### Post by duff on 2007-01-02
If you setup your FileChooserDialog to select a folder, you can use **glob.glob** to list the the contents of the directory returned by get_filename().

---

### Post by Hairy_Palms on 2007-01-03
thx, but thats what i dont know how to do, set my filechooserdialog to select a folder.

---

### Post by duff on 2007-01-03
you need to set the action to **gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER**

---

### Post by Hairy_Palms on 2007-01-03
thanks duff :) worked like a charm, 

is there a way to check whether the item returned by glob in a folder is another folder or or a file?

last question, i promise :)

---

### Post by duff on 2007-01-03
You could get that information from **os.stat**, but if you're needing to dive into nested directories, try **os.walk** instead of glob.

---

