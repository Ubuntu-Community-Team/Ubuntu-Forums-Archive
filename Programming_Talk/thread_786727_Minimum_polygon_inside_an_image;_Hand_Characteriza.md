---
title: "Minimum polygon inside an image; Hand Characterization;"
date: 2008-05-08
forum: Programming Talk
---

### Post by Belerophon on 2008-05-08
Hey.
My problem is: I need to characterize a human hand (image).
So I intended to first get the PALM off the image, so I could get an image
with just the fingers. With just the fingers, it would be easier to get some measures of the them.

Convex hull of an image is somewhat standard. I was wondering if getting the smallest polygon inside an image (---> the hand palm) is also standard.

Does anyone know something written in Java to do this??

Thanks.

---

### Post by WW on 2008-05-08
> **Belerophon said:**
> 
Convex hull of an image is somewhat standard. I was wondering if getting the smallest polygon inside an image (---> the hand palm) is also standard.

The smallest polygon?  Wouldn't you want something like the *largest convex polygon* that is within the outline of the hand?

---

### Post by Belerophon on 2008-05-08
> **WW said:**
> The smallest polygon?  Wouldn't you want something like the *largest convex polygon* that is within the outline of the hand?

Ok...lol...my mistake. 


I need the "*largest convex polygon* that is within the outline of the hand", that is the hand palm, so I can take it off the image.

---

### Post by WW on 2008-05-08
For what it's worth:
[http://www.springerlink.com/content/w23l27w3545904v7/](http://www.springerlink.com/content/w23l27w3545904v7/)
[http://www.springerlink.com/content/7690661732276521/](http://www.springerlink.com/content/7690661732276521/)

---

### Post by WW on 2008-05-08
And this: [http://answers.google.com/answers/threadview?id=452313](http://answers.google.com/answers/threadview?id=452313)

---

