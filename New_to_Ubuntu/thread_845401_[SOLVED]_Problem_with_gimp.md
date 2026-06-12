---
title: "[SOLVED] Problem with gimp"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by honkey on 2008-06-30
Gimp dosent run after clicking on the gimp symbol in the applications menu

---

### Post by Inxsible on 2008-06-30
wow...you sure are having problems today. I see 4 of your thread on page 1 alone !!

Does it give you any errors? if yes, what ?

---

### Post by billgoldberg on 2008-06-30
> **honkey said:**
> Gimp dosent run after clicking on the gimp symbol in the applications menu

Try opening a terminal and type in "gimp" (and press enter).

See if there are any errors given by the terminal.

If so copy/paste them.

--

This can most likely also be fixed by **completely removing** it in synaptic packager and then reinstalling it.

-- 

This error should not happen by itself, changes are you did something to mess it up.

---

### Post by bumanie on 2008-06-30
Go to synaptic, type gimp in search and check for the box for reinstallation. See if that works.

---

### Post by honkey on 2008-07-01
i've startet gimp in terminal and it were installed new

tanx for this tipp

---

### Post by honkey on 2008-07-01
run in terminal:
honk@monk:~$ gimp
/usr/local/lib/gimp/2.0/plug-ins/print: error while loading shared libraries: libgimpprint.so.1: cannot open shared object file: No such file or directory

(gimp:13917): LibGimpBase-WARNING **: gimp: wire_read(): error
honk@monk:~$ 

Cannot open in app menu

---

### Post by nowshining on 2008-07-01
in synaptic look for something close to or called libgimpprint and install it - it should work now. If u see it installed - try re-installing it.

---

### Post by honkey on 2008-07-13
thanks

---

### Post by nowshining on 2008-07-13
ur welcome. :)

---

