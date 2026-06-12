---
title: "Make File Dependencies"
date: 2007-03-31
forum: Programming Talk
---

### Post by ShareBuntu on 2007-03-31
Hi,

I need to install the following modules to make a file:

    *  libwww-perl
    * HTML::Parser
    * URI
    * XML::RSS
    * Digest::MD5
    * Encode

Any idea how I determine their package names so I can download and install them through the repositories?

---

### Post by lnostdal on 2007-03-31
try `aptitude search'

---

### Post by WW on 2007-03-31
You can also use the Search function in Synaptic.  For example, a search for "libwww-perl" finds a package with exactly that name. A search for "html parser perl" results in a few possibilities; the one that you want is probably **libhtml-parser-perl**.

(This was in dapper; some package names may have been changed in edgy or feisty.)

---

### Post by ShareBuntu on 2007-03-31
Thanks for the responses.

I'm trying to install [http://www.mackers.com/projects/theyoke/]("http://www.mackers.com/projects/theyoke/"). I tried running it without downloading any of those modules but I get the following error:

bash: ./theyoke: /usr/local/bin/perl: bad interpreter: No such file or directory

Any ideas?

---

### Post by WW on 2007-03-31
In ubuntu, perl is in /usr/bin, not /usr/local/bin.  You could change the first line of the program to
```

#!/usr/bin/perl

```

---

### Post by lnostdal on 2007-03-31
replace the first line in the file with:

```
#!/usr/bin/env perl
```

---

### Post by WW on 2007-03-31
In case you are wondering about the two different suggestions for changing the first line...

Both will work, but lnostdal's is better, because it should work on a wider variety of systems (as long as they have the env command in /usr/bin).  The author of theyoke should have used **#!/usr/bin/env perl** in the first place.

---

### Post by ShareBuntu on 2007-03-31
Ah, yes, that fixed it. Thanks for that. I installed libwww-perl and libhtml-parser-perl through aptitude as well. I'm still not sure about XML::RSS, URI, Digest::MD5 and Encode. Any idea what these may represent? The aptitude search function returns tons of results.

---

### Post by lnostdal on 2007-03-31
maybe:

```

root@ibmr52:~# aptitude search rss | grep perl
p   libxml-rss-perl                 - Perl module for managing RSS (RDF Site Sum
p   libxml-rsslite-perl             - Lightweight, "relaxed" RSS (and XML-ish) p
root@ibmr52:~# aptitude search uri | grep perl
p   courier-filter-perl             - purely Perl-based mail filter framework fo
p   libgd-securityimage-perl        - Security image (captcha) generator.       
p   liburi-fetch-perl               - Smart URI fetching/caching                
p   liburi-find-delimited-perl      - Find URIs which may be wrapped in enclosin
p   liburi-find-perl                - Find URIs in arbitrary text               
i   liburi-perl                     - Manipulates and accesses URI strings      
p   liburi-query-perl               - class providing URI query string manipulat
root@ibmr52:~# aptitude search md5 | grep perl
p   libcrypt-passwdmd5-perl         - interoperable MD5-based crypt() for perl  
v   libdigest-md5-perl              -                                           
p   libmd5-perl                     - backwards-compatible wrapper for Digest::M

```

didn't find anything for encode though

---

### Post by WW on 2007-03-31
Try the Search function in Synaptic, and use a few relevant words.  For example, I searched for "xml rss perl", and got just one hit: **libxml-rss-perl**.  (But I don't know enough about perl to be able to tell if this provides the module that you need.)

---

### Post by WW on 2007-03-31
It appears that Encode is part of the package **perl-modules**.  You probably already have it installed.

---

### Post by ShareBuntu on 2007-03-31
I installed a few packages from [http://packages.ubuntu.com/feisty/perl/]("http://packages.ubuntu.com/feisty/perl/") and using aptitude's search function. Turns out I needed another package called libterm-size-perl that isn't listed on theyoke's web site. Thanks again. :)

I have one last quick question. Let's say I want to copy the output of a program to a file. How would I do that?

---

### Post by lnostdal on 2007-03-31
```

lars@ibmr52:~/programming/lisp/swtree$ ls > saved-output.txt
lars@ibmr52:~/programming/lisp/swtree$ cat saved-output.txt 
backends
conditions.fasl
conditions.lisp
conditions.lisp~
_darcs
node.fasl
node.lisp
node.lisp~
NOTES
NOTES~
package.fasl
package.lisp
package.lisp~
saved-output.txt
scratch.lisp
swtree.asd
swtree.asd~
swtree.fasl
swtree.lisp
swtree.lisp~
tests
tree.fasl
tree.lisp
tree.lisp~

```

---

### Post by ShareBuntu on 2007-03-31
Thank you very much. :KS

---

