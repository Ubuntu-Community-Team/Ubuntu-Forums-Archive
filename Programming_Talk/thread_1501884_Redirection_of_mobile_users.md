---
title: "Redirection of mobile users"
date: 2010-06-04
forum: Programming Talk
---

### Post by puzzler995 on 2010-06-04
How would I redirect a user using cell phone web browsers (such as those on Android and the iPhone) to another page in your site? 
I have already read the FAQ and have hit nothing but dead ends.
Thank you,
Puzzler995

---

### Post by soltanis on 2010-06-04
Almost every web browser transmits its identity as well as limited details about the platform it is running on using the HTTP User-agent field. In CGI and PHP scripts, you can inspect this field, checking for the specific User Agents that Android/iPhone/other smartphones send and redirect them to a different site.

Many websites also use the convention of "m.example.com" if your site were located at "www.example.com"; mobile web browsers seem to try to go to this site first. I'm talking about low-end range devices though, such as Nokia S40's using the built-in browser; powerful smartphones may or may not do this.

---

### Post by SoFl W on 2010-06-04
[http://w3schools.com](http://w3schools.com) If done properly finding out the media type should be in the [cascading style sheet]("http://w3schools.com/css/css_mediatypes.asp")

---

### Post by puzzler995 on 2010-06-04
> **soltanis said:**
> Almost every web browser transmits its identity as well as limited details about the platform it is running on using the HTTP User-agent field. In CGI and PHP scripts, you can inspect this field, checking for the specific User Agents that Android/iPhone/other smartphones send and redirect them to a different site.

how would I do that? I'm truthfully only experienced in (X)HTML  and XML, but I have minor experiance in CSS and Python

> Many websites also use the convention of "m.example.com" if your site were located at "www.example.com"; mobile web browsers seem to try to go to this site first. I'm talking about low-end range devices though, such as Nokia S40's using the built-in browser; powerful smartphones may or may not do this.
I unfortunately don't have the 'm.example.com' convention, as my site is [http://la-vida.sourceforge.net]("http://la-vida.sourceforge.net")

> **SoFl W said:**
> [http://w3schools.com](http://w3schools.com) If done properly finding out the media type should be in the [cascading style sheet]("http://w3schools.com/css/css_mediatypes.asp") 
The only problem with this is that newer touch-based smartphones require a TOTALLY different (X)HTML page. I'm having to totally rewrite the site, not just the theme, and I'm pretty sure CSS cannot do redirects... Thanks anyway :)

---

