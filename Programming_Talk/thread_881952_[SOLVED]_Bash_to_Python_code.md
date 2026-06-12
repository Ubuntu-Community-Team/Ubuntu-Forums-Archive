---
title: "[SOLVED] Bash to Python code"
date: 2008-08-06
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2008-08-06
Please if someone can guide me to Python's re.
     
Can this BASH code:

```
ls some_path | sed -ne's/.*\(-[0-9]\+\..*\)/\
```

be converted into Pythons one using re module or similar ?

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> Please if someone can guide me to Python's re.
     
Can this BASH code:

```
ls some_path | sed -ne's/.*\(-[0-9]\+\..*\)/\
```

be converted into Pythons one using re module or similar ?

There is an ' missing at the end to enclose the regular expression.
What are you trying to do exactly, replace negative floating point number by something else? Or maybe removing any character in infront of a negative floating point?

Did you try the sub(pattern, repl, string[, count]) function in the re module?
Documentation: [http://docs.python.org/lib/node46.html](http://docs.python.org/lib/node46.html)

---

### Post by DamjanDimitrioski on 2008-08-06
I'm doing this>
```

ls /media/Storage/pkgs/PKGs/pkg/ |sed -ne's/.*\(-[0-9]\+\..*\)/\1/p'

```

it output's me>
-2.22.1-1-i686.pkg.tar.gz
for each package.

Sorry about earlier I was ;) hungry, I ate couple a letters in the code.

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> I'm doing this>
```

ls /media/Storage/pkgs/PKGs/pkg/ |sed -ne's/.*\(-[0-9]\+\..*\)/\1/p'

```

it output's me>
-2.22.1-1-i686.pkg.tar.gz
for each package.

Sorry about earlier I was ;) hungry, I ate couple a letters in the code.

Bon apetit ;).
I'm not such a big regular expression hacker, so I usally don't use them if its not necessary to think about them.

