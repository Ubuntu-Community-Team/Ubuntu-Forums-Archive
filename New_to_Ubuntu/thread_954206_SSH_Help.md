---
title: "SSH Help"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-10-20
I need to grab some files off my schools computer (username@blah.blah).    I need to do it from my end so I don't have to worry about the firewall. I've done this before, but I don't remember the code. What would be the proper code to do this?

---

### Post by PointyWombat on 2008-10-20
I assume you're trying to just copy over ssh???
```

scp user@blah:/full/path/to/your/files .

```

---

### Post by garyed on 2008-10-20
Assuming you can access the remote computer using the ssh command you can just use the scp command.

To copy the file "file1.txt" from a remote host to the local host

   ```
    scp your_username@remotehost.edu:file1.txt /local/directory 
```

---

### Post by alphacrucis2 on 2008-10-21
> **subaruwrc01 said:**
> I need to grab some files off my schools computer (username@blah.blah).    I need to do it from my end so I don't have to worry about the firewall. I've done this before, but I don't remember the code. What would be the proper code to do this?


You can supposedly do this from Nautilus if you want graphical drag and drop etc. Take a look at this:

[URL="http://linux.about.com/od/ubuntu_doc/a/ubudg10t9.htm"]http://linux.about.com/od/ubuntu_doc/a/ubudg10t9.htm

[/URL]

---

### Post by DirtDawg on 2008-10-21
For a nice, Nautilus/GUI option, use Places>Connect To Server then under Service Type choose SSH and fill out the appropriate information.

---

### Post by Nepherte on 2008-10-21
Another option is to use filezilla with sftp as file transfer protocol. The above suggestions are possible too of course.

---

### Post by Idefix82 on 2008-10-21
Just to add to the above suggestions:
if you want to get several files and to maybe also upload some, you can do
```
sftp your_username@remotehost.edu
```
and then to get a file
```
get file
```
and to upload a file
```
put file
```
You can also browse the remote directory with the usual cd, ls and so on. When you are done type
```
exit
```
to close the connection.

---

