---
title: "Make mv not move directories"
date: 2019-10-19
forum: Programming Talk
---

### Post by atypicalyasaki on 2019-10-19
Hey ! New shell user here. So I tried the following 

```

ryan@ryan-MS-7A46:~/Cours/TP5/Jokers$ ls

aB25s  Boileau    e1xv4   gasUo    iv3dHp  mjkwdhw  p6u1Bi   Ronsard  tsdkj4F  urgwe6  vwjEqk3w
arjhe  bwus7X     esDrhn  glaskda  jacf    mnja     pA3sjge  taki     u7k3f    v5jh    zuk4
bFte   Corbeille  fr3H2   i4jhg    jktf    oFte     r4stTi   tk6E     ud53     vawGl

ryan@ryan-MS-7A46:~/Cours/TP5/Jokers$ mv [aeiouyAEIOUY]* Corbeille/

ryan@ryan-MS-7A46:~/Cours/TP5/Jokers$ ls

bFte     bwus7X     fr3H2  glaskda  jktf     mnja    pA3sjge  Ronsard  tk6E     v5jh   vwjEqk3w
Boileau  Corbeille  gasUo  jacf     mjkwdhw  p6u1Bi  r4stTi   taki     tsdkj4F  vawGl  zuk4

ryan@ryan-MS-7A46:~/Cours/TP5/Jokers$ mv *[A-Z]? Corbeille/

mv: cannot move 'Corbeille' to a subdirectory of itself, 'Corbeille/Corbeille'


```

Why would it prompt me that *[A-Z]? selects Corbeille ? Also is there a thing to not select directories at all on mv ?

Thanks

---

### Post by The Cog on 2019-10-19
> Why would it prompt me that *[A-Z]? selects Corbeille ?
I don't understand that. What does [FONT=Courier New]**[COLOR="#0000CD"]ls *[A-Z]?[/COLOR]**[/FONT] show?

> Also is there a thing to not select directories at all on mv ?
I don't think so. You can use find though:
```
find -maxdepth 1 -type f -name '*[A-Z]?'
```
and move those using find's exec option, ('{}' becomes the found name and \; terminates the command):
```
find -maxdepth 1 -type f -name '*[A-Z]?' -exec mv '{}' Corbeille \;
```

---

### Post by sudodus on 2019-10-19
Like The Cog I would also use a 'find -maxdepth 1 -type f  ...' command line for this purpose to avoid moving directories.

That said, I will try to understand what you want with the attempt to use an expression with wild-cards, *[A-Z]?

In order to use a well defined regular expression you can use the option -regex with find. Please run the following command lines in your directory with Corbeille.

```

find . -maxdepth 1 -regex '\./[A-Z].*' -exec echo mv {} Corbeille/ \; | sort

```

and

```

find . -maxdepth 1 -regex '\./[^A-Z].*' -exec echo mv {} Corbeille/ \; | sort

```

 '\./' takes care or the beginning of each output './' and the dot should be excaped with a backslash character because otherwise it means 'one character of any kind'.

Here [A-Z] means one upper case letter and nothing else at the beginning of the proper file name,
and [^A-Z] means that the file name should *not* start with an upper case letter.

'.*' means that any string of characters may follow in the file name.

---

### Post by TheFu on 2019-10-19
bash file *globbing* is different from regex patterns.
[https://www.tldp.org/LDP/abs/html/globbingref.html](https://www.tldp.org/LDP/abs/html/globbingref.html) explains bash globbing.

**mv** has been working a specific way for decades.  Any changes to the way it works would break millions of existing scripts.  For any specific options, there is the manpage for each command. Always check the manpage ON THE SYSTEM where you are running the command. It will be correct for the specific version installed there.  

Unrelated, but I like to **alias ls='ls -F'** so directories jump out in listings more clearly.  Color directory listings are too hard for me to read. If you do setup that alias, the mv command has a handy option, --strip-trailing-slashes .

I commonly will create a script that makes another script to accomplish what I want.  So, with the -F option to ls, I could easily remove any results from ls -F which contain any '/' characters.
**ls -F1 | egrep -v '/'** which would leave just the non-directory objects - files, symbolic links, pipes, etc.  Drop that into a new file, prepend mv and append Corbeille/ .... bam, I have the script that only moves non-directories into Corbeille/.   If I need something to be run many times, then I wouldn't use **ls** at all.  ls is notorious for creating unexpected results in scripts.

Lots of different options.

---

### Post by The Cog on 2019-10-20
> I commonly will create a script that makes another script to accomplish what I want. So, with the -F option to ls, I could easily remove any results from ls -F which contain any '/' characters.
ls -F1 | egrep -v '/' which would leave just the non-directory objects - files, symbolic links, pipes, etc. Drop that into a new file, prepend mv and append Corbeille/ .... bam, I have the script that only moves non-directories into Corbeille/. 
I like that idea. I like its simplicity.

---

### Post by spjackson on 2019-10-21
> **atypicalyasaki said:**
> 
Why would it prompt me that *[A-Z]? selects Corbeille ?
This is a very interesting question.
  
[LIST]
[*]* matches 'Corbeil' 
[*][A-Z] matches 'l' (for many collations) 
[*]? matches 'e' 
[/LIST]
 
*[A-Z]? would not match bbbbab because 'a' is outside the range A-Z but all other lowercase characters are in the range (for many collations).

---

### Post by Holger_Gehrke on 2019-11-02
Which leaves the question 'What should atypicalyasaki have written to get the intended result ?'
```

LC_ALL=C ls *[A-Z]?       # changes collation to C-standard for one command

shopt -s globasciiranges  # changes globbing to use ASCII-ranges instead of ranges according to localized collation
ls *[A-Z]?
shopt -u globasciiranges  # changes globbing back to ranges according to localized collation

ls *[[:upper:]]?          # use a POSIX character class

```

Holger

---

