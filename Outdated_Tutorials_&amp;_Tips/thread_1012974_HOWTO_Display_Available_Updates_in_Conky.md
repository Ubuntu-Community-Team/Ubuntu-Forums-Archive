---
title: "HOWTO: Display Available Updates in Conky"
date: 2008-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by plb on 2008-12-16
I've written this script for Debian but Ubuntu should work just the same provided the user in question is able to gain root access via sudo without a password. Simply save the code as debupdates.sh in your ~/bin and mark it executable. Here is the code:

> #!/bin/bash
# Conky script for displaying available updates
# in Debian. This script assumes you are in the
# sudo group and require no password for root
# access. Add something as such to your conkyrc:
#${color}APT: ${color D7D3C5}${execi 28800 ~/bin/debupdates.sh}

sudo apt-get -qy update > /dev/null
NUMOFUPDATES=$(sudo aptitude search "~U" | wc -l)
echo $NUMOFUPDATES Updates Available


Next, simply add something like such to your conkyrc:

> $color}APT: ${color D7D3C5}${execi 28800 ~/bin/debupdates.sh} 

Here is a screenshot of the output:

---

### Post by tomski on 2010-01-26
dude i have been looking everywhere for something like this
nice share cheers!!

---

### Post by notbad on 2010-02-08
yeah, thanks, man!!!

---

