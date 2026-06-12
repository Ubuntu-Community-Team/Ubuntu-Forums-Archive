---
title: "How to use this Python script?"
date: 2010-10-24
forum: Programming Talk
---

### Post by jannn on 2010-10-24
[http://hughperkins.com/techblog/2010/04/11/converting-cantofish-dictionary-for-stardict/](http://hughperkins.com/techblog/2010/04/11/converting-cantofish-dictionary-for-stardict/)

I would like to create a stardict file from the database of cantofish, which is a firefox plugin that works like a dictionary. I know nothing about programming and I'm also a LInux newbie so I can't follow what the blogger said at all. :( (I understand steps after tabfile is created. I just don't know how to perform the conversion.)

I would like to know how to use this script.

I tried to copy the script to text editor and saved it as .py. I typed the location of that dat file and output location into "cantopath" and "outpath" . Then I right-clicked properties and checked "allow executing file as program". 
But there is no conversion at all. 

Thanks for helping!!

[URL="http://www.sendspace.com/file/pbf5q3"]
[/URL]

---

### Post by benson444 on 2010-10-24
When you say that you typed the location of the files into 'cantopath' and 'outpath', do you mean that you edited the script itself?

You need to execute the script from the command prompt, passing the name of the .dat file and a name to give the converted file as arguments.

Paste the code into a file, save it as, for example, script.py and make it executable. Then put the .dat file into the same directory, which will make the execution command a bit simpler.

Then open a terminal (Applications > Accessories > Terminal), change to the directory that holds the files, e.g.
```
cd cantofish_test
```
and execute the script:
```
./script.py canto.dat outfile_name
```

---

### Post by jannn on 2010-10-24
thx benson444! 
it works!

---

