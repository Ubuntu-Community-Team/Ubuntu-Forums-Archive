---
title: "Css help"
date: 2008-09-25
forum: Programming Talk
---

### Post by dmitrijledkov on 2008-09-25
I have a tag
#maincontent {
    /* loads of options */
}

and in html I use it like this <div id="maincontent">.

How do I change all h1 within #maincontent?

Cause I don't want to use <h1 id="maincontent_h1">, and I don't want to mess up h1 in other div's.

Please help me =(((

---

### Post by kostkon on 2008-09-25
> **dmitrijledkov said:**
> I have a tag
#maincontent {
    /* loads of options */
}

and in html I use it like this <div id="maincontent">.

How do I change all h1 within #maincontent?

Cause I don't want to use <h1 id="maincontent_h1">, and I don't want to mess up h1 in other div's.

Please help me =(((
You can simply do it like this
```
#maincontent h1 {
}
```
some things are inherited from the container so if you want to override them you should redefine them in there

You could also do it
```
#maincontent>h1 {
}
```
but some browsers do not recognise this rule (e.g. IE6)

---

