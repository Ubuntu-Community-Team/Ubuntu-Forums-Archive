---
title: "awk problems"
date: 2008-07-19
forum: Programming Talk
---

### Post by lachild on 2008-07-19
Hello everyone,

I had a bit of awk code that I somehow managed to slop together.  The code use to work from Dapper on.  Unfortunatly in Hardy the same code stoped working.  

Here's the code I am using...
```
echo 'c:\windows\profiles\My Documents\somefile.html' | awk 'BEGIN{ FS="\\" } { for (i=1; i<NF+1; i++){ print
$(i) "\n" } }'
```

should produce

```
windows
profiles
My Documents
somefile.html
```

instead it's producing

```
c:\windows\profiles\My Documents\somefile.htm
c:\windows\profiles\My Documents\somefile.htm
c:\windows\profiles\My Documents\somefile.htm
c:\windows\profiles\My Documents\somefile.htm
```


Thanks in advance for any help you can provide.
Lachild

---

### Post by WW on 2008-07-19
Here's what I get (on gutsy):
```

$ echo 'c:\windows\profiles\My Documents\somefile.html' | awk 'BEGIN{ FS="\\" } { for (i=1; i<NF+1; i++){ print $(i) "\n" } }'
c:

windows

profiles

My Documents

somefile.html

$

```
so maybe you want something like this:
```

$ echo 'c:\windows\profiles\My Documents\somefile.html' | awk 'BEGIN{ FS="\\" } { for (i=2; i<NF+1; i++){ print $(i) } }'
windows
profiles
My Documents
somefile.html
$ 

```

---

### Post by ghostdog74 on 2008-07-19
```

# echo 'c:\windows\profiles\My Documents\somefile.html' | awk '1' RS='\'
c:
windows
profiles
My Documents
somefile.html

```

---

### Post by lachild on 2008-07-19
Thanks guys all three of our awk programs worked.  As it turnes out, the problem I was having was actually with firefox and not awk at all.  Firefox cant seem to load the reworked file path Unless there is a SPACE just before the closing (")...  For instance, the following does NOT work:

```
$!/bin/bash

##Set Path
a= "/home/myhome/.wine/drive_c/windows/profiles/myhome/somesite/index.html"

##Run Firefox
firefox "$a"
```


Oddly enough this next one DOES work.

```
$!/bin/bash

##Set Path
a= "/home/myhome/.wine/drive_c/windows/profiles/myhome/somesite/index.html"

##Run Firefox
firefox "$a "
```


Thanks again for all your help.  If you guys wouldn't have givin me the other two awk codes, I'd have never tracked it down.

---

### Post by lachild on 2008-07-19
Oh ps.

If your trying to replicate the problem,  it only happened when I added the "." for the wine folder.  If you take out the period, the path worked fine.  Put it back in and Firefox freaks out until you add a space at the end of the file path.

---

### Post by ghostdog74 on 2008-07-19
there should not be a space after the variable "a"
```

a="/home....."

```
you can also use single quote instead of double quotes

---

### Post by lachild on 2008-07-21
I agree there should NOT be a space after the $a... But if you don't include the space and you are pointing to a hidden directory (like ".wine") it fails to load the URL.

For instance consider the following:

```
~# firefox "/home/myhome/.wine/drive_c/windows/My Documents/profiles/myhome/some_site/index.html"
``` 

This brings up the following URL in FireFox

"file:///home/myhome/Documents/profiles/myhome/some_site/index.html"

Now if you do this:

```
~# firefox "/home/myhome/.wine/drive_c/windows/My Documents/profiles/myhome/some_site/index.html "
```

It brings up the URL correctly.


It's the strangest thing I think I've seen in quite a while.. (PS I've only seen this problem in Hardy, I don't know if it's Ubuntu specific or FF3 is at fault)

---

### Post by unutbu on 2008-07-21
Both of these work for me on a Gutsy system.

```
bad@math:~% firefox "$HOME/test/.wine/drive_c/windows/My Documents/profiles/myhome/some_site/index.html"
bad@math:~% firefox "$HOME/test/.wine/drive_c/windows/My Documents/profiles/myhome/some_site/index.html "
bad@math:~% firefox --version
Mozilla Firefox 2.0.0.14, Copyright (c) 1998 - 2008 mozilla.org
```

/usr/bin/firefox is a script. Please post yours as an attachment. I'll diff it against mine and see if anything interesting pops up.

---

