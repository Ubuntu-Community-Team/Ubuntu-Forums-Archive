---
title: "gtk file chooser - save as specific filetype"
date: 2008-07-02
forum: Programming Talk
---

### Post by pcman312 on 2008-07-02
Is there a way of having the GtkFileChooser save files as a specific filetype? I have it currently so that the filename is checked to see if it has the proper extension in my signal function and corrects it (a -> a.tar.bz2) however, if the file exists (a.tar.bz2 for example) and I just put in "a" into the dialog box, the name will be corrected to a.tar.bz2, however it will not prompt me that the file already exists.

I'm wondering if there is a way to force the GtkFileChooser to save files as a specific filetype or to force a recheck to see if the file exists. I'd rather not have to manually write it to do the check and pop up a "are you sure?" box. No need to reinvent the wheel.

---

### Post by Can+~ on 2008-07-02
Use the GtkFileFilter

[PHP]filter = gtk.FileFilter()
filter.set_name("Disc Image")
filter.add_pattern("*.iso")
file_chooser.add_filter(filter)[/PHP]

About auto-adding the .extension, I don't know.

---

### Post by pcman312 on 2008-07-02
I looked in to the GtkFileFilter, but it only seems to limit what is displayed in the chooser. You can still type in a filename that doesn't correspond with the proper extension.

I forgot to mention, I'm writing this in C/C++ (if it really matters).

---

### Post by garolou on 2010-12-23
I know this is an old post, but for those interested, you can find a python script at the following link that works for folders, with a few tweaks it could be changed to create & validate filenames.

link--> [http://stackoverflow.com/questions/4515916/pygtk-gtk-filechooser-is-it-possible-to-validate-user-entry-before-file-or-fold]("http://stackoverflow.com/questions/4515916/pygtk-gtk-filechooser-is-it-possible-to-validate-user-entry-before-file-or-fold")

---

