---
title: "Replace Unicode Characters"
date: 2008-03-14
forum: Programming Talk
---

### Post by mikeym on 2008-03-14
Hi,

I'm trying to use *xsel* to feed any selected text into festival to be converted to speech but I'm hitting a problem that some of my text comes back with unicode characters in it for things it should be able to read like:

```
(23–27 keV)

$xsel -o
(23\u201327 keV) 
```

or 

```
$xsel -o -u 
(23â&#128;&#147;27 keV)
```

Now is there anyway of replacing these basic unicode characters with their ascii equivalents?

---

### Post by mikeym on 2008-03-15
I can get a slightly more readable version with the line:

```
$xsel -o -u | uni2ascii -a A
(23<U2013>27 keV)
```

This would at least let me use *sed* on it. Is there some was of running sed to replace codes like this for ascii equivalents? As I understand it the common unicode codes are the same as the ascii codes only with leading zeros.

---

### Post by mikeym on 2008-03-15
OK. I have this, but there has to be a better way:

stdtext
```

#!/bin/bash
echo "<html><body>" > /tmp/convert.htm
cat | uni2ascii -a Q -a D >> /tmp/convert.htm
echo "</html></body>" >> /tmp/convert.htm
cat /tmp/convert.htm | lynx -stdin -dump
rm /tmp/convert.htm

```

Then to read it using festival add as a command in the window manager:

```

xsel -o -u | stdtext | festival --tts

```

---

### Post by mikeym on 2008-03-26
ANy ideas?

---

