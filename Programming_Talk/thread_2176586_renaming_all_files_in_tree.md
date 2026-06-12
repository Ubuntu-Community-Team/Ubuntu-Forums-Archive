---
title: "renaming all files in tree"
date: 2013-09-25
forum: Programming Talk
---

### Post by squakie on 2013-09-25
Please excuse an extremely stupid question:

I have a series of files in a series of folders under folder "famhist".  In Windows of course things weren't case sensitive, so when it opened "I0042.html" it found "i0042.html" and would open it.  I know how to make the rename command work for changing the "i" to "I", but only within a single folder.  Is there a way at the command line to use rename recursively down through a folder tree?

---

### Post by whitesmith on 2013-09-25
The question is not stupid. My favorite for stuff like this is the find command, which allows command execution on found files. See [http://en.wikipedia.org/wiki/Find_%28Unix%29](http://en.wikipedia.org/wiki/Find_%28Unix%29)

---

### Post by squakie on 2013-09-25
I was having problems making the find recursive, so I went back and read the information on your link as well as the man page again.  I missed the "-maxdepth" option so it wasn't walking the directory tree.  I have that working now (thanks!), so I'm going to try to add the exec for rename to change the "i" to and "I".

Wish me luck, and thanks again!

---

### Post by steeldriver on 2013-09-25
Another way is to enable recursive shell globbing

```
shopt -s globstar
```

Then for example

```

$ rename -nv 's/data/\u$&/' **/*.html
tests/sub1/data1.html renamed as tests/sub1/Data1.html
tests/sub1/subsub1/data7.html renamed as tests/sub1/subsub1/Data7.html
tests/sub1/subsub2/data7.html renamed as tests/sub1/subsub2/Data7.html
tests/sub1/subsub3/data7.html renamed as tests/sub1/subsub3/Data7.html
tests/sub2/data2.html renamed as tests/sub2/Data2.html
tests/sub3/data3.html renamed as tests/sub3/Data3.html

```

---

### Post by squakie on 2013-09-25
hummmmm.......ok, if I understand this correctly, I would need to do:

rename -nv 's/data/\u$&/' **/*.html

from my /home/dave/famhist folder?

if the \u$& saying Uppercase the $ (first) character in the name?

P.S. - I already tried my previous find, adding the exec from the wiki for passing the matching filenames to rename via xargs, but I failed miserably and changed every file or folder with "i" in the name to have "I" in the name - "luckily" within my home folder on down.  But, I still made a mess.  Tried reversing the lower/upper case "i" in the find to reset them - "almost" worked.  Thought it might be wise to double-check here before doing anything more ;)

---

### Post by steeldriver on 2013-09-25
Yes \u$& upper-cases the first character of the matched string (\**U**\& upper-cases the whole thing)

The nice thing about 'rename' is that with the -nv switches you can dry-run the replacement and tweak it to get it right before committing

Are you trying to change ALL html files or just ones with a particular matching name (e.g. beginning with i)?

---

### Post by squakie on 2013-09-25
I was trying to change just files that are in the syntax of "i" followed by a numeric string, with a type of html.  Fortunately for me (whew!) I tried this and only had a few other html files that it hit that had an "i" in the name but not as the first character.  I was able to manually change those back.

Many, many years ago on an old mainframe editor I would have used s/^i/I/ saying substitute the beginning "i" (the caret being the beginning of line character) with the "I".  Is there some sort of similar syntax for the rename?

---

### Post by Vaphell on 2013-09-25
yes, this thing works the same way in rename (rename is based on perl and perl is pretty much a superset of (s)ed capability) but given that you work recursively you get all the files with the path portion in front of the name. Obviously ^ won't point where you would want it to point.

you'd have to do something like this
```
rename -nv 's:(.+/)i:$1I:'
```
save everything before i as $1 and reuse it later.

example
```
$ touch i0001.html
$ rename -nv 's/^i/I/' i0001.html 
i0001.html renamed as I0001.html
$ rename -nv 's/^i/I/' ./i0001.html  # nothing happens because expression doesn't match
$ rename -nv 's:(.*/)i:$1I:' ./i0001.html 
./i0001.html renamed as ./I0001.html
```
but it's not rock solid
```
$ mkdir iii
$ touch iii/test.html iii/i0002.html
$ rename -nv 's:(.*/)i:$1I:' ./iii/*.html 
./iii/i0002.html renamed as ./iii/I0002.html
./iii/test.html renamed as ./[COLOR="#FF0000"]I[/COLOR]ii/test.html
```
this on the other hand is
```
$ rename -nv 's:(.*/)i([^/]+)$:$1I$2:' ./*html ./iii/*.html  
./i0001.html renamed as ./I0001.html
./iii/i0002.html renamed as ./iii/I0002.html
```

but if you change **/*.html to **/i*.html you can go with the shorter version 
```
rename -nv 's:(.*/)i:$1I:' **/i*.html
```
as the case that made it fail becomes impossible.

---

