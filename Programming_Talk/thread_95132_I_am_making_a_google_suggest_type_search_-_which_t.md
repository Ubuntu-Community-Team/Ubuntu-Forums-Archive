---
title: "I am making a google suggest type search - which textbox event do I use?"
date: 2005-11-25
forum: Programming Talk
---

### Post by idn on 2005-11-25
Hi, I am making a search similar to the google suggest type search, where ii shows results as you type in the text box in a div below it.

Everything is fine, except at the moment I am using the 'onkeyup' event, so its pretty slow as it search each time a character is pressed. I only search when valid characters are pressed, but still its pretty slow. 

I was wondering what is the best way to do this

I dont want to have a search button, because that would be no way as good. I want the search to run quickly, as soon as the user has stopped typing. Can anyone help me with this?

Any ideas?

How does google do it?

I notice it does it in the advance search for the forum, for searching users.

---

### Post by nagilum on 2005-11-26
[QUOTE=idn]How does google do it?[/QUOTE]
Well, just have a look at their solution. This AJAX stuff is implemented in client-side javascript and thus public. All the Google functions are defined in [http://www.google.com/ac.js](http://www.google.com/ac.js)

---

