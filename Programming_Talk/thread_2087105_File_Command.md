---
title: "File Command???"
date: 2012-11-22
forum: Programming Talk
---

### Post by madinc on 2012-11-22
Is there a way of using the file command in a bash script to organize files based on their mime type?:)

---

### Post by Vaphell on 2012-11-22
it's trivial.
*file -b --mime-type* can be used to extract the mime string.
any specifics?

---

### Post by madinc on 2012-11-22
> **Vaphell said:**
> it's trivial.
*file -b --mime-type* can be used to extract the mime string.
any specifics?
Hi i have many different files with no "dot"extension and i would like to make a script with "file" command to organize them.

---

### Post by madinc on 2012-11-22
> **Vaphell said:**
> it's trivial.
*file -b --mime-type* can be used to extract the mime string.
any specifics?

I have tried like this but with no result.

```
#!/bin/bash
testdir=~/Mad-Projects/madorganizer/test-0

for f in `file -b --mime-type *`
do


    case ${f} in
        text/plain) cp ${f} $testdir;
                 echo "Moved ${f} to $testdir";;
    esac
done
```

Any ideas please??:)

---

### Post by Vaphell on 2012-11-22
assuming no dot in filename
```
#!/bin/bash

src=$HOME/unsorted
dest=$HOME/sorted
while IFS= read -rd $'\0' f
do
  mt=$( file -b --mime-type "$f" )
  **echo** mkdir -p "$dest/${mt#*/}"
  **echo** mv -v "$f" -t "$dest/${mt#*/}"
done < <( find "$src" -iregex '.*/[^.]+' -type f -print0 )
```
i used *find* in case you want to go recursive.
It won't do anything until you remove echos, either way test it before running on true data.

---

### Post by madinc on 2012-11-22
> **Vaphell said:**
> assuming no dot in filename
```
#!/bin/bash

src=$HOME/unsorted
dest=$HOME/sorted
while IFS= read -rd $'\0' f
do
  mt=$( file -b --mime-type "$f" )
  **echo** mkdir -p "$dest/${mt#*/}"
  **echo** mv -vi "$f" -t "$dest/${mt#*/}"
done < <( find "$src" -iregex '.*/[^.]+' -type f -print0 )
```it won't do anything until you remove echos

  Hey Vaphell many thanks for the answer and can it do different files??:confused: can you please explain it better to me i'm a bit newb when it comes to scripts but i love learning it. :)

---

### Post by steeldriver on 2012-11-22
> **madinc said:**
> I have tried like this but with no result.

```
#!/bin/bash
testdir=~/Mad-Projects/madorganizer/test-0

for **[COLOR=Red]f in `file -b --mime-type *`[/COLOR]**
do


    case ${f} in
        text/plain) cp **[COLOR=Red]${f}[/COLOR]** $testdir;
                 echo "Moved **[COLOR=Red]${f}[/COLOR]** to $testdir";;
    esac
done
```Any ideas please??:)

I think something like this would work - except you are mixing up the file and the derived type

```
$ echo "text" > myfile
$ for file in *; do **type=$(file -b --mime-type "$file")**; case **${type}** in "text/plain") echo **"$file"** is plaintext;; esac; done
myfile is plaintext

```

---

### Post by Vaphell on 2012-11-22
**find "$src" -iregex '.*/[^.]+' -type f -print0** generates the list of null-separated file names that lack . after the last / (though i'd modify iregex to '.*/[^.**/**]+' to be sure it matches right files)

**while IFS= read -rd $'\0' f** iterates the list with delimiter set to null (to match null delimiter from find) and puts current file in $f

** mt=$( file -b --mime-type "$f" )** obviously extracts mime string of currently processed file
  **mkdir -p "$dest/${mt#*/}"** tries to create *$dest/2nd_part_of_mime* dir (eg $dest/plain for text/plain)
  **mv -v "$f" -t "$dest/${mt#*/}"** moves the file to $dest/<mime>

---

### Post by madinc on 2012-11-22
> **steeldriver said:**
> I think something like this would work - except you are mixing up the file and the derived type

```
$ echo "text" > myfile
$ for file in *; do **type=$(file -b --mime-type "$file")**; case **${type}** in "text/plain") echo **"$file"** is plaintext;; esac; done
myfile is plaintext

```

:)Thanks steeldriver it works great is it ok to use like this??

```
#!/bin/bash
testdir=~/Mad-Projects/madorganizer/test-0

for file in *; do type=$(file -b --mime-type "$file");

    case ${type} in
        "text/plain") cp $file $testdir;
                      echo "$file" is plaintext;
                      echo "Moved $file to $testdir";;

    esac

done
```

