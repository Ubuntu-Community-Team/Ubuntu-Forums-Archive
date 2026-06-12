---
title: "Download script"
date: 2007-06-06
forum: Programming Talk
---

### Post by Peter Sommer-Larsen on 2007-06-06
Hey ppl.

I would like to make a script for downloading video-lectures (in linux). My problem is, that 
they are huge and there are a lot of lectures. It would be nice to have my computer 
downloading automatically all the time. The address's are on a very simple form, like;

[www.physics~.......~/lecture1.avi](www.physics~.......~/lecture1.avi)
[www.physics~.......~/lecture2.avi](www.physics~.......~/lecture2.avi)
[www.physics~.......~/lecture3.avi](www.physics~.......~/lecture3.avi)
[www.physics~.......~/lecture4.avi](www.physics~.......~/lecture4.avi)
[www.physics~.......~/lecture5.avi](www.physics~.......~/lecture5.avi)
[www.physics~.......~/lecture6.avi](www.physics~.......~/lecture6.avi)
[www.physics~.......~/lecture7.avi](www.physics~.......~/lecture7.avi)
.   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
.   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
.   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
.   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
.   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
.   .   .   .   .   .   .   .   .   .   .   .   .   .   .   .
[www.physics~.......~/lecture21.avi](www.physics~.......~/lecture21.avi)

It can not be that hard to program. Some of you clever guys most know how to do it..!
Unfortunately I only do numeric programming, but I am trying to learn C.

Thx.
Peter.

---

### Post by snoop on 2007-06-06
For this you can use wget, which is a command line program that can download (and resume) anything. 
It might already be installed on ubuntu. There are also options to download certain media from a certain webpage or from a list of links in a text file. Its really awesome!

If you really want to program, try writing a simple script in python, perl or whatever you prefer.
you can just have a for loop which concatenates the link "www.physics~.......~/lecture" + number + ".avi"

and have it download the file!

---

### Post by pmasiar on 2007-06-06
> **Peter Sommer-Larsen said:**
> It can not be that hard to program. ...
Unfortunately I only do numeric programming, but I am trying to learn C.

try Python instead! :-)
It is much simpler, and has good libraries to solve problems like that. Module [urllib](http://docs.python.org/lib/module-urllib.html) has special method for you - urlretrieve.

"urlretrieve(  	url[, filename])... The second argument, if present, specifies the file location to copy to"

---

### Post by jyba on 2007-06-07
I don't know enough python yet so I'd bash it like this:
 
```
URL='www.physics~.......~/'
for number in $(seq 1 21); do
	wget -c "${URL}lecture${number}.avi"
done
```

---

