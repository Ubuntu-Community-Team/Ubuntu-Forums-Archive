---
title: "(Javascript) Is it possible to access the script dom element from inside the script?"
date: 2010-08-25
forum: Programming Talk
---

### Post by Yuzem on 2010-08-25
Hello, I know that I could use an id but I wonder if there is another way to do it for example:

```

<body>bla, bla, bla...

<script>alert(this.tagName)</script>

</body>

```

Alert should display: "script"
Thanks in advance.

---

### Post by soapytheclown on 2010-08-25
dunno if this is gonna be any help but assigning an id to the script tag works
```

<script id="test">
alert( document.getElementById('test').innerHTML );
</script>

```

---

### Post by Yuzem on 2010-08-25
Yes, yes, I know that I can use an id but I meant without id, class, or other alike solutions.
For example if I am not mistaken document.write writes in the current element, I want to get that element without identifying the script tag.
Is it possible?

---

### Post by dv3500ea on 2010-08-25
I'm curious as to why you want to do this. There may be a better way of achieving what you want to do without getting the script DOM element. 

document.write(s) is equivalent to document.body.innerHTML = s (it writes to the body element, overwriting the current content.)

It is hard to get the script element without using an id but you can use
document.getElementsByTagName('script'), which returns an array of script elements in the order they appear on the page.

---

### Post by Yuzem on 2010-08-25
> **dv3500ea said:**
> I'm curious as to why you want to do this.
I have a page that loads content dynamically and sometimes the content that gets loaded has a script that manipulates the loaded content.
Currently I assign an unique id to the script on the server that is the number of the process plus an increasing counter in case there were many script in the same request.
I thought that if it is possible, it would be much simpler and easy to get the element from inside the script like with events: onclick="myfunction(this)"

---

