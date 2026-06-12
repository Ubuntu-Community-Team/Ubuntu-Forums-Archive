---
title: "Please help me understand this code"
date: 2012-11-08
forum: Programming Talk
---

### Post by vasa1 on 2012-11-08
I came across code which performs the same command on **several** files but I don't understand part of it.
```
find . -name "*.svg" -type f -print0 | xargs -0 -I file sh -c 'F="file"; F="${F%.svg}.opt.svg"; /PATH/TO/scour.py --OPTIONS -i "file" -o "$F"'
```
The context is to perform a **scour** on several svg files to reduce their size and was described here in comment #4:[Run scour for a batch of svgs]("https://answers.launchpad.net/ubuntu/+source/scour/+question/148801").

While the code works just fine, I can't understand how part of it (in bold) works:
find . -name "*.svg" -type f -print0 | xargs -0 **-I file sh -c 'F="file"; F="${F%.svg}.opt.svg";** /PATH/TO/scour.py --OPTIONS -i "file" -o "$F"'

So find passes a list of svg files to xargs  but what happens after that isn't clear to me. It appears that each file that is to be "scoured" will be renamed from file1.svg to file1.opt.svg

The command for scouring a **single** file is:
```
/usr/share/pyshared/scour.py --OPTIONS -i input.svg -o output.svg
```

--OPTIONS can be something like "--disable-style-to-xml" or "--remove-metadata" etc.

---

### Post by Vaphell on 2012-11-08
i'd guess it emulates a loop where every file is put in *file* and then 
```
F="*file*"; F="${F%.svg}.opt.svg"; /PATH/TO/scour.py --OPTIONS -i "*file*" -o "$F"
``` is executed as a single command (sh -c ...)

personally i don't see much use of xargs and i find it fugly and convoluted. You can write a tidy loop to do the same.
```
while read -rd $'\0' f
do
  /usr/share/pyshared/scour.py -i "$f" -o "${f%.svg}.opt.svg"
done < <( find -iname '*.svg' -type f -print0 )
```

---

### Post by vasa1 on 2012-11-08
That works as well so I'm marking it SOLVED but now I will scratch my head to understand what the new code is all about :)

---

### Post by ofnuts on 2012-11-08
> **Vaphell said:**
> i'd guess it emulates a loop where every file is put in *file* and then 
```
F="*file*"; F="${F%.svg}.opt.svg"; /PATH/TO/scour.py --OPTIONS -i "*file*" -o "$F"
``` is executed as a single command (sh -c ...)

personally i don't see much use of xargs and i find it fugly and convoluted. You can write a tidy loop to do the same.

Onelineritis is indeed a terrible disease... but xargs lets you call one instance of the command with all the files. If you loop you start one command instance for each file, which is often OK, but there are cases where it won't cut it (sort -u, for instance).

---

### Post by Vaphell on 2012-11-08
new code as in 'while read ...'?

fuel while loop with *find ... -print0* output (\0-delimited files) - same as with that xargs code
*read -rd $'\0' f*, also using \0 as delimiter, takes chunks of that output (individual names) and puts them in f variable - again, similar thing happened in xargs line.
in loop body that gets executed for each value of $f, scour.py is used with that $f.


> xargs lets you call one instance of the command with all the files. If you loop you start one command instance for each file, which is often OK, but there are cases where it won't cut it (sort -u, for instance).

that's true, but *xargs* is mostly used with file names, usually coming from *find* - afaik find supports *-exec ... \+* which does more or less the same? (never tried it)
```
$ ls
in.txt  out.txt  while.sh
$ find . -exec echo {} \;
.
./in.txt
./out.txt
./while.sh
$ find . -exec echo {} \+
. ./in.txt ./out.txt ./while.sh
```
seems to work


I also think it's possible to use pure bash solution to run single command with tons of parameters using array. It won't be a oneliner though, more like 3 ;-)
imho it's much more beneficial to understand how bash works than how to do stuff with obscure commands.

Care to elaborate what's up with *sort -u*?

---

### Post by ofnuts on 2012-11-08
> **Vaphell said:**
> new code as in 'while read ...'?

fuel while loop with *find ... -print0* output (\0-delimited files) - same as with that xargs code
*read -rd $'\0' f*, also using \0 as delimiter, takes chunks of that output (individual names) and puts them in f variable - again, similar thing happened in xargs line.
in loop body that gets executed for each value of $f, scour.py is used with that $f.




that's true, but *xargs* is mostly used with file names, usually coming from *find* - afaik find supports *-exec ... \+* which does more or less the same? (never tried it)
```
$ ls
in.txt  out.txt  while.sh
$ find . -exec echo {} \;
.
./in.txt
./out.txt
./while.sh
$ find . -exec echo {} \+
. ./in.txt ./out.txt ./while.sh
```seems to work


I also think it's possible to use pure bash solution to run single command with tons of parameters using array. It won't be a oneliner though, more like 3 ;-)
imho it's much more beneficial to understand how bash works than how to do stuff with obscure commands.

Care to elaborate what's up with *sort -u*?

Yes there is a difference between "find ... ;" and "find ... +" but it works only with find (and assumes you use the file list directly...). "Mostly" isn't the same as "all" and file names can have other sources (existing file, list of TAR/ZIP contents...).

You are right, the '-u' isn't even necessary. 'sort $files' doesn't create the same output as 'for file in $files; do sort $file;done'

---

### Post by Vaphell on 2012-11-08
in cases where find \+ is not available there are always arrays.
*read -a array <...; sort "${array[@]}"*

*sort $files* is bad as there are non-trivial issues with IFS, *sort "$files"* wont work for obvious reasons.
The biggest fail of all is that most linux tools don't support custom delimiters, especially \0. Try having \n-laden file names and then do something productive with whatever string these tools produce, eg *line1^Jline2* (unzip -l) or *line1?line2* (ls).

---

### Post by nothingspecial on 2012-11-08
> **vaphell said:**
> 
imho it's much more beneficial to understand how bash works than how to do stuff with obscure commands.



+1

---

