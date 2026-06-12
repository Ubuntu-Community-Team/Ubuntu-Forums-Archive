---
title: "sort multiple logfiles by month,date, time ascending"
date: 2011-11-11
forum: Programming Talk
---

### Post by Lampi on 2011-11-11
I have some problems sorting a date string:

```
zegrep -h <searchpattern> /var/log/syslog* | sort
```

- This will grep <searchpattern> in syslog.* and syslog.*.gz - as expected
- sort should finish by putting it in the right order again - here's where I am having problems: NOV 10 is not sorted correctly, it's lower than 9?!?

How do I sort logfiles in the right order again? - logfile syntax is:

<mm> <dd> <tt:tt:tt>

and month is alphabetic (NOV = november)

---

### Post by Lars Noodén on 2011-11-11
There should be many tools out there to do this common task, but I can't find even one.  You may have to write a short script in Perl or Python to do the sorting.  

If the log files had used the [ISO 8601](http://www.iso.org/iso/date_and_time_format) date format from the beginning then a plain sort would work just fine.

---

### Post by Lampi on 2011-11-11
@Lars: it's the default log syntax - can you try what you gather with this sort line:

```
sort -k 1,2M -k 2,3n -k 3,4n | less
```

according to the sort manpage this should treat key #1 as:

> compare (unknown) < `JAN' < ... < `DEC'

key #2 should be sorted numeric (stop at key #3 instead end of line)
key #3 should be sorted numeric (stop at key #4 instead end of line)


it's almost working, but I doubt it does handle the month syntax well?

---

### Post by Lars Noodén on 2011-11-11
> **Lampi said:**
> @Lars: it's the default log syntax - can you try what you gather with this sort line:

```
sort -k 1,2M -k 2,3n -k 3,4n | less
```


Wow.  Thanks.  That sort options (M,n) can be appended to -k was not at all clear from the man page.

---

### Post by Lampi on 2011-11-11
@lars: if you can tell me how I can convert the month letter to uppercase (Nov > NOV) it might work. can't tr or sed do this?

---

### Post by Lars Noodén on 2011-11-11
@Lampi, this seems to work for sorting:

```

sort -k 1,2Mf -k 2,3n -k 3,4n | less

```

If you want to force the month into uppercase, you can use awk.
```

awk '{ $1=toupper($1); print $0} ' < /var/log/syslog

```

---

### Post by Lampi on 2011-11-11
I tried both, but it doesn't look good for month sorting in key1

try to mix it with some other month and you'll notice it will mess up the month argument. After this I tried to use pipe with 3 sort commands and the 3 keys:

```
| awk '{ $1=toupper($1); print $0} ' | sort -k 1,2M | sort -k 2,3n | sort -k 3,4n | less
```

but the result is the same: for example "MAR" (=March) is mixed up in "NOV" and "OCT" instead of beeing first.

I have to agree with you, that rsyslog should stick with numeric month values. I noticed most other logfiles already use a better syntax.

---

### Post by Lars Noodén on 2011-11-11
Try like this.

```
| awk '{ $1=toupper($1); print $0} ' | sort -k 1,2Mf -k 2,3n -k 3,4n | less
```

---

### Post by Lampi on 2011-11-11
it's not working :-(

Did you try it yourself with some other month? I wanted to be sure it runs fine, so I copied the syslog files to /tmp and changed the month in a few files to MAR and FEB.

So I had a set of syslog with NOV,OCT,MAR,FEB

Can you try this yourself and check if it fails as well?

---

### Post by Lars Noodén on 2011-11-11
I tried it out myself, that why I posted it.  I took an excerpt from syslog and changed the dates so that it would need sorting, and used that for the test.  

Actually I find I can get by without awk even.

---

### Post by Lampi on 2011-11-11
can you test my attachment I added in the last post? why is it not working in this case?

---

### Post by Lars Noodén on 2011-11-11
Works for me even on your test data.

---

### Post by Lampi on 2011-11-11
unbelievable ... I still use lucid - could this be a bug? Because I can't see what I'm doing different than what you are telling me ...

What *ubuntu are you using?

sort --version # is giving me
sort (GNU coreutils) 7.4


I might try it on an older *buntu or Debian/stable

---

### Post by Lars Noodén on 2011-11-11
I tested it on Oneiric and on Debian Squeeze

$ lsb_release -rd
Description:	Ubuntu 11.10
Release:	11.10

$ apt-cache policy coreutils
coreutils:
  Installed: 8.5-1ubuntu6
  Candidate: 8.5-1ubuntu6
  Version table:
 *** 8.5-1ubuntu6 0
        500 [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) oneiric/main i386 Packages
        100 /var/lib/dpkg/status

---

### Post by Lampi on 2011-11-11
I have to be using it wrong then - what's wrong with this syntax?

```
sort -k 1,2Mf -k 2,3n -k 3,4n tests.txt | less
```
this will place OCT before FEB then NOV

same goes if I use cat filename | sort

I have tested this on squeeze now

sort --version                                                                  
sort (GNU coreutils) 8.5

---

### Post by Lars Noodén on 2011-11-11
I can't see anything wrong with your syntax.  I've tried on both Oneiric and Squeeze and it seems to work for me.  I'm stumped.

---

### Post by Lampi on 2011-11-11
so am I ... thanks anyway Lars, I'll try some more things later

---

### Post by Lampi on 2011-11-11
Can we break this down to a minimum?
```
echo -e "OCT 02 02:56:44 some text\nFEB 22 18:11:59 some other text\nNOV 19 22:46:15 and some more text"  | sort -k 1,2M -k 2,3n -k 3,4n

```
will give me this output:
```
OCT 02 02:56:44 some text
FEB 22 18:11:59 some other text
NOV 19 22:46:15 and some more text
```
what is your output?

---

### Post by Lars Noodén on 2011-11-11
It still works:

```

$ echo -e "OCT 02 02:56:44\nFEB 22 18:11:59\nNOV 19 22:46:15" | sort -k 1,2M -k 2,3n -k 3,4n
FEB 22 18:11:59
OCT 02 02:56:44
NOV 19 22:46:15

```

Edit: Works on Precise, too.

---

### Post by Lampi on 2011-11-11
beats me ... is your /bin/sh pointing to /bin/dash as well?

how is this possible ?!?

---

### Post by Lars Noodén on 2011-11-11
I'm running the sort from bash.  This should be independent of bash or dash.

---

### Post by Lampi on 2011-11-11
I have to admit my coreutils are older than yours, but in squeeze it was the same.

apt-cache policy coreutils
coreutils:
  installed: 7.4-2ubuntu3
  candidate: 7.4-2ubuntu3
  Version-Table:
 *** 7.4-2ubuntu3 0

lsb_release -rd
Description:    Ubuntu 10.04.3 LTS
Release:        10.04

---

### Post by Arndt on 2011-11-11
> **Lampi said:**
> I have to admit my coreutils are older than yours, but in squeeze it was the same.

apt-cache policy coreutils
coreutils:
  installed: 7.4-2ubuntu3
  candidate: 7.4-2ubuntu3
  Version-Table:
 *** 7.4-2ubuntu3 0

lsb_release -rd
Description:    Ubuntu 10.04.3 LTS
Release:        10.04

Could the locale have to do with it?

---

### Post by Lampi on 2011-11-11
possibly

LANG=de_CH.UTF-8
LANGUAGE=
LC_CTYPE="de_CH.UTF-8"
LC_NUMERIC="de_CH.UTF-8"
LC_TIME="de_CH.UTF-8"
LC_COLLATE="de_CH.UTF-8"
LC_MONETARY="de_CH.UTF-8"
LC_MESSAGES="de_CH.UTF-8"
LC_PAPER="de_CH.UTF-8"
LC_NAME="de_CH.UTF-8"
LC_ADDRESS="de_CH.UTF-8"
LC_TELEPHONE="de_CH.UTF-8"
LC_MEASUREMENT="de_CH.UTF-8"
LC_IDENTIFICATION="de_CH.UTF-8"
LC_ALL=


It's German locale - how should I change this for a quick test?

---

### Post by Lars Noodén on 2011-11-11
Try pasting:

export LANG=en_US.UTF-8
export LANGUAGE=en_US:en
export LC_CTYPE="en_US.UTF-8"
export LC_NUMERIC="en_US.UTF-8"
export LC_TIME="en_US.UTF-8"
export LC_COLLATE="en_US.UTF-8"
export LC_MONETARY="en_US.UTF-8"
export LC_MESSAGES="en_US.UTF-8"
export LC_PAPER="en_US.UTF-8"
export LC_NAME="en_US.UTF-8"
export LC_ADDRESS="en_US.UTF-8"
export LC_TELEPHONE="en_US.UTF-8"
export LC_MEASUREMENT="en_US.UTF-8"
export LC_IDENTIFICATION="en_US.UTF-8"
export LC_ALL=


From the man page:

" ***  WARNING  ***  The locale specified by the environment affects sort
       order.  Set LC_ALL=C to get the traditional sort order that uses native
       byte values."

---

### Post by Lampi on 2011-11-11
confirmed, it's locale related:
```
echo -e "OKT 02 02:56:44\nFEB 22 18:11:59\nNOV 19 22:46:15" | sort -k 1,2M -k 2,3n -k 3,4n
FEB 22 18:11:59
OKT 02 02:56:44
NOV 19 22:46:15
```
:)

