---
title: "Help With Bash Script In Multiple Directories"
date: 2012-06-27
forum: Programming Talk
---

### Post by jlacroix on 2012-06-27
Hello everyone. I wrote a Bash script that strips specific portions out of XML files. It works. However, it has to be run against over 16,000 XML files. I'm not in a hurry to do that manually. So I'm hoping there's a quick and dirty trick to make it run against the XML files in each subdirectory.

I need to run these commands against the first (and only the first) file in each subdirectory, and not the subsequent files:
```
sed -i '/<Footer>/,/<\/Footer>/d' file.xml
sed -i '/<\/CASE>/d' file.xml
```

I need to run the following commands against all files except for the first in each subdirectory:
```
sed -i '/<?xml version="1.0" encoding="iso-8859-1"?>/d' file.xml
sed -i '/<CASE version="3.0">/d' file.xml
sed -i '/<Header>/,/<\/Header>/d' file.xml
sed -i '/<Footer>/,/<\/Footer>/d' file.xml
sed -i '/<\/CASE>/d' file.xml
```

So to recap, those commands work perfectly fine, but I want to enter each subdirectory, run the first set against only the first file, run the second set against all files other than the first, leave the directory, enter the next directory, and repeat.

If someone can help me with this, they'll be a lifesaver.

---

### Post by Vaphell on 2012-06-27
define 'the first in each directory'

you could try to enable globstar option of shell
shopt -s globstar
it allows for ** symbol which matches subdirs of any depth (including 0)

eg. **/*.txt

**/file.xml would match
file.xml
dir1/file.xml
dir2/file.xml
dir3/dir4/file.xml
so assuming you have a tidy structure with dirX/file.xml you would be able to modify all relevant files with
```
sed -i ... **/file.xml
```

btw, i hope you have your data files backed up, modifying files in place in a potentially destructive manner is not a good idea.


