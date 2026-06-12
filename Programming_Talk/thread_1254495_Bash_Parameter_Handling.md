---
title: "Bash Parameter Handling"
date: 2009-08-31
forum: Programming Talk
---

### Post by Penguin Guy on 2009-08-31
What I'm trying to achieve is to be able to set a variable with parameters two ways: [COLOR="Green"]-n <name> | --name=<name>[/COLOR]. I have achieved this, but the code looks ugly, long, and complicated. I was wondering if anyone has any suggestions to make it more readable?

```
while [ "$1" != "" ]; do
	if [[ "${1:0:2}" =~ '--' ]]; then
		if [[ "${1:2:5}" =~ 'name=' ]]; then
			NAME="${1:7:128}"
			break
		fi
	fi
	if [[ "${1:0:1}" =~ '-' ]]; then
		i=1
		while [ "${1:$i:1}" != "" ]; do
			if [[ "${1:$i:1}" =~ 'n' ]]; then
				shift
				NAME="$1"
				break
			fi
		i=`expr $i + 1`
		done	
	fi
	shift
done
```

You can either use getopt (unfortunately it's not a POSIX command so may not work on all systems), or use a loop.

---

### Post by dwhitney67 on 2009-08-31
Consider using getopt.  See the man-page for a description.

---

### Post by Penguin Guy on 2009-08-31
> **dwhitney67 said:**
> Consider using getopt.  See the man-page for a description.
Thanks, I'll look into that. :KS

---

### Post by petrus4 on 2009-08-31
I didn't know about getopt; that's cool.

I try and stay away from while loops, though; I tend to stick to for loops instead, since I feel that there's less likely to get an infinite one.

---

### Post by geirha on 2009-09-02
I would not recommend the external getopt command. Either use getopts, or a while-loop.

[http://mywiki.wooledge.org/BashFAQ/035](http://mywiki.wooledge.org/BashFAQ/035)

---

### Post by dwhitney67 on 2009-09-02
> **geirha said:**
> I would not recommend the external getopt command. Either use getopts, or a while-loop.

[http://mywiki.wooledge.org/BashFAQ/035](http://mywiki.wooledge.org/BashFAQ/035)

Why would you not recommend getopt?  Is it because someone (Greg?) said not to use it in their blog?  That someone also did not provide a reason.  Seems kinda suspicious to me that someone is biased against something, but doesn't know why.

---

### Post by geirha on 2009-09-02
> **dwhitney67 said:**
> Why would you not recommend getopt?  Is it because someone (Greg?) said not to use it in their blog?  That someone also did not provide a reason.  Seems kinda suspicious to me that someone is biased against something, but doesn't know why.

That's a good question, and I've tried to find the answer to why getopt is «unsafe» myself. The only answer I've got is that some old version didn't handle quotes properly (though I can't find any references to back this up).

The reason I recommend against using getopt is because it is an external non-posix command that may not be available on all systems where bash is available. And also, if you don't need the extra few features getopt gives you, I'd go with a while loop and/or getopts which will be more efficient.

And lastly, by personal preference, I always try to avoid eval.

Oh, and it's a wiki, not a blog btw.

---

