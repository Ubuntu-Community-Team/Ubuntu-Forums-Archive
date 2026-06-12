---
title: "the BASIC guide to COMPILING."
date: 2005-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by kakashi on 2005-11-09
hello this my first how-to so bear with me. 
this is for compiling programs. not all programs but many. 
the only restriction i place on the prgrams you can compile is that the program
must  be in the the repositories. 
now you may ask why compile it if its n repositories well 
1. first of all for fun(like me) 
2. to get the latest version (even latest CVS)
3. to include features not compiled into the packages in repositories. 

here's the steps.
better more detailed steps can be sound at [ubuntu guide]("http://www.ubuntuguide.org/")
```

sudo gedit /etc/apt/sources.list

```
here uncomment any deb-src lines. 
then do 
```

sudo apt-get update
[code]

now do 
[code]
sudo apt-get build-dep program-name

```

now you have have installed all the build-dependencies of the pakages.

i am asummin you know the basics of compiling like 
```

./configure
make
make install

```

if you don't then its not too much trouble. 
i'll explain the basics.
./configure basically configure the package according to what it detects to in your computer .
make compiles the program 
and make install copies the compiles thing to the director.

i found this neat trick very important when compiling 
here it is. 
./configure has an option called --prefix 
used like this 
```

./configure  --prefix=DIR

```
where DIR refers to the directory you are installing to. all the files are copied into this diirectory at make install  time. by default it is most of the time in > /use/local/
but if you want to be safe change it to some other directory. i use ```
$HOME/souce_compiled/PROGRAM_NAME
```

this helps by ensuring that if the compiling or installing or current version of program is screwed up than your system won't be affected. 

if you are satisfied with the compiled prgram (hopeufully after checking) the do this 
```

cp -R $HOME/souce_compiled/PROGRAM_NAME/* /usr/
[code]
this will copy the program to the /usr folder where all your programs are stored and where PATH refers to. or you could add $HOME/souce_compiled/ to you PATH ensuring that you can ruin your programs normally and it won't affect your system. 

adding to PATH is still new to me but i found a great site that explains it.[URL="http://www.newlinuxuser.com/howto-add-a-directory-to-my-path-statementvariable/"]
here[/URL]

now you can safetly compile programs (most anyways) and still not worry that your current system will be affected. if you are not happy with a compiation you can simply delete the folder
[code]rm -R  $HOME/souce_compiled/PROGRAM_NAME/
```

---

### Post by kakashi on 2006-01-14
bump

---

### Post by hen3rz on 2006-01-14
This is a great tutorial. Thanks heaps.

---

### Post by kakashi on 2006-02-17
bump

---

