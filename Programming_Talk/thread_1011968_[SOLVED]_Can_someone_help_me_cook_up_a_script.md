---
title: "[SOLVED] Can someone help me cook up a script?"
date: 2008-12-15
forum: Programming Talk
---

### Post by zenkaon on 2008-12-15
Hello,

I am in need of a script that will change the permissions of lots of directories and files, but my scripting is rusty.

I am looking to set the chmod of all directories to 2775 and all files within those directories to 0644.

I have been recommended using:
```
       
find ./ -type d -exec chmod 2775 '{}' \;
find ./ -type f -exec chmod 0664 '{}' \;

``` 

Which would work fine if I didn't have spaces in my directory and file names. My files are organised like:
```

~/Some Band/There first Album/01 - Some Song.ogg

```

The find lines above can't find the directory "Some" or the directory "Band" and hence doesn't do what I want.

Can anyone cook up a shell script which would do what I'm after?

Cheers

---

### Post by mssever on 2008-12-15
> **zenkaon said:**
> ```

find ./ -type d -exec chmod 2775 '{}' \;
find ./ -type f -exec chmod 0664 '{}' \;

```Which would work fine if I didn't have spaces in my directory and file names.
Are you sure you used exactly those commands? They work for me as written with files and directories containing spaces.

---

### Post by mkrahmeh on 2008-12-15
you need to instruct find command to handle newlines, spaces,..etc in file names properly, here is my suggestion
```
find ./ -type d -print0 | xargs -0 chmod 2775
```
as for files, just modify the command accordingly

though its not your case, but its noteworthy that the working directory "./" will be the first to be affected by chmod, so in case the new mode prevents execution, the chmod wont be able to continue working upon inner directories
good luck..

---

### Post by zenkaon on 2008-12-16
Cheers mkrahmeh

That's worked a treat. My permissions are all sorted now.

I'm doing this on a Western Digital MyBookWorld, which is running Linux 2.6.17.14 and didn't like my original find lines.

---

### Post by mkrahmeh on 2008-12-16
glad i helped..anyway, i still dont know how to remove x mode from all directories, since the outer directory will be the first to be affected
i mean
```
find ./ -type d -print0 | xargs -0 chmod a-x
```
will only remove the x mode for ./ and thus chmod for inner directories will be denied !!

---

### Post by mssever on 2008-12-16
> **mkrahmeh said:**
> glad i helped..anyway, i still dont know how to remove x mode from all directories, since the outer directory will be the first to be affected
i mean
```
find ./ -type d -print0 | xargs -0 chmod a-x
```will only remove the x mode for ./ and thus chmod for inner directories will be denied !!
You could do it in two steps, the first being ```
find * .* -type d -print0 | xargs -0 chmod a-x
```But, the OP didn't ask to clear the x bit, and good reasons to do so must be very obscure indeed.

---

