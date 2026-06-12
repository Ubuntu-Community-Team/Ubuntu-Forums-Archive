---
title: "No borders/padding on an iframe?"
date: 2011-04-28
forum: Programming Talk
---

### Post by Dustin2128 on 2011-04-28
I'm working on a social website for my friends and me to use, and I'm going for a more... unified look and feel. The website contains a forum, however, which cannot be made to cleanly integrate into the rest of the website. So what I did was I created a page with both the title/navbar, and a frame pointed at the forum. However, there are two things that annoy me about this solution:
A. The frame does not occupy all of the width of the body- there are slivers on the left right and bottom where undesired strips of background image can be seen, and
B. The frame has a border that cannot be removed with border="0". Ideas?
EDIT: Resolved A, but b is a standing issue.

---

### Post by myrtle1908 on 2011-04-28
> **Dustin2128 said:**
> 
B. The frame has a border that cannot be removed with border="0". 

```
style="border:0px"
```

or

```
style="border:none"
```

One of those oughta do it ... untested.

---

### Post by fdrake on 2011-04-28
check this site :[http://devedge-temp.mozilla.org/library/manuals/1998/htmlguide/tags11.html]("http://devedge-temp.mozilla.org/library/manuals/1998/htmlguide/tags11.html")

---

### Post by Dustin2128 on 2011-04-28
> **myrtle1908 said:**
> ```
style="border:0px"
```or

```
style="border:none"
```One of those oughta do it ... untested.
ah, thanks, that fixed it!

---

