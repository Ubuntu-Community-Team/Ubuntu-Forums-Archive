---
title: "cpp crisis"
date: 2008-09-23
forum: Programming Talk
---

### Post by thefestival on 2008-09-23
I have a huge program I've done for school and i also have an alias to time everything. it's g++ -pg.  I tried to use this forgetting where the -o goes and did this:
  505  timing -o earthquake.cpp a.out

now my earthquake.cpp has disappeared.

1. is there a way to undo everything you've done to a certain point? (not holding my breath on this)

2. why can I not simply enter a.out, rename it earthquake.cpp and away we go. it won't change it or revert it.

edit: my ./earthquake still works fine.  would i be able to rebuild it from that?

help needed

heres my log, just in case it wasn't that particular command that did it.

```
  505  timing -o earthquake.cpp a.out
  506  clear
  507  timing earthquake.cpp a.out
  508  timing earthquake.cpp -o a.out
  509  alias
  510  timing earthquake.cpp a.out
  511  timing -o earthquake.cpp a.out
  512  cpp earthquake earthquake.cpp
  513  ls
  514  cpp earthquake earthquake.cpp
  515  alias
  516  cpp earthquake earthquake.cpp
  517  cpp earthquake.cpp earthquake
  518  clear
  519  ./earthquake
  520  ls
  521  vim a.out
  522  vim test.out
  523  vim earthquake.tt
  524  vim earthquake.txt
  525  vim a.out
  526  vim earthquake.cpp
  527  ls
  528  vim test.out
  529  vim gmon.out
  530  vim oeq.cpp
  531  vim earthquake
  532  vim a.out
  533  vim earthquake.cpp 
  534  ls
  535  cat test.out
  536  clear
  537  ls
  538  vim gmon.out
  539  list
  540  man list
  541  u #
  542  ls
  543  vim a.out
  544  vim earthquake.c
  545  vim earthquake.cpp 
  546  vim earthquake
  547  vim gmon.out
  548  vim earthquake.cpp 
  549  vim test.out
  550  history | more > hist
```

---

### Post by issih on 2008-09-23
The a.out file is compiled native machine code, it doesn't resemble the source code any more, so I'd forget that idea. I'm not sure what you've done to lose your original earthquake file, because I don't know what the -o option of the timing program has done with it, let alone what the timing program is actually for, nor why it would need the source code and the compiled program as inputs, frankly I'm confused by it.

I'd suggest looking for an earthquake.cpp~ file in the same directory, linux often saves backups of files that alter using that format.

---

### Post by SeanHodges on 2008-09-23
Agree with issih, try:

```
cp earthquake.cpp~ earthquake.cpp
```

Vim makes a backup file as it goes.

If you get your file back, remember to back it up regularly from now on!

---

### Post by thefestival on 2008-09-23
There is no backup, first thing I checked.  I'm thinking that i may be able to reverse the executable(??) 

And yes I have learned my lesson about backing up.  Such a harsh lesson though.

---

### Post by LaRoza on 2008-09-23
> **thefestival said:**
> I'm thinking that i may be able to reverse the executable(??) 

You disassemble it (that is what it is called), but you'd have to know GAS and Linux extremely well to use it for anything.

---

### Post by thefestival on 2008-09-23
I guess i'm well and truly screwed.

But thanks guys.

---

### Post by Lux Perpetua on 2008-09-23
Decompilation is possible, but it's impossible in general to recover the original source code. I could be totally wrong, but I'd expect decompilation to be more useful when the source code includes debugging symbols, as when compiled with g++ -g. I could be wrong, but hang on to your executable until you're sure. 

If you can't get your code back, don't feel too bad; I've done worse. Once I did this: 
```
$ rm core *
rm: core: no such file or directory
rm: cannot remove directory XXX
rm: cannot remove directory YYY
...
$   # Oh, @#$%
```
It took me weeks to rewrite the code for that project.

---

