---
title: "bash find/if help"
date: 2011-11-19
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-11-19
I'm trying to get a bash if statement to test if a find command is successful

for example:

the test I'm trying to carry out:
```
find /home/me/Desktop/folder -type d -mmin -1

```
in other words I want to check if the folder (or contents) were modified in the last minute. I'm not sure this is correct....?
if i use the ```
-exec echo TRUE \;
``` option I can get it to work (rather messily)

Now i want to combine this with an if statement:

```
if [ find /home/me/Desktop/folder -type d -mmin -1 ]; then
 *block of commands*
```

How would i check if the find returned True and use that in an if?

thanks

---

### Post by papibe on 2011-11-19
I would use what find returns. If it is not empty you can execute the block:
```
result=$(find /home/me/Desktop/folder -type d -mmin 1)

if [ "$result" != "" ]; then

    # block of commands

fi
```
or just:
```
if [ "$(find /home/me/Desktop/folder -type d -mmin 1)" != "" ]; then

    # block of commands

fi
```
Just a thought.
Regards.

---

### Post by Bachstelze on 2011-11-19
One way

```
firas@itsuki ~ % if [ -z `find . -type d -mmin -1 2> /dev/null` ]; then echo no; else echo yes; fi 
no
firas@itsuki ~ % touch .   
firas@itsuki ~ % if [ -z `find . -type d -mmin -1 2> /dev/null` ]; then echo no; else echo yes; fi
yes

```

Note that this is not what find returns, but what find prints. What it returns is its exit status, which is not useful here.

---

### Post by flyingsliverfin on 2011-11-19
Thanks these are helpful

---

### Post by flyingsliverfin on 2011-11-19
[QUOTE=Bachstelze;11472630]
```
firas@itsuki ~ % if [ -z `find . -type d -mmin -1 2> /dev/null` ]; then echo no; else echo yes; fi 
no
firas@itsuki ~ % touch .   
firas@itsuki ~ % if [ -z `find . -type d -mmin -1 2> /dev/null` ]; then echo no; else echo yes; fi
yes

```

I've seen those 2> before... don't quite remember what they are. Something about redirecting a stream to null?
Which stream? also what's the point?

---

### Post by Bachstelze on 2011-11-19
It redirects standard error to /dev/null. If I don't do it I get this:

```
firas@itsuki ~ % find . -type d -mmin -1
find: &#8216;./software/ubuntu/chroots/natty/var/cache/ldconfig&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/cron/atspool&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/cron/atjobs&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/private&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/public&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/incoming&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/active&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/bounce&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/defer&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/deferred&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/flush&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/saved&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/corrupt&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/maildrop&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/hold&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/var/spool/postfix/trace&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/etc/ssl/private&#8217;: Permission denied
find: &#8216;./software/ubuntu/chroots/natty/root&#8217;: Permission denied

```

It has no influence on the result, but it's not pretty.

---

### Post by flyingsliverfin on 2011-11-20
got it

---

