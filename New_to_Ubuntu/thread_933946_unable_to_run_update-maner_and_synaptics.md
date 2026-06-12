---
title: "unable to run update-maner and synaptics"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by jjanolo1 on 2008-09-30
"I can't run update manager and synaptics. I added this repository "http://packages.medibuntu....org" and all of a sudden I get this--see below

I get this error

'E:Type '' is not known on line 47 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


Any help would be great. Newbee here.

---

### Post by IusedTObeSOMEONEelse on 2008-09-30
try
```
sudo apt-get -f install
sudo dpkg --configure -a
```
I do believe we may need to see your sources list as I believe you have some thing wrong in it

---

### Post by jemate18 on 2008-09-30
you might have entered a new repos in the sources.list which is erroneous....

Maybe post your sources.list so we could see where did the error came...

---

