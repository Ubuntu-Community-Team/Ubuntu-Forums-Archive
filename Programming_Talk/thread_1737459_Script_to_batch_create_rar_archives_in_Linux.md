---
title: "Script to batch create rar archives in Linux"
date: 2011-04-23
forum: Programming Talk
---

### Post by chagos on 2011-04-23
I have several folders which contain files and subfolders.
Those folders are located in /home/UserName/Archives
My directories tree from /home/UserName/Archives looks like this:

====================================
DIR1
    ->SUBDIR1
             ->FILE1
             ->FILE2
    ->FILE1
    ->FILE2
    ->FILE3
DIR2
    ->FILE1
    ->FILE2
    ->SUBDIR1
            ->FILE1
            -FILE2
.
.
.
====================================

I use the next script (run from root user) to create separate archives for contents of DIR1, DIR2, DIR3,...:

====================================
cd "/home/UserName/Archives/DIR1"
rar a -m0 -r -v10m "DIR1-Archives"
mv *.rar "/home/UserName/Archives"
rm -rf "/home/UserName/Archives/DIR1"

cd "/home/UserName/Archives/DIR2"
rar a -m0 -r -v10m "DIR2-Archives"
mv *.rar "/home/UserName/Archives"
rm -rf "/home/UserName/Archives/DIR2"

cd "/home/UserName/Archives/DIR3"
rar a -m0 -r -v10m "DIR3-Archives"
mv *.rar "/home/UserName/Archives"
rm -rf "/home/UserName/Archives/DIR3"
.
.
.
=====================================

Is possible to use a smaller script which can automatically find directories names (DIR1, DIR2,...) ?

---

### Post by Vaphell on 2011-04-23
```
#!/bin/bash

arch="/home/UserName/Archives"

find "${arch}" -mindepth 1 -maxdepth 1 -type d | while read dir
do
  dname="${dir##*/}"
  cd "${dir}"
  echo rar a -m0 -r -v10m "${dname}-Archives"
  echo mv *.rar "${arch}"
  echo rm -rf "${arch}/${dname}"
done
```

try this, it will print out commands to perform. Test it thoroughly, i wouldn't want to destroy your data if something went wrong, as you got that nasty rm -rf there. if everything is ok, remove echo.

---

### Post by chagos on 2011-04-23
I've run the script logged in as 'merlin':
```
arch="/home/merlin/Archives"

find "${arch}" -mindepth 1 -maxdepth 1 -type d | while read dir
do
  dname="${dir##*/}"
  cd "${dir}"
  echo rar a -m0 -r -v10m "${dname}-Archives"
  echo mv *.rar "${arch}"
  echo rm -rf "${arch}/${dname}"
done
```$ sudo chmod +x /home/merlin/Archives/createrars.sh
$ sudo /home/merlin/Archives/createrars.sh
and I've got this error:
```
: not foundn/Archives/createrars.sh: 2: 
/home/merlin/Archives/createrars.sh: 11: Syntax error: end of file unexpected (expecting "do")
```

---

### Post by Vaphell on 2011-04-24
i copypasted that code, added #!/bin/bash in the first line (i expanded code in my previous post with that line) to force bash to execute it (though it is optional in such a simple script) and it ran just fine
it complains that 'do' is missing but it shouldn't, 'do' is there, opening the while loop. While loop syntax:
```
while <stuff>; **do**
...
done

```
or
```
while <stuff>
**do**
...
done
```

btw, if you do stuff in your home dir you don't have to and really should not use sudo. Sudo is required for administrative tasks and you own your files so you don't have to elevate your rights. One messed up rm -rf elevated with sudo and you can kiss your system goodbye. Use sudo only when you deal with files outside your home dir.

---

### Post by chagos on 2011-04-24
With the new addition and running like in my previous post, but without 'sudo', I have this error:
```
bash: ./createrars.sh: /bin/bash^M: bad interpreter: No such file or directory
```It's tested in Ubuntu Studio 10.10 Maverick 64 bit with GNOME desktop.

---

### Post by Vaphell on 2011-04-24
how did you create your script file? ^M is related to dos/windows carriage return, it shouldn't show up if the file is created in linux.
Microsoft OSes end lines with a combination of \n and \r (special characters) and linux uses only \n, that extra char is shown as ^M

try
```
sed -ri 's/\s*$//' createrars.sh
```

or create that file in linux directly

you shouldn't solve problems other than 'permission denied' with sudo (and that only when outside of /home/username/). You will hose your system sooner or later.

---

### Post by chagos on 2011-04-24
First time, I've paste the text from Windows in Linux (virtual machine), on next attempt, I've copied the file from Windows host in virtual machine with Linux; your  last command made the file compatible with Linux.

This one will create separate archives for every folder located in:
/home/merlin/Archives
(will add to archives all content recursively and archives will have the same name as subfolders, followed by '-Archives' string):
```
#!/bin/bash

arch="/home/merlin/Archives"

find "${arch}" -mindepth 1 -maxdepth 1 -type d | while read dir
do
  dname="${dir##*/}"
  cd "${dir}"
  rar a -m0 -r -v1g "${dname}-Archives.rar"
  mv *.rar "${arch}"
  rm -rf "${arch}/${dname}"
done
```I've copied the above code in a file called createrars.sh placed in: /home/merlin/Archives
Then, I've run the next commands logged as root user, from the terminal (one by one):
```
# sed -ri 's/\s*$//' /home/merlin/Archives/createrars.sh
# chmod +x /home/merlin/Archives/createrars.sh
# /home/merlin/Archives/createrars.sh
```

---

