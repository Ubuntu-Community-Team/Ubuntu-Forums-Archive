---
title: "File copying"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by sandeep10101993 on 2012-04-14
Hey guys help required immediately. i want to copy contents of a file from one directory to another without actually copying the whole file. i will create a new file by myself in a directory and then i want to copy the contents of a file in another directory. step by step instructions pls.... i'm still a learner.(ubuntu terminal) .cpp-type files.

---

### Post by anejo on 2012-04-14
Firstly, you don't specify what TYPE of file you're wanting to copy the contents of.
Irrespective...
It should go kinda the same way.
Lets assume something common like a document where the type could be text, RTF, ODT, DOC...
Lets assume you wanted to copy content from 'something.doc' to 'otherthing.doc'...
1. open /path2/somefolder/something.doc
2. start a new doc called otherthing.doc
3. copy content you wanted from the one to the other
4. when you're done, save /path2/otherfolder/otherthing.doc

IF your question was understood... it should be that simple!

---

### Post by jroa on 2012-04-14
Are you wanting to take the contents of one file and attach it to the contents of another file using only the command line?  Also, what type of files are we talking about?

---

### Post by ajgreeny on 2012-04-14
I asume you mean copying in the command line or terminal, and if so you can do it with various terminal comands, including **tee**, which I've never used, or more easily (for me at least) with **cat**.
```
cat /path/to/source/file >> /path/to/new/file
``` The >> appends the output you get from the cat command to the end of the new file you made. If the new file does not yet exist the command would write that new file without you making it first.  The original file will remain untouched, exactly as it was.

This will only work properly with simple text files, not much else, as far as I am aware.

---

### Post by sandeep10101993 on 2012-04-15
yes. .cpp files. i just want a new file with same contents as old file but with its date of creation changed and also i should be able to change its directory(of new file). i know that this can be done using command: cp oldfile newfile |But the new file will be in same directory as old file.

---

### Post by sandeep10101993 on 2012-04-15
i think ur reply is helpful must try it in lab. does it require any admin rights? someone told that typing sudo will help
.

---

### Post by ajgreeny on 2012-04-15
> **sandeep10101993 said:**
> yes. .cpp files. i just want a new file with same contents as old file but with its date of creation changed and also i should be able to change its directory(of new file). i know that this can be done using command: cp oldfile newfile |But the new file will be in same directory as old file.
The date will not be the same, as you say if you do not use the -p option. It  will instead have the copy date.

Also the directory will not be the same if you use the full new file pathway in the cp command, eg ```
cp /home/username/foldername/file.txt /full/new/path/to/file.txt
``` You can name the new file as something completely different if you wish.

---

### Post by sandeep10101993 on 2012-04-15
yes i wanted the date(of newfile) to be changed to the date on which the file was copied. THANK YOU.

---

### Post by Hadaka on 2012-04-15
You can also change the file time/date stamp with the touch command.
man touch      for options.

---

