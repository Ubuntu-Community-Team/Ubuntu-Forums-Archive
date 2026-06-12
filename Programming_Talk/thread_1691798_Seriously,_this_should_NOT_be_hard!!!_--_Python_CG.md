---
title: "Seriously, this should NOT be hard!!! -- Python CGI"
date: 2011-02-20
forum: Programming Talk
---

### Post by garfonzo on 2011-02-20
Ok, all I want to do is have a python CGI script open a web page within my site. 

Here's the way it happens:

1) A user completes a form on my site, clicks "Submit"
2) The submit button calls a python script to email the contents of the form.

Now, after the CGI has emailed the form info, I want it to simply navigate to a web page in my site (namely, a "thank you for your info" type page). You know, to let the user know their info has been sent. 

Grr!! I can't figure this out!!

---

### Post by t1497f35 on 2011-02-20
Sorry I noticed you're a bit pissed off, hopefully this will help
[http://www.google.com/images?hl=en&q=a%20cup%20of%20rage&um=1&ie=UTF-8&source=og&sa=N&tab=wi&biw=2112&bih=942](http://www.google.com/images?hl=en&q=a%20cup%20of%20rage&um=1&ie=UTF-8&source=og&sa=N&tab=wi&biw=2112&bih=942)

---

### Post by garfonzo on 2011-02-20
[This about sums it up.]("http://dya.mine.nu/forum/rage3.png")

Seriously though, I am going a bit nuts.....

---

### Post by memilanuk on 2011-02-20
Have you tried googling 'python cgi'?

what code have you actually tried to get working?

---

### Post by wmcbrine on 2011-02-20
You can either:

1. Return a 302 response instead of 200, or
2. Send a web page with a meta refresh tag, or
3. Have the script output the "Thank you" page itself.

In classic CGI, IIRC, the response is already sent by the web server, so option 1 is unavailable.

---

### Post by garfonzo on 2011-02-20
> **wmcbrine said:**
> You can either:

1. Return a 302 response instead of 200, or
2. Send a web page with a meta refresh tag, or
3. Have the script output the "Thank you" page itself.

In classic CGI, IIRC, the response is already sent by the web server, so option 1 is unavailable.

I got fed up and went with option 3.

---

### Post by wmcbrine on 2011-02-21
Option three is a pretty normal thing for a CGI script to do, so I'm not sure why you think of this as giving up.

---

### Post by greenmonkeey on 2011-02-21
can u tell me where to learn python language...

---

### Post by Yeti can't ski on 2011-02-21
> **greenmonkeey said:**
> can u tell me where to learn python language...

I am also learning it. This was a very a good starting point: 

[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3/Wikibook]("http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python_3/Wikibook")

---

### Post by Calliham on 2011-02-21
Google: learn python language free

---

### Post by Portmanteaufu on 2011-02-24
You can have your CGI script simply provide a Location header as its sole output.

e.g.
```

#!/usr/bin/python
print("Location: /some/thank_you/page.html\n")

```

Note that if you output anything at all before that header, it won't work.

---

