---
title: "Download script"
date: 2006-06-07
forum: Programming Talk
---

### Post by Damnation667 on 2006-06-07
Hi

Say I don't want to use Atomatix or any of those apps. I want to write a script to download certain codecs and software etc. I'm fairly new to Linux. Could I just put in the script the normal commands I would use to download those things through the console, for example: sudo apt-get blah blah.

And how will the commands be executed? Say I have the following:

sudo apt-get blah1 blah2
sudo apt get blah 3 blah4

Will those commands be executed after each other or should I put in some kind of pause?

Pointing me in the direction of a tutorial would also work.

Regards

---

### Post by Gustav on 2006-06-07
Look at this for a tutorial [http://www.pegasus.rutgers.edu/~elflord/unix/bash-tute.html](http://www.pegasus.rutgers.edu/~elflord/unix/bash-tute.html)

(I haven't read it myself so I don't know how good it is)

---

### Post by Damnation667 on 2006-06-07
Read through it. Didn't help much though. Thx anyway.

I'll keep googling.

Any suggestions welcome

Regards

---

### Post by simplyw00x on 2006-06-07
If you create a bash script (see the utorial Gustav posted) in the basic form:
```
#!/bin/bash
command1
command2
```
then save it as something (e.g. foo.sh - can be any extension) and
```
chmod +x foo.sh
```
and
```
./foo.sh
```
it is the equivalent of typing
```
command1 <enter>
....<wait for command1 to finish>
command2 <enter>
....<wait for command1 to finish>
```

I don't see why you'd use seperate apt-get install lines though. If you want to install 2 packages, just do:
```
sudo apt-get install package1 package2
```

---

