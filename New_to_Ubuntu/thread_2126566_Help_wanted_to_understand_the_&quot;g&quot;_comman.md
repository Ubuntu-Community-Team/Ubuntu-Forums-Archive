---
title: "Help wanted to understand the &quot;g&quot; command in sed"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by vasa1 on 2013-03-17
I made these two small files:
**a1.txt**
this is the first line
this is the second line
there are two lines above this one
and
**a2.txt**
this is line a
this is line b
lines a and b are above this one

Then, to recover just the lines from each file containing "above", I can use:
```
sed -nrs '/above/p' a*.txt
```
To introduce blank lines below each of the lines, I can use:
```
sed -nrs '/above/p;${g;p}' a*.txt
```
I want help to understand the function of **g** in the second code.
I looked at *info sed* and it has this to say about **g**: 
"Replace the contents of the pattern space with the contents of the hold space."

My understanding is that each line is stored in the "pattern space" and then processed by the specified commands, but at what point does the "hold space" figure and how does that end up providing a blank line?

Basically, what does "${g;p}" do? I know it works. But how?

---

### Post by steeldriver on 2013-03-17
I *think* the way it works is that because you have not swapped anything into the hold buffer, it is empty (i.e. a blank line); so {g;p} puts a blank line into pattern space and then prints it

So for example if you swap the pattern space into the hold space first, it will print the last line ($) instead of a blank line (also the matched line in this case - so you see it twice)

```

$ sed -nrs '/above/p;${h;g;p}' a1.txt
there are two lines above this one
there are two lines above this one

```

or (to make it clearer)

```

$ echo "last line" >> a1.txt
$
$ sed -nrs '/above/p;${g;p}' a1.txt
there are two lines above this one

$ sed -nrs '/above/p;${h;g;p}' a1.txt
there are two lines above this one
last line

```

---

### Post by vasa1 on 2013-03-17
Thanks for your answer :)
 So **h** is the "opposite" of **g**? I'll play with that a bit and come back and mark the thread "solved" if I don't have any further questions.

---

### Post by schragge on 2013-03-18
Yes, **steeldriver** is absolutely right. In case you're trying to understand how [post=12554337]that script[/post] works, I put *${g;p}* in there just to force a blank line at the end of output from each file processed by sed. As the hold space contains nothing at that point, *g* simply erases the previous contents of the last line, but retains the newline at its end, and *p* prints the now empty line.

---

### Post by vasa1 on 2013-03-18
> **schragge said:**
> Yes, **steeldriver** is absolutely right. In case you're trying to understand how [post=12554337]that script[/post] works, I put *${g;p}* in there just to force a blank line at the end of output from each file handled by sed. As the hold space contains nothing at that point, *g* simply erases the previous contents of the last line, but retains the newline at its end, and *p* prints the now empty line.
Thanks for clarifying but it wasn't that script but the [first one]("http://ubuntuforums.org/showthread.php?t=2124743&p=12554090#post12554090") you posted for me :)

---

### Post by schragge on 2013-03-18
Actually, I could do *$s/.*//p* to the same effect there. And with the GNU sed, it's also possible to write *${z;p}*

---

### Post by vasa1 on 2013-03-18
> **schragge said:**
> Actually, I could do *$s/.*//p* to the same effect there. And with the GNU sed, it's also possible to write *${z;p}*
I took the code I referred to above and changed it slightly and then put in the other two options you provided:

```

[10:28 PM] ~ $ time sed -nrs '1d;/^(Name|Exec)=/p;${g;p}' /usr/share/applications/*.desktop > ab

real	0m0.012s
user	0m0.008s
sys	0m0.004s
[10:28 PM] ~ $ time sed -nrs '1d;/^(Name|Exec)=/p;$s/.*//p' /usr/share/applications/*.desktop > ac

real	0m0.011s
user	0m0.008s
sys	0m0.004s
[10:28 PM] ~ $ time sed -nrs '1d;/^(Name|Exec)=/p;${z;p}' /usr/share/applications/*.desktop > ad

real	0m0.012s
user	0m0.004s
sys	0m0.004s
[10:29 PM] ~ $ 

```

I guess for a small set, the difference isn't significant but if the set is large, there would be a preference for the most efficient. So what do real, user, and sys mean here? I took a look at `man time` but ended up no wiser :(

---

### Post by schragge on 2013-03-18
At least, z should be more efficient than s/.*// as [stated]("http://www.gnu.org/software/sed/manual/html_node/Extended-Commands.html") in the sed info page. I guess it should also be more efficient than g as all it does is discarding everything in the current pattern space. I cannot say how s/.*// and g would compare. However, z is a GNU extension. It's unportable and won't work with other sed impementations, e.g. with the BusyBox sed applet. This means you cannot use z in sed scripts invoked from initramfs rescue shell.

---

