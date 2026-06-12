---
title: "Problem Finding Multiple File Extensions in Bash"
date: 2009-04-24
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-04-24
I found this with a google search:
```

find ./ -regex ".*\(php\|html\|tpl\)$"

```

but when I change it to conform to my filename extensions:
```

$ find ./ -regex ".*\(m3u\nfo\)$"
$

```

I get no output and this is what I have in my current directory:
```

$ ls
[1-5]  chaat  cleaner.sh  emptry  empty1  mastaz.m3u  test.nfo  test.sh  touchy

```

I have also tried this variation:
```

t$ find ./ -type f -name \*.m3u
./mastaz.m3u
./chaat/chutney/brazton.m3u
./chaat/killz.m3u

```

which works, but if I try this:
```

$ find ./ -type f -name "\*.(m3u\nfo\)$"

```

I get no output either. Anything I am doing wrong? Thanks.

---

### Post by Arndt on 2009-04-24
> **StunnerAlpha said:**
> I found this with a google search:
```

find ./ -regex ".*\(php\|html\|tpl\)$"

```

but when I change it to conform to my filename extensions:
```

$ find ./ -regex ".*\(m3u\nfo\)$"
$

```

I get no output and this is what I have in my current directory:
```

$ ls
[1-5]  chaat  cleaner.sh  emptry  empty1  mastaz.m3u  test.nfo  test.sh  touchy

```

I have also tried this variation:
```

t$ find ./ -type f -name \*.m3u
./mastaz.m3u
./chaat/chutney/brazton.m3u
./chaat/killz.m3u

```

which works, but if I try this:
```

$ find ./ -type f -name "\*.(m3u\nfo\)$"

```

I get no output either. Anything I am doing wrong? Thanks.

You have lost the | in \| from the example. It's the \| which means "or" in that formalism.

An alternative is to extend the -name approach:

```
$ find ./ -type f -name \*.m3u -o -name \*.nfo
```

---

### Post by StunnerAlpha on 2009-04-24
> **Arndt said:**
> You have lost the | in \| from the example. It's the \| which means "or" in that formalism.

An alternative is to extend the -name approach:

```
$ find ./ -type f -name \*.m3u -o -name \*.nfo
```
Wow awesome man, thanks. I am really stupid :/ do you recommend the -regex method or the -type f -name method?

---

### Post by Arndt on 2009-04-24
> **StunnerAlpha said:**
> Wow awesome man, thanks. I am really stupid :/ do you recommend the -regex method or the -type f -name method?

It might be the case that -regex isn't available on all Unix platforms; it was new to me actually. The other method is older.

---

### Post by StunnerAlpha on 2009-04-24
> **Arndt said:**
> It might be the case that -regex isn't available on all Unix platforms; it was new to me actually. The other method is older.
I have tried googlin this to no avail, it is similar to my earlier problem, so I will post it in this thread. How do I go about finding all folders that do NOT have files with certain extensions in them? I tried using an exclamation point... but bash didn't recognize that...Thanks in advance!

---

### Post by Arndt on 2009-04-24
> **StunnerAlpha said:**
> I have tried googlin this to no avail, it is similar to my earlier problem, so I will post it in this thread. How do I go about finding all folders that do NOT have files with certain extensions in them? I tried using an exclamation point... but bash didn't recognize that...Thanks in advance!

Something like this perhaps?

```
find . -type d | sh -c 'while read x; do ls $x/*.log >/dev/null 2>&1 || echo $x; done'
```

---

### Post by ghostdog74 on 2009-04-24
> **StunnerAlpha said:**
>  How do I go about finding all folders that do NOT have files with certain extensions in them? I tried using an exclamation point... but bash didn't recognize that...Thanks in advance!
show your code

---

### Post by StunnerAlpha on 2009-04-24
> **ghostdog74 said:**
> show your code
I dont have what I tried anymore.

---

### Post by StunnerAlpha on 2009-04-24
> **Arndt said:**
> Something like this perhaps?

