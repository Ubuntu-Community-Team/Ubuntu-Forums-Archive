---
title: "PHP Web Dev question...?"
date: 2012-01-18
forum: Programming Talk
---

### Post by hockey97 on 2012-01-18
Hi, I just notice my domain name provider allows me to use Cnames.

like for instance [www.mydomain.com](www.mydomain.com) or mobile.mydomain.com

the first part.

the problem is how can I use them? 


I want to have mobile.mydomain.com to direct the user to a mobile format of my website.

---

### Post by Lars Noodén on 2012-01-18
Set up one name as the A name and then the others as CNAMEs.  You can then use name-based virtual hosts to have different sites, one of which would be your mobile site.

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

---

### Post by hockey97 on 2012-01-18
> **Lars Noodén said:**
> Set up one name as the A name and then the others as CNAMEs.  You can then use name-based virtual hosts to have different sites, one of which would be your mobile site.

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

oh, ok so I have to set it up as a new site via vhosts?

is there any good tutorials to teach me how to make my website mobile friendly?

---

### Post by Lars Noodén on 2012-01-19
For making your site mobile-friendly, the easiest way is to follow accessibility guidelines religiously.  Using CSS for layout and using relative units helps the most with that.  If you can change the size and shape of your browser's window to any extreme, with and without images, increasing or decreasing font size, and still be able to *use* the site (worry less about how it looks) then you're good for mobile devices too.  

[http://www.w3.org/WAI/](http://www.w3.org/WAI/)
[http://www.umich.edu/webaccess/best/quickguide.html](http://www.umich.edu/webaccess/best/quickguide.html)

Same goes for [lynx](apt://lynx).  If you can use your site with lynx, then it can also be used with a mobile device.  That's a bit extreme, but works solidly.

---

