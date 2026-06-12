---
title: "How do I display the squares and cubes using HTML and JavaScript, as requested?"
date: 2017-02-12
forum: Programming Talk
---

### Post by s3a on 2017-02-12
Question 3:
[https://www.docdroid.net/PDphWiR/soen287-winter2017-assignment-2.pdf.html#page=5](https://www.docdroid.net/PDphWiR/soen287-winter2017-assignment-2.pdf.html#page=5)

I successfully got it working by giving the HTML tag I tested an id called "demo" (without the quotes) and putting the following right before the closing body tag.:
<script type="text/javascript">
	document.getElementById("demo").innerHTML = Math.pow(3,3);
</script>

My current problem, though, is that the question seems to want me to have the JavaScript syntax in the head tags (but that the syntax I just showed above doesn't work there, because what's in the body displays after what's in the head).

So, what exactly does this question want me to do?

Any input would be greatly appreciated!

---

### Post by norobro on 2017-02-13
if you create the whole table in a javascript function, you can put the function between the head tags. Do a search for "javascript create table".

---

### Post by s3a on 2017-02-17
> **norobro said:**
> if you create the whole table in a javascript function, you can put the function between the head tags. Do a search for "javascript create table".
Thanks! That was what I needed to know!

---