edit: @Lars, yes - if I export your locale in a shell script it is resulting in
```
FEB 22 18:11:59 some other text
OCT 02 02:56:44 some text
NOV 19 22:46:15 and some more text
```

I'll mark it to solved then, thank you Lars and Arndt

---

### Post by Arndt on 2011-11-11
> **Lampi said:**
> confirmed, it's locale related:
```
echo -e "OKT 02 02:56:44\nFEB 22 18:11:59\nNOV 19 22:46:15" | sort -k 1,2M -k 2,3n -k 3,4n
FEB 22 18:11:59
OKT 02 02:56:44
NOV 19 22:46:15
```
:)

edit: @Lars, yes - if I export your locale in a shell script it is resulting in
```
FEB 22 18:11:59 some other text
OCT 02 02:56:44 some text
NOV 19 22:46:15 and some more text
```

I'll mark it to solved then, thank you Lars and Arndt

It may be enough to prefix the command with LANG=en_US.UTF-8
so you don't have to copy environment variables here and there.

---

### Post by Lampi on 2011-11-11
Indeed Arndt,

I reduced my script to this:
```

#!/bin/bash

LANGPREVIOUS=$LANG              # backup $LANG
export LANG=en_US.UTF-8
echo -e "OCT  2 02:56:44 some text\nFEB 22 18:11:59 some other text\nNOV 19 22:46:15 and some more text" | sort -k 1,2M -k 2,3n -k 3,4n
export LANG=$LANPREVIOUS        # restore $LANG
```
result:
```
FEB 22 18:11:59 some other text
OCT  2 02:56:44 some text
NOV 19 17:46:15 and some more text
```
Thanks Arndt!

