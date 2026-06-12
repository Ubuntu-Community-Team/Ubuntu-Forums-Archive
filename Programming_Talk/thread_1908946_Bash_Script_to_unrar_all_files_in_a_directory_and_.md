---
title: "Bash Script to unrar all files in a directory and sub directories"
date: 2012-01-14
forum: Programming Talk
---

### Post by thedemon13666 on 2012-01-14
Hi

As the title suggests I am interested in writing a 'simple' bash script to unrar all files in a directory and subdirectories.

My problem is that I am very very new to bash (I have only written a one line script).

I am by no means asking you to write this for me however I would greatly appreciate any pointers in the right direction.

I realise how vague a question I am asking but any help is appreciated.

Thanks

---

### Post by WasMeHere on 2012-01-14
Hi

The program ***unrar*** can do the job. If you don't have it, install by ```
sudo apt-get install unrar
```
Read the manual for details ```
man unrar
```

```
unrar <command> [-<switch 1> -<switch N>] archive [files...] [path...]
```
As you can see in the manual, the option -r recurses subdirectories.

Have fun finding out :-)
Olle

---

### Post by thedemon13666 on 2012-01-14
I had already gotten unrar as I figured my bash script would probably have to use it.  Does it work when each rarred file has a different filename?

---

### Post by WasMeHere on 2012-01-14
You don't have to specify the names of all the rarred files, only the name(s) of the archive(s). And you can test if it works with wild cards *.rar for the archive name. If it works you can easily manage with a simple command line

Otherwise you might search for the rar archive files with ***find*** and let it execute an unrar command for each archive.

```
man find
```
Example: since you want to do some thinking yourself ;-)
```
find . -name "*.rar" -exec echo {} \;
```

---

### Post by thedemon13666 on 2012-01-14
Sorry to be an idiot but I am suprised by the potential of unrar all on its own, so I would just like to clarify....


Say I have a Directory containing two folders A and B.  Within A there is A.001 A.002 etc, same for B, but also within folder B there is another folder C which contains C.001 C.002 etc

With a one line command using unrar I can make it extract A.rar, B.rar and C.rar, is this correct?

---

### Post by WasMeHere on 2012-01-14
> **thedemon13666 said:**
> Sorry to be an idiot but I am suprised by the potential of unrar all on its own, so I would just like to clarify....


Say I have a Directory containing two folders A and B.  Within A there is A.001 A.002 etc, same for B, but also within folder B there is another folder C which contains C.001 C.002 etc

With a one line command using unrar I can make it extract A.rar, B.rar and C.rar, is this correct?

What do you mean by folder? Do you mean a (sub)directory or a rar archive?

---

### Post by thedemon13666 on 2012-01-14
Sorry did not mean to be ambiguous, I meant (sub)directory except for the files *.001 etc

---

### Post by WasMeHere on 2012-01-14
If you have some rar files and 00x files (like you described) it might be
a.rar
a.001
a.002
...
meaning that it is one rar archive split into several files (a.rar).

You must dare to try and see what happens. If you are afraid to destroy something, backup your system (or some critical files) before you start. Trial and error is often the best way to learn.

Go to the top directory of your rar archives, when you dare to write files (the extracted files) there.

Try with ```
unrar e -r *.rar 
```

---

### Post by thedemon13666 on 2012-01-14
Lol I understand the split files part, I was just using them as an example, guess ti would have been easier to just say split rar though,

Last question,

what does the 'e' do in the above code line you posted...

---

### Post by thedemon13666 on 2012-01-14
Ah never mind I see it is just extracting them all to the current directory I am in, I actually dont want that, I would rather they were extracted in the directory that they are originally located in,

would 'x' work rather than 'e'?

the manual says that x extracts files with full path...

---

### Post by WasMeHere on 2012-01-14
Yes, indeed :-)

But do you really want that? It might mean overwriting files all over the file system. Of course you can check that with the list command (lowercase L) **l** before you really extract them.

You can also add 'path_to_extract' as the last parameter of the command line according to the help info by running unrar without parameters
```
unrar
```

---

### Post by thedemon13666 on 2012-01-14
ok I tried unrar with x and it placed them in the directory I was currently in which I don't want, I also tried it with e and it also placed them all in the directory I was currently in.....

---

### Post by WasMeHere on 2012-01-14
Strange, that is not according to the manual. Do you know that there should be other paths? Are those paths available and do you have write access to them? Do you use some option or parameter, that might over-ride the x-path-option?

Anyway, you get your files from the archives. Does it also recurse into subdirectories?

---

### Post by thedemon13666 on 2012-01-14
Yes it does everything I want it to (including subdirectories) except for extracting them in the directory the rars reside in...

---

### Post by WasMeHere on 2012-01-14
> **thedemon13666 said:**
> Yes it does everything I want it to (including subdirectories) except for extracting them in the directory the [COLOR="Red"]rars reside[/COLOR] in...

Well, actually that is not the idea. Instead, the files are supposed to be extracted to the original directories, from where they were archived. And that information must be saved during archiving. So if that is not the case, you will get what happens now. What if you run ```
unrar v -r *.rar
```
Are there any paths printed, or only the file names?

---

### Post by thedemon13666 on 2012-01-14
The only path printed is the one from where I am executing the unrar command to where the rar file is.  I think the problem may be that the file path has white space in it, however I have started to sort this problem by writing a script which actually does the job

```


#!/bin/bash  
#newpart 
SAVEIFS=$IFS 
IFS=$(echo -en "\n\b")  

#old part 
for i in $(find $(pwd) -name '*.rar')  
do 
cd $(dirname $i) 
unrar e $i 
done  

#new part again 
IFS=$SAVEIFS

```

I have, however, ran into another problem, I have found that one of the directories has split rar files within it, this is not normally a problem, however each split file ends in .rar, which means that the same file gets extracted ~15 times with the above script, is there anyway to avoid that?

EDIT I have avoided the above problem by adding to the find criteria, ie

```
find -name '*.r01' -o -name '*01.rar'
```Inst a particularly glamorous way around the problem and I believe I will need to add more to it as well, I have also modified the script slightly to allow the input of unrar switches change the unrar line to

```
 unrar $1 e $i 
```Then just add the switches as you normally would, ie -y,

---

### Post by WasMeHere on 2012-01-14
> **thedemon13666 said:**
> The only path printed is the one from where I am executing the unrar command to where the rar file is.  I think the problem may be that the file path has white space in it, however I have started to sort this problem by writing a script which actually does the job

```


#!/bin/bash  #newpart SAVEIFS=$IFS IFS=$(echo -en "\n\b")  #old part for i in $(find $(pwd) -name '*.rar')  do cd $(dirname $i) unrar e $i done  #new part again IFS=$SAVEIFS

```

I have, however, ran into another problem, I have found that one of the directories has split rar files within it, this is not normally a problem, however each split file ends in .rar, which means that the same file gets extracted ~15 times with the above script, is there anyway to avoid that?

Then you must identify how to tell the difference between the start file and the continuation files and select only the start files. Since only you know the file names, you must find out yourself how to do it. Or post the file naming convention if you want help.

---

### Post by thedemon13666 on 2012-01-14
I think the simplest solution for me is the one I posted above, if it turns out that I have insufficient find parameters at a later date they can be altered to resolve a new problem, at least I think....

---

