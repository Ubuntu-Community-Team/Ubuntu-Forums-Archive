---
title: "PHP Editor with apache preview?"
date: 2007-03-06
forum: Programming Talk
---

### Post by swkiller on 2007-03-06
Hey everyone,

I was wondering if anyone knew of a good PHP type IDE editor which included a website preview, that would be able to connect to your localhost and have your apache server display the results?

I believe a windows editor, UltraEdit, did this....but I've yet to find a good editor in ubuntu :/

Thanks :)

---

### Post by clouserw on 2007-03-07
Why not just run a browser and refresh the page when you want to see the results?

---

### Post by swkiller on 2007-03-08
Well this is true, and in fact it's what I do right now.  I was just curious if there was such an application, because I feel it would be more handy.

---

### Post by pmasiar on 2007-03-08
> **swkiller said:**
> I was wondering if anyone knew of a good PHP type IDE editor which included a website preview, that would be able to connect to your localhost and have your apache server display the results?)

If I was develioping any such editor and was deciding (after fixing all bugs :-) ) between adding this feature or any other, my concerns would be: Why spend time implementing something (browser) which big teams of developers spend years to implement? Then, any serious developer  compares how his site looks like in at least two major browsers (IE and Firefox/Mozilla) and maybe bunch of smaller ones, like Opera, Konqueror etc. So reimplementing only one of them would not do me any good. Especially if this can be done trivially by opening the site in browser and reloading the page: Alt-Tab, F5. And this solutions does not add any new bugs - is maintenance free :-)

If something *can* be done, it does not mean it should be done. Even (or especially) in free software development, developer's time is not free.

---

### Post by Mirrorball on 2007-03-08
I think Eclipse + PDT ([http://www.eclipse.org/pdt/index.php](http://www.eclipse.org/pdt/index.php)) has it. Regardless, it's an** excellent** IDE for PHP.

---

### Post by Dygear on 2007-03-09
ScITE has it as long as you have it pointed towards your php.exe, press F5 and you have the output of the program, HTML or not. The only issue is that it does not open up a browser window. But I'm almost 100% sure that you could set that up.

---

