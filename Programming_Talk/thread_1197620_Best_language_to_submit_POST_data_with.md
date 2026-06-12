---
title: "Best language to submit POST data with"
date: 2009-06-26
forum: Programming Talk
---

### Post by Pyro.699 on 2009-06-26
Hello,

I know that some languages are better at preforming some tasks better than others. I'm looking on some feedback on what you guys think would be the best language to do this and why. I'm currently using Python and had to download [ClientForm](http://wwwsearch.sourceforge.net/ClientForm/). It works fine now, but ive knoticed it can have problems with some forms. Another thing that is a requirement is the storing of cookies and such. With python i currently use the cookielib module and create this code:

```

global opener
cookiejar = cookielib.CookieJar()
opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cookiejar))

```

Then when i want to open a url i just call opener.open("url").

All of this works fine but i cant help but feel like i could be doing a much better job of this.

If you missed the question, its basically... is there a better way i could be opening urls, storing the cookies, and submitting post data?

Thanks
~Cody Woolaver

---

### Post by master_kernel on 2009-06-26
Still Python, IMHO. I guess you could use Perl, but the code might be a bit longer.

---

