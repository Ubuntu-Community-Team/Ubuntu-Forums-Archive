---
title: "Running rar with file-roller"
date: 2005-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by dbrodie on 2005-05-30
Want to run file-roller for rar files but just can't seem to get them to work?

First install the unrar-nonfree package from multiverse (or just unrar but that dosn't support RAR files 3.0)

Then download this file, and then run from the directory it is in:
sudo cp rar.txt /usr/bin/rar
sudo chown root:root /usr/bin/rar
sudo chmod 755 /usr/bin/rar

Note: this could probably be replaced by a bash script, but:
a. it wouldn't make much of a difference
b. I can't stand writing in 15 minutes in bash what takes me 5 in python
c. if there are any more incompatabilities that I don't know about that the script will need to fix then it will be simpler to add them in python
d. if anyone does rewrite it in bash, please do send me a copy

---

### Post by bored2k on 2005-05-30
I've used rars with file-roller countless times. No script.

---

### Post by rider343 on 2005-05-30
File-Roller works whitout script!

---

### Post by dbrodie on 2005-05-30
Well are you guys using rar instead of unrar or unrar-nonfree? That program should have other issues (like expires).

[edit]
Btw, dosn't seem to work here? (which was why I hacked up the script)

---

### Post by Darrena on 2005-05-30
In the OP's defense, while I don't have this issue I have heard others complain that they have problems with unrar so this might be their solution...

---

### Post by bored2k on 2005-05-30
[QUOTE=dbrodie]Well are you guys using rar instead of unrar or unrar-nonfree? That program should have other issues (like expires).

[edit]
Btw, dosn't seem to work here? (which was why I hacked up the script)[/QUOTE]
 I install rar and unrar-nonfree. After that, no problems.

P.S. - I still prefer dealing with .RARs through Crossover Office's Winrar (when I'm not using the right click > extract here or rar e file.rar).

---

### Post by dbrodie on 2005-06-02
Well since you installed the rar package it seems that that is what file-roller uses (and not unrar). But let me quote from the description of rar that:
"This program is shareware and you must register it after 40 days of use."

Which is why I didn't want to install it. Have you been able to use it for more then 40 days without problems?

---

### Post by tzutolin on 2005-06-02
[QUOTE=dbrodie]Well since you installed the rar package it seems that that is what file-roller uses (and not unrar). But let me quote from the description of rar that:
"This program is shareware and you must register it after 40 days of use."

Which is why I didn't want to install it. Have you been able to use it for more then 40 days without problems?[/QUOTE]
 yeah, i'm curious about this, too. :-)

---

### Post by McQuaid on 2005-06-02
How I handled it was install unrar-nonfree, which afaik does not expire.  and then make a sym link in usr/bin called rar pointing to unrar and file-roller stopped failing on rar's after that.  I guess with this setup I can't make rar's in linux but why would I do that.

---

### Post by diego.maniacco on 2008-09-15
> **dbrodie said:**
> 
d. if anyone does rewrite it in bash, please do send me a copy


#! /bin/bash
echo "Post-install of unrar (non-free version) as rar"
sudo rm /usr/bin/rar

cat > ./rar.txt << 'EOF'
#! /usr/bin/python
# Released under Public Domian
# By Daniel Brodie <daniel@brodienet.com>

import sys
import subprocess

newargv = ['unrar']
for i,v in enumerate(sys.argv[1:]):
    if v == '--':
        continue
    else:
        newargv.append(v)
        
subprocess.call(newargv)
EOF

sudo cp ./rar.txt /usr/bin/rar
sudo chown root:root /usr/bin/rar
sudo chmod 755 /usr/bin/rar
sudo rm ./rar.txt

echo "Done!"

---

