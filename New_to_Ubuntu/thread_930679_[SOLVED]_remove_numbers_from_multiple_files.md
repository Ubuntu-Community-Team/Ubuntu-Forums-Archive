---
title: "[SOLVED] remove numbers from multiple files"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by szaqlon on 2008-09-26
I have a lot of files that start with numbers, 00152, 00153, etc. I want to remove the number at the beginning and keep all the rest. I looked at gprename but couldn't see how that could be done. Is there another way to do this, or am I missing something on gprename?

---

### Post by sisco311 on 2008-09-26
> **szaqlon said:**
> I have a lot of files that start with numbers, 00152, 00153, etc. I want to remove the number at the beginning and keep all the rest. I looked at gprename but couldn't see how that could be done. Is there another way to do this, or am I missing something on gprename?
In the *Insert / Delete* tab select the *Delete between* option.

In your case set it to *Delete between 0 5*.

Click on the *Preview* button, before Rename the files.

---

### Post by digitalvectorz on 2008-09-26
this code should work to remove all the leading numbers off of the filenames in the CURRENT Working Directory, then copy it to a the appropriate filename
COPY:
```

ls | perl -ne '$a = $_; if( $_ =~ s/^\d+// ) {chop $a; `cp $a $_`}'

```


This version will just straight foward "move" the file (rename them):
MOVE:
```

ls | perl -ne '$a = $_; if( $_ =~ s/^\d+// ) {chop $a; `mv $a $_`}'

```


This version will remove the files with the leading numbers:
REMOVE:
```

ls | perl -ne '$a = $_; if( $_ =~ s/^\d+// ) {chop $a; `rm ./$a`}'

```


***DISCLAIMER/WARNING:
I would advise you not to user the 'mv' unless you're sure of what you're doing....I would advise to use the COPY version first and then the REMOVE (if you want to remove them), just so you at least are able to see the backup.

Always be careful and use warning when using command with 'rm' and other commands  you aren't completely sure of what they do.

-dvz

---

### Post by szaqlon on 2008-09-26
> **sisco311 said:**
> In the *Insert / Delete* tab select the *Delete between* option.

In your case set it to *Delete between 0 5*.

Click on the *Preview* button, before Rename the files.

Beautiful. That did it. thank you.

---

### Post by sisco311 on 2008-09-26
Cool!
Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by ghostdog74 on 2008-09-26
you can use the Python script File Renamer in my sig
example usage:
```

 # ls -1 0*filename*
00152filename1
00153filename2

# filerenamer.py -p "^[0-9]+" -e "" -l "0*filename*"
==>>>>  [ /home/00152filename1 ]==>[ /home/filename1 ]
==>>>>  [ /home/00153filename2 ]==>[ /home/filename2 ]

# filerenamer.py -p "^[0-9]+" -e ""  "0*filename*"
/home/00152filename1  is renamed to  /home/filename1
/home/00153filename2  is renamed to  /home/filename2 

# ls -1 *filename*
filename1
filename2


```

---

