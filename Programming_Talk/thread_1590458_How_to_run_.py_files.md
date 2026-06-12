---
title: "How to run .py files??"
date: 2010-10-07
forum: Programming Talk
---

### Post by BlackRat90 on 2010-10-07
This seems stupid of me to ask, but how can i run my program outside of IDLE? I made the .py file executable, but when i run it, nothing happens....

This is my program:
```
import os; import time

#Apartment Type:1
CurrentArea = ['Hallway','A1','A2','A3']
EntranceFrom = ['Outside','Hallway','Hallway','Hallway']
AreaAcess = ['yes','no','no','no']
AreaClear = ['yes','no','no','no']

i = 0 #cr = currentroom
game = 'playing'
    
while game == 'playing':
    
    if i == 0:
        AreaAcess[0] = 'yes';AreaAcess[1] = 'yes';AreaAcess[2] = 'yes';AreaAcess[3] = 'yes'
    if i == 1:
        AreaAcess[0] = 'yes';AreaAcess[1] = 'yes';AreaAcess[2] = 'no';AreaAcess[3] = 'no'
    if i == 2:
        AreaAcess[0] = 'yes';AreaAcess[1] = 'no';AreaAcess[2] = 'yes';AreaAcess[3] = 'no'
    if i == 3:
        AreaAcess[0] = 'yes';AreaAcess[1] = 'no';AreaAcess[2] = 'no';AreaAcess[3] = 'yes'
        
    print "Your current area:", CurrentArea[i]
    print "0.", CurrentArea[0],"- Acess:", AreaAcess[0]," Clear:", AreaClear[0]
    print "1.", CurrentArea[1],"- Acess:", AreaAcess[1]," Clear:", AreaClear[1]
    print "2.", CurrentArea[2],"- Acess:", AreaAcess[2]," Clear:", AreaClear[2]
    print "3.", CurrentArea[3],"- Acess:", AreaAcess[3]," Clear:", AreaClear[3]
    print "What room do you want to acess?"
    room = input()
    if AreaAcess[room] == 'no':
        print "You cant get into that room yet!!"
        time.sleep(2)
        os.system(clear)
    else :
        i = room
        AreaClear[i] = 'yes'
```

---

### Post by cgroza on 2010-10-07
Add this at the beginning of the file : 

```
#!/usr/bin/env python
```And try again.

This happens because the system does not know where to find the interpreter. The line above indicates it.

---

### Post by BlackRat90 on 2010-10-07
Wow! ok thank you!

---

### Post by nvteighen on 2010-10-08
> **BlackRat90 said:**
> Wow! ok thank you!

A little more explanation may be useful for you not only for Python but for other languages.

The so-called shebang line (#!) is the way you can tell the shell what kind of file this is and therefore, what interpreter to use. Think about it, a Perl, a Python and a Ruby script are all ASCII text files, so they don't have any magic number that can indentify of what file type they are.

Almost all interpreted languages need that line if you want the file to be executable (it also has to have execution permissions, of course). So, what you write is:

```

#!<path to the interpreter>

```

---

### Post by kc9jvn on 2012-08-21
I tried this, but when I double click the .py file it still opens in the text editor.

---

### Post by trent.josephsen on 2012-08-21
Double clicking a file is not the same thing as running it. Double clicking relies on some software mapping of file type to program that depends on the file manager you're using. Running a file, e.g. by typing ./file in a shell (where file is executable), invokes the mechanism nvteighen describes. (It's actually done by the kernel, not by the shell, but that's irrelevant.)

If you want double clicking to run a file instead of opening it in an editor, you'll need to change the file type association in your file manager. Try right-clicking on a .py file and look for an option called "Open As" or something like that.

Or just run it from a shell, it'll likely save you a world of grief anyway.

---

### Post by era86 on 2012-08-22
[php]python ./filename
[/php]
Or add the shebang to the beginning and do:
[php]
chmod +x filename
./filename[/php]

---

### Post by mcduck on 2012-08-22
> **kc9jvn said:**
> I tried this, but when I double click the .py file it still opens in the text editor.

In the file manager's preferences you'll find an option for choosing what to do with executable text files. You can set it to execute, open, or ask each time.

(...of course if you didn't already set the execute permission on the file before this, thats etting wouldn't even apply as the file would count as just a normal text file instead)

---

