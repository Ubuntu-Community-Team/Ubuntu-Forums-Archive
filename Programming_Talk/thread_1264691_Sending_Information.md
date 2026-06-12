---
title: "Sending Information"
date: 2009-09-12
forum: Programming Talk
---

### Post by Hosmion on 2009-09-12
How do I make (in HTML) a page where I make a box, and when someone submits information in the box and hit send it automatically sends it to my email.

Like, if I asked, how many (item) would you want?

They would put in their answer in the text box and hit send.

The information they put in the box would be sent to my email.

---

### Post by wmcbrine on 2009-09-12
Apart from mailto: URLs (little-used these days), email is outside the scope of HTML. What you can do is write a small CGI script that takes the contents of a submitted form and sends an email based on them.

---

### Post by Hosmion on 2009-09-12
And how exactly can I do that?

---

### Post by myrtle1908 on 2009-09-12
> **Hosmion said:**
> And how exactly can I do that?

It depends.  Have you access to the web server?  If so, what can you run there?  Perl, Python, Java, PHP?  You need to be able to process the data from the HTML form on the web server, after which time you can email it somewhere.  How you process the data depends on the technology your web server employs.  There are many many articles on the web regarding this.  If, for example, your webserver is Apache you are using PHP then a simple Google search for: "processing form data +apache +cgi +php +example" would yield many results.

---

