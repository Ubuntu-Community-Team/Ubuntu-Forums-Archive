---
title: "Need to undo sed command.. medibuntu related."
date: 2008-04-09
forum: Programming Talk
---

### Post by esc1 on 2008-04-09
Programming hurts my brain.. and I'm gonna take the easy road and asks someone how to undo the following..

sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

The above takes the non free components out but I want to enable them now.

I have feisty. If I just run this again..

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

will I have access to the non free components?  I'm such a noob.

---

### Post by ghostdog74 on 2008-04-09
make a copy of the file first before changing anything in future. when you need it back, just rename the original.

---

### Post by nanotube on 2008-04-10
> **esc1 said:**
> 
I have feisty. If I just run this again..

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

will I have access to the non free components?  I'm such a noob.

yes you will - that command gets a fresh copy of the medibuntu.list off the medibuntu webserver.

but ghostdog gives good advice - back up your files before you play with them, it's good practice. :)

---

### Post by buried on 2008-04-10
Wow it's already answered, although I was gonna :P

---

