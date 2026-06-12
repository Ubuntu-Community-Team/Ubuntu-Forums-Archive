---
title: "perl xml query"
date: 2008-03-03
forum: Programming Talk
---

### Post by mrphd on 2008-03-03
Hi, I'm writing a perl script, part of which involves restructuring an xml file. The file I have has the following structure:

```
<a1>
   <b1 something1 /b1>
   <b2 something2 /b2>
   ... maybe further nesting
</a1>
<a1>
  <b3>
      <c1 something3 /c1>
      <c2 something4 /c2>
      ... maybe further nesting
   </b3>
</a1>
<a2>
    etc...
```

I want to merge the levels so I have:

```
<a1>
   <b1 something1 /b1>
   <b2 something2 /b2>
   <b3>
      <c1 something3 /c1>
      <c2 something4 /c2>
      ... maybe further nesting
   </b3>
   ... maybe further nesting
</a1>
<a2>
    etc...
```

is there a simple way of doing this in perl? please let me know if this is not clear. many thanks.

mrphd

---

