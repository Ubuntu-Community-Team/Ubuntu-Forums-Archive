---
title: "modifying classes using javascript"
date: 2011-09-02
forum: Programming Talk
---

### Post by maclenin on 2011-09-02
I would like to change the value of a style component within a css class....

I have a number of divs which all share the same class.

I would like to be able to change the single class vs. having to modify multiple divs....

Essentially:

**CLASS**
```
a.classA {display:block; width:100px;}
```

**DIV**
```
#div1
#div2
#div3
#div4
#div5
```

**DIV + CLASS**
```
<div id="div1"><a class="classA"></a></div>
<div id="div2"><a class="classA"></a></div>
<div id="div3"><a class="classA"></a></div>
<div id="div4"><a class="classA"></a></div>
<div id="div5"><a class="classA"></a></div>
```

Is there a **document.getElement(s)** (or other) method by which I can dynamically change the "width" value within **a.classA**?

Thanks for any help!

---

