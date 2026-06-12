---
title: "can someone tell me what is wrong with this script"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by cosmoshell on 2008-11-18
im trying to make a sort of a apt-get shortcut so I dont have to type to much crap in.

#!/bin/bash        
          if [ "-i" "$1" ]; then
o="install"
     elif [ "-r" "$1" ]; then
o="remove"
else
$0 o="help"
fi
read name
sudo apt-get $o $name

---

### Post by Melindrea on 2008-11-18
I may be missing something (bash isn't my strong point in programming) but there doesn't seem to be any comparison?

Am I understanding you correctly that you want to call, for instance:

sudo apt-get -i skype to install skype and
sudo apt-get -r skype to remove skype?

Then you'd probably need to do a "-i" = "$1" in the first and "-r" = "$1" in the second bit.

---

### Post by cosmoshell on 2008-11-19
thanks your suggestion worked.

---

### Post by kerry_s on 2008-11-19
> **cosmoshell said:**
> im trying to make a sort of a apt-get shortcut so I dont have to type to much crap in.

#!/bin/bash        
          if [ "-i" "$1" ]; then
o="install"
     elif [ "-r" "$1" ]; then
o="remove"
else
$0 o="help"
fi
read name
sudo apt-get $o $name

that's what alias's are for.
if i want to search i type> s name
if i want to install i type> i name
etc...

gedit ~/.bashrc
(you can put them in there or in .bash_aliases, but you'll have to uncomment the line in .bashrc)

i only use a few:

```
alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get --purge remove'
alias upd='sudo apt-get update;sudo apt-get upgrade;sudo apt-get clean;echo All done!'
alias mc='deco'

```

---

