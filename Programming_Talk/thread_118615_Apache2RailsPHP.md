---
title: "Apache2/Rails/PHP"
date: 2006-01-17
forum: Programming Talk
---

### Post by ikazuchi on 2006-01-17
Okay, I'm attempting to get both Ruby on Rails and PHP working on my dev box. I currently work in PHP, but would like to learn ruby. However, it seems impossible to configure apache2 to use PHP but set specific directories to be used with ruby.

Am I missing something or is it truly impossible to set up apache2 to use PHP except for certain directories and serve those with ruby?

---

### Post by Burke on 2006-01-27
OK, so if this is just a dev box, you should be fine to use Rails's integrated web server, webrick. (pretty sure that's what its called). It will operate on a different port, like 9xx or something. This way, you can have PHP on your Apache server and Rails on some other server. After you install rails, you go into your project directory and type "ruby script/server".

---

### Post by dudus on 2006-02-02
this is exactly what I have now and it's fine. But if you want to deploy RoR use apache or lighttpd

---

