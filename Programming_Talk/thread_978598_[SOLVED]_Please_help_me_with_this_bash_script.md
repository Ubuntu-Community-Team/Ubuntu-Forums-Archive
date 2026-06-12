---
title: "[SOLVED] Please help me with this bash script"
date: 2008-11-11
forum: Programming Talk
---

### Post by robz0rz on 2008-11-11
Hi all

I have never scirpted in bash, and I just hacked this little script together, but it's spiting out an error at me. Can someone please tell me how to fix it, and maybe how to improve it? Thanks already


```
#!/bin/bash

#function
function setdist {
	cp .abyss/$1.svg scalable/places/start-here.svg
	cp .abyss/$1.32.png 32x32/places/start-here.png
	cp .abyss/$1.24.png 24x24/places/start-here.png
	cp .abyss/$1.22.png 22x22/places/start-here.png
	cp .abyss/$1.16.png 16x16/places/start-here.png
	
	echo "You chose $1"
}


# command line args or chooser
if [ -n "$1" ]
then
  distro=$1
else
  select distro in "fedora" "generic" "gnome" "suse" "ubuntu"
fi

# change distro
case $distro in
  "fedora") setdist "fedora";;
  "generic") setdist "generic";;
  "gnome") setdist "gnome";;
  "suse") setdist "suse";;
  "ubuntu") setdist "ubuntu";;
esac


exit
```

```
[rob@rob-thinkpad:~/.icons/Tangolicious$] ./changedist.sh 
./changedist.sh: line 21: syntax error near unexpected token `fi'
./changedist.sh: line 21: `fi'

```


For those that don't get what this script is about - I'm throwing together my own icon theme, and this script should make it easier to change the affinity of the theme.

---

### Post by dexter on 2008-11-11
The select statement isn't correct, it expects this format:
```

select  item in itemlist
do
    Statements
done

```
(see [http://www.softpanorama.org/Scripting/Shellorama/Control_structures/select_statements.shtml](http://www.softpanorama.org/Scripting/Shellorama/Control_structures/select_statements.shtml))

A quick fix in you case would be the following:
```

select distro in "fedora" "generic" "gnome" "suse" "ubuntu"; do
  break
done

```

It would even be nicer code if you merged the case statement that follows in it.

---

### Post by robz0rz on 2008-11-11
Awesome! Thanks! It works now :) Time to get permissions and stuff so I can get this nice icon theme out there. Thanks a bunch!

---

