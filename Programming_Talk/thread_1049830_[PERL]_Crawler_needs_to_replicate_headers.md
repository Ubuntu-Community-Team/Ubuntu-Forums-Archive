---
title: "[PERL] Crawler needs to replicate headers"
date: 2009-01-25
forum: Programming Talk
---

### Post by zackiv31 on 2009-01-25
I've written some perl crawlers before, but this one needs to simulate headers that my browser would be sending.  I have a site of which makes an AJAX request to specific pages.  It spits back data (I can see it through firebug) that I need to then parse.  Simply calling those href's through perl doesn't spit anything back, which makes me think its because of the headers.

Does anyone have a tutorial on how to do this or can point me in the right direction?

---

### Post by loell on 2009-01-25
an ajax request is executed only at a Javascript enabled and capable browser, javascripts snippets won't be executed by just calling the url in perl.

---

### Post by zackiv31 on 2009-01-25
so are you saying there is no way to do what I want to do?

There must be a way to make an ajax POST to this specific URL and receive the data back... (I have a website/server if this is a necessity)

---

### Post by loell on 2009-01-25
try to scan the javascript of the page through firebug maybe there are specific POST request there.

edit--
after re-reading your first post (you already looked at those POST request enclosed in the script?).

---

### Post by zackiv31 on 2009-01-26
I looked at the POST's, but trying to replicate them through my own webpage doesn't send any data back.

---

