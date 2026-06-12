---
title: "Large text file"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by roodypoo on 2012-02-29
I have a large text file (~7G) I can split it, but when I try to open it I get an error about wrong encoding and to make sure it is not a binary file.

How can I open this file type?

---

### Post by papibe on 2012-02-29
Hi roodypoo.

If you just want to browse the file, you can use the terminal commands 'more' or 'less'. For instance:
```
less big_file.txt
```
Just a thought.
Regards.

---

### Post by roodypoo on 2012-02-29
Thank you, that works great.

I can see there is a bunch of junk in there.

How can I remove everything except numbers, letters and standard characters? ( !@#%^&*<>?:;_-+*)

---

### Post by papibe on 2012-02-29
The simplest way I can think of is to use the 'sed' command to remove all non printable characters.

Try this to test it:
```
sed -r  's/[^[:print:]]//g'  big_file.txt  |  less
```
And if that is good enough, create a new clean file like this:
```
sed -r  's/[^[:print:]]//g'  big_file.txt  >  big_clean_file.txt
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by roodypoo on 2012-03-01
Thank you for the reply.

There is still a lot of junk in the file, but it cleaned it up.

I'm not good with sed at all.

---

### Post by roodypoo on 2012-03-01
Here is some of the file
```

^@<C5>^@n^@<E4>^@s^@e^@t^@s^@^M^@
^@<E4>^@n^@^M^@
^@<E4>^@n^@d^@<E5>^@^M^@
^@<E4>^@n^@d^@<F6>^@v^@e^@r^@d^@r^@a^@g^@^M^@
^@<E4>^@n^@d^@a^@^M^@
^@<E4>^@n^@d^@a^@d^@^M^@
^@<E4>^@n^@d^@a^@d^@e^@^M^@
^@<E4>^@n^@d^@a^@d^@e^@s^@^M^@
^@<E4>^@n^@d^@a^@l^@y^@k^@t^@^M^@
^@<E4>^@n^@d^@a^@l^@y^@k^@t^@e^@n^@^M^@
^@<E4>^@n^@d^@a^@l^@y^@k^@t^@e^@n^@s^@^M^@
^@<E4>^@n^@d^@a^@l^@y^@k^@t^@s^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@e^@n^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@e^@n^@s^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@e^@t^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@e^@t^@s^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@s^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@s^@e^@n^@l^@i^@g^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@s^@e^@n^@l^@i^@g^@a^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@s^@e^@n^@l^@i^@g^@a^@r^@e^@^M^@
^@<E4>^@n^@d^@a^@m^@<E5>^@l^@s^@e^@n^@l^@i^@g^@a^@s^@t^@^M^@

``````

file -bi sortedmaster.txt 
application/octet-stream; charset=binary

``````

recode ascii sortedmaster.txt 
recode: sortedmaster.txt failed: Invalid input in step `ANSI_X3.4-1968..CHAR'

```

The file is supposed to be a text file, one that I created from several different text files.

Is there a way to convert it to ASCII?

---

