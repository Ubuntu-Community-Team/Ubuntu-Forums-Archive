---
title: "Passing arguments to 'grep' through 'xargs'"
date: 2010-07-18
forum: Programming Talk
---

### Post by Dill on 2010-07-18
I'm stumped on how to program this elegantly, and could some extra mind-power to help out!

Basically, I have one file that is a list of URLs; let's call this file 'urlFile'. I have another file, error.log, which is the file to which I write my *wget* errors (through the *-a* option). The two files look something like this:

_**urlFile**_
[http://www.hello.com/test](http://www.hello.com/test)
[http://ftp.hello.com/test2](http://ftp.hello.com/test2)
...

_**error.log**_
[http://www.hello.com/test](http://www.hello.com/test)
ERROR in download
...
[http://test.test.com/foo](http://test.test.com/foo)
ERROR in download

In the end, I want to e-mail a list of URLs that *wget* couldn't download (found in 'error.log'); additionally, I'd like to have the script find the line number of these URLs in 'urlFile'. Here's what I have so far:

```
grep -B1 "ERROR" error.log
```

This grabs the lines in error.log that match **ERROR**, as well as the line above (which is the URL that *wget* had trouble downloading.

I pipe that output to 

```
grep -v "[ERROR|^\-\-]"
```

which strips the lines with "ERROR" info (which we don't really care about), as well as any lines with "--" (which grep substitutes in place of a series of non-matching lines between your matching ones). This leaves us with a set of suspect URLs, each on its own line.

I'm trying to find the line number of each of these URLs in 'urlFile'. This would seem the most elegant way to complete the pipe:

```
xargs -0 grep -n [url] urlFile >> suspectUrls
```

which would take each argument passed to *xargs* as the search string in *grep*, appending that output to a file called 'suspectUrls'. The contents of that file would look something like this:

```
satherdy@lamp:~$ cat suspectUrls
2:http://test.test.com/foo
5:http://ftp.bar.com
```

I'm not an expert with *xargs* by any means, and I'm looking for some insight on how to accomplish what my pseudocode is trying to do :). 

**In sum, how do I take *xargs* arguments and pass them as a *grep* search string?** Or, is there a more elegant way to accomplish the same thing?

Cheers,
Dill

---

### Post by Dill on 2010-07-18
I think I found it: *xargs **-I*** accomplishes exactly what I want

```
satherdy@lamp:~/Desktop/malware$ grep -B1 "ERROR" error.log | grep -v "[ERROR|^\-\-]" | xargs -I {} grep -n {} urlFile | sed 's/^\([0-9]\{1,\}\:\)/Line \1 /g'
Line 2: http://test
Line 1: hello
```

*xargs* is so sexy ;)...

If anyone has other suggestions besides *xargs*, I'm also still open to suggestions!

Cheers,
Dill

---

### Post by DaithiF on 2010-07-19
Hi, i would probably do it something like this:
```
cat -n urlfile | while read num line
do
  grep -q "$line" error.log
  [[ $? == 0 ]] && echo $num $line
done

```

---

### Post by Ole Tange on 2010-07-19
> **Dill said:**
> I'm stumped on how to program this elegantly, and could some extra mind-power to help out!


If you have GNU Parallel [http://www.gnu.org/software/parallel/](http://www.gnu.org/software/parallel/) installed:

```
cat urlfile | parallel wget {} '||' grep -n {} urlfile 2>> errorlog | mail dill@example.com
```I believe it does not come much more elegant than that.

Add -j0 if you want to run as many jobs in parallel as possible (make sure your web servers can cope with that if the urls are hosted on the same physical servers).

Watch the intro video for GNU Parallel at: [http://www.youtube.com/watch?v=OpaiGYxkSuQ]("http://swiss.ubuntuforums.org/Watch%20the%20intro%20video%20for%20GNU%20Parallel%20at:%20http://www.youtube.com/watch?v=OpaiGYxkSuQ")

But be warned: If you find xargs sexy, you may have to change underwear after learning about GNU Parallel :)

---

### Post by ghostdog74 on 2010-07-23
> **DaithiF said:**
> Hi, i would probably do it something like this:
```
cat -n urlfile | while read num line
do
  grep -q "$line" error.log
  [[ $? == 0 ]] && echo $num $line
done

```

this whole portion is equivalent to 
```

grep -n -f urlfile error.log

```

---

### Post by DaithiF on 2010-07-24
> **ghostdog74 said:**
> this whole portion is equivalent to 
```

grep -n -f urlfile error.log

```
no, the OP wanted to show the line numbers from the urlfile, ie the source of the patterns,  not the target file he is grepping.

---

