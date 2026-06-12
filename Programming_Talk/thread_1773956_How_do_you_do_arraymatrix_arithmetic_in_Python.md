---
title: "How do you do array/matrix arithmetic in Python?"
date: 2011-06-02
forum: Programming Talk
---

### Post by mihalybaci on 2011-06-02
How do you perform arithmetic with arrays of floating point numbers in Python? Forgive me if this seems like a simple problem, but I've only just begun learning Python.  In IDL the syntax is pretty simple:

x = [1.0,2.0,3.0]
y = x+0.5  ; gives y =  [1.5,2.5,3.5]
z = x*x ; gives z = [1.0,4.0,9.0]

I just can't seem to figure out how to do this Python. I've spent some time reading about the ARRAY module, but that didn't help.

Also as an aside, I have Python3.2 installed, but the default is still v2.7, so the packages I install (e.g. Enthought Python Distribution) are directed to 2.7 not 3.2. Is there a way to make Python3.2 the default for my system? I'm running Ubuntu 11.04.

Thanks for any help.

---

### Post by schauerlich on 2011-06-02
Python doesn't have anything like this built in. However, you can use [NumPy](http://www.scipy.org/Tentative_NumPy_Tutorial#head-4c1d53fe504adc97baf27b65513b4b97586a4fc5). As a bonus, it'll be much faster than using python lists directly.

---

### Post by mihalybaci on 2011-06-02
I have EPD installed, which includes NumPy, SciPY, and a bunch of other science-based modules. What would be the module/syntax to use?

---

### Post by schauerlich on 2011-06-02
> **mihalybaci said:**
> I have EPD installed, which includes NumPy, SciPY, and a bunch of other science-based modules. What would be the module/syntax to use?

I've actually never used NumPy before, but the page I linked you to looks like a good start on answering those questions.

---

### Post by mihalybaci on 2011-06-02
Ah yes, I missed that link before. And that is extremely helpful. Thanks.

---

