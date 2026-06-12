---
title: "Search tool"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by analogdialog on 2013-02-09
I can not find a tread about this; I need a tool to find files by name or content. The one in MS Windows works so well. Yes, Nautilus has a search tool, but it has not worked for me. One time, Nautilus crashed, an other time it searched forever...
What else, the Dash ? No, I think it searches in "recently used" or something. It was unable to find a file I picked as example.
So, the software center then ? Yes, there is "search for files". It won't search for a text string in a file, you can't select a time frame. A little to simple. Why does Ubuntu not ship with a decent file and folder search tool, on par with MS Windows 2000 (>10 years old) ?

---

### Post by 3v3rgr33n on 2013-02-09
Searching in a folder is achieved through ctrl-F (graphical way in a folder).

It's worth looking at the manual pages of the cmd 'find'  and 'locate'
e.g to find JohnDoe.txt in your home directory try: find ~ -iname JohnDoe.txt

locate is used like so : locate JohnDoe.txt

---

### Post by Frogs Hair on 2013-02-09
Gnome Desktop Utilities in the software center includes a search tool that at least for me works much better than the one in Nautilus. It also starts from the muitifucnion key on my keyboard.

---

### Post by sudodus on 2013-02-09
If you want to search for content (words or text strings) in documents (e.g. odt, doc, pdf files), you can use Recoll. Install with

```
sudo apt-get install recoll
```

Remember to update index

***File -- Update Index***

before starting to search

---

### Post by tgalati4 on 2013-02-09
There are many search tools in linux:

apropos
which
locate
find
grep

tgalati4@Mint14-Extensa ~ $ apropos search
apropos (1)          - search the manual page names and descriptions
badblocks (8)        - search a device for bad blocks
bsearch (3)          - binary search of a sorted array
bzegrep (1)          - search possibly bzip2 compressed files for a regular expression
bzfgrep (1)          - search possibly bzip2 compressed files for a regular expression
bzgrep (1)           - search possibly bzip2 compressed files for a regular expression
Class::ISA (3pm)     - report the search path for a class's ISA tree
find (1)             - search for files in a directory hierarchy
git-bisect (1)       - Find by binary search the change that introduced a bug
hsearch (3)          - hash table management
hsearch_r (3)        - hash table management
lfind (3)            - linear search of an array
lsearch (3)          - linear search of an array
lzegrep (1)          - search compressed files for a regular expression
lzfgrep (1)          - search compressed files for a regular expression
lzgrep (1)           - search compressed files for a regular expression
manpath (1)          - determine search path for manual pages
mate-search-tool (1) - the MATE Search Tool
memdiskfind (1)      - utility to search for a MEMDISK instance
oldfind (1)          - search for files in a directory hierarchy
res_search (3)       - resolver routines
strcspn (3)          - search a string for a set of characters
strpbrk (3)          - search a string for any of a set of characters
strspn (3)           - search a string for a set of characters
tsearch (3)          - manage a binary tree
wcschr (3)           - search a wide character in a wide-character string
wcscspn (3)          - search a wide-character string for any of a set of wide characters
wcspbrk (3)          - search a wide-character string for any of a set of wide characters
wcsrchr (3)          - search a wide character in a wide-character string
wmemchr (3)          - search a wide character in a wide-character array
XFreeFontPath (3)    - set, get, or free the font search path
XGetFontPath (3)     - set, get, or free the font search path
XrmGetResource (3)   - retrieve database resources and search lists
XrmQGetResource (3)  - retrieve database resources and search lists
XrmQGetSearchList (3) - retrieve database resources and search lists
XrmQGetSearchResource (3) - retrieve database resources and search lists
XSetFontPath (3)     - set, get, or free the font search path
xzegrep (1)          - search compressed files for a regular expression
xzfgrep (1)          - search compressed files for a regular expression
xzgrep (1)           - search compressed files for a regular expression
zegrep (1)           - search possibly compressed files for a regular expression
zfgrep (1)           - search possibly compressed files for a regular expression
zgrep (1)            - search possibly compressed files for a regular expression
zipgrep (1)          - search files in a ZIP archive for lines matching a pattern

apt-cache search search

I'll let you load that last command.

---

