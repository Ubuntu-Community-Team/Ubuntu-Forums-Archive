---
title: "HTTP POST: hidden form field question"
date: 2009-04-06
forum: Programming Talk
---

### Post by andrew222 on 2009-04-06
Is there anyway that we can send data to another web application/server through attributes set in a HTTP POST method's hidden form field. 

 Is it only used for session information for a particular user in a single web app? 

Or can we use that data to send to a completely different web page outside of the web application?

---

### Post by cabalas on 2009-04-06
A hidden input on a web form is like any other input in a form it gets sent to the address specified in the action field as a set of name/value pairs.  If the web app/server located at the address is expecting values with those names it will use them.

---

### Post by s.fox on 2009-04-07
Hi,

I agree with cabalas.

Alternatively you could try [SOAP]("http://en.wikipedia.org/wiki/SOAP") to send the data to another server but might be overkill for what you need to do.

-Ash R

---