if your script works only with current dir (you haven't mentioned if it accepts any params) you could go with something like this

```
while read -d $'\0' -r d
do
  cd "$d"
  # run script here
  echo run script in "$d"
  # sed directly?
  sed '...' "$d"/file.xml
done < <(find "$PWD" -mindepth 1 -maxdepth 1 -type d -print0)
```
it would be run from the master dir, and iterate over its direct children (depth 1)

---

### Post by jlacroix on 2012-06-27
> **Vaphell said:**
> define 'the first in each directory'

you could try to enable globstar option of shell
shopt -s globstar
it allows for ** symbol which matches subdirs of any depth (including 0)

eg. **/*.txt

**/file.xml would match
file.xml
dir1/file.xml
dir2/file.xml
dir3/dir4/file.xml

btw, i hope you have your data files backed up, modifying files in place in a potentially destructive manner is not a good idea.
I made a copy of these files so that I can play with them freely without disturbing the originals.

I thought further about this and simplified my needs a bit. I'm no longer concerned with these commands at all in regards to my needing help:
```
sed -i '/<Footer>/,/<\/Footer>/d' file.xml
sed -i '/<\/CASE>/d' file.xml
```
So we can get rid of those.

So now, the first thing I need is to run these commands against all files except the first:
```
sed -i '/<?xml version="1.0" encoding="iso-8859-1"?>/d' file.xml
sed -i '/<CASE version="3.0">/d' file.xml
sed -i '/<Header>/,/<\/Header>/d' file.xml
sed -i '/<Footer>/,/<\/Footer>/d' file.xml
sed -i '/<\/CASE>/d' file.xml
```

Here is what I mean by "the first file." If I do an 'ls' command in a directory, let's say I get the following output (please note that the file names are 100% different in each folder):

A.xml
B.xml
C.xml
D.xml
E.xml

So basically, I want to run those commands against files B, C, D, and E, but not A, because A is the first file in alphabetical order in the directory. So essentially, I'm skipping the first but executing the commands against files that come afterwards.

...After I solve that, I just need to have this cycle through each subdirectory.

I hope that makes more sense. Thanks!

---

### Post by jlacroix on 2012-06-27
Another thing, I noticed I can get a listing of all the files except the first by doing:
```
ls | tail -n +2
```
So now if I can run the command against all the files in that output, that will solve the first portion.

---

### Post by Vaphell on 2012-06-27
```
n=0
while read -d $'\0' f
do
  if (( n==0 ))
  then
    # do stuff here
    echo "$f" is first
  else
    # do stuff here
    echo "$f" is not first
  fi
  (( n++ ))
done < <( find -maxdepth 1 -mindepth 1 -type f -print0 | sort -z )
```

i went find/sort -> while read route with null delimited values because ls should not be used in anything related to the program logic. It's for visual feedback only and there is no guarantee it will handle corner cases correctly (eg newlines in names are allowed and ls would fail horribly on them)


in any case you want to use output of some command to iterate over it, your general approach should be like this
```
while read variable(s); do something with $variable; done < <( cmd1 ... | cmd2 ... | cmd3 ... )
```

---

### Post by jlacroix on 2012-06-27
> **Vaphell said:**
> ```
n=0
while read -d $'\0' f
do
  if (( n==0 ))
  then
    # do stuff here
    echo "$f" is first
  else
    # do stuff here
    echo "$f" is not first
  fi
  (( n++ ))
done < <( find -maxdepth 1 -mindepth 1 -type f -print0 | sort -z )
```

i went find/sort -> while read route with null delimited values because ls should not be used in anything related to the program logic. It's for visual feedback only and there is no guarantee it will handle corner cases correctly (eg newlines in names are allowed and ls would fail horribly on them)


in any case you want to use output of some command to iterate over it, your general approach should be like this
```
while read variable(s); do something with $variable; done < <( cmd1 ... | cmd2 ... | cmd3 ... )
```
Almost there. I hope I am understanding your commands correctly. Here is what I deduced from your example:
```
#!/bin/bash
# init
n=0
while read -d $'\0' f
do
 if (( n==0 ))
	then
		sed -i '/<Footer>/,/<\/Footer>/d' *.xml
		sed -i '/<\/CASE>/d' *.xml
		echo "$f" is first
  else
    		sed -i '/<?xml version="1.0" encoding="iso-8859-1"?>/d' *.xml
		sed -i '/<CASE version="3.0">/d' *.xml
		sed -i '/<Header>/,/<\/Header>/d' *.xml
    		echo "$f" is not first
  fi
  (( n++ ))
done < <( find -maxdepth 1 -mindepth 1 -type f -print0 | sort -z )
```
It almost works. The "echo's" are correct. It declares the corect file is first and the rest are not. However, it is executing all the sed commands regardless of whether or not the file is first.

Secondly, the script will not process sub directories, it ends after the first.

Thanks so much though, I can see immense progress, more than I was able to do on my own. :)

Edit: I see the problem, the "*.xml" is the culprit. Sorry I wasn't sure how to tailor my commands to your example.

---

### Post by Vaphell on 2012-06-27
```
while read -d $'\0' [COLOR="Blue"]f[/COLOR]
```

f here is the variable that is supposed to hold the current file from the list produced by find
just use "$f" instead of *.xml (which expands to 'all files matching .xml')

as for iterating over directories, you need to combine the loop dealing with files with my previous suggestion that dealt with directories

```
while read -r -d $'\0' **dir**         # outer loop for dirs
do
  echo "dir: **$dir**"
  n=0                              # reset file counter
  while read -r -d $'\0' **file**      # inner loop for files
  do
    if (( n==0 ))
    then
      echo "**$file**" is first
      sed -i ... "**$file**"
    else
      echo "**$file**" is not first
      sed -i ... "**$file**"
    fi
    (( n++ ))
  done < <( find "**$dir**" -maxdepth 1 -mindepth 1 -type f -print0 | sort -z )  
done < <( find -maxdepth 1 -mindepth 1 -type d -print0 )
```