---

### Post by madinc on 2012-11-22
> **Vaphell said:**
> **find "$src" -iregex '.*/[^.]+' -type f -print0** generates the list of null-separated file names that lack . after the last / (though i'd modify iregex to '.*/[^.**/**]+' to be sure it matches right files)

**while IFS= read -rd $'\0' f** iterates the list with delimiter set to null (to match null delimiter from find) and puts current file in $f

** mt=$( file -b --mime-type "$f" )** obviously extracts mime string of currently processed file
  **mkdir -p "$dest/${mt#*/}"** tries to create *$dest/2nd_part_of_mime* dir (eg $dest/plain for text/plain)
  **mv -v "$f" -t "$dest/${mt#*/}"** moves the file to $dest/<mime>

Thanks for explaining Vaphell but steeldriver's option seems more ease to me dziekuje bardzo.:)

---

### Post by steeldriver on 2012-11-22
Hmm OK - Vaphell's solutions for things like this are usually more robust though (I often miss the subtle things that can go wrong...)

---

### Post by madinc on 2012-11-22
> **steeldriver said:**
> Hmm OK - Vaphell's solutions for things like this are usually more robust though (I often miss the subtle things that can go wrong...)
So which option you think is better and why please?

---

### Post by steeldriver on 2012-11-22
Vaphell's solution will likely be safer for filenames with 'special' characters in them and will handle large numbers of matches better (by buffering them through the 'read' function)... possibly some other things as well

I guess it depends a bit what you want to do when you find the files - the 'case... esac' structure gives you a bit more flexibility whereas if you just want to move all files of one type to the appropriate dir find / read / mv should do the job fine

---

### Post by Vaphell on 2012-11-22
depends on your needs
if you want to 'manually sort' (this type->that dir) case would be better
if you want full auto, my code would do that (it creates dest dirs for whatever mimetypes it meets)

usually without knowing exact conditions i try to write the broadest possible code so it can be easily tailored to specific needs.
**while IFS= read -d $'\0' ... < <( find ... -print0 )** looks bulky (and it is) but it is a standard boilerplate code if you have to create a list of files that matches some set of criteria.

It is the most scalable solution of all, functionally it's a superset of standard for loop+globs, it's recursive by default (globs require enabled globstar for that), offers more flexibility in criteria and that null delimiter business means it's completely resistant to troublesome characters like whitespace (globs are resistant too). Null is forbidden by filesystems so it allows for 100% safe file lists (eg newline is legit in filenames so you can't depend on it). I agree that this approach often it is an overkill (like when you don't need recursion and standard globbing is enough) but it will always work and you can't go wrong with suggesting it without knowing specifics.
Simply put if i don't know that *for f in ** will be enough or what kind of weirdo names will be processed, i default to full blown *while read*.

---

### Post by madinc on 2012-11-22
> **steeldriver said:**
> Vaphell's solution will likely be safer for filenames with 'special' characters in them and will handle large numbers of matches better (by buffering them through the 'read' function)... possibly some other things as well

I guess it depends a bit what you want to do when you find the files - the 'case... esac' structure gives you a bit more flexibility whereas if you just want to move all files of one type to the appropriate dir find / read / mv should do the job fine

Well since i already have all the directories for all my files in a harddrive this script will look in my downloads and move all my video, audio, text, images to their respective directories i guess i will try both solutions and see which one works best thank you guys for everything.:)

---

### Post by madinc on 2012-11-22
> **Vaphell said:**
> depends on your needs
if you want to 'manually sort' (this type->that dir) case would be better
if you want full auto, my code would do that (it creates dest dirs for whatever mimetypes it meets)

usually without knowing exact conditions i try to write the broadest possible code so it can be easily tailored to specific needs.
**while IFS= read -d $'\0' ... < <( find ... -print0 )** looks bulky (and it is) but it is a standard boilerplate code if you have to create a list of files that matches some set of criteria.


I think your code is great i'm playing with it right now lol:) i think it will be perfect in my new harddrive, i just one more question will it deal with spaces in file names too???
Thank you very much:)

---

### Post by Vaphell on 2012-11-22
yes, it deals with any legit character you can throw at it (unless i ommitted "" somewhere... always quote your variables to prevent whitespace disasters, unless you are 110% sure no surprise can happen)

---

### Post by madinc on 2012-11-22
> **Vaphell said:**
> yes, it deals with any legit character you can throw at it (unless i ommitted "" somewhere... always quote your variables to prevent whitespace disasters, unless you are 110% sure no surprise can happen)

Thank you very much Vaphell that was really helpful.:)

---