### Post by lisati on 2008-09-23
> **thefestival said:**
> There is no backup, first thing I checked.  I'm thinking that i may be able to reverse the executable(??) 

And yes I have learned my lesson about backing up.  Such a harsh lesson though.

> **LaRoza said:**
> You disassemble it (that is what it is called), but you'd have to know GAS and Linux extremely well to use it for anything.

My limited experience of reverse engineering (disassembly etc) suggests that although not completely impossible, it could be difficult to restore the original c++ code. Having debugging information stored in the executable might be of some help to the disassembler but it will still mean a lot of work and head scratching to reconstruct usable source.

---

### Post by LaRoza on 2008-09-23
> **lisati said:**
> My limited experience of reverse engineering (disassembly etc) suggests that although not completely impossible, it could be difficult to restore the original c++ code. Having debugging information stored in the executable might be of some help to the disassembler but it will still mean a lot of work and head scratching to reconstruct usable source.

My experience with reverse engineering (only disassembling, of my own code, which I deleted by accident by putting a space between the word and "*".) was quite good. Python assembly is quite easy to read.

---

### Post by monkeyking on 2008-09-24
Just out of curiosity which editor did you use?

---

### Post by John164918a on 2008-09-24
I've always wanted to know is there some easy program that looks for data remenance? It might not have been overwritten and if you can remember some of the lines?

---

### Post by John164918a on 2008-09-24
Well the command numbered 505 and all commands with "-o earthquake.cpp" dont have any input files that are decent c++ source code, so they wont compile, so g++ shouldnt write anything to earthquake.cpp, even though it might have deleted it.

If you saved an empty file, then even if it was in the same disk space as the original file that got deleted, it probably hasnt actually overwritten anything.

When a file gets deleted, the data is not replaced with all zeros, so the source code is probably on your hard disk somewhere. How easy this is really depends on what file system you have. What file system do you have? the default for ubuntu I think is ext3, which looks quite hard to recover from, but there are various ways to do it.

---

### Post by SeanHodges on 2008-09-25
> **John164918a said:**
> I've always wanted to know is there some easy program that looks for data remenance? It might not have been overwritten and if you can remember some of the lines?

Ext3 cannot undelete because it clears the inode pointers to the file.

> In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone. - [http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

But you can sometimes recover the file by doing a grep search against the device filesystem:

[http://jblevins.org/computing/linux/ext3-undelete](http://jblevins.org/computing/linux/ext3-undelete)

I've just tested this against a file I created a and deleted as a test, and it worked. You must do it quickly before the deleted file is overwritten, and it doesn't seem to like it if you have the disk mounted (it worked when I ran it from a live CD).

---

### Post by issih on 2008-09-25
Even if (assuming that the timing command is g++ -pg) those attempts at compilation did only delete the file rather than overwrite it, the cpp commands later might have done nasty things. I am unsure what passing a binary file as the input to the c pre processor will do. I semi expect it will just write out that binary file into the output file as it won't find any preprocessor directives in the "text". Therefore I suspect that the file has been overwritten by now anyway...sadly.

---

### Post by nvteighen on 2008-09-25
> **LaRoza said:**
> My experience with reverse engineering (only disassembling, of my own code, which I deleted by accident by putting a space between the word and "*".) was quite good. Python assembly is quite easy to read.

Can we consider Python bytecode to be an Assembly language? Or are you talking about something else?

---

### Post by LaRoza on 2008-09-25
> **nvteighen said:**
> Can we consider Python bytecode to be an Assembly language? Or are you talking about something else?

[http://www.python.org/doc//2.4/lib/module-dis.html](http://www.python.org/doc//2.4/lib/module-dis.html)

Why not?

---

### Post by nvteighen on 2008-09-25
> **LaRoza said:**
> [http://www.python.org/doc//2.4/lib/module-dis.html](http://www.python.org/doc//2.4/lib/module-dis.html)

Why not?
Interesting. I didn't know that.

---

