---
title: "VIM question"
date: 2006-04-12
forum: Programming Talk
---

### Post by krypto_wizard on 2006-04-12
Hi,

I am an average VIM user and have this doubt.

As I write docment my right side goes to infinity. I mean suppose a line has 500 characters it shows all in one line. I want atmost only 80 char to be show and then automatically goto the next line for visual purposes. 

What do I need to modify in .vimrc file.


Thanks

---

### Post by gnu2tux on 2006-04-12
set textwidth=79 

?

regards,

Al.

---

### Post by kabus on 2006-04-12
set textwidth=80

---

### Post by shawnhcorey on 2006-04-13
Open a VIM session, type the following and press RETURN:

  :help ins-textwidth

This will give you a description of many formatting options.

shc

---

