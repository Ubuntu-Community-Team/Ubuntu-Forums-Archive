---
title: "why can't this regex match?"
date: 2009-11-25
forum: Programming Talk
---

### Post by hbarai on 2009-11-25
I have been trying to run this regex on some data sets but for some reason it doesn't match yet i feel it should.

```
if(/^\>(\w*) (gi|.*) bs=\s*(\S*) hsplen=\s*(\S*) pid=\s*(\S*) expect=\s*(\S*)\s*(.*)$/)
```

i expect it to match this header line;

> gi|10954454|ref|NC_001911.1| bs=2985 hsplen=1527 pid=99.5415848068107 expect=0.0 Buchnera aphidicola Dn plasmid pLeu-Dn, complete sequence


but alas!no match!!!

can someone out there help? this is in perl

;)

---

### Post by Grenage on 2009-11-25
Have a dabble here :)

[http://gskinner.com/RegExr/](http://gskinner.com/RegExr/)

---

### Post by Arndt on 2009-11-25
> **hbarai said:**
> I have been trying to run this regex on some data sets but for some reason it doesn't match yet i feel it should.

```
if(/^\>(\w*) (gi|.*) bs=\s*(\S*) hsplen=\s*(\S*) pid=\s*(\S*) expect=\s*(\S*)\s*(.*)$/)
```

i expect it to match this header line;




but alas!no match!!!

can someone out there help? this is in perl

;)

Your string starts with "gi", but in your regexp, there is a space before "gi". There is also \>. What does it do? When I try it, it seems to match a literal >.

---

### Post by hbarai on 2009-11-25
> Your string starts with "gi", but in your regexp, there is a space before "gi". There is also \>. What does it do? When I try it, it seems to match a literal 

[LIST]
[*]sorry i forgot the ">" but it's a part of the string
[*]for some reason, a colleague is running  exactly the same software(same scripts) and he's getting this particular string matched
[*]and i dont have to escape the "|"][/LIST] 

(*,)

---

### Post by Arndt on 2009-11-25
> **hbarai said:**
> [LIST]
[*]sorry i forgot the ">" but it's a part of the string
[*]for some reason, a colleague is running  exactly the same software(same scripts) and he's getting this particular string matched
[*]and i dont have to escape the "|"][/LIST] 

(*,)

I can only recommend that both you and your colleague try to trim down the strings and regexps, you just to the point where it starts to match, and then both add things back until you see exactly what the difference is.

Are the versions of Perl the same?

---

