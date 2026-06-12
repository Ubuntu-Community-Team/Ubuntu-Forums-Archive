---
title: "mkdir help in python needed"
date: 2006-07-19
forum: Programming Talk
---

### Post by KevinW on 2006-07-19
Hi guys..I am a total noob with programming, so go easy on me:rolleyes: 
I am trying to write a simple little prog in python thats interactive. I want to be able to type in a folder name and have the code make that directory.

I just can't figure out how to make this input data work in the "os.mkdir" line in the "pictures" directory. 

Hope this makes sense.. Thanks for any help 

Kevin 

```
FLDRNM = raw_input ('type folder name here:::')
os.mkdir('/home/kevin/pictures/')
```

---

### Post by Sendervictorius on 2006-07-19
You could try:
```

import os

cmd="mkdir " + inputline
os.system(cmd)

```

---

### Post by Ragazzo on 2006-07-19
If the pictures directory doesn't exist yet, you need to use os.makedirs('/home/kevin/pictures/' + FLDRNM).

[http://docs.python.org/lib/os-file-dir.html]("http://docs.python.org/lib/os-file-dir.html")

---

### Post by j.vimal on 2006-07-19
> **KevinW said:**
> Hi guys..I am a total noob with programming, so go easy on me:rolleyes: 
I am trying to write a simple little prog in python thats interactive. I want to be able to type in a folder name and have the code make that directory.

I just can't figure out how to make this input data work in the "os.mkdir" line in the "pictures" directory. 

Hope this makes sense.. Thanks for any help 

Kevin 

```
FLDRNM = raw_input ('type folder name here:::')
os.mkdir('/home/kevin/pictures/')
```
Or, if you are familiar with the bash like commands, you could try
```

import os
os.popen("mkdir directory")

```
or
```

os.popen("mkdir -p /this/entire/path/will/be/created")

```

---

### Post by thumper on 2006-07-19
Just use the os.makedirs command like what **Ragazzo** said.

Don't use system, or popen!

---

### Post by KevinW on 2006-07-19
Thanks guys.. the " + FLDRNM" worked like a champ
Now i'm trying to copy files to this folder..I am sure I'll be back soon!!hehe

---

### Post by KevinW on 2006-07-19
OK..I'm back "sigh"
Its obvious I have no idea what I'm doing, but I am trying..I am 41 yrs old, maybe too old to try to learn this stuff.

what I'm trying to do is copy images from a compact flash  media card to a folder. The first two lines of this code works great thanks to you guys.Now the copying part I can't get.This is just one of the lines I've tried. It needs to copy all folders after the DCIM folder to the FLDRNM..

Thanks again!!

```
FLDRNM = raw_input ('type folder name here:::') 
os.mkdir('/home/kevin/pictures/' + FLDRNM)      
import shutil
shutil.copy ( /media/EOS_DIGITAL/DCIM/,/home/kevin/picture/ + FLDRNM )
```

---

### Post by scxtt on 2006-07-19
shutil.copy appears to copy a FILE, not a whole directory ... not to mention it would probably want your directory paths in '' ...

take a look at copytree: [http://docs.python.org/lib/module-shutil.html](http://docs.python.org/lib/module-shutil.html) -- looks like it can even save you the mkdir command ...

---

### Post by KevinW on 2006-07-19
> **scxtt said:**
> shutil.copy appears to copy a FILE, not a whole directory ... not to mention it would probably want your directory paths in '' ...

take a look at copytree: [http://docs.python.org/lib/module-shutil.html](http://docs.python.org/lib/module-shutil.html) -- looks like it can even save you the mkdir command ...

Thanks scxtt for your time and response,,  Could you give me an example of how this would be written correctly,, I've tried and still can't get it to work.

```
shutil.copytree ('/media/EOS_DIGITAL/DCIM/ * / * / , /home/kevin/picture/ +FLDRNM')
```

---

### Post by scxtt on 2006-07-19
```
shutil.copytree ('/media/EOS_DIGITAL/DCIM/', '/home/kevin/picture/' + FLDRNM)
```from the info on the command itself, from python.org's module list - it looks like copytree will created the "FLDRNM" directory itself and copy EVERYTHING that exists in the DCIM folder, all files and all folders - recursively ...

---

### Post by KevinW on 2006-07-19
> **scxtt said:**
> ```
shutil.copytree ('/media/EOS_DIGITAL/DCIM/', '/home/kevin/picture/' + FLDRNM)
```from the info on the command itself, from python.org's module list - it looks like copytree will created the "FLDRNM" directory itself and copy EVERYTHING that exists in the DCIM folder, all files and all folders - recursively ...

Got it!! Thanks you so much 

Kevin

---

