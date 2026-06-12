---
title: "How do I extract a .tgz file simply and consistently without errors?"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by nauru on 2011-11-27
Everytime I try to follow a set of instructions I get 

Cannot open: No such file or directory
Error is not recoverable: exiting now
Child returned status 2
Exiting with failure status due to previous errors

I have checked the filename multiple times.  It is correct.  android-sdk_r15-linux.tgz

First I tried with it sitting in a folder

Then with the file sitting on the desktop.

I am typing according to a set of instructions: tar xvfz android-sdk_r15-linux.tgz

Is there any GUI alternative for extracting tar files, for people like me who just suck at Linux?  I miss 7zip, extracting a file and getting a new application up and running was so simple...

If it is actually just as simple here in ubuntu, and I'm missing some huge shortcut, please let me know.

---

### Post by CryptAck on 2011-11-27
I usually use a dash, not sure if it matters though...
```

tar -xvzf <filename>.tgz

```
Could give that a shot.

---

### Post by Telengard C64 on 2011-11-27
> **nauru said:**
> 
I am typing according to a set of instructions: tar xvfz android-sdk_r15-linux.tgz

You've transposed a couple letters in the command. Try like this:

```
tar -xvzf android-sdk_r15-linux.tgz
```

> Is there any GUI alternative for extracting tar files, for people like me who just suck at Linux?

Yes. On Kubuntu I use Ark.

> I miss 7zip, extracting a file and getting a new application up and running was so simple...

You can install 7-Zip on Ubuntu. Look for these packages:
[list]
[*]p7zip - 7zr file archiver with high compression ratio
[*]p7zip-full - 7z and 7za file archivers with high compression ratio
[*]p7zip-rar - non-free rar module for p7zip
[/list]

Note that p7zip does not come with a GUI, so command line only unless you have a GUI frontend like Ark.

---

### Post by CryptAck on 2011-11-27
I think file-roller (a GUI) will actually perform this operation for you...

---

### Post by beew on 2011-11-27
If all you need is to access the content,--rather than learning the intrincacies of the tar command,-- then simply right click and either choose "extract here" from the drop down menu, or choose "open with file manager" and when it is opens, click "extract to" and pick a destination for the extracted files.

---

### Post by beew on 2011-11-27
> **Telengard C64 said:**
> 
Note that p7zip does not come with a GUI, so command line only unless you have a GUI frontend like Ark.

  There is a third party GUI for p7zip, it is called Q7Z, then it becomes J7Z. Q7Z works quite well but I have not been able to get J7Z to work. You can find both here[ http://sourceforge.net/projects/k7z/files/]("http://sourceforge.net/projects/k7z/files/")

---

### Post by Paqman on 2011-11-28
> **beew said:**
> right click and <snip> "extract here"

This. No need at all to be messing about with the command line for such an easy task.

---

### Post by 3rdalbum on 2011-11-28
> **nauru said:**
> Is there any GUI alternative for extracting tar files, for people like me who just suck at Linux?

That awkward moment when someone tells you that you can just double-click on the archive and your wish will come true :-)

I've never once extracted a .tar.gz or any other archive on the command-line. I always just double-click it and extract it in the GUI.

---

