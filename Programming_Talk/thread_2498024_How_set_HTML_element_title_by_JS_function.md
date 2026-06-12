---
title: "How set HTML element title by JS function ?"
date: 2024-05-27
forum: Programming Talk
---

### Post by maketopsite on 2024-05-27
How can I please make something like that:
```
<p title=<script>SomeJSFunctionReturningString();</script> 
...
/p>

```

---

### Post by &amp;KyT$0P# on 2024-05-27
Is this for your own webpage, or are you writing a user script?
Could you please explain more details of what you're trying to achieve with setting title attribute by script?

The answer will involve
```
.setAttribute('title', SomeJSFunctionReturningString());
```
But that is a very incomplete Javascript code snippet that isn't enough to work.  The rest depends what you're trying to do, when & how often you want the title updated.

---

### Post by maketopsite on 2024-06-09
> **halogen2 said:**
> Is this for your own webpage, or are you writing a user script?
Could you please explain more details of what you're trying to achieve with setting title attribute by script?

The answer will involve
```
.setAttribute('title', SomeJSFunctionReturningString());
```
But that is a very incomplete Javascript code snippet that isn't enough to work.  The rest depends what you're trying to do, when & how often you want the title updated.

It's a user script for some webpage.

I need show some text (Tooltip) any time mouse hover over some text.

Solution:
```
<script>function setTitleTo(elem,value) {
    elem.title= value;
}</script>
...
<p title="default" onmouseover="setTitleTo(this,'Sometext')" onmouseout="setTitleTo(this,'Othertext')"
```
source:

[https://www.linuxquestions.org/questions/programming-9/how-set-html-element-title-by-js-function-4175737426/#post6504045](https://www.linuxquestions.org/questions/programming-9/how-set-html-element-title-by-js-function-4175737426/#post6504045)

---

