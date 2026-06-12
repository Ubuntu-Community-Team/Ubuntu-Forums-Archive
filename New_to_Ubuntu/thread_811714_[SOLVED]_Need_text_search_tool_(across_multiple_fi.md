---
title: "[SOLVED] Need text search tool (across multiple files)"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by swarup on 2008-05-29
I need a tool that will search for text (i.e. one word) in the text of multiple files and folders. The "Search for Files" tool under "Places" doesn't seem to do it. If in that tool I leave the file name blank, open "Select more options" -> "Contains the text", and type in a word there, it doesn't find any files. 

I am using Ubuntu Hardy 8.04

---

### Post by FuturePilot on 2008-05-29
Have you tried Tracker?

---

### Post by Inxsible on 2008-05-29
You are probably looking for a mix of the find command and the grep command. In a terminal type in```
man find
``` to get more info on it and its usage.

---

### Post by tacutu on 2008-05-29
```
grep "something" *.txt
```
to search for "something" in all files which have the txt extension.

---

### Post by Monicker on 2008-05-29
> **tacutu said:**
> ```
grep "something" *.txt
```
to search for "something" in all files which have the txt extension.

```
grep -R "something" /dir
```

For a recursive search in subdirectories also.

---

### Post by swarup on 2008-05-29
I will be searching OOo Writer files (.odt). And the search tool has to be able to accept Indian Language fonts through the SCIM/m17n keymap system. For example, if I type " &#2343;&#2352;&#2381;&#2350; " then I want to be able to find out which among the 50 OOo Writer Hindi files I have, contains this word.

---

### Post by swarup on 2008-05-29
I've been experimenting with the various options listed above. 

Tracker allowed me to type in Hindi in the search window, but when I clicked on search, it said it did not find anything. So basically, it didn't work.

To my surprise, the Terminal window does allow me to type in Hindi in it. When I type

```
grep " &#2346;&#2369;&#2352;&#2369;&#2359; " *.odt
```

though, nothing happens.

And when I type

```
swarup@swarup-laptop:~$ grep -R " &#2343;&#2352;&#2381;&#2350; " *.odt
grep: invalid option -- 
Usage: grep [OPTION]... PATTERN [FILE]..
```.

I just get the above error. So I guess I haven't really found a workable option yet.

---

### Post by tacutu on 2008-05-29
odt files are not simple text files. they are in fact zip archives, so I guess grepping them won't help. There is a way to make this work, but perhaps tracker is easier than this:
```
for i in *.odt;
do unzip -ca $i | grep -q "&#2343;&#2352;&#2381;&#2350;";
if [ $? -eq 0 ];
then echo "string found in $i";
fi;
done
```

(assuming you have all the odf files in the same directory)

---

### Post by swarup on 2008-05-29
> **tacutu said:**
> odt files are not simple text files. they are in fact zip archives, so I guess grepping them won't help. There is a way to make this work, but perhaps tracker is easier than this:
```
for i in *.odt;
do unzip -ca $i | grep -q "&#2343;&#2352;&#2381;&#2350;";
if [ $? -eq 0 ];
then echo "string found in $i";
fi;
done
```

(assuming you have all the odf files in the same directory)

Oops! Yes, you're right-- these are not "text" files I'm dealing with, but .odt files. I guess I (albeit unknowingly) misled everyone with the title to this thread.

All the files I want to search are in this directory: 

/home/swarup/Hindi Files

Will the above which you've given, do the job? Or do I need to specify somewhere in those commands, the path to the directory I've given here?

And you mentioned that Tracker would be easier to use. --How is Tracker used for this work? I opened tracker, but it did not seem to offer a window for specifying which folder I want to search, and more importantly when I typed in the word of interest and clicked on "search", it didn't do anything.

---

### Post by tacutu on 2008-05-29
well, I&#12288;don't use tracker so I don't really know what I'm saying, but is indexing enabled? tracker needs to build a database first and only then you can use it...
anyway, you can type the above code in a terminal after:
```
cd /home/swarup/Hindi\ Files
```
or you can change the first line into:
```
for i in /home/swarup/Hindi\ Files/*.odt;
```

any of these should work. Are all the files in one folder or do you also have subfolders in Hindi Files? Because in the latter case, files in subfolders won't be found. You'd have to use find, probably.

---

### Post by tacutu on 2008-05-29
also, you'd better replace $i by "$i" if you have blanks in your filenames

---

### Post by swarup on 2008-05-29
> **tacutu said:**
> well, I&#12288;don't use tracker so I don't really know what I'm saying, but is indexing enabled? tracker needs to build a database first and only then you can use it...

Well, then this is an crtical point. When I open tracker, there are no options at all is just completely bare. I don't know how or where one would build the database. Is there perhaps something further that needs to be downloaded to work with Tracker, so that the database can be built? 

And then, is this going to be one of those tools that always runs in the backround maintaining the database i.e. when new files/email etc comes into the computer?

> **tacutu said:**
> Are all the files in one folder or do you also have subfolders in Hindi Files? Because in the latter case, files in subfolders won't be found. You'd have to use find, probably.

No subfolders. I have around 70 files, all directly located in the folder I mentioned.

---

### Post by swarup on 2008-05-29
tacutu, you are a genius. I did just as you said, and got the output into the terminal window straight off. That was amazing. I had no thought that such a complex series of commands was actually going to work! :)

