---
title: "Pango escape '&lt;' and '&gt;'"
date: 2009-02-23
forum: Programming Talk
---

### Post by tom66 on 2009-02-23
I assume it is necessary to escape '<' and '>' in a pango string if they need to be displayed themselves. For example, if I had an input box and a program converted it to bold, it would wrap bold tags around the text. How would I handle an input of '<s>hello</s>' which would be parsed as a strike-through text? I want all of the input to be visible.

---

### Post by G|N| on 2009-02-23
```
&lt;s&gt;hello&lt;/s&gt;
```

&lt; = <
&gt; = >

---

