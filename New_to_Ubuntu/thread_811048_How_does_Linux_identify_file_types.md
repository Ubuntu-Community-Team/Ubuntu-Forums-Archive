---
title: "How does Linux identify file types?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by deleyd on 2008-05-28
In Windows a file's type is identified by it's filename extension. I heard in Linux that isn't so, and file type is identified by the first line of the file, such as
```
#!/bin/sh
```
identifies the file as a, umm, 

Where can I read more about this? And I'd like a list of common file types and their corresponding first line.

---

### Post by Oldsoldier2003 on 2008-05-28
actually that line tells the script the path to te command interpreter. for a perl script it would be tell you where perl is located etc...

---

### Post by SunnyRabbiera on 2008-05-28
It depends, most file types out there will be recognized by Linux by default...
usually stuff like configuration files have no extension so people dont mess them up, but they can be opened by the text editor and such...

---

### Post by sdennie on 2008-05-28
You may want to google for unix magic numbers.  That should move you in the right direction.

---

### Post by lisati on 2008-05-28
Just a slightly off-topic "aside": With windows and MS-DOS, it kinda "depends" too - MS-DOS & the Windows DOS prompt do use the extension as a guide some versions do a little bit more work. I've seen DOS ".COM" files which are really ".EXE" files in disguies, which the command interpreter quite happily recognizes and deals with appropriately. And there's ".EXE" and there's ".EXE" - some work only with Windows, some both Windows & DOS, and some with DOS only; this is achieved by having different information recorded in the EXE file header (not present in the "real" COM file format that the OS is able to use to decide whether or not to run the program. (And just to confuse things further: "COM" in Windows can have a different meaning to that in MS-DOS)

---

### Post by nick_h on 2008-05-29
You can find additional information in the manual page for the *file* command:
```
man file
```

---

### Post by Martje_001 on 2008-05-29
[COLOR="Red"]Edit2: Below information is not true, sorry[/COLOR]

Linux has got nothing to do with file reconizing. The Linux kernel only knows if it is executable and with what permissions. It doesn't know if it is a windows file, or a emerald file.

The thing that recognizes files is nautilus (in gnome), or so-called a 'file-browser'.

Edit: Look at the command `ls -l` to see how the kernel see's things

---

### Post by Zacariaz on 2008-05-29
I don't know which part is responsible, but linux, like most other OS does indeed recognize file types.
File types are usually recognized by looking at the header and the footer in the file, fx. the first 8 bytes of a png file is always "137 80 78 71 13 10 26 10" and the last 8 is "73 69 78 68" plus a 4 byte crc I can't remember.

So, it is fairly easy to recognize a file type if you know what to look for. This is also the reason that you can execute an exe file as a com file (or any other extension in theory) in windows. The only reason you need and extension like exe or com is for safety reasons. Fx. it wouldn't be cool to download a document which the executed some sort of virus or something, when trying to open it. Just like files need permission to be executed in linux.

---

### Post by niteshifter on 2008-05-29
Hi,

> Linux has got nothing to do with file reconizing. The Linux kernel only knows if it is executable and with what permissions. It doesn't know if it is a windows file, or a emerald file.

The thing that recognizes files is nautilus (in gnome), or so-called a 'file-browser'.

Actually .... it does. Before you go "no way" there are two types of "magic" here:

Userland file identifiers as per the utility find. See:
```
man find
man magic

```
The part of the OS that deals with these is the shell.

The other "magic numbers" that the kernel itself deals with are the file system type identifiers - the "super-magic" numbers. If you have linux-headers installed you can see these defined in:
```
cat /usr/src/linux-headers-`uname -r`/include/linux/magic.h
```

---

### Post by KingTermite on 2008-05-29
> **lisati said:**
> Just a slightly off-topic "aside": With windows and MS-DOS, it kinda "depends" too - MS-DOS & the Windows DOS prompt do use the extension as a guide some versions do a little bit more work. I've seen DOS ".COM" files which are really ".EXE" files in disguies, which the command interpreter quite happily recognizes and deals with appropriately. And there's ".EXE" and there's ".EXE" - some work only with Windows, some both Windows & DOS, and some with DOS only; this is achieved by having different information recorded in the EXE file header (not present in the "real" COM file format that the OS is able to use to decide whether or not to run the program. (And just to confuse things further: "COM" in Windows can have a different meaning to that in MS-DOS)

I'm not claiming to be an expert on this...but from my memory of the good old DOS days......

I believe COM files came first, in the early DOS days. They were the first executable files. They were created by a user from a built in (DOS) utility which allowed you to program assembly or machine code (I think it might have had to be machine code) and then link it (with linker.exe or linker.com).

As time evolved, EXE files became the norm and COM files became less and less common. There were still a few because they were remnants from the  previous days.

---

### Post by Xerp on 2008-05-29
The "file" command can be used to show what a file is. For example:

$ file unknownfile.extension

---

### Post by ShodanjoDM on 2008-05-29
> **Xerp said:**
> The "file" command can be used to show what a file is. For example:

$ file unknownfile.extension

Exactly. Here's an example that I just encountered yesterday.

My sister got back from her office and gave me her laptop (that I've installed Ubuntu last month). She told me that she couldn't open a MS Word document that she created in another computer.

At first I though it was a .docx (MS Office 2007) format, so I downloaded the .docx converter. But even with the converter installed, the document was still unreadable.

So I summoned the terminal, and type the command that I know Linux does best:

```
file Document.doc
```

The output shown that it's a data file, not a Microsoft Word document. Then I noticed that the file was only 26kb - I don't think a full A4 page of sentences, saved in MS Word format, could be so small.

My suspicion confirmed after I made a comparison. I created a document in OpenOffice with only six letters and saved in MS Word format. It was 65kb and the "file" command correctly identified it as MS Document format.

What was it then? I highly suspect that the "Document.doc" file was actually a virus, since I've seen a virus corrupted MS Office files so bad and deflated the size to around 20 -30kb.

Too bad the "file" command doesnt gave output something like "Hey, kiddo, this is a virus, OK? Lucky you, you don't run Windows anymore." :lolflag:

---

### Post by KaliVoid on 2008-05-29
read the description part of the "file" command manual 
it will give you some idea how it (try to) recognize file types

type in terminal
```
man file
```

---

### Post by nick_h on 2008-05-29
> read the description part of the "file" command manual 
Yes, this is the command I intended in my earlier post - the man page is worth a read.

---

