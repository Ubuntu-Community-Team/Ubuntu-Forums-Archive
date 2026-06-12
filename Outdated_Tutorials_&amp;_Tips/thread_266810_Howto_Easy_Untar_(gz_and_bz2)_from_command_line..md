---
title: "Howto: Easy Untar (gz and bz2) from command line."
date: 2006-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by hikaricore on 2006-09-27
So I'm sure some of you are as lazy as I am and can never remember the
flags for using tar to extract source (or whatever else) to it's predefined
directory location.  If it's just me, oh well [SIZE="1"]#$@%[/SIZE] you anyway.  :D

This will be my sad contribution to the Tips and Tricks forums.

From command line:
```
sudo pico /bin/etard
```
[SIZE="1"]^This is my reference to all the kandy kids who spent countless hours lying on the floor with me in dirty random warehouses not so long ago.  <3 Midwest US HHC Ravescene.  R.I.P.[/SIZE]


And here we paste or type:
```

!# /bin/bash
tar -xvzf $*

```
save it (ctrl+o then enter) and exit (ctrl+x)

NEXT

From command line:
```
sudo pico /bin/btard
```

And here we paste or type:
```

!# /bin/bash
tar -xvjf $*

```

If everything went to plan, in command line:
```
whereis etard btard
```

should return this:
[B]etard: /bin/etard
btard: /bin/btard[/B]

....if not, well errmmmm... *slap*

anyway, one last thing before our lazy creations will work.

Command line:
```
sudo chmod ugao+x /bin/etard /bin/btard
```

^Now I'm sure giving everyone who could possibly access your system full access to these execute these two files is probably a really really bad idea, but as I'm very lazy and very trusting, I don't care.

so now you're set to use:

**etard** for _gz_ files
*and*
**btard** for _bz2_ files

from anywhere on your system via command line.  :mrgreen: 

Oh and one more thing I just thought of, since I'm entirely too lazy to type MV (to move) and insist on typing RN (which should be rename but doesn't exist) there's an easy fix if you also suffer this compulsion.

```
sudo ln -s /bin/mv /bin/rn
```

[INDENT]Thank you and goodnight.[/INDENT]


[INDENT][INDENT]--Aaron[/INDENT][/INDENT]

[I][SIZE="1"]all references to canada, cows, billy corgan, polar bears, ect.; living or dead are purely coincidential.  also random fits of confusion, anger, loss of purpose, and/or canada; may be blamed on you...in which case you will be killed in the slowest possible way while watching the sexual organs of any of your close friends be unwillingly fed to large satanic carebears.  all comments dealing with the non-existance of god are to be taken as fact unless otherwise proven by written notice/birth certificate.  you may be castrated in the state of neveda for molesting small children.  throwing lit candles at large bulls may be hazardous to your health, unless of course you are dead....then the proceeding statement is null and void.
[/SIZE][/I]

---

### Post by DDM on 2006-09-28
This could be handy, I'd like to see a script from someone that automatically determines the filetype based on the file's extension. However, sometimes verbose output is a bad thing when extracting archives with many files, like a kernel source. Maybe I'll look into writing one.

---

### Post by hikaricore on 2006-09-28
Eh I could have had it check for file type, but that's not really my style :)

Lazy > Functionallity

---

### Post by skymt on 2006-09-28
I used to have basically this implemented with aliases. Now I use a shell script that checks the file type. It handles around a half-dozen formats. I'd post it, but I'm not at my desktop.

---

### Post by Rui Pais on 2006-10-01
> **hikaricore said:**
> So I'm sure some of you are as lazy as I am and can never remember the
flags for using tar to extract source (or whatever else) to it's predefined
directory location.  If it's just me, oh well [SIZE="1"]#$@%[/SIZE] you anyway.  :D


And I was thinking that ***I*** was the only one with that kind of problems with the tar command :-? 


well i made the basic script called untar: 
(it does minimal file type checking based on extension file name)
```
#!/bin/bash

TYPE="${1:${#1}-3}"

#If it is not a compressed file tar will deal with it!

[[ "${2}" != "" ]] && [[ -e "${2}" ]] && cd "${2}"

[[ ! -e "${1}" ]] && exit 1

case $TYPE in
	[bB]z2)
		echo "bz2 file"
		tar -jxvf "${1}"
		;;
	[tT]ar)
		echo "tar file"
		tar -xpvf "${1}"
		;;
	.[Gg][[Zz])
		echo "gz2 file"
		tar -xpzf "${1}"
		;;
	*)
		echo "Not a compressed File!" 
		;;
esac
exit 0

```

---

