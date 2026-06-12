---
title: "gnome catalog issues importing"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-08-27
I have really begun liking gnome catalog. However, it seems a little hit or miss when it comes to importing from certain CDs/DVDs/HDDs. some directories it will import and others it quits importing almost immediately after starting with the following error

 /usr/bin/..

(gnomecatalog:20867): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/gnomecatalog/glade/gcatalog.png': No such file or directory

(gnomecatalog:20867): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `icon'
/var/lib/python-support/python2.5/gnomecatalog/ui/gladeconnect.py:11: GtkWarning: gtk_widget_grab_default: assertion `GTK_WIDGET_CAN_DEFAULT (widget)' failed
  self.glade = gtk.glade.XML(utils.locate_file(file, "glade"), domain = "gnomecatalog")
Creado : /tmp/tmpWrtgHb
Montando file:///home/user
label: /home (60.9 GB)
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.5/threading.py", line 446, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/var/lib/python-support/python2.5/gnomecatalog/data.py", line 50, in import_disk
    disk = self.reader.read(path, self.app.progress_bar)
  File "/var/lib/python-support/python2.5/gnomecatalog/reader.py", line 44, in read
    self.count_files = self.dir_count(uri)
  File "/var/lib/python-support/python2.5/gnomecatalog/reader.py", line 21, in dir_count
    if info.type and info.type == 2: count += self.dir_count(uri + "/" + info.name)
  File "/var/lib/python-support/python2.5/gnomecatalog/reader.py", line 21, in dir_count
    if info.type and info.type == 2: count += self.dir_count(uri + "/" + info.name)
  File "/var/lib/python-support/python2.5/gnomecatalog/reader.py", line 21, in dir_count
    if info.type and info.type == 2: count += self.dir_count(uri + "/" + info.name)
  File "/var/lib/python-support/python2.5/gnomecatalog/reader.py", line 21, in dir_count
    if info.type and info.type == 2: count += self.dir_count(uri + "/" + info.name)
  File "/var/lib/python-support/python2.5/gnomecatalog/reader.py", line 19, in dir_count
    for info in gnomevfs.DirectoryHandle(uri):
InvalidURIError: Invalid URI




Any help is appreciated

---

