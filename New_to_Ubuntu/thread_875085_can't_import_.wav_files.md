---
title: "can't import .wav files"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by danny138 on 2008-07-30
Hello All, I'm quite new but am trying to learn by reading and searching forums. I wanted to get some .wav files for my Hardy and thought it would be simple, drag and drop, cut and paste, etc. I did everything that could within permissions but still couldn't copy/import these. I did notice under the permissions that root was not an option in the drop box. If anyone can help I would greatly appreciate it. Thanks, danny

---

### Post by t0p on 2008-07-30
Welcome to Ubuntu!  

You haven't made it clear what exactly you're trying to do.  Are you trying to download these files from a website?  Are they on a CD?  Are you trying to transfer them from another partition on the same computer?  You say that "root is not an option on the drop box" - what drop box? Why do you think root *should* be an option?

---

### Post by OffAxis on 2008-07-30
Sounds like a permission problem. you can elevate to the super user account and open nautilus by typing this into a terminal
```
gksudo nautilus
```
and then do your cut and paste thing.

---

### Post by danny138 on 2008-07-30
I'm sorry about the lack of info. Thes are two .wav files brought from one of my other machines via a 4G flash drive. The root observation was on the Properties-> Permissions-> Group. The wav files in /usr/share/sounds/ have root selected in Group. Thanks for fast response, danny

---

### Post by t0p on 2008-07-30
Are you trying to install the files to your home directory, or to /usr/share/sounds?  If to your home directory, I don't know why you're experiencing these problems - but following OffAxis's advice should sort it out.  If you are trying to install to /usr/share/sounds, you are having problems because users don't normally have permission to write to /usr.  Again, 

```
gksudo nautilus
```

will solve the issue.  **But:** Are you *sure* you want to save to this location?

---

