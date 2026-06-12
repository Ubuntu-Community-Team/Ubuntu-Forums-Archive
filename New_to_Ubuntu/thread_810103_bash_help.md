---
title: "bash help"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Zacariaz on 2008-05-27
I have a very simple problem, which I thought I knew how to solve, but I have kinda forgotten and I simply don't know what to search and have spend the better part of an hour looking at bash tutorials...

Anyway, the problem is as follows:

(example)
I have a lot of log files on a server of mine and I want to download some of them using wget. the log files are of the form logyymmdd.txt

Now, I only want files for a given interval so what I thought I could do was this:
```
wget http://server.com/logs/log08[01-03][01-31].txt
```

Of course this doesn't work, however, I know that something similar is possible, fx. it works if I make a list instead:
```
wget http://server.com/logs/log08{01,02,03}{01,02,03,...,31}.txt
```
but this is rather stupid.


Thanks in advance.

---

### Post by sdennie on 2008-05-28
Have you tried wrapping the URL with single or double quotes?

---

### Post by Zacariaz on 2008-05-28
I have now, no luck.

---

### Post by sam_delta on 2008-05-28
have you tryied separating it into single digits?
```
wget http://server.com/logs/log080[1-3][0-3][0-9].txt
```
sam

---

### Post by Zacariaz on 2008-05-28
Not in the the way your suggest, but I have made sure that the leading zero is not the problem.

Also, I have of course tryed what you suggested, just to be sure, but it does not work.

Should it work?

---

### Post by sam_delta on 2008-05-28
not sure, it was my guess. let me play a bit with the terminal and see if i can get something

sam

---

### Post by HalPomeranz on 2008-05-28
> **Zacariaz said:**
> 
```
wget http://server.com/logs/log08[01-03][01-31].txt
```


No chance of this ever working for two reasons:

1) [...] is a character class match.  "[A-Z]" is the set of characters from 'A' thru 'Z' inclusive, but "[01-03]" is non-sensical.

2) [...] only matches against local files.  Trying to include it in an external URL also doesn't make sense.

If you don't want to list the two parameters manually, you could always use loops:

```

for m in `seq 1 3`; do
    for d in `seq -w 1 31`; do
        wget http://server.com/logs/log080$m$d.txt
    done
done

```

May I ask, however, why you're using wget for this and not something like rsync or scp?  Either would make your life much easier because you could use shell globbing on the remote system, e.g.:

```

scp server.com:/some/path/to/logs/log08\*.txt .

```

---

### Post by sam_delta on 2008-05-28
explained above

if it wont work in a Url then why did the list syntax worked?

and yes, you can use [...] with numbers, as long as they are single digit, (just tested it with ls)

sam

---

### Post by niteshifter on 2008-05-28
Hi,

I think what you want is:

```
wget -r -l1 --no-parent -A"log0801*.txt" http://server.com/logs/
wget -r -l1 --no-parent -A"log0802*.txt" http://server.com/logs/
wget -r -l1 --no-parent -A"log0803*.txt" http://server.com/logs/
```

if you have to use wget and http. Far easier to do with wget via ftp, then regex can be used. See the man page on wget and this [page]("http://www.gnu.org/software/wget/manual/wget.html"), which is a bit more complete than the man page.

---

### Post by Zacariaz on 2008-05-28
> **HalPomeranz said:**
> May I ask, however, why you're using wget for this and not something like rsync or scp?  Either would make your life much easier because you could use shell globbing on the remote system, e.g.:

You may...
1. I'm fairly new to linux and therefore have a limited knowledge of the tools available.
2. It seemed like the obvious approach.

---

### Post by HalPomeranz on 2008-05-28
> **sam_delta said:**
> 
if it wont work in a Url then why did the list syntax worked?


Because {1,2,3,...} is a list of values, not a pattern match against local file names.  "[...]" is a shell "glob" and has to be matching against something local.

> **sam_delta said:**
> 
and yes, you can use [...] with numbers, as long as they are single digit, (just tested it with ls)

Of course.  "[0-9]" is a valid character class just like "[A-Z]".  But "[01-03]" doesn't make any kind of sense at all.

---

### Post by HalPomeranz on 2008-05-28
> **Zacariaz said:**
> You may...
1. I'm fairly new to linux and therefore have a limited knowledge of the tools available.
2. It seemed like the obvious approach.

These are certainly valid reasons.  However, wget may not be the best approach here.  After all, if you can wget these files then other people who can talk to your web server would also be able to download these files.  It's not clear to me that you want to be making your log files available to all and sundry (or sending them over the network in the clear).

scp and rsync have the advantage that they will require at least some form of authentication (even if it's just a password) and the session will be encrypted.

---

### Post by sam_delta on 2008-05-28
> **HalPomeranz said:**
> Because {1,2,3,...} is a list of values, not a pattern match against local file names.  "[...]" is a shell "glob" and has to be matching against something local.



Of course.  "[0-9]" is a valid character class just like "[A-Z]".  But "[01-03]" doesn't make any kind of sense at all.

makes sense now,, thx for the explanation

sam

---

