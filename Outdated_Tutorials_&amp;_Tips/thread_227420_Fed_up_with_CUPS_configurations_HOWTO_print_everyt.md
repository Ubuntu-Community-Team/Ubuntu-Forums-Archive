---
title: "Fed up with CUPS configurations? HOWTO print everything (ps)"
date: 2006-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by pau on 2006-08-01
I was a bit fed up of trying to configure the printers everytime I am working in a different institute (which happens often), so that I wrote this small script to print a ps file if you have the server name... enjoy (you could also add more options, like convert to ps if it's not a ps but I let you that). You can change the shell you're using... mine is zsh, and don't forget to chmod u+x print2hostname.sh

```
#!/usr/bin/env zsh

# print2hostname.sh
# Copyright Pau Amaro-Seoane, license GPL
# http://www.fsf.org/licensing/licenses/gpl.txt


tty -s && stdin_is_human=1
tty -s <&1 && stdout_is_human=1

clear ;

print "The document must be a ps";

print "";

echo -n "What's the name of the server (blabla.institute.bloblo.edu)?  ";

read Servidor ;

print "";

echo -n "What's the ps file you want to print (give me the path too if it's not here)?  ";

read Fitxer ;

cat ./$Fitxer | telnet $Servidor 9100 ;

clear ;

print "The file $Fitxer is being printed on $Servidor"
```

---

