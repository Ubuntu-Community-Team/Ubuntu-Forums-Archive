---
title: "What Nautilus Scripts are must haves?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-06-27
I've never really used any Nautilus Scripts. 

I had open with sudo gedit but never really used it. 

Are their any that a really useful in anyones opinion?

---

### Post by pluckypigeon on 2008-06-27
Do people really use nautilus scripts? 

What sort of stuff can you do with them?

---

### Post by cozmicharlie on 2008-06-27
"Browse as root" and "open gedit as root".  All you need to do is right click on a file and you can access it as root or edit as root.  There are other ways to do this but I find it very handy.

---

### Post by flytripper on 2008-06-27
does anyone know how to include a right click entry so i can ope a termianl in that location rather than haviing to cd all the time?  that would be useful

---

### Post by wdaniels on 2008-06-27
> **flytripper said:**
> does anyone know how to include a right click entry so i can ope a termianl in that location rather than haviing to cd all the time?  that would be useful

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by wdaniels on 2008-06-27
> **pluckypigeon said:**
> I've never really used any Nautilus Scripts. 

I had open with sudo gedit but never really used it. 

Are their any that a really useful in anyones opinion?

Not really if you're a typical user - anything very typical and generally useful would usually end up being implemented by nautilus as standard.

Unless there's something that comes to mind for you personally that you always want to be able to do from nautilus (as an example, the subversion scripts can be very useful for developers) then I can't think of any "must have" scripts to recommend other than perhaps open-terminal as just mentioned.

---

### Post by pluckypigeon on 2008-06-27
> **wdaniels said:**
> (as an example, the subversion scripts can be very useful for developers) 

what are the subversion scripts?

---

### Post by flytripper on 2008-06-27
thanks wdaniels

---

### Post by wdaniels on 2008-06-27
> **pluckypigeon said:**
> what are the subversion scripts?

Subversion is a source code control system which allows developers to manage changes to source code files by keeping track of the differences between each version of each file. This is particularly helpful for allowing multiple developers to work against the same set of code and then merge their changes together.

The nautilus scripts just allow you to perform subversion operations like check out, update, revert, commit etc. against files by right-clicking on them in nautilus, instead of having to open a command like and type the "svn" commands in a shell.

There are other revision control systems as well as Subversion (Ubuntu developers use one called Bazaar).

Unless you work on any development projects using Subversion, the scripts are not really relevant to you, I just brought it up as an example that there are a few "must have" scripts for certain groups of users, but not so much for general users. I probably needn't have mentioned it and did so really because these are the only nautilus scripts I use myself.

I've heard of people using things like Subversion to manage changes to sets of configuration files as well as program source code, but unless you're managing lots of machines that's not really something to consider either.

---

### Post by kaibob on 2008-06-27
I use Nautilus Actions rather than Nautilus scripts, but the following site contains many useful Nautilus scripts:

[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

I use PDF files a lot and find the ability to combine and split PDF files to be useful. The first of the following very-simple scripts combines two or more selected PDF files into one PDF file. The second script splits a PDF file into individual pages. Both scripts require Ghostscript. 

```
#!/bin/bash
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sOutputFile=combined.pdf "$@"
```

```
#!/bin/bash
lastpage=$(pdfinfo "$1" | grep ^Pages | sed 's/Pages:[[:space:]]*//')
for i in $(seq $lastpage) ; do
gs -sDEVICE=pdfwrite -dQUIET -dNOPAUSE -dBATCH -dFirstPage=$i \
-dLastPage=$i -sOutputFile=/home/bob/temp/page-$i.pdf "$1" 2>/dev/null
done
```

---

