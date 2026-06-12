---
title: "Need a BASH code to lookup German words into Internet?"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by honeybear on 2012-12-20
Hi,

I have wordnet for english, but now I need german too

WOuld you have a program for that?

I have for wordnet this one. 

```

#!/bin/sh


if  [  "$1" = ""  ] ; then 
	printf "Enter word to define :> "; read WORD ; elinks "http://wordnetweb.princeton.edu/perl/webwn?s=${WORD}"   | awk ' {  if ( $0 == "References" ) { exit }   ; print $0 } ' | tail -n +9
	exit
fi



WORD="$1"
elinks "http://wordnetweb.princeton.edu/perl/webwn?s=${WORD}"   | awk ' {  if ( $0 == "References" ) { exit }   ; print $0 } ' | tail -n +9


```


I would Need almost the same program for German please.

thanky

---

### Post by audiomick on 2012-12-20
I have no experience at all with that, but it looks like the Universität Tübingen has someting going.

[http://www.sfs.uni-tuebingen.de/lsd/index.shtml]("http://www.sfs.uni-tuebingen.de/lsd/index.shtml")

[https://code.google.com/p/perlapi4germanet/]("https://code.google.com/p/perlapi4germanet/")

Viel Glück damit. ;)

---

