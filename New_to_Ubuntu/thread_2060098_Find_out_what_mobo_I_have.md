---
title: "Find out what mobo I have?"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by sillyboy on 2012-09-19
Not sure of the exact model of my mother board.  What do I type in the terminal to find out?

Thanks

---

### Post by f8l_0e on 2012-09-19
You could try ```
sudo dmidecode
```

---

### Post by sillyboy on 2012-09-19
> **f8l_0e said:**
> You could try ```
sudo dmidecode
```

Thank You so much!!

---

### Post by Frogs Hair on 2012-09-19
The method at the link doesn't work correctly for me because built my computer and no OEM information is included other than the bios and connector compatibility. As the builder I already have the information.   
 
[http://www.ehow.com/how_5089174_determine-motherboard-type-using-ubuntu.html](http://www.ehow.com/how_5089174_determine-motherboard-type-using-ubuntu.html)

---

### Post by SlugSlug on 2012-09-19
You can also use

```
sudo lshw 
```

---

### Post by Frogs Hair on 2012-09-19
> **SlugSlug said:**
> You can also use

```
sudo lshw 
```

That works ```
 product: M4N78 PRO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 100986770001493
       slot: To Be Filled By O.E.M.

```

---