---

### Post by jlacroix on 2012-06-27
> **Vaphell said:**
> ```
while read -d $'\0' [COLOR="Blue"]f[/COLOR]
```

f here is the variable that is supposed to hold the current file from the list produced by find
just use "$f" instead of *.xml (which expands to 'all files matching .xml')

as for iterating over directories, you need to combine the loop dealing with files with my previous suggestion that dealt with directories

```
while read -r -d $'\0' **dir**         # outer loop for dirs
do
  echo "dir: **$dir**"
  n=0                              # reset file counter
  while read -r -d $'\0' **file**      # inner loop for files
  do
    if (( n==0 ))
    then
      echo "**$file**" is first
      sed -i ... "**$file**"
    else
      echo "**$file**" is not first
      sed -i ... "**$file**"
    fi
    (( n++ ))
  done < <( find "**$dir**" -maxdepth 1 -mindepth 1 -type f -print0 | sort -z )  
done < <( find -maxdepth 1 -mindepth 1 -type d -print0 )
```
Thank you so much! I can't believe I didn't notice the $f parameter and its relation. I feel silly. I combined your example and my commands and this is what I ended up with:
```
#!/bin/bash
# init

while read -r -d $'\0\' dir 	##Outer loop for directories
do
	echo "dir: $dir"
	n=0 			##Reset file counter
	while read -d $'\0' f 	##Innter loop for files
	do
 		if (( n==0 ))
		then
			sed -i '/<Footer>/,/<\/Footer>/d' $f
			sed -i '/<\/CASE>/d' $f
			echo "$f" is first
  		else
    			sed -i '/<?xml version="1.0" encoding="iso-8859-1"?>/d' $f
			sed -i '/<CASE version="3.0">/d' $f
			sed -i '/<Header>/,/<\/Header>/d' $f
			sed -i '/<Footer>/,/<\/Footer>/d' $f
			sed -i '/<\/ACES>/d' $f
    			echo "$f" is not first
  		fi
  	(( n++ ))
	done < <( find "$dir" -maxdepth 1 -mindepth 1 -type f -print0 | sort -z )  
done < <( find -maxdepth 1 -mindepth 1 -type d -print0 )
```

But the output I get is this:
```
./TEST: line 20: unexpected EOF while looking for matching `''
./TEST line 26: syntax error: unexpected end of file

```
No matter how many times I look at lines 20 and 26 I don't see the problem. It's probably obvious.

---

### Post by ofnuts on 2012-06-27
> **jlacroix said:**
> No matter how many times I look at lines 20 and 26 I don't see the problem. It's probably obvious.
```

while read -r -d $'\0\' dir

```has a dangling apostrophe (the 2nd one is escaped...) so most of the code is a big string literal(*)...


(*) for some value of "string literal" in bash syntax, you pedants :)

---

### Post by jlacroix on 2012-06-27
> **ofnuts said:**
> ```

while read -r -d $'\0\' dir

```has a dangling apostrophe (the 2nd one is escaped...) so most of the code is a big string literal(*)...


(*) for some value of "string literal" in bash syntax, you pedants :)
Good catch! I changed it to:
```
while read -r -d $'\0\'' dir 
```

I'm testing it now. It's going through the folders. Hopefully the output is what I expect.

It works! OMG! You guys are awesome!!!

---

### Post by Vaphell on 2012-06-27
why would you want to escape that ' anyway? its $'' with \0 inside, just like in the inner loop
$ symbol used with single quotes enables interpretation of \-escaped symbols and \0 is null character

```
$ echo 'abc\0'; echo $'abc\0'
abc\0
abc
$ echo 'abc\tde\nf'; echo $'abc\tde\nf'
abc\tde\nf
abc	de
f
```

---

