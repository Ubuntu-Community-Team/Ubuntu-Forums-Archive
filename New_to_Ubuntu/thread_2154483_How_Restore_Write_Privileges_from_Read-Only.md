---
title: "How Restore Write Privileges from Read-Only?"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by Iggy64 on 2013-06-14
Oops!  I used chmod to change privileges to 444 on a directory full of files, so that they would be read-only for everyone, and no one could accidentally or otherwise erase or modify them.

Now, I want to make them writable for myself, so I can do some editing.  But I seem to be in a "Catch 22."  I try to again used chmod to change back to 744, but I don't have write privileges to do that.  I get the error message: 

chmod: cannot access file <filename> permission denied

This seems to imply that I cannot write to the inode table if the file is read-only for me.  I never thought of that.

Is there some way I can make the files writable again.

I'll bet I'm going to be even more embarrassed when I get some comments.  But I will appreciate help.  I have a lot to learn.

---

### Post by steeldriver on 2013-06-14
Does your account have 'sudo' privileges? if so you can try

```
sudo chmod -R u=rwX,go=rX *directory*
```

(note the upper case X) - that should set all files below *directory* to 644 and any subdirectories to 755 (directories need to be executable even if the files are read-only in order for their contents to be read)

---

### Post by Iggy64 on 2013-06-14
Thanks, Steeldriver!  That worked great.

I see that the key is having the directories be executable, so that their contents can be read.

The permissions area seems to be one of the most challenging for me.  Your help is very much appreciated.

---

### Post by Rebelli0us on 2013-06-15
You can also use Nautilus "Permissions" tab.

---

### Post by Iggy64 on 2013-06-15
Although I do not have Nautilus as my FM, I tried using the Permissions tab in PCManFM.  But, as this apparently is just a front end for the chmod command, it would not make the requested changes.  I first had to make the directories executable, as suggested by Steeldriver.  So I learned a lot from this little problem.

Thanks for taking time to offer the suggestion, though.  It certainly makes sense to try that.

---

