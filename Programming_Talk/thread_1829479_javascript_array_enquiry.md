---
title: "javascript array enquiry"
date: 2011-08-20
forum: Programming Talk
---

### Post by maclenin on 2011-08-20
**A tiny bit of background:**

I have two arrays - one parent and one child, if you will.

The child is a subset of the parent.

parent array:
```
parent=new Array()
parent[0]=image1;
parent[1]=image2;
parent[2]=image3;
parent[3]=image4;
parent[4]=image5;
parent[5]=image6;
```

child array:
```
child=new Array()
child[0]=parent[0];
child[1]=parent[**[COLOR="DarkOrange"]3[/COLOR]**];
child[2]=parent[4];
```

Each image "value" (in the parent array) has unique parameters - e.g. horizontal vs. vertical orientation - which I address in a third array. When images are selected - from a web-based thumbnail gallery (which could be made up of the parent or the child subset of images) - the (larger) image is displayed with proper positioning and orientation. 

**The central issue:**

I am searching for a way to **access the index number** of the parent "value" within the child array - i.e. the "**[COLOR="DarkOrange"]3[/COLOR]**" within parent[**[COLOR="DarkOrange"]3[/COLOR]**] - as this number is keyed to the formatting characteristics (of image4, for example) defined within the 3rd array.

Thanks for any suggestions.

---

### Post by simeon87 on 2011-08-20
Store the id together with the image and use that id to do a lookup in the third array. Or better, store the information of the third array together with the image so the third array is no longer needed.

---

### Post by maclenin on 2011-08-20
Thanks, **simeon87** for the advice. What I ended up doing (for the time being, at least) is incorporating a "lastIndexOf()" statement, which, when run on the output of the child array, provides the "i" I'm looking for.

Essentially, the result of a "click" on child[1] is image4. When "image4" is captured as variable x, the solution seems to be...

```
i=parent.lastIndexOf(x);
```

...which yields [COLOR="DarkOrange"]**3**[/COLOR]!

Thanks, again, for your help!

---

