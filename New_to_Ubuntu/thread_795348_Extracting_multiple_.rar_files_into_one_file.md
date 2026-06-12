---
title: "Extracting multiple .rar files into one file"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by NightMystic on 2008-05-15
I'm new to all this so I really can use the help. Only started using it today.

Is there a way to extract multiple .rar files into one file? Every time I extract the .rar files (44 of them) it ends up becoming 44 different files instead of one. 

What do I need to do to fix this? 

Thanks.

---

### Post by bluefrog on 2008-05-15
you need the unrar program (look for it in synaptic, you need to enable the universe/multiverse repository)

then unrar the first file should be enough.

---

### Post by PartisanEntity on 2008-05-15
use this command to unrar a series of files into one:

```
unrar x name_of_file.r00
```

---

### Post by MrWES on 2008-05-15
Mine runs right from Nautilus. Once install unrar, just right click on the first file in the archive and hit extract.

---

### Post by Paqman on 2008-05-15
> **MrWES said:**
> Mine runs right from Nautilus. Once install unrar, just right click on the first file in the archive and hit extract.

Ditto, it all happens automatically.

---

### Post by NightMystic on 2008-05-15
> you need the unrar program (look for it in synaptic, you need to enable the universe/multiverse repository)

can you explain how to do this. I'm pretty clueless.

---

### Post by bouta on 2008-05-15
Open a terminal window and type in: 

sudo apt-get install rar 

then:
sudo ln -fs /usr/bin/rar /usr/bin/unrar ..

---

### Post by NightMystic on 2008-05-15
thanks, finally got it .:KS

---

### Post by k.eight.a on 2008-09-19
Hello,

I was searching this forum for: "How to *extract multiple RAR, archive*s"?
I have found something, but haven't found answer I wanted to read...

My problem is that I have *XXX.part01.rar* > *XXX.part59.rar*
Please help me how to extract the content easily and right > eg. 1 file from more volumes and so on...
It's so time consuming to extract every volume manualy and I don't think it will be extracted the way it should be...

Edit: I mean there are some files that are in more archives as well as more files in one archive. I'd rather use some GUI application such as most people, who came from Windows to Ubuntu, have known WinRAR...

---

### Post by k.eight.a on 2008-09-19
I'm sorry, if I'd be more patient I'd found it without asking.```
unrar x XXX.part01.rar
```...have done the trick for me and extracted it the way I was asking. :)

Anyway I wonder why this simple task is not possible to perform by the archive extractor in Ubuntu...? :confused:

What GUI archive manipulator would you recommened me?

---

### Post by pigphish on 2009-09-05
The windows gui WinRar creates these part files instead of the more conventional rXX. 

Extract from the last part file and file-roller ( default Ubuntu archive manager ) should be smart enough to start from the beginning and extract all the files. 

Cheers, George

---

### Post by aktiwers on 2009-09-05
I always pick the first one, ie. xx.part1.rar, right-click and  "extract here"

---