So the ugly hack way if you just want to wrap the shell script:
[http://docs.python.org/lib/module-commands.html](http://docs.python.org/lib/module-commands.html)
example:
[PHP]
import commands

# use r prefix to string to define it as 'raw'
# so that python doesn't escape stuff (backslashes remain backslashes)
cmd = r"ls /media/Storage/pkgs/PKGs/pkg/ |sed -ne's/.*\(-[0-9]\+\..*\)/\1/p'"

# use a shell
results = commands.getoutput(cmd).split()

# list of file names
print results
[/PHP]

Ugly, ugly, but maybe for you now sufficient and quick.
Better option
[http://docs.python.org/lib/module-glob.html](http://docs.python.org/lib/module-glob.html)
example:

[PHP]
import glob
import os

# glob works as ls command
# of course, you could here also use *.pkg.tar.gz
fullpaths = glob.glob('media/Storage/pkgs/PKGs/pkg/*')

# only keep basenames (strip containing dir)
paths = [os.path.basename(p) for p in fullpaths]

print paths
[/PHP]

So, unless you have other sorts of files in that dir that you don't want to put in a list, there is no need for regular expressions.
Otherwise, to continue the code above:

[PHP]
import re

# create a regular expression object (not necessary for quick matches,
# read the doc., but for now it's clearer code)
fp = re.compile('-[0-9]+\..*') 

# filter the names in the list paths by testing if match() returns something

paths = [p for p in paths if fp.match(p)]

print paths
[/PHP]

Hope this helps.

---

### Post by DamjanDimitrioski on 2008-08-06
The last one the regular expression doesn't work, I've tried>
paths = "/media/&#1052;&#1072;&#1075;&#1072;&#1094;&#1080;&#1085;/pkgs/PKGs/pkg/"
paths = "package-it-2.0.0.12-2-i686.pkg.tar.gz"
paths = "/media/&#1052;&#1072;&#1075;&#1072;&#1094;&#1080;&#1085;/pkgs/PKGs/pkg/package-it-2.0.0.12-2-i686.pkg.tar.gz"
each of them gives me []

---

### Post by DamjanDimitrioski on 2008-08-06
By the way, the thing is I have function that gives me a list of files into a list, now I've removed the path for each file in the list.

What I need now is to give me the version of the pkg, the bash version worked, but I like pure Python code.


This is the whole deal>

pkgs = ["firefox-2.0.0.12-2-i686.pkg.tar.gz","firefox-2.0.0.13-1-i686.pkg.tar.gz","firefox-2.0.0.14-1-i686.pkg.tar.gz"]
I Need to get>
-2.0.0.12-2-i686.pkg.tar.gz
-2.0.0.13-1-i686.pkg.tar.gz
-2.0.0.14-1-i686.pkg.tar.gz
I have another function that replaces -i686.pkg.tar.gz and all the dots and other chars and I get just numbers :).

I managed to make earlier some sort splitter, but it had problems with different types of pkg names :'(.

Here it was>
```
pkg = "packageit-2.0.0.12-2-i686.pkg.tar.gz"
pkg1 = "package-it-2.0.0.12-2-i686.pkg.tar.gz"
pkg2 = "pack-age-it-2.0.0.12-2-i686.pkg.tar.gz"

def pkg_it(pkg):
    the = pkg.replace( "-i686.pkg.tar.gz", '' )
    the = the.rpartition("-")
    the = the[0].rpartition("-")
    ver = the[2]
    ver = ver.replace( ".", '' )
    return the[0], ver
        
print pkg_it(pkg)[0], pkg_it(pkg)[1]
print pkg_it(pkg1)[0], pkg_it(pkg1)[1]
print pkg_it(pkg2)[0], pkg_it(pkg2)[1]
```

The problem with it is if the pkg has different name like .pkg.tar.gz or have rc or svn in it's version number and things like that.
When there was clean name I got good results, but whenever was a change I got half version number and sometimes name plus two numbers of the version.

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> The last one the regular expression doesn't work, I've tried>
paths = "/media/&#1052;&#1072;&#1075;&#1072;&#1094;&#1080;&#1085;/pkgs/PKGs/pkg/"
paths = "package-it-2.0.0.12-2-i686.pkg.tar.gz"
paths = "/media/&#1052;&#1072;&#1075;&#1072;&#1094;&#1080;&#1085;/pkgs/PKGs/pkg/package-it-2.0.0.12-2-i686.pkg.tar.gz"
each of them gives me []

No, paths was supposed to be a list of strings, not a single string.
As a single string, you're iterating over characters in the string and testing each single char with the regular expression, which of course results in no matches, thus you end up with an empty list of results.

But now that you give more examples, I see there is a prefix to the filenames too, I hadn't understood that.
In that case you should use search() instead of match(). Again, please look at the documentation of these functions:
[http://docs.python.org/lib/node46.html](http://docs.python.org/lib/node46.html)

Again, the code was meant to be combined with the code above.
So the complete thing would now be
[PHP]

import re
import glob
import os

# glob works as ls command
# of course, you could here also use *.pkg.tar.gz
fullpaths = glob.glob('media/Storage/pkgs/PKGs/pkg/*')

# only keep basenames (strip containing dir)
paths = [os.path.basename(p) for p in fullpaths]

# create a regular expression object (not necessary for quick matches,
# read the doc., but for now it's clearer code)
fp = re.compile('-[0-9]+\..*') 

# filter the names in the list paths by testing if match() returns something

paths = [p for p in paths if fp.search(p)] # <--- USING SEARCH HERE!!!

print paths 

[/PHP]

As a naming convention, I use fullpaths and paths (plurals!) as variable names to denote lists.

Here is a simpler example now we're at it:
[PHP]

import re

paths = [
  "foobar.tar.gz", # not going to match
  "package-it-2.0.0.12-2-i686.pkg.tar.gz", # this will match
  "helloworld-2.0.0.12-2-i686.pkg.tar.gz", # this will match too
  "sdfsgsdfgsgsdfsgsdfg", # no match
]

# create a regular expression object (not necessary for quick matches,
# read the doc., but for now it's clearer code)
fp = re.compile('-[0-9]+\..*') 

# filter the names in the list paths by testing if match() returns something

paths = [p for p in paths if fp.search(p)] # <--- USING SEARCH HERE!!!

print paths 

[/PHP]

---

### Post by DamjanDimitrioski on 2008-08-06
I see only the full list of all the files in the folder, what your code does ?

I need to split the name and the version of each package, like this>
name        version
firefox       2.0.0.2
where with my other functions I'll get>
name        version
firefox        2002

---

### Post by DamjanDimitrioski on 2008-08-06
That's odd, I counted the number of packages and it gave me 1855, but my folder has 1900 packages.

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> By the way, the thing is I have function that gives me a list of files into a list, now I've removed the path for each file in the list.

What I need now is to give me the version of the pkg, the bash version worked, but I like pure Python code.


This is the whole deal>

pkgs = ["firefox-2.0.0.12-2-i686.pkg.tar.gz","firefox-2.0.0.13-1-i686.pkg.tar.gz","firefox-2.0.0.14-1-i686.pkg.tar.gz"]
I Need to get>
-2.0.0.12-2-i686.pkg.tar.gz
-2.0.0.13-1-i686.pkg.tar.gz
-2.0.0.14-1-i686.pkg.tar.gz
I have another function that replaces -i686.pkg.tar.gz and all the dots and other chars and I get just numbers :).

I managed to make earlier some sort splitter, but it had problems with different types of pkg names :'(.

Here it was>
```
pkg = "packageit-2.0.0.12-2-i686.pkg.tar.gz"
pkg1 = "package-it-2.0.0.12-2-i686.pkg.tar.gz"
pkg2 = "pack-age-it-2.0.0.12-2-i686.pkg.tar.gz"

def pkg_it(pkg):
    the = pkg.replace( "-i686.pkg.tar.gz", '' )
    the = the.rpartition("-")
    the = the[0].rpartition("-")
    ver = the[2]
    ver = ver.replace( ".", '' )
    return the[0], ver
        
print pkg_it(pkg)[0], pkg_it(pkg)[1]
print pkg_it(pkg1)[0], pkg_it(pkg1)[1]
print pkg_it(pkg2)[0], pkg_it(pkg2)[1]
```

The problem with it is if the pkg has different name like .pkg.tar.gz or have rc or svn in it's version number and things like that.
When there was clean name I got good results, but whenever was a change I got half version number and sometimes name plus two numbers of the version.

AAAAAAAAAAAAAAAAAhhhh, now i get it :D

[PHP]
import re

pkgs = ["firefox-2.0.0.12-2-i686.pkg.tar.gz","firefox-2.0.0.13-1-i686.pkg.tar.gz","firefox-2.0.0.14-1-i686.pkg.tar.gz"]

# create regex for the version number only
pattern = re.compile('-[0-9]+([\.-][0-9]+)*')

# search the files
matches = [pattern.search(pkg) for pkg in pkgs]

# elements are now either Match objects, or None (again see documentation)
versions = [m.group() for m in matches if m != None]

print versions
# result:
# ['-2.0.0.12-2', '-2.0.0.13-1', '-2.0.0.14-1']

[/PHP]

Is that what you mean?
By the way, if you post code on the forums here, it is better to use the [PHP] tags instead of [CODE] tags because of the syntax highlighting.

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> I see only the full list of all the files in the folder, what your code does ?

I need to split the name and the version of each package, like this>
name        version
firefox       2.0.0.2
where with my other functions I'll get>
name        version
firefox        2002

Ok, ok, last try, with python magic:

[PHP]
import re

pkgs = ["firefox4-2.0.0.12-2-i686.pkg.tar.gz","firefox-2.0.0.13-1-i686.pkg.tar.gz","firefox-2.0.0.14-1-i686.pkg.tar.gz"]

pattern = re.compile('-[0-9]+([\.-][0-9]+)*')

matches = [pattern.search(pkg) for pkg in pkgs]

# pair up matched items with the original string name
# and create a tuple with first part of string upto the match start
# and with the match itself, but removing the first dash '-'
results = [(p[:m.start()], m.group()[1:]) for p, m in zip(pkgs, matches) if m != None]

print results
# results:
# [('firefox4', '2.0.0.12-2'), ('firefox', '2.0.0.13-1'), ('firefox', '2.0.0.14-1')]

[/PHP]

If this isn't it, I give up :p

---

### Post by DamjanDimitrioski on 2008-08-06
Sorry for the highlighting but I read on the button code :D, I thought code.

Thanks for the glob-ing :)

