---
title: "sudo -u #uid"
date: 2007-08-06
forum: Programming Talk
---

### Post by chandra on 2007-08-06
Folks,

I wish to invoke sudo with the -u option and want to use the UID rather than the username. The man page says (among other things):

sudo [-u username|#uid]

However, when I invoke sudo with, say UID 1000, as:

sudo -u 1000 <some command>

I get

sudo: no passwd entry for 1000!

If I try

sudo -u #1000 <some command>

I only get the help text.

Can anyone shed some light on this behaviour and help out, please?

Thank you.

---

### Post by nitro_n2o on 2007-08-06
you need to add youself to /etc/sudoers to edit the file 
```
sudo visudo
```
unfortunately I don't know what should u enter in that file exactly

---

### Post by kpatz on 2007-08-06
> **chandra said:**
> Folks,

I wish to invoke sudo with the -u option and want to use the UID rather than the username. The man page says (among other things):

sudo [-u username|#uid]

However, when I invoke sudo with, say UID 1000, as:

sudo -u 1000 <some command>

I get

sudo: no passwd entry for 1000!

If I try

sudo -u #1000 <some command>

I only get the help text.

Can anyone shed some light on this behaviour and help out, please?

Thank you.The shell treats # as a comment delimiter, so you'll need to escape it or put it inside quotes.

Any of these will work:

sudo -u \#1000 <some command>
sudo -u '#1000' <some command>
sudo -u "#1000" <some command>

---

### Post by chandra on 2007-08-19
> The shell treats # as a comment delimiter, so you'll need to escape it or put it inside quotes.

Any of these will work:

sudo -u \#1000 <some command>
sudo -u '#1000' <some command>
sudo -u "#1000" <some command>

Thanks.  That did the trick :-)

---

