---
title: "[SOLVED] [Python] Print matching lines in a file"
date: 2008-06-30
forum: Programming Talk
---

### Post by durand on 2008-06-30
Hi,
This should be a pretty simple question but I can't seem to find an answer on the web. How would you do the equivalent of:

```
grep file "string" 
``` with python. I've found one method so far using re.

Here it is:

[PHP]    pattern = re.compile( Variable1 )
    
    for line in data:
        a_match = pattern.search( line )
        if ( a_match ):
            print line
            
[/PHP]
The problem is that "string", or Variable1 in the code, should not be parsed for regex.

Thanks in advance :)

---

### Post by Can+~ on 2008-06-30
You don't want to parse it as a regexp, then why are you using regexps in the first place?

Matching exactly the line (w/o regexp):
[PHP]search_str = "hello"
search_file = open("myfile", "r")

for line in search_file:
	if line.strip() == search_str:
		print line

search_file.close()
[/PHP]

Matching a substring
[PHP]search_str = "hello"
search_file = open("myfile", "r")

for line in search_file:
	if line.strip().find(search_str) != -1:
		print line

search_file.close()
[/PHP]

Check string methods:
[http://docs.python.org/lib/string-methods.html](http://docs.python.org/lib/string-methods.html)

(Extra: Add try/except IOError/finally when managing files).

---

### Post by LaRoza on 2008-06-30
```

for line in open("unix.text"):
    if "Gurus" in line:
        print line
```
```

~$cat unix.text
Get GUMMed
----------
 
The Gurus of Unix Meeting of Minds (GUMM) takes place Wednesday, April 1, 2076
(check THAT in your perpetual calendar program), 14 feet above the ground
directly in front of the Milpitas Gumps.  Members will grep each other by the
hand (after intro), yacc a lot, smoke filtered chroots in pipes, chown with
forks, use the wc (unless uuclean), fseek nice zombie processes, strip, and
sleep, but not, we hope, od.  Three days will be devoted to discussion of the
ramifications of whodo.  Two seconds have been allotted for a complete rundown
of all the user-friendly features of Unix.  Seminars include "Everything You
Know is Wrong", led by Tom Kempson, "Batman or Cat:man?" led by Richie Dennis
"cc C?  Si!  Si!" led by Kerwin Bernighan, and "Document Unix, Are You
Kidding?" led by Jan Yeats.  No Reader Service No. is necessary because all
GUGUs (Gurus of Unix Group of Users) already know everything we could tell
them.
		-- Dr. Dobb's Journal, June 1984
```

---

### Post by Can+~ on 2008-06-30
> **LaRoza said:**
> ```

for line in open("unix.text"):
    if "Gurus" in line:
        print line
```


Right, I always forget the [FONT="Courier New"]in[/FONT] operator. :KS

---

### Post by LaRoza on 2008-06-30
> **Can+~ said:**
> Right, I always forget the [FONT="Courier New"]in[/FONT] operator. :KS

It is handy :-)

It is also faster I think.

---

### Post by durand on 2008-07-01
Thanks both of you! I used LaRoza's method because it was a lot simpler. I thought I tried that yesterday but my IDE froze for a while. I think I know why. It outputs a lot very quickly so redrawing everything uses up the cpu completely.

One more question, what is the preferred way of outputting to a text file and would it work on every platform? At the moment I'm using print:

```
print >> file, "string"
```
but I get *IOError: [Errno 2] No such file or directory* if the file doesn't exist. Is there the equivalent of unix touch in python? (has to be cross platform)

Thanks again.

---

### Post by geirha on 2008-07-01
You need to open the file in write or append mode. help(file)
```

f= file("/tmp/foo.txt", "w")
print >> f, "something"
f.close()

```

---

### Post by durand on 2008-07-01
Okie, I was using r+ instead of w, maybe that was my problem....Thanks.

---