You saved me lots of code.
Observe>
[PHP]
class vchitaj_paketi():
    def __init__(self, baza):        
        self.baza = baza
        self.pravi_lista_dat()
        #print site_paketi
        
    def datoteki(self, papka):
        for path, papki, files in os.walk(papka):
                for ime in files:
                            yield os.path.join(path,ime)

    def pravi_lista_dat(self):
        print "++++++++++++++++++++++++++++++++++++++++++++++"
        print "\t::&#1055;&#1088;&#1072;&#1074;&#1072;&#1084; &#1083;&#1080;&#1089;&#1090;&#1072;::"
        print "&#1055;&#1086;&#1083;&#1077;&#1090;&#1091;&#1074;&#1072;&#1084;&#1077; &#1074;&#1086;: " + self.baza
        baza = self.baza
        for adresa in self.datoteki(self.baza):
            #print adresa
            site_paketi.append(adresa)
            #site_paketi.append(os.path.basename(adresa))
            #print os.path.basename(adresa)
[/PHP]

And I appologize that it's not English I write it as a joke how big was it.

Now about the name of the package, can the name getting thing be made, and could they be joined in a Tuple, like (full_path,name, version).

Actually this is my program plan>

list all files [done]
split each pkg into> name, version
for each pkg by version in a list, i.e all pkg firefox in one sublist of a list
then removing  each version only keeping the latest version
make 3 folders for each group, check each pkg from what group is, 
and call the move [done]
function to move it [done]
delete all left pkg's [done]
make database (nevermind this). [done]

