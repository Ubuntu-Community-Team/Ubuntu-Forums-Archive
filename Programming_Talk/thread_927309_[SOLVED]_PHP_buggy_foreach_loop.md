---
title: "[SOLVED] PHP buggy foreach loop?"
date: 2008-09-22
forum: Programming Talk
---

### Post by null-cipher on 2008-09-22
OK, so I need a little help with this...

The school holidays are approaching, and to stave off boredom, I am making a Web-Based database for the second hand parts we get at work.
Here's my trouble:

```

foreach ($valueArray as $key => $value){
  if ($value == '' OR $value == 'all'){
     continue;
  }
  $queryString = $queryString . $value . " = " . $key . "&&";
}

```
So effectively what I am trying to do, is limit a MySQL query with "WHERE" by reading values out of an array. If the key's value is nothing or 'all', then don't include it in the string.

However, instead of it looking like:
```

SELECT * from ram WHERE size = "sodimm"&&capacity = "512"

```

It looks more like:
```

SELECT * FROM ram WHERE size = "sodimm"&&capacity = "512"&&type = ""&&price = ""

```

Can anybody help at all? I would be ever so grateful!

---

### Post by kjohansen on 2008-09-22
without code that shows how your arrays are defined I dont think we will be of any help...

---

### Post by null-cipher on 2008-09-22
Fair enough, I've uploaded the script I'm using here. It's a little bit of a mess, as I have been fighting with it for a few hours now, but it should be of use.

---

### Post by null-cipher on 2008-10-07
The error was on my part. Apologies.
I had left quotes in my arrays, so naturally they were not in fact empty.

Thank you for your patience.

---

