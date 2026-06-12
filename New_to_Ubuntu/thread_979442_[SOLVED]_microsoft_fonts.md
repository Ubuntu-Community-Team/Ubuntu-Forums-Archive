---
title: "[SOLVED] microsoft fonts"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by misswham on 2008-11-12
I used to have microsoft fonts on my ubuntu before i reinstalled it and now i cant find how to download them again. Will someone please tell me where to find them.  I dont see them in synaptic.

---

### Post by Tatty on 2008-11-12
```
sudo apt-get install msttcorefonts
```

I think thats it.

---

### Post by Pro-reason on 2008-11-12
You need to install the Microsoft TrueType Core Fonts.```

sudo apt-get install **msttcorefonts**

```

---

### Post by misswham on 2008-11-12
i have done that twice and it starts loading and when it ask me to type y/n i type y and enter and this is what i get

 msttcorefonts uses defoma                                                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474; 
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474; 
 &#9474; configure it to use defoma fonts.                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474; 
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474; 
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474; 
 &#9474; printing) this is not required.                                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>    

dont know what to do after this

---

### Post by IceBadger on 2008-11-12
Make sure that you enable the third-party software repositories.  I have not had the problem you describe, but I also enable these repos right away.

---

### Post by iaskedalice09 on 2008-11-12
> **misswham said:**
> i have done that twice and it starts loading and when it ask me to type y/n i type y and enter and this is what i get

 msttcorefonts uses defoma                                                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use   &#9474; 
 &#9474; the fonts provided by this package under the X Window System, you must    &#9474; 
 &#9474; configure it to use defoma fonts.                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; The easiest way to do so is to use the x-ttcidfont-conf package. For      &#9474; 
 &#9474; more information, install the x-ttcidfont-conf package and consult its    &#9474; 
 &#9474; documentation under /usr/share/doc/x-ttcidfont-conf.                      &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; For uses of msttcorefonts not related to the X Window System (e.g.        &#9474; 
 &#9474; printing) this is not required.                                           &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>    

dont know what to do after this
To accept, you mean? Hit the right arrow key and then hit Enter. 

Hope this helps!

---

