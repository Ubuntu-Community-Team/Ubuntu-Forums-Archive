---
title: "installing teamviewer.tar.gz"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by tocal on 2013-03-03
I'm want to practise to install progam in tar.gz format. So I bumped to try install Teamviewer, downloadef Teamviewer 7  here [http://www.teamviewer.com/en/download/dyngate.aspx](http://www.teamviewer.com/en/download/dyngate.aspx) . And did as some tutorial to install other tar.gz program, extracted successfuly but when I run
```
 ./configure
make
make install
```

there were answers
```
tt9@ubuntu:/usr/teamviewer/teamviewer7$ ./configure
bash: ./configure: No such file or directory
tt9@ubuntu:/usr/teamviewer/teamviewer7$ make
make: *** No targets specified and no makefile found.  Stop.
tt9@ubuntu:/usr/teamviewer/teamviewer7$ make install
make: *** No rule to make target `install'.  Stop.
tt9@ubuntu:/usr/teamviewer/teamviewer7$ 
```

in extracted folder there is file *teamviewer* which I can't see it's extention 
```
#!/bin/bash

TV_script_dir="$(dirname "$(readlink -f "$0")")"
"$TV_script_dir/wrapper" wine "c:\Program Files\TeamViewer\Version7\TeamViewer.exe" "$@"

true
```
I'm absolute beginner in Linnux.
Could you help me to understand this case. Or it's need to compile or use directly. Some links would be nice, too.

---

### Post by steeldriver on 2013-03-03
The *./configure - make - make install* method is for compiling programs from source, whereas the thing you downloaded appears to be just a wrapper to run teamviewer under wine

AFAIK there's no actual linux port of teamviewer - see here [http://en.wikipedia.org/wiki/TeamViewer#Linux_port](http://en.wikipedia.org/wiki/TeamViewer#Linux_port)

If you want to practice installing from source, then you will need to find a different program - remember that a tar.gz file is just a compressed archive, the extensions themselves don't tell you anything about what the archive contains.

---

### Post by bro on 2013-03-03
You say you are a beginner in Linux. Beginner or advanced, why install anything from source. There is little to benefit from when you do. And there are plenty of problems you can get when you keep doing it with many programs. Just use the repositories. If it isn't there see if there is a reliable repository that you can add. If it isn't there reconsider. Still want it? Download the .deb file and install.

---

### Post by tocal on 2013-03-07
Thanks for your answers. I installed .deb with no problem. Guess I still to simple mind to thinks about this.

---

