---
title: "Encoding to ascii values outside of the range."
date: 2008-01-04
forum: Programming Talk
---

### Post by tyoc on 2008-01-04
Hi there.

Im trying the following.

```

import codecs
codecs.ascii_encode("ñaña")

```it fail with

> UnicodeDecodeError: 'ascii' codec can't decode byte 0xf1 in position 0: ordinal not in range(128)thought I know it mean is not a value under 128, I really want to encode it in 8bits. (or in the range, ñ in complement 2 is negative, because it is writed like F1)

I mean, I have a CSV file

```
IDML2,2,tengo 18 años
IDMLV,15,no estoy
```Im importing that CSV file into a sqlite database (and it work in some way), but reading fails always (thought I can dump the sqlite)

Error when reading
> l = db_curs.fetchall()
OperationalError: Could not decode to UTF-8 column 't' with text '18 años'sqlite .dump & copy of the row

> INSERT INTO "identificadores" VALUES(2,'IDML_ADV_2','18 a±os');A hex editor has show the following

> 31 38 20 61 F1 6F 73 <----> 18 añosAnd I want that it read/write the F1 correctly, I mean ñ, that is because Im using sqlite, but the problem is about encoding/decoding.

---

### Post by dwblas on 2008-01-04
If I understand correctly, you have to define the variable as unicode.
test = u"ñaña"
or u=unicode("ñaña", "utf-8")
See the python unicode page and/or Google for unicode tutorials for more info, like 
[http://stuff.vandervossen.net/archive/weblog/2003/07/unicode_in_python](http://stuff.vandervossen.net/archive/weblog/2003/07/unicode_in_python)

---

### Post by tyoc on 2008-01-04
O yes, I understand that you can do u"ñañaña", but I dont want to u"the string".

I only want to if there is a failure save the value as is in a 8bit space, like I have said, an hex editor show that the "ñ" is coded as "F1", which is "1111_0001"in 2-complement is "-15" see that ascii is from 0 to 127 but in a 8bit (byte) there is also the "negative part".

And I want that the encoding save that part. (instead of fail, continue)

see this
```

test = "ñañaña"
for c in test:
    print ord(c)
test = u"ñañaña"
for c in test:
    print ord(c)

```
also see that ord not print values as negative, but it take the byte as integer.


It is more like a raw input.... the problem is that those read/writes are behind the sqlite.fetchall() request... thus reading is the 1 that fail (I think writing just work like I spect)

I think a example of what Im doing will help... I will do that... in some time.

---

### Post by pmasiar on 2008-01-05
Wait for Py3K, all strings will be Unicode :-)

---

### Post by tyoc on 2008-01-05
That will be a pain in the ***... hehe.

Still think none of you see the problem clearly... sorry that I haven't put a part of my "problem", but I went to see a serie.

---

### Post by [h2o] on 2008-01-06
How about converting the input file from whatever codec you use to utf-8 before opening it?

---

### Post by popch on 2008-01-06
ASCII defines character codes in the range [0,127] which is hex [0,7F].

In your text sample the character ñ is encoded as (hex) F1 which clearly is outside of the range [0,7F]. Therefore, the character ñ can not be encoded in the ASCII coding scheme, and the character encoded as F1 can not occur in any text which is correct ASCII.

However, in the ANSI encoding scheme, the character ñ is indeed encoded as F1.

Hence, ñ is not encodable in ASCII. It is encodable in ANSI, and the code is hex F1.

Therefore: you must declare your text to be encoded in the ANSI encoding scheme and not in the ASCII encoding scheme.

There might also be other encoding schemes than ANSI which can apply.

---

### Post by tyoc on 2008-01-07
Yep, that is what Im saying, the problem is that is the fetchall from sqlite that is failing reading, I know that for example for a file
```

# -*- coding: cp1252 -*-

```Here the error:
```
    l = db_curs.fetchall()
OperationalError: Could not decode to UTF-8 column 't' with text 'años'
```I have opened the database with a hexeditor (like previously) and there is the 0xF1, in fact I'm saving that data from the same Python, that is: I import it in code from a CVS file, thus the data in the database is ANSI or CP1252 like readed from the CSV.

The problem like I see it, is that reading from sqlite try to read it like ASCII, thus it fail the fetchall behind the scenes ("operational error"). And I dont know how to say to python that the data inside the database is ANSI or CP1252.


The solution is not to pass it to other encoding, is a constrain of the system, thus there is no option.


Hope, people, you get the idea of my problem by now.

---

### Post by tyoc on 2008-01-07
Here is the little code with a sample db with 1 record that show clearly the error.

[http://tyoc.nonlogic.org/darcsrepos/snip1.zip](http://tyoc.nonlogic.org/darcsrepos/snip1.zip)

I think now you get the why the encodings in the file doesnt work, I guess is something simple (in some way we all know what is the source).

---

