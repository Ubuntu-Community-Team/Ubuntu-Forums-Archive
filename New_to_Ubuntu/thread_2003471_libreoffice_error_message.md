---
title: "libreoffice error message"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by al.adab on 2012-06-14
hello

all of a sudden when I open libreoffice writer I get the following error message: 

[I]LibreOffice 3.5
error loading BASIC of document
file:///home/imageraw/.config/libreoffice/3/user/basic/dialog.xlc:
General Error
General imput/output error[/I]

what does that mean? I need to click twice on the "OK" on the error message to open a blank document. If I *gedit* it the file appears to be empty. What am I supposed to do?

thanks.

---

### Post by chamber on 2012-06-14
[http://www.oooforum.org/forum/viewtopic.phtml?t=22402](http://www.oooforum.org/forum/viewtopic.phtml?t=22402)

Some info.

Look at post 7

---

### Post by al.adab on 2012-06-14
thanks chamber for pointing me to this. I can follow the steps up to "the Libraires tab in the Macro Organize window" but then I'm lost. I can see no "web wizard", and the reference this post and the other one included in it (re: "my macro library had an old/bad entry") doesn't make much sense to me...

LibreOffice worked fine till last night. I downloaded a Xubuntu update this morning - can't remember what was in it - and I now get this error. I don't know if the two things are related, but in Synaptics I can't see anything unusual re: LibreOffice. Or maybe I'm not looking at the right place/entries. 

Any idea? The version of LibreOffice I have is the 3.5.4.2. It came with the latest version of Xubuntu.

---

### Post by chamber on 2012-06-14
check first if the file is actually there

```
ls -la home/imageraw/.config/libreoffice/3/user/basic/dialog.xlc
```

If it's there, open it with geditand check the content for invalid paths.

If there's no dialog.xlc at that place search for it and then copy it back in where it should be

```
locate dialog.xlc
cp [location of file] home/imageraw/office/.libreoffice/3/user/basic/dialog.xlc
```

---

### Post by al.adab on 2012-06-14
feeling kind of stupid, sorry...:

[I]locate dialog.xlc
/usr/lib/libreoffice/presets/basic/dialog.xlc
/usr/lib/libreoffice/share/basic/dialog.xlc[/I]

[I]~$ cp /usr/lib/libreoffice/share/basic/dialog.xlc /home/imageraw/office/.libreoffice/3/user/basic/dialog.xlc
cp: cannot create regular file `/home/imageraw/office/.libreoffice/3/user/basic/dialog.xlc': No such file or directory[/I]

...

---

### Post by chamber on 2012-06-14
post the output of 

```
ls -l /home/imageraw/office/.libreoffice/3/user/
ls -l /home/imageraw/office/.libreoffice/3/user/basic/
```

---

### Post by al.adab on 2012-06-17
[I]imageraw@T42:~$ ls -l /home/imageraw/office/.libreoffice/3/user/
ls: cannot access /home/imageraw/office/.libreoffice/3/user/: No such file or directory
imageraw@T42:~$ ls -l /home/imageraw/office/.libreoffice/3/user/basic/
ls: cannot access /home/imageraw/office/.libreoffice/3/user/basic/: No such file or directory[/I]

---

### Post by chamber on 2012-06-17
Then it must be 

```
cp [location of file] home/imageraw/office/.libreoffice/3/imageraw/basic/dialog.xlc
```

Be sure to double check the actual foldername.

---

### Post by al.adab on 2012-06-18
thanks chamber for your help. Sorry it still doesn't seem to work. I've eventually decided to purge+remove LibreOffice and install the latest version. The error message is now gone.

---

### Post by chamber on 2012-06-18
No worries.  As long as it works for you.

---

