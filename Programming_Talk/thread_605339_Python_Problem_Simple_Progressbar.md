---
title: "Python Problem: Simple Progressbar"
date: 2007-11-06
forum: Programming Talk
---

### Post by arsenic23 on 2007-11-06
Ok, so I'm stumped again.

I've had a bit of time on my hands lately, and so I've been trying to write a python script for mass downloading images to further my education.

ANYWAY, I have all the functional stuff working, but I can't quite get my progress bar to work.  I just wanted to do something really simple; break the download into 10 parts and and print a '=' out after each part downloads.  But it seems that if I try to print everything out on one line then nothing prints out until the entire file finishes and the while statement terminates.

Here's my testing code:
```
import sys
import urllib2

val="http://www.ubuntu.com/files/dict/mainbar.jpg"
pie=urllib2.urlopen(val)
localfile=open(val.split('/')[-1],'a')

filesize = int(pie.headers.get("content-length"))
blocksize = int(int(filesize)/10)
att=0

while 1:
	localfile.write(pie.read(blocksize))
	att+=blocksize
	# Figure out how to print the progress bar

	if att >= filesize: break

localfile.close
pie.close
```

I've tried using,
print "=",
print "\r=",
print "\r%s" % '='
sys.stdout.write("=")

-- but the only way it updates acurately is if I print earch character on its own line.  I have no idea why it works this way, but I'd appriciate any pointers or tips anyone could give me.

---

### Post by arsenic23 on 2007-11-07
Ok, so after much reading of __doc__ strings and messing around I found that I need to do something like this:
```
sys.stdout.write("=")
sys.stdout.flush()
```

So I take it that going down to a new line flushes the IO buffer, and that without doing that the contents of stdout arn't writen to the screen ?

I'm still interested in other solutions or pointers if anyone has them though.

---

### Post by smartbei on 2007-11-07
Tou may want to take a look at ncurses and use one of the included widgets. For example, [http://search.cpan.org/~marcus/Curses-UI-0.95/lib/Curses/UI/Progressbar.pm](http://search.cpan.org/~marcus/Curses-UI-0.95/lib/Curses/UI/Progressbar.pm) or [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/168639](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/168639) - Scroll down, there are comments about curses.

---