It really is wonderful. I can use this any time, by just replacing the Hindi word I need into the brackets, and I'll get the output right away.

If I were able to find a GUI that would accomplish this, it would be nice I guess. --One which had a few bells and whistles such as telling how many times the word occurred or even citing the sentence(s) in which it was found. I've seen such text search GUI's in various distros, but they didn't accept Indic font input the way your terminal command did.

Anyhow, what you gave is amazing. Thank you! :)

---

### Post by tacutu on 2008-05-30
glad I could help. :)
THis is the power of Unix and trust me, it can do many more wonderful things. I am not a guru, but other people can do real magic with the command line.

If memory serves right, trackerd options are under System-> preferences->?Searching?
and yes, it would stay loaded in your computer's RAM all the time, but I think it can index Openofice documents and I'm pretty sure it is capable of searching for Hindi phrases.

---

### Post by swarup on 2008-05-30
> **tacutu said:**
> If memory serves right, tracker options are under System-> preferences->?Searching?
and yes, it would stay loaded in your computer's RAM all the time, but I think it can index Openoffice documents and I'm pretty sure it is capable of searching for Hindi phrases.

Thanks for the tip. I tried to set it up so it would only watch one folder inside my home directory in which I keep OOo Writer files all of which are written in Hindi using the Hindi font.

I opened System->Preferences->Search and Indexing, and set the settings as I thought would be proper. First I enabled "indexing" and "watching" by clicking on the respective boxes. --I only want Tracker to index and watch one folder inside my home folder. Aside from that, I don't want it to index or watch anything. So I left "Index mounted directories" checked (I thought if I don't leave that checked, it may not check anything at all), unchecked "index and watch my home directory", and in the browser window for "additional paths to index and watch", I added the pathway to the one folder (inside my /home) which I want to index and watch. I then clicked "apply", and an icon for tracker appeared on my upper panel.

But when I then opened tracker's search window and typed in a hindi word to search, it came back with "no files found". And I know that that word is in several of the files. 

It makes me wonder whether either the above settings I set are incorrect, or whether perhaps it cannot search for Hindi text? One point about this is that in the setup window for "Search and Indexing", there is one option for "Stemming language". I've read a bit about "stemming"-- it is a central tool used by the search utility for carrying out its search, and it is language-dependent. And in the "stemming language" options, several languages are there-- but Hindi is not one of them. Could it be that because Hindi is not one of the offered stemming languages, so Tracker will not be able to search for Hindi text?

---

### Post by mrinvader on 2009-12-20
I dont know if this is gravedigging or not, but I want to do the same thing recursively from $PWD and maybe output the line containing the string. I adapted tacutu's code to allow feeding the query string from command line and added a shell program call at the top:

```
#!/bin/bash
for i in *.odt;
do unzip -ca "$i" | grep -q "$*";
if [ $? -eq 0 ];
then echo "string found in $i";
fi;
done
```



In concept, i'd like correct syntax for 

for i in (the output of find ./ -name "*odt")

I tried

```
for i in "`find . -name "*odt"`"
```

but it didn't work - it took the output as one large value for $i.

I need $i set for each line in the output of `find . -name "*odt"`

I was going to start a new thread but this seemed like the perfect thread with a great solution.

Thanks!

---

### Post by kaibob on 2009-12-20
> **mrinvader said:**
> I dont know if this is gravedigging or not, but I want to do the same thing recursively from $PWD and maybe output the line containing the string....In concept, i'd like correct syntax for 

for i in (the output of find ./ -name "*odt")

I modified your script to use the find command as shown below. Echoing the line that contains the search string is more difficult because ODT files are not text files. Perhaps another forum member will be able to help with this.

```
#!/bin/bash

find . -type f -name "*.odt" | while read i ; do
   [ "$1" ] || { echo "You forgot search string!" ; exit 1 ; }
   unzip -ca "$i" | grep -q "$*"
   if [ $? -eq 0 ] ; then
      echo "string found in $i"
   fi
done
```

---

