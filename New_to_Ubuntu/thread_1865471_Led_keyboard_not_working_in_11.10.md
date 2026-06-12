---
title: "Led keyboard not working in 11.10"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by ouija1979 on 2011-10-20
Hi, I have an led keyboard that lights using the scroll key, I have used the following guide...


you can enable the scroll lock key by typing:

xmodmap -pm

to find an unused modifier ... on my machine, mod3 is free
to set up the scroll lock key on mod3, you can type:

xmodmap -e 'add mod3 = Scroll_Lock'

now the scroll lock key should work
but i don't know if Gnumeric will ignore it or not.

When I type this I get this in terminal it works and the scroll key lights up the keyboard, after a restart I have to do it all again, very frustrating, What can I type into terminal to make scroll lock start at startup? or how can I get ubuntu to recognize it as a key without having to type this all the time? Thanks.

---

