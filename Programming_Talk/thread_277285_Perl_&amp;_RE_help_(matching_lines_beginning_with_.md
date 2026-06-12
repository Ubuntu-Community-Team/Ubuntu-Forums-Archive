---
title: "Perl &amp; RE help (matching lines beginning with spaces...)"
date: 2006-10-14
forum: Programming Talk
---

### Post by enigma_0Z on 2006-10-14
I'm writing a script in perl, but for some reason it doesn't seem to be matching spaces at the beginning of lines... here's the RE I'm using (I just want to match 1 or more spaces at the beginning of lines and delete them)

s/^ +//g

That is right, isn't it? Thanks.

---

### Post by Houman on 2006-10-14
Hi there, 
to specify whitespaces you have to use \s, try this:

s/^\s+//g;

although this will remove all whitespaces
also if your string is multiline (you slurped the text for example) I think you gotta use the m modifier as well as g (i think):

s/^\s+//gm;

regards 

Houman

---

