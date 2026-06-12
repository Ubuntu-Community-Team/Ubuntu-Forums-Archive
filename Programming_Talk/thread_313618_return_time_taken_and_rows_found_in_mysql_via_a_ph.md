---
title: "return time taken and rows found in mysql via a php query"
date: 2006-12-06
forum: Programming Talk
---

### Post by apjone on 2006-12-06
I am looking into how to get a php+mysql to report number of rows found and the time taken to complete a query.

Can any one help with the time taken stat ?
I know how to get return the number of rows found.

---

### Post by tocleora on 2006-12-06
This may not be the proper way to do it, but a quick code I do is this... At the very top of the page I do this:

```
$starttime = date("Y-m-d H:i:s");
```

And at the end of the page I do this:

```
echo $starttime.' - '.date("Y-m-d H:i:s");
```

It doesn't do any calculations but gives you a quick visual of how long the page took to load.  I'm sure there's something better though. :)  If you need a quick fix you might try that.

---