---

### Post by DamjanDimitrioski on 2008-08-06
Wow, thanks it's cool.
But, why I get 1899 pkg's when I have 1900 in the folder :confused:.
I got the number with:
[PHP]print len(results)[/PHP]

---

### Post by catchmeifyoutry on 2008-08-06
see my latest post, adding the orginal path should now be easy.
Assuming that pkgs contains a list of strings of full path names (such as returned by glob), WITH the other code for re, matches etc., just compute the results as

[PHP]
import os # add this too

results = [(p, os.path.basename(p[:m.start()]), m.group()[1:]) for p, m in zip(pkgs, matches) if m != None] 
[/PHP]

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> Wow, thanks it's cool.
But, why I get 1899 pkg's when I have 1900 in the folder :confused:.
I got the number with:
[PHP]print len(results)[/PHP]

dude, i have no idea :p
Think you should debug that yourself ;)
Maybe the regex is not sophisticated enough, it might fail on some crazy package names.

---

### Post by DamjanDimitrioski on 2008-08-06
If your code gives only one error, that's like 99.99% perfect, rather then mine <30 % perfect where I got all the packages but less in good shape :D.

---

### Post by catchmeifyoutry on 2008-08-06
> **DamjanDimitrioski said:**
> If your code gives only one error, that's like 99.99% perfect, rather then mine <30 % perfect where I got all the packages but less in good shape :D.

Ok then, glad I could help.
Here, you may try to add this to the end to find out what's getting skipped now:

[PHP]
# filter the packages that had NO match
failed = [p for p,m in zip(pkgs, matches) if m == None]
print failed
[/PHP]

Good luck with your project!

---

### Post by DamjanDimitrioski on 2008-08-06
Hm, the code 100 % is working, I found a database pkg, which was not a regular pkg, so that's was the error, thanks again,

see ya :).

---

