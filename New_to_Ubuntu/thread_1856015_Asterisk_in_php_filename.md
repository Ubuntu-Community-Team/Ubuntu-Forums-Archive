---
title: "Asterisk in php filename"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by BigSnooze on 2011-10-07
Hi

Can anyone tell me what the asterisk is for on the end of a filename. EG. filename.php*
I have these on a system I have inherited and don't know what they are for. I have Googled it and found nothing.
Thanks

---

### Post by Azdour on 2011-10-07
Hi,

The asterick usually denotes that the file is marked as executable. If you have inherited this machine it maybe has an alias for the ls command. You can check this in the terminal by entering:

alias ls

---

### Post by BigSnooze on 2011-10-07
Thanks, sorry but what significance does the ls alias have to the php* filename?
The alias for ls is --color=auto

---

### Post by SeijiSensei on 2011-10-07
I'd say someone copied some files poorly.  There's no reason for the asterisk to be there, and Apache isn't likely to recognize .php* as a proper extension for PHP scripts.

---

### Post by Azdour on 2011-10-07
Hi,

By using 'alias ls' I wanted to see if the ls command had the -F parameter. If you run ls with -F it show astericks on executable files. Since your ls alias looks normal I would say that SeijiSensei maybe right.

---

