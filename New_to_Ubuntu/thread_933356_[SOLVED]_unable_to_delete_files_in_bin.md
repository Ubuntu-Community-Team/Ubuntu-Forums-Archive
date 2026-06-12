---
title: "[SOLVED] unable to delete files in bin?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by cairnzi on 2008-09-29
hi people, i am unable to delete 3 albums in my bin, i get the error " Permission denied "it wont let me change the permissions either so as to delete the files, its just a pain having 400+MB in the bin and not being able to delete, any help would be great.

Many Thanks.

---

### Post by SpenceMakesSense on 2008-09-29
press alt+f2 then type 
```
sudo nautilus
``` it will open up a file browser that lets you do anything

---

### Post by SuperSonic4 on 2008-09-29
If you're confident in the command line you can do ```
sudo rm -r /<directory>
```

but be very sure about this, it's much safer to do what Spence says

---

### Post by jerome1232 on 2008-09-29
> **cairnzi said:**
> hi people, i am unable to delete 3 albums in my bin, i get the error " Permission denied "it wont let me change the permissions either so as to delete the files, its just a pain having 400+MB in the bin and not being able to delete, any help would be great.

Many Thanks.

Are you talking about your Trash? At first I thought you were talking about /bin and was very confused about why you would be putting files in /bin in the first place :)

If you are talking about your trash then you could:

[COLOR="Red"]edit:I just tested running nautilus as root, then deleting the files is not a good method, it simply moves the files from your trash to root trash (located at /home/trash-##) so cli is the way to go[/COLOR]

```
gksudo nautilus
# Browse to your normal users home directory (/home/youruserhere)
  Now hit ctrl+h to view hidden files/folders
  Browse to .local/share/Trash/files
  Delete anything in here
```

or cli (easier but don't MISTYPE it could have dire consequences)
-r  remove directories and subdirectories, remove everything in them
-f  force the delete operation
-v  print what is removed into the terminal
-I  asks for confirmation before preforming the operation
```
sudo rm -rfvI ~/.local/share/Trash/files/
```

---

### Post by cairnzi on 2008-09-29
i have done as spence said and got the file browser up but cannot locate the trash folder? i am probably doing something stupid i suppose? :confused:

---

### Post by perlluver on 2008-09-29
> **cairnzi said:**
> i have done as spence said and got the file browser up but cannot locate the trash folder? i am probably doing something stupid i suppose? :confused:

Read the above post by Jerome, it is explained there.  Press Ctrl-H in your home folder and look for /.local/share/Trash/

---

### Post by cairnzi on 2008-09-29
@jerome thats it, many thanks, sorry i should have said trash and not bin. just learning lol, thanks again:D

---

### Post by perlluver on 2008-09-29
> **cairnzi said:**
> @jerome thats it, many thanks, sorry i should have said trash and not bin. just learning lol, thanks again:D

Please mark as solved.

---

### Post by jerome1232 on 2008-09-29
I hope you notice my edit, deleting them in a root nautilus just moves them to a different trash located at /home/.Trash-## where ## can be any number (it was 01 for me I suspect the same for you)

You will need to hold shift and press the delete key to actually delete the files instead of moving them to roots trash.

---

### Post by cairnzi on 2008-09-29
@jerome, yes i did, like i said just learning but think this is the right place to, many thanks again.

---