---

### Post by Arndt on 2011-11-11
> **Lampi said:**
> Indeed Arndt,

I reduced my script to this:
```

#!/bin/bash

LANGPREVIOUS=$LANG              # backup $LANG
export LANG=en_US.UTF-8
echo -e "OCT  2 02:56:44 some text\nFEB 22 18:11:59 some other text\nNOV 19 22:46:15 and some more text" | sort -k 1,2M -k 2,3n -k 3,4n
export LANG=$LANPREVIOUS        # restore $LANG
```
result:
```
FEB 22 18:11:59 some other text
OCT  2 02:56:44 some text
NOV 19 17:46:15 and some more text
```
Thanks Arndt!

Good that it worked. Then something even shorter will work:

LANG=en_US.UTF-8 sort -k 1,2M -k 2,3n -k 3,4n

---

### Post by Lampi on 2011-11-11
I see, if I don't export it I won't have to reset it

it works!

```
echo -e "Oct  2 02:56:44 some text\nFeb 22 18:11:59 some other text\nNov 19 22:46:15 and some more text" | LANG=en_US.UTF-8 sort -k 1,2Mf -k 2,3n -k 3,4n
Feb 22 18:11:59 some other text
Oct  2 02:56:44 some text
Nov 19 22:46:15 and some more text
```

---

