---
title: "converting pack() usage from ruby to perl"
date: 2014-02-05
forum: Programming Talk
---

### Post by Lars Noodén on 2014-02-05
I'm not a ruby programmer but I'd like to figure out what the following ruby function is doing.

```

["foobar",0x11,0x22,0x33,0x44,0x55,0x66,0x77,0x88].pack("a*cccccccc")

```

What are the "a*" and the "cccccccc" doing?  I've searched a bit and the "a*" is some kind of directive possibly to make output an ASCII string?  And the "cccccccc" has 8 pieces to correspond to 0x11 - 0x88?

Ultimately I'd like to do the equivalent in perl.

---

### Post by Vaphell on 2014-02-05
[http://www.ruby-doc.org/core-2.1.0/Array.html](http://www.ruby-doc.org/core-2.1.0/Array.html)

apparently a* takes the whole word 'foobar' (* width=length), a would take only 'f' and a3 would take only 'foo'
c is a signed char

```
$ ruby <<< 'puts ["foobar",0x22,0x33,0x44,0x55].pack("acccc")'
f"3DU
$ ruby <<< 'puts ["foobar",0x22,0x33,0x44,0x55].pack("a3cccc")'
foo"3DU
$ ruby <<< 'puts ["foobar",0x22,0x33,0x44,0x55].pack("a*cccc")'
foobar"3DU
$ ruby <<< 'puts ["foobar",0x22,0x33,0x44,0x55].pack("A10cccc")'
foobar    "3DU
```


```
a         | String  | arbitrary binary string (null padded, count is width)
A         | String  | arbitrary binary string (space padded, count is width)
c         | Integer | 8-bit signed (signed char)
```


there is a huge table of these placeholders.

---

### Post by Lars Noodén on 2014-02-05
Thanks.  How ASCII is the 'a' there?  Would it allow Unicode letters or is it limited to 8-bit or even 7-bit?

---

### Post by Vaphell on 2014-02-05
well, i have no idea about ruby myself :-) i just looked at the array page in ruby docs and tested combinations :-)
it appears to allow unicode just fine. The function itself look rather low level in purpose, given it works on a byte level and is able to deal with endianness and **** (its table of directives... damn). You can look at its code if you feel like it

```
$ ruby <<< 'puts ["&#1040;&#1041;&#1042;&#1043;&#1044;",0x22,0x33,0x44,0x55,4491].pack("A*ccccU")'
&#1040;&#1041;&#1042;&#1043;&#1044;"3DU&#4491;
$ ruby <<< 'puts ["&#1040;&#1041;&#1042;&#1043;&#1044;",0x22,0x33,0x44,0x55,4491].pack("A4ccccU")'
&#1040;&#1041;"3DU&#4491;
```


U: int->unicode
width for a/A is in bytes, obviously, so there is a potential of breakage in case of misalignment with unicode codepoints.

---

### Post by Lars Noodén on 2014-02-07
That clears it up.  The following two are equivalent:

```

ruby -rdigest/md5 -e 'puts Digest::MD5.hexdigest(["foobar",0x11,0x22,0x33,0x44,0x55,0x66,0x77,0x88].pack("a*cccccccc"))'

perl -M"Digest::MD5 qw(md5_hex)" -e "print md5_hex(pack('a*cccccccc', 'foobar', 0x11,0x22,0x33,0x44,0x55,0x66,0x77,0x88)),qq(\n);" 

```

---

