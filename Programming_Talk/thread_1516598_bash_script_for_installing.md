---
title: "bash script for installing"
date: 2010-06-23
forum: Programming Talk
---

### Post by lun on 2010-06-23
I am messing around with bash and have written a script for installing virtualbox (inb4 use apt-get).  For some reason the script will not accept -3.2 in virtualbox-3.2, the font changes color and the script lags when executed at that point (it will print up to 4).  I do not think that - is a special character, but if it is, i do not know how to make it not.  I am pretty sure the script is fine otherwise.  I am noob.

```
#!/bin/bash

echo "Would you like to install VirtualBox (PUEL)? [y|n]"
read vb

if [ "$vb" = 'n' ] || [ "$vb" = 'N' ]; then
        echo "Exiting."
        exit 0
elif [ -z "$vb" ] || [ "$vb" = 'y' ] || [ "$vb" = 'Y' ]; then
        echo "* Installing VirtualBox..." && echo "VirtualBox" >> README
        echo "deb http://download.virtualbox.org/virtualbox/debian lucid non-free" >> /etc/apt/sources.list
                echo "1"        
        wget -o /dev/null -O oracle_vbox.asc http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc
                echo "2"
        apt-key add oracle_vbox.asc && rm oracle_vbox.asc > /dev/null
                echo "3"
        aptitude update > /dev/null
        aptitude -y safe-upgrade > /dev/null
                echo "4"
        aptitude -y install dkms virtualbox**-3.2** > /dev/null
                echo "5"
        aptitude -y -f install > /dev/null
        echo "VirtualBox installed."
fi

exit 0

```

Any suggestions?  Probably has a simple answer.

Thanks,
Nick

--I think that - followed by a number invokes some kind of math something.  If i try something like gnome-core, the -core does not change color like it does if i try gnome-1 (becomes red in vim).

---

### Post by lun on 2010-06-24
Thanks for all the replies.  Issue was not in the -3.2 as originally thought.  Instead, i was missing a > between wget -o > /dev/null.  The script should work thusly:

```
#!/bin/bash

echo "Would you like to install VirtualBox (PUEL)? [y|n]"
read vb

if [ "$vb" = 'n' ] || [ "$vb" = 'N' ]; then
        echo "Exiting."
        exit 0
elif [ -z "$vb" ] || [ "$vb" = 'y' ] || [ "$vb" = 'Y' ]; then
        echo "* Installing VirtualBox..." && echo "VirtualBox" >> README
        echo "deb http://download.virtualbox.org/virtualbox/debian lucid non-free" >> /etc/apt/sources.list
       ** wget -o > /dev/null** -O oracle_vbox.asc http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc
        apt-key add oracle_vbox.asc && rm oracle_vbox.asc > /dev/null
        aptitude update > /dev/null
        aptitude -y safe-upgrade > /dev/null
        aptitude -y install dkms virtualbox-3.2 > /dev/null
        aptitude -y -f install > /dev/null
        echo "VirtualBox installed."
fi

exit 0

```

Script modified from [**[COLOR="Blue"]ubuntu-minimal[/COLOR]**]("http://www.cs.uml.edu/~aveilleu/projects/ubuntu-minimal/")

It is a nice script for a minimal install.
Nick:popcorn:

---

### Post by geirha on 2010-06-24
That "fix" will leave a file named "-O" containing wget's log in the current dir (cat ./-O). The previous wget line was correct, though pointless. You can just use -q to achieve the same.
```
wget -q -O oracle_vbox.asc http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc
```

Usually though, you have wget output the public key to stdout and pipe it to apt-key, which you tell to read the key from stdin.
```
wget -q -O- http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc | apt-key add -
```

Also, I recommend putting third-party repositories in separate files.
```
echo 'deb http://download.virtualbox.org/virtualbox/debian lucid non-free' > /etc/apt/sources.list.d/virtualbox.list
```
Makes them easier to disable later; just change the extension.

Lastly, don't use the [ command in bash-scripts, use the more powerful [[ keyword for string comparisons; it accepts globs too. E.g.
```
if [[ $vb = [Nn] ]]; then ...
```
[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by juancarlospaco on 2010-06-24
> **geirha said:**
> 
Also, I recommend putting third-party repositories in separate files.
```
echo 'deb http://download.virtualbox.org/virtualbox/debian lucid non-free' > /etc/apt/sources.list.d/virtualbox.list
```


Also, I recommend:

```
echo 'deb http://download.virtualbox.org/virtualbox/debian **`lsb_release -cs`** non-free' > /etc/apt/sources.list.d/virtualbox.list
```

*Makes it Release independent, works for all releases.*

---

