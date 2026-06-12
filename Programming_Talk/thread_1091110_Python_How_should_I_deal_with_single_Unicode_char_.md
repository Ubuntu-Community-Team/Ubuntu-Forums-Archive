---
title: "Python: How should I deal with single Unicode char in string"
date: 2009-03-09
forum: Programming Talk
---

### Post by lavinog on 2009-03-09
I am writing a python script that tracks stats on a ut2004 server using the udp query protocol.
The problem I am having is that when a player has a unicode char in their name, it displays question marks.
An example would be:
```
\player_2\}{P&#65533;rtera}{\
```
hexdump:
```
5c 7d 7b 50 f8 72 74 65  72 61 7d 7b 5c 66 72 61  |\}{P.rtera}{\fra|
```
where the unicode char is f8 which is the unicode char for the small o with stroke
The Character Map shows it as:
```
UTF-8: 0xC3 0xB8
UTF-16: 0x00F8

```

Any ideas how I should deal with this?
It looks like the char code is stored, but it isn't being displayed properly.

Is there a way to find characters that are greater than 0x80 such as 0xf8 and replace them with u"\u00f8"?
Or is there a better way?

Also how do i post unicode characters on the forum?

---

### Post by lavinog on 2009-03-09
Figures, I have been trying to solve this for the past couple of hours, and as soon as I posted this, I figured out a solution:

```

teststr="\\player_2\\}{P"+chr(0xf8)+"rtera}{\\"

def unifix(s):
    t=''
    for c in s:
        d=ord(c)
        
        if d>127:
            t+=unichr(d)
        else:
            t+=c
    return t

print unifix(teststr)

```

seems kind of crude to me, but it looks like it might work.
Also this will work too:
```

def unifix(s):
    t=''
    for c in s:
        t+=unichr(ord(c))
    return t

```

Both functions allow me to display the unicode characters, but if I try to pipe the output to head, or less...etc I get:
```
    print unifix(teststr)
UnicodeEncodeError: 'ascii' codec can't encode character u'\xf8' in position 117: ordinal not in range(128)

```
So I think I might still have a future issue.
Any thoughts?

---

### Post by The Cog on 2009-03-09
The byte sequence you have retrieved is not in UTF8 format. Nor is it ASCII. It looks to be encoded using ISO8859-1. You can decode into a proper unicode string like this:
> >>> a='P\xf8rtera'
>>> print a
P&#65533;rtera
>>> b = a.decode("iso8859-1")
>>> print b
Pørtera
>>> 

hth

---

### Post by lavinog on 2009-03-09
Thank you

---

