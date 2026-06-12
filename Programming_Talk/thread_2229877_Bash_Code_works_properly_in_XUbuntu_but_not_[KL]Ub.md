---
title: "Bash Code works properly in XUbuntu but not [K/L]Ubuntu (VM)"
date: 2014-06-15
forum: Programming Talk
---

### Post by octius4u on 2014-06-15
Greetings,

I've got a (for me) unusual problem, and I'm hoping someone kind enough could offer some clarification.

I have got some bash code that works fine under 
XUbuntu 14.04 (Core i7 + 8gb RAM)(GNU bash, version 4.3.11(1)-release (x86_64-pc-linux-gnu)) 
**but fails in the VirtualBox Machines **
Kubuntu 14.04 (GNU bash, version 4.3.8(1)-release (x86_64-pc-linux-gnu)) or 
Lubuntu 14.04 (GNU bash, version 4.3.8(1)-release (i686-pc-linux-gnu)).
```

PartnerRepo=$(grep -x deb\ http://archive.canonical.com/ubuntu\ trusty\ partner /etc/apt/sources.list)

if [ $(id -u) == 0 ]; then                                                      # If Root, install
    if ! [ "$PartnerRepo" == "deb http://archive.canonical.com/ubuntu trusty partner" ]; then
        echo -e "\n$CommentColor       **$ColRESET Now enabling Canonical's 'partner' repository. "; sleep 3
        sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list
        sed -i "/^# deb-scr .*partner/ s/^# //" /etc/apt/sources.list
        apt-get update
    fi
fi

```

Recently I have learned to use error traps, and have found them to be very useful. Oddly enough in this case I do not get a error message but I know these lines to be at fault because if I comment them out the script does not stop abruptly. The "sed" lines have been copied from a forum because I do not yet understand the use of SED.

I am hoping somebody could explain what I can do to correct the problem. Thank you all for your help.

---

### Post by octius4u on 2014-06-15
Basically, all I wish to accomplish is to check if the canonical partner repository in not present and in that case to remove the # form the "# deb".

---

### Post by ofnuts on 2014-06-15
Did you check that the script is really executed by Bash, and not by whatever /bin/sh would point to?

---

### Post by octius4u on 2014-06-15
Well I'm testing the script by running it like this:

sudo bash MyScript.sh, that is when I wish it to have root previleges, otherwhise just bash MyScript.sh.
The script is written to respond correspondingly if the id -u is not 0 for root.
The shebang is #!/bin/bash.

---

### Post by octius4u on 2014-06-15
An additional thought would be, the application of a different method to accomplish the same thing.
I mean to add the partner repository. I don't know how the syntax of different bash versions has changed 
but may be there is different method that is more compatible on older bash versions.

---

### Post by octius4u on 2014-06-15
Upon further trial and error I found that it's not the error trap that causes the the script to exit but the "set -e" command.
I noticed that if I comment out the "set -e" command the above code does work properly and ads the repository.
I hope somebody understands why this is happening because I would like to keep use the set -e command.

---

### Post by octius4u on 2014-06-15
I am still puzzled about why it worked on one system but not on an other, however the following modification seems to have solved the issue.
```

if ! [ "$(grep -x deb\ http://archive.canonical.com/ubuntu\ trusty\ partner /etc/apt/sources.list)" == "deb http://archive.canonical.com/ubuntu trusty partner" ]; then
        echo -e "\n$CommentColor       **$ColRESET Now enabling Canonical's 'partner' repository. "; sleep 3
        sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list
        apt-get update
fi

```

---

### Post by ofnuts on 2014-06-16
Then your problem is that some command has a non-zero return code that you don't expect, either because its behavior is different (different version installed) or because the environment is different (so it doesn't find a file or else). "set -e" is a double-edged sword.

---

### Post by octius4u on 2014-06-16
I have verified the code in all VM's and it works properly. :D
Thanks.

---

