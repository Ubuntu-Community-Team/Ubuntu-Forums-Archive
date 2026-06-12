---
title: "Regular Expression Question"
date: 2010-08-23
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-08-23
I have lines of a vector file which look like this:

/*More text here*/  {V {**clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;**}} /*More text here*/

To select the part inside the outermost brackets, I used this regex:

\{.*\}

How do I select the contents inside the innermost brackets (in bold)?

---

### Post by nebu on 2010-08-23
put another set of brackets around it!

---

### Post by yalyari on 2010-08-23
Something like this;

\{[^{}]*\}

Sytax might be slightly different, depending on the regex flavor.

---

### Post by surfer on 2010-08-23
kodos is a nice regex testing application... just in case.

---

### Post by SNYP40A1 on 2010-08-23
> **yalyari said:**
> Something like this;

\{[^{}]*\}

Sytax might be slightly different, depending on the regex flavor.

Thanks for the quick responses!

nebu, your response would work too and I thought of it, but there was one other case that I forgot to specify, something like this:

{V {clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;} W {wfs=3;}}

I just want to capture the "V" vector part.  yalyari, solution works.  I also appreciate the kodos note.  Notepad++ also supports regular expressions.  It's Win32, but runs fine under Wine.

---

### Post by StephenF on 2010-08-23
.*?\{V \{(.*?)\}

Proof.
```

stephen@tmb ~ $ python
Python 2.6.5 (release26-maint, Aug  6 2010, 22:54:47) 
[GCC 4.3.4] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import re
>>> re.match(".*?\{V \{(.*?)\}", "/*More text here*/ {V {clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;}} /*More text here*/")
<_sre.SRE_Match object at 0xb73c17a0>
>>> re.match(".*?\{V \{(.*?)\}", "/*More text here*/ {V {clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;}} /*More text here*/").group(1)
'clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;'

```

---

### Post by SNYP40A1 on 2010-08-24
Yeh, I've been meaning to learn Python...

---

### Post by ghostdog74 on 2010-08-24
> **SNYP40A1 said:**
> I have lines of a vector file which look like this:

/*More text here*/  {V {**clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;**}} /*More text here*/

To select the part inside the outermost brackets, I used this regex:

\{.*\}

How do I select the contents inside the innermost brackets (in bold)?

regular expression is the last thing to come to mind. Don't fret yourself with regex. Here's one way to leave home without it 

```

$ s="/*More text here*/ {V {clk_pins=0; inputsetup1_pins={ i want here} 0 0 0 0 1 0 0 0 0 0;} } /*More text here*/"

$ echo $s|awk -vRS="}" -F"{" '/{/{print $NF}'
 i want here

$ s="/*More text here*/ {V {clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;}} /*More text here*/"

$ echo $s|awk -vRS="}" -F"{" '/{/{print $NF}'
clk_pins=0; inputsetup1_pins=0 0 0 0 1 0 0 0 0 0;


```


Basically, set record separator to "}". (in Python, just use split() )
Then set field separator to "{". The last column ( in Python, use s[-1] after splitting by "{" ) will be the column you want.

---