```
find . -type d | sh -c 'while read x; do ls $x/*.log >/dev/null 2>&1 || echo $x; done'
```
Nice it works thank you very much... looks very complex haha. I have been trying to add multiple extensions to it like so(the first output is correct folder anotherone shouldn't shot up, in future iterations folder anotherone and current directory shouldnt show up):
```

$ find . -type d | sh -c 'while read x; do ls $x/*.flac >/dev/null 2>&1 || echo $x; done'
.
./[1-5]
./empty1
./chaat
./chaat/chutney
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
$ find . -type d | sh -c 'while read x; do ls "$x/*.(flac\|mp3\)$" >/dev/null 2>&1 || echo $x; done'
.
./[1-5]
./empty1
./chaat
./chaat/chutney
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
./chaat/filez/brawls/anotherone
$ find . -type d | sh -c 'while read x; do ls $x/*.flac -o $x/*.mp3 >/dev/null 2>&1 || echo $x; done'
.
./[1-5]
./empty1
./chaat
./chaat/chutney
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
./chaat/filez/brawls/anotherone

```

Yeah... so what have I been doing wrong? I tried subsituting what I did for finding multiple file extensions and that didn't work... Sorry for being such a noob. :(

---

### Post by Arndt on 2009-04-24
> **StunnerAlpha said:**
> Nice it works thank you very much... looks very complex haha. I have been trying to add multiple extensions to it like so(the first output is correct folder anotherone shouldn't shot up, in future iterations folder anotherone and current directory shouldnt show up):
```

$ find . -type d | sh -c 'while read x; do ls $x/*.flac >/dev/null 2>&1 || echo $x; done'
.
./[1-5]
./empty1
./chaat
./chaat/chutney
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
$ find . -type d | sh -c 'while read x; do ls "$x/*.(flac\|mp3\)$" >/dev/null 2>&1 || echo $x; done'
.
./[1-5]
./empty1
./chaat
./chaat/chutney
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
./chaat/filez/brawls/anotherone
$ find . -type d | sh -c 'while read x; do ls $x/*.flac -o $x/*.mp3 >/dev/null 2>&1 || echo $x; done'
.
./[1-5]
./empty1
./chaat
./chaat/chutney
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
./chaat/filez/brawls/anotherone

```

Yeah... so what have I been doing wrong? I tried subsituting what I did for finding multiple file extensions and that didn't work... Sorry for being such a noob. :(

The "ls" there is the ordinary 'ls' command; just list the arguments one after the other: ls $x/*.x $x/*.y.

If this is going to become a halfway serious script, make a shell script of it all (if you don't write it in Perl or Python), where you can spread out things and make them more readable. You may want to write the second half in Python, which often is very easy to read, but sort of impossible to do one-liners with.

---

### Post by unutbu on 2009-04-24
Save as ~/bin/dirs_without.py

[PHP]
#!/usr/bin/env python
import os
import sys
path=sys.argv[1]
suffixes=sys.argv[2:]
for root, dirs, files in os.walk(path,topdown=False):
    for filename in files:
        if os.path.splitext(filename)[1] in suffixes:
            break
    else:
        print root
[/PHP]

Make executable:```

chmod 755 ~/bin/dirs_without.py
```

Run like this:```


dirs_without.py /path/to/dir .mp3 .flac
```

---

### Post by ghostdog74 on 2009-04-24
Perl.
```

use File::Find;
use File::Basename;
my %all;
my %seen;
sub wanted {
     $name = $File::Find::name;     
     $dirname = dirname($name);
     $all{$dirname}++ ;
     if ( basename($name) =~ /\.log/){ $seen{$dirname}++;}
 }
File::Find::find({wanted => \&wanted}, '/path');
foreach my $k (keys %seen){  delete $all{$k}; }
foreach my $k (keys %all){  print "directory with no .log file: $k\n"; }

```

with find /awk
```

find /path -printf "%h:%f\n"  |awk -F":" '{all[$1]++}
 $2 ~ /\.log$/ { seen[$1]++ }
 END{  
  for(i in seen){ delete all[i] }
  for (i in all){ print "dir: "i }  
 }'


```

---

### Post by StunnerAlpha on 2009-04-24
> **Arndt said:**
> The "ls" there is the ordinary 'ls' command; just list the arguments one after the other: ls $x/*.x $x/*.y.

If this is going to become a halfway serious script, make a shell script of it all (if you don't write it in Perl or Python), where you can spread out things and make them more readable. You may want to write the second half in Python, which often is very easy to read, but sort of impossible to do one-liners with.
Arndt if I do what you say by adding the other filename extensions like so: ls $x/*.x $x/*.y the script end up anding them rather than oring, which is what I needed, nevertheless thank you very much for that script.

Unutbu thanks for the code as well, but I want to do this excercise in bash rather than phython(or was it PHP???). Really appreciate the code, will come back to it another time.

Yeah ghostdog you hit the nail on the head, that bash script with awk was perfect thanks a lot for it. Here is what I converted it to to fit my needs:
```

#!/bin/bash

find . -printf "%h:%f\n"  |awk -F":" '{all[$1]++}
	$2 ~ /\.mp3$/ { seen[$1]++ }
	$2 ~ /\.wma$/ { seen[$1]++ }
	$2 ~ /\.m4p$/ { seen[$1]++ }
	$2 ~ /\.m4a$/ { seen[$1]++ }
	$2 ~ /\.wav$/ { seen[$1]++ }
	$2 ~ /\.flac$/ { seen[$1]++ }
	$2 ~ /\.ogg$/ { seen[$1]++ }
 END{  
  for(i in seen){ delete all[i] }
  for (i in all){ print i }  
 }'

```

Thanks again for all the help fellas! :)

---

### Post by ghostdog74 on 2009-04-24
> **StunnerAlpha said:**
> 

find . -printf "%h:%f\n"  |awk -F":" '{all[$1]++}
	$2 ~ /\.mp3$/ { seen[$1]++ }
	$2 ~ /\.wma$/ { seen[$1]++ }
	$2 ~ /\.m4p$/ { seen[$1]++ }
	$2 ~ /\.m4a$/ { seen[$1]++ }
	$2 ~ /\.wav$/ { seen[$1]++ }
	$2 ~ /\.flac$/ { seen[$1]++ }
	$2 ~ /\.ogg$/ { seen[$1]++ }
 ...
[/code]

Thanks again for all the help fellas! :)


```

$2 ~ /\.(mp3|wma|mp4|wav|flac|ogg)$/

```

---

### Post by StunnerAlpha on 2009-04-24
> **ghostdog74 said:**
> ```

$2 ~ /\.(mp3|wma|mp4|wav|flac|ogg)$/

```
Ah! Thanks. Also... I am trying to figure out how to get the script to not display folders that lay in the path of other folders that contain these files. For example:
```

$ find .
.
./test.sh
./megaZORD.sfv
./rule3-2.sh
./emptry
./makill.mp3
./[1-5]
./r
./empty1
./rule3.sh
./touchy
./chaat
./chaat/test.nfo
./chaat/megamix.wma
./chaat/chutney
./chaat/chutney/hellz
./chaat/chutney/brazton.m3u
./chaat/chutney/watermalon
./chaat/filez
./chaat/filez/makillaz
./chaat/filez/makillaz/thedebs.m4a
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz/emptyounces/READMEH
./chaat/filez/makillaz/spiderman
./chaat/filez/makillaz/spiderman/ogre.ogg
./chaat/filez/brawls
./chaat/filez/brawls/anotherone
./chaat/filez/brawls/anotherone/flackcannon.flac
./chaat/filez/brawls/anotherone/m.mp3
./chaat/filez/brawls/anotherone/thewave.wav
./chaat/filez/warsaw.m4p
./chaat/mastaz.m3u
./chaat/killz.m3u
./chaat/heythere
./chaat/nole
./cleaner.sh
./meta.txt
./bombackaz.nfo
$ bash rule3.sh 
./chaat/chutney
./chaat/filez/brawls
./chaat/filez/makillaz/emptyounces

```
The output from rule 3 is technically correct, but the path ./chaat/filez/brawls falls along the path to ./chaat/filez/brawls/anotherone/flackcannon.flac which is not good if I am to delete the output from this script... any ideas? This seems a bit complex and I wonder if it is possible to do it with the code I have taken from ghostdog.

---

### Post by StunnerAlpha on 2009-04-24
> **ghostdog74 said:**
> ```

$2 ~ /\.(mp3|wma|mp4|wav|flac|ogg)$/

```
Yeah I tried this and it didn't work:
```

$ bash rule3.sh 
./chaat/chutney
./chaat/filez/makillaz/spiderman
./chaat/filez/brawls
./chaat/filez
./chaat
.
./chaat/filez/makillaz/emptyounces
./chaat/filez/makillaz
./chaat/filez/brawls/anotherone

```
Which is wrong compared to what I had earlier I even tried altering what you gave me to:
```

$2 ~ /\.(mp3\|wma\|m4p\|m4a\|wav\|flac\|ogg)$/

```
...and that didn't work either. :/ Thanks!

---

### Post by ghostdog74 on 2009-04-24
then have you tried the Python one?

---

### Post by unutbu on 2009-04-24
Did you try```


$2 ~ /\.(mp3|wma|mp4|wav|flac|ogg)$/** { seen[$1]++ }**
```

---

### Post by StunnerAlpha on 2009-04-24
Doh! Yeah now I did and it works, thanks.

The python one gives me this:
```

$ python rule3py.py 
Traceback (most recent call last):
  File "rule3py.py", line 4, in <module>
    path=sys.argv[1]
IndexError: list index out of range

```

And besides I have a fat bash script that I am making this for, I would like to do this in bash if it is not too much trouble.

---

### Post by Arndt on 2009-04-25
> **StunnerAlpha said:**
> Doh! Yeah now I did and it works, thanks.

The python one gives me this:
```

$ python rule3py.py 
Traceback (most recent call last):
  File "rule3py.py", line 4, in <module>
    path=sys.argv[1]
IndexError: list index out of range

```

And besides I have a fat bash script that I am making this for, I would like to do this in bash if it is not too much trouble.

Did you call the python script the way it was suggested? It needs at least one argument: where to start looking.

```
dirs_without.py /path/to/dir .mp3 .flac
```

---

### Post by StunnerAlpha on 2009-04-25
> **Arndt said:**
> Did you call the python script the way it was suggested? It needs at least one argument: where to start looking.

```
dirs_without.py /path/to/dir .mp3 .flac
```
Thanks but when I do this:
```

$ python rule3py.py .mp3 .wav .flac .ogg
$

```
It gives me absolutely no output, is there something I am missing again? Thanks.

---

### Post by unutbu on 2009-04-25
Try:
```
python rule3py.py . .mp3 .wav .flac .ogg

```
The first period after rule3py.py tells the program to search through the current directory.

---

### Post by StunnerAlpha on 2009-04-25
Ah ok, yeah so it worked... here is the output:
```

$ python rule3py.py . .mp3 .wav .flac .ogg .m4p .m4a .wma
./[1-5]
./empty1
./chaat/chutney
./chaat/filez/makillaz/emptyounces
./chaat/filez/brawls

```
Seems to work better than my other script in that it gets the immediate folders without music files as well. Here is the other script and my directories:
```

$ bash rule3.sh ./chaat/chutney
./chaat/filez/brawls
./chaat/filez/makillaz/emptyounces
$ ls -al
total 52
drwxr-xr-x 5 aaron aaron 4096 2009-04-25 15:46 .
drwxr-xr-x 5 aaron aaron 4096 2009-04-25 04:45 ..
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:55 [1-5]
-rw-r--r-- 1 aaron aaron    0 2009-04-23 22:27 bombackaz.nfo
drwxr-xr-x 4 aaron aaron 4096 2009-04-23 23:38 chaat
-rw-r--r-- 1 aaron aaron 3084 2009-04-25 05:04 cleaner.sh
-rw-r--r-- 1 aaron aaron    0 2009-04-21 19:59 emptry
drwxr-xr-x 2 aaron aaron 4096 2009-04-23 20:24 empty1
-rw-r--r-- 1 aaron aaron    0 2009-04-23 23:37 makill.mp3
-rw-r--r-- 1 aaron aaron    0 2009-04-23 22:27 megaZORD.sfv
-rw-r--r-- 1 aaron aaron    0 2009-04-23 22:27 meta.txt
-rw-r--r-- 1 aaron aaron  304 2009-04-24 00:55 r
-rw-r--r-- 1 aaron aaron  680 2009-04-24 19:17 rule3-2.sh
-rw-r--r-- 1 aaron aaron  264 2009-04-24 20:25 rule3py.py
-rw-r--r-- 1 aaron aaron  264 2009-04-24 20:27 rule3py.sh
-rw-r--r-- 1 aaron aaron  196 2009-04-24 20:23 rule3.sh
-rw-r--r-- 1 aaron aaron   83 2009-04-21 20:40 test.sh
-rw-r--r-- 1 aaron aaron   13 2009-04-21 19:46 touchy
aaron@T60:~/Documents/Programming/BashProjects/test$ ls -Rl
.:
total 44
drwxr-xr-x 2 aaron aaron 4096 2009-04-21 01:55 [1-5]
-rw-r--r-- 1 aaron aaron    0 2009-04-23 22:27 bombackaz.nfo
drwxr-xr-x 4 aaron aaron 4096 2009-04-23 23:38 chaat
-rw-r--r-- 1 aaron aaron 3084 2009-04-25 05:04 cleaner.sh
-rw-r--r-- 1 aaron aaron    0 2009-04-21 19:59 emptry
drwxr-xr-x 2 aaron aaron 4096 2009-04-23 20:24 empty1
-rw-r--r-- 1 aaron aaron    0 2009-04-23 23:37 makill.mp3
-rw-r--r-- 1 aaron aaron    0 2009-04-23 22:27 megaZORD.sfv
-rw-r--r-- 1 aaron aaron    0 2009-04-23 22:27 meta.txt
-rw-r--r-- 1 aaron aaron  304 2009-04-24 00:55 r
-rw-r--r-- 1 aaron aaron  680 2009-04-24 19:17 rule3-2.sh
-rw-r--r-- 1 aaron aaron  264 2009-04-24 20:25 rule3py.py
-rw-r--r-- 1 aaron aaron  264 2009-04-24 20:27 rule3py.sh
-rw-r--r-- 1 aaron aaron  196 2009-04-24 20:23 rule3.sh
-rw-r--r-- 1 aaron aaron   83 2009-04-21 20:40 test.sh
-rw-r--r-- 1 aaron aaron   13 2009-04-21 19:46 touchy

./[1-5]:
total 0

./chaat:
total 12
drwxr-xr-x 2 aaron aaron 4096 2009-04-23 20:35 chutney
drwxr-xr-x 4 aaron aaron 4096 2009-04-23 23:40 filez
-rw-r--r-- 1 aaron aaron   10 2009-04-21 19:46 heythere
-rw-r--r-- 1 aaron aaron    0 2009-04-23 20:34 killz.m3u
-rw-r--r-- 1 aaron aaron    0 2009-04-23 20:23 mastaz.m3u
-rw-r--r-- 1 aaron aaron    0 2009-04-23 23:38 megamix.wma
-rw-r--r-- 1 aaron aaron    0 2009-04-21 01:56 nole
-rw-r--r-- 1 aaron aaron    0 2009-04-23 20:37 test.nfo

./chaat/chutney:
total 4
-rw-r--r-- 1 aaron aaron  0 2009-04-23 20:35 brazton.m3u
-rw-r--r-- 1 aaron aaron 14 2009-04-21 19:47 hellz
-rw-r--r-- 1 aaron aaron  0 2009-04-21 19:48 watermalon

./chaat/filez:
total 8
drwxr-xr-x 3 aaron aaron 4096 2009-04-23 23:41 brawls
drwxr-xr-x 4 aaron aaron 4096 2009-04-23 23:41 makillaz
-rw-r--r-- 1 aaron aaron    0 2009-04-23 23:38 warsaw.m4p

./chaat/filez/brawls:
total 4
drwxr-xr-x 2 aaron aaron 4096 2009-04-24 18:17 anotherone

./chaat/filez/brawls/anotherone:
total 0
-rw-r--r-- 1 aaron aaron 0 2009-04-23 23:40 flackcannon.flac
-rw-r--r-- 1 aaron aaron 0 2009-04-24 18:17 m.mp3
-rw-r--r-- 1 aaron aaron 0 2009-04-23 23:40 thewave.wav

./chaat/filez/makillaz:
total 8
drwxr-xr-x 2 aaron aaron 4096 2009-04-23 23:39 emptyounces
drwxr-xr-x 2 aaron aaron 4096 2009-04-23 23:42 spiderman
-rw-r--r-- 1 aaron aaron    0 2009-04-23 23:39 thedebs.m4a

./chaat/filez/makillaz/emptyounces:
total 0
-rw-r--r-- 1 aaron aaron 0 2009-04-23 23:39 READMEH

./chaat/filez/makillaz/spiderman:
total 0
-rw-r--r-- 1 aaron aaron 0 2009-04-23 23:42 ogre.ogg

./empty1:
total 0

```

However it still wants to delete the folder brawls when the folder anotherone has music files in it that I wish to keep that is in brawls.

---

### Post by unutbu on 2009-04-25
The previous python script reported all directories which did not contain files with certain suffixes in its top level.

The script below will report all directories which do not contain files with certain suffixes in its top level or any of its subdirectories.
[PHP]
#!/usr/bin/env python
import os
import sys

path=sys.argv[1]
suffixes=sys.argv[2:]
junk_dirs=[]
def is_keep(path,suffixes):
    if os.path.isdir(path):
        files=os.listdir(path)
        suf_found=any([is_keep(os.path.join(path,afile),suffixes)
                       for afile in files])
        if not suf_found:
            junk_dirs.append(path)
        return suf_found
    elif os.path.splitext(path)[1] in suffixes:
        return True
    else:
        return False
        
is_keep(path,suffixes)
print('\n'.join(junk_dirs))[/PHP]

As before, make it executable, and then run it like this:
[PHP]
rule3py.py . .mp3 .wav .flac .ogg .m4p .m4a .wma[/PHP]

---

### Post by StunnerAlpha on 2009-04-25
> **unutbu said:**
> The previous python script reported all directories which did not contain files with certain suffixes in its top level.

The script below will report all directories which do not contain files with certain suffixes in its top level or any of its subdirectories.
[PHP]
#!/usr/bin/env python
import os
import sys

path=sys.argv[1]
suffixes=sys.argv[2:]
junk_dirs=[]
def is_keep(path,suffixes):
    if os.path.isdir(path):
        files=os.listdir(path)
        suf_found=any([is_keep(os.path.join(path,afile),suffixes)
                       for afile in files])
        if not suf_found:
            junk_dirs.append(path)
        return suf_found
    elif os.path.splitext(path)[1] in suffixes:
        return True
    else:
        return False
        
is_keep(path,suffixes)
print('\n'.join(junk_dirs))[/PHP]

As before, make it executable, and then run it like this:
[PHP]
rule3py.py . .mp3 .wav .flac .ogg .m4p .m4a .wma[/PHP]

Hmm... I am still getting the same output:
```

$ python rule3py.py . .mp3 .wav .flac .ogg .m4p .m4a .wma  
./[1-5]
./empty1
./chaat/chutney
./chaat/filez/makillaz/emptyounces
./chaat/filez/brawls

```

---

### Post by unutbu on 2009-04-25
Check that the rule3py.py has been updated. I've run the script against a mockup of your directory structure. It works for me.

---

### Post by StunnerAlpha on 2009-04-26
> **unutbu said:**
> Check that the rule3py.py has been updated. I've run the script against a mockup of your directory structure. It works for me.
Yeah you are right... it didn't save correctly for some reason... thanks. Now if I wanted to do that in bash I can just put the line:
```

python rule3py.py . .mp3 .wav .flac .ogg .m4p .m4a .wma

```
in my bash script and make sure I have both the bash script and the pyton script in the same directory and it will run just fine? I know I can also make them executables and place them in the /bin folder to have them accessable from anywhere.

Edit: Oh and if I wanted to code this up in bash, would it be possible? I know it would most likely be very tedious. Thanks.

---

