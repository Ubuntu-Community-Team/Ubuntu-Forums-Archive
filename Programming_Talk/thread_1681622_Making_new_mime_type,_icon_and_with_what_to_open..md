---
title: "Making new mime type, icon and with what to open."
date: 2011-02-04
forum: Programming Talk
---

### Post by hakermania on 2011-02-04
Ok, I have made a new mime type by creating the files
/usr/share/mime/application/x-myproject-project.xml :
```
<?xml version="1.0" encoding="utf-8"?>
<mime-type xmlns="http://www.freedesktop.org/standards/shared-mime-info" type="application/x-my-project">
  <!--Created automatically by update-mime-database. DO NOT EDIT!-->
  <sub-class-of type="text/xml"/>
  <comment>Myproject project</comment>
  <glob pattern="*.myproject"/>
</mime-type>
```
/usr/share/mime/packages/myproject.xml :
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="application/x-myproject-project">
    <sub-class-of type="text/xml"/>
    <comment>Myproject project</comment>
    <glob pattern="*.myproject"/>
  </mime-type>
</mime-info>
```

By running update-mime-database and restarting nautilus, when I click for file's properties, I get
```
Myproject project (application/x-myproject-project)
```

So, I suppose that the new mime type has been created!

Now, 
1)
i) How to I make this file to be opened by default with my program?
ii) Is the file opened as an argument to the command? e.g. myprogram /path/to/file ?
2) How do i add a custom icon to this file?

Thx in advance for any information, because these are really helpful for me, as I need to have ready these before a date, soon.:p

---

### Post by hakermania on 2011-02-04
I just solved question 2 (You have to place the png icons to /usr/share/icons/THEME/mimetypes/ and then restart nautilus (nautilus -q)

But question 1i and 1ii are still here....

---

### Post by hakermania on 2011-02-04
Ok, so, I followed these steps and it didn't work
1.Make a description xml for the file type:
```
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="application/x-myapp-project">
    <sub-class-of type="text/xml"/>
    <comment>Myapps project</comment>
    <glob pattern="*.myproject"/>
  </mime-type>
</mime-info>
```
2.run "xdg-mime install --novedor myapp-myproject.xml"
3.make a myapp.desktop file for your application:
```
[Desktop Entry]
Version=1.0
Name=FULL APP NAME
GenericName=APP
Comment=HELLO
Icon=/usr/share/app/files/app.png
Exec=myapp
Terminal=false
Type=Application
Categories=Qt;Utility;
MimeType=application/x-myapp-project
```
4. run "xdg-mime default myapp.desktop application/x-myproject"


I did all these steps and restarted nautilus as well. Nothing.

---

