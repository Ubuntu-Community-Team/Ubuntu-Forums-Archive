---
title: "Firefox not displaying Google home page correctly"
date: 2015-08-06
forum: New to Ubuntu
---

### Post by kapi on 2015-08-06
Have a weird issue with FF. 

when trying view google page [www.google.co.uk](www.google.co.uk) in the browser, the page is missing nearly all of the content. If I try and type anything in the search bar then the search bar stays empty but I get a drop down showing me search suggestions.

Missing images, text and just plain weirdness... any ideas please?

I've reinstalled ff from the repositories twice so far

Cheers

---

### Post by ruzekle on 2015-08-06
What version of Ubuntu are you using? Have you tried using a different address?
[https://en.wikipedia.org/wiki/List_of_Google_domains](https://en.wikipedia.org/wiki/List_of_Google_domains)

---

### Post by kapi on 2015-08-06
yeah tried [www.google.com.au](www.google.com.au) and still the same. 
I think it's definitely ff. Other sites are displaying ok. 

When I tried to reply to your message in ff it would'nt let me type so I'm using chromium as we speak.

---

### Post by kapi on 2015-08-06
I'm also getting this when I run ff from the command line. 

(process:3151): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

---

### Post by Vladlenin5000 on 2015-08-06
Reinstalling whilst keeping the some user profile rarely if ever worked.

Try removing you profile - if you don't have anything important - or renaming the folder. Then open FF and a new fresh profile will be created. Test it.

---

