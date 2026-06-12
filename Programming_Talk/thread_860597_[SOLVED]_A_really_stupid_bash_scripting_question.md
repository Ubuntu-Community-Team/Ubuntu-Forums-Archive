---
title: "[SOLVED] A really stupid bash scripting question"
date: 2008-07-15
forum: Programming Talk
---

### Post by cardinals_fan on 2008-07-15
I wrote a Perl script to display my school grades last year, but it got erased when I moved back to Xubuntu from Slackware.  After reading a thread about displaying baseball scores in the command line, I decided that I could use the lynx text browser in a bash script to perform this task more efficiently.  I use Perl to filter out my overall percentages, and everything works fine.  However, I want to prepend the subject to each percentage.  I have only rudimentary bash knowledge, and I'm not sure how to do this.  Here's an example script for one subject:
```
echo "History:" & lynx -nonumbers -dump *grade web page* | perl -n00 -e 'print $1,"\n" if /Overall Grade.*?([\d.]+%)/ms'
```
This puts "History:" and the grade on seperate lines.  How do I combine them on the same line?

---

### Post by |{urse on 2008-07-15
I know it's in quotes, but does removing the "\n" help?

---

### Post by cardinals_fan on 2008-07-15
> **|{urse said:**
> I know it's in quotes, but does removing the "\n" help?
Nope, that appends a space AFTER the grade, not after the label.  My problem is that the "&" between the label and the percentage puts them on seperate lines, but I can't think of any other way to link them.

---

### Post by ghostdog74 on 2008-07-15
it would save us the trouble if you have posted a sample.

---

### Post by cardinals_fan on 2008-07-15
> **ghostdog74 said:**
> it would save us the trouble if you have posted a sample.
I DID post a sample.  Look at the code in my original post...

---

### Post by LaRoza on 2008-07-15
> **cardinals_fan said:**
> I DID post a sample.  Look at the code in my original post...

Probably means a sample of the output. (It can't be run without certain packages that everyone might not have)

---

### Post by ghostdog74 on 2008-07-15
yes, a sample of the output from the lynx command.

---

### Post by cardinals_fan on 2008-07-15
> **ghostdog74 said:**
> yes, a sample of the output from the lynx command.
Sorry about that.  As I mentioned, it prints out on two lines (see below):
```

93.8%
100.0%
92.5%
129.2%
93.4%
History:
92.8%

```
As you can see, history is on a seperate line from the appropriate grade (because it runs after the ampersand).

---

### Post by ghostdog74 on 2008-07-15
in your perl script, check for pattern "History", if found, don't print "\n". How's that? otherwise, describe how your output will be!
Also, provide the web page link

---

### Post by dominiquec on 2008-07-15
> This puts "History:" and the grade on seperate lines. How do I combine them on the same line? 

Try this:

```
echo "History: " `mycommand`
```

Putting a command between ` quotes will send its output to echo.

---

### Post by cardinals_fan on 2008-07-15
> **ghostdog74 said:**
> in your perl script, check for pattern "History", if found, don't print "\n". How's that? otherwise, describe how your output will be!
Also, provide the web page link
History isn't in the page; that's why I'm adding it with echo.  But my problem's solved :)
> **dominiquec said:**
> Try this:

```
echo "History: " `mycommand`
```

Putting a command between ` quotes will send its output to echo.
Thanks!  That solved it.

---

