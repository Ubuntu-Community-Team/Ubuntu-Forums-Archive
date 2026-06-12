---
title: "Help me learn basic BASH scripting by posting examples"
date: 2010-03-27
forum: Programming Talk
---

### Post by TheLions on 2010-03-27
i have an bash scripting exam in 2 days in which I will get simple bash scripts and I'll need to tell what are they doing.

You can help me by posting bash oneliners or even longer scripts focused on:

echo
sed
grep
sort
uniq
cat
cut
find
getops
read
chmod
ls
more
less
wc
test
piping
expression expansion ("" '' ``)
input parameters
regular expressions
loops: for, while, until
flow control: if, elif, case

---

### Post by falconindy on 2010-03-27
echo use google

---

### Post by slakkie on 2010-03-27
```

bla=$(wget -O - http://google.com/search?q=bash+manual | grep bash)
echo -e "$bla" | awk '{print $NF}'

```

Enjoy.

---

### Post by TheLions on 2010-03-27
> **slakkie said:**
> ```

bla=$(wget -O - http://google.com/search?q=bash+manual | grep bash)
echo -e "$bla" | awk '{print $NF}'

```

Enjoy.
thanks

```
wget http://www.gnu.org/software/bash/manual/bashref.pdf
```

---

### Post by schauerlich on 2010-03-27
```
echo -e "\x5c\x64\x2e\x24\x6f\x40\x33\x20\x79\x5e\x26\x6f\x75\x40\x72\x20\x6f\x40\x28\x35\x77\x6e\x20\x24\x77\x21\x6f\x23\x72\x25\x6b" | sed 's/[\\\.\$\@3\^\(5\!\#\%\&]//g'
```

---

### Post by TheLions on 2010-03-27
> **schauerlich said:**
> ```
echo -e "\x5c\x64\x2e\x24\x6f\x40\x33\x20\x79\x5e\x26\x6f\x75\x40\x72\x20\x6f\x40\x28\x35\x77\x6e\x20\x24\x77\x21\x6f\x23\x72\x25\x6b" | sed 's/[\\\.\$\@3\^\(5\!\#\%\&]//g'
```

echo prints \d.$o@3 y^&ou@r o@(5wn $w!o#r%k

and sed is searching globaly for eather of this characthers:
(special charathers are escaped with \)
\
.
$
@
3
^
(5
!
#
%
&



and replaces them with nothing, it deletes them

so i get "do your own work"

nice example!

Thanks

---

### Post by schauerlich on 2010-03-27
Explain how the forkbomb [here](http://ubuntuforums.org/announcement.php?f=11) works. (The one with all the colons and parentheses)

---

### Post by red_Marvin on 2010-03-27
You might find the man pages for the commands handy, they are the de facto reference anyway so you might as well get comfortable.
I would also like to point to [http://www.dartmouth.edu/~rc/classes/ksh/ksh-vs-sh.html](http://www.dartmouth.edu/~rc/classes/ksh/ksh-vs-sh.html) I've learned a few tricks from there.
Some scripts for you to dissect, a little more than one line, and perhaps horrible kludges each:

Running a game, mounting the iso first if not already done, and unmounting it afterwards. (bash variables, conditional execution, echo, file existense tests, grep) usage: [COLOR="Navy"]$ hardwar[/COLOR]
```
#!/bin/sh
ISONAME=Hardwar_D1.iso
ISOFOLDER=$HOME/.hardwar
ISOMOUNTPOINT=/media/iso
LOOPDEVICE=/dev/loop0
echo $ISOFOLDER/$ISONAME

if [[ $(mount|grep Hardwar_D1.iso) ]]
then
    echo Hardwar iso already mounted.
else
    echo Hardwar iso not mounted, will now mount
    echo sudo mount $ISOFOLDER/$ISONAME $ISOMOUNTPOINT -o loop=$LOOPDEVICE
    sudo mount $ISOFOLDER/$ISONAME $ISOMOUNTPOINT -o loop=$LOOPDEVICE
    sudo -k
fi
if [[ -d $HOME/.wine/drive_c/Program\ Files/Hardwar ]]
then
    echo Hardwar installed. Running Hardwar.
    wine "c:\Program Files\hardwar\Hardman.exe"
else
    echo Hardwar not installed.
fi
```

Changing the .xinitrc file before starting X if parameter given (bash parameter variables, conditional execution) usage: [COLOR="Navy"]$ sx[/COLOR] or [COLOR="Navy"]$ sx openbox[/COLOR] (if .xinitrc.openbox exists)
```
#!/bin/sh
if [[ -f .xinitrc.$1 ]];then cp .xinitrc.$1 .xinitrc;fi
startx
```
.Xdefaults -> framebuffer console colour codes (for loops, subshells and ...sed) usage: [COLOR="Navy"]$ termcolors[/COLOR]
```
#!/bin/bash
for line in $(sed -n "/color/s/.*\*color\([0-9]\{1,2\}\).*#\([0-9A-Fa-f]\)/P\1 \2/;T;s/P1\([0-9]\)/P\1/;Tf;y/012345/abcdef/;:f;s/\(P.\) \(......\)/\\\e]\1\2/;p" ~/.Xdefaults); do echo -en $line; done; clear
```

Changing the (oss4) volume, master defaust, or a specific channel given as parameter (conditional execution, variable existense test, parameter variables, grep, cut) usage: [COLOR="Navy"]$ vol 10[/COLOR] or [COLOR="Navy"]$ vol pcm5 10[/COLOR]
```
#!/bin/bash
if [[ -z $2 ]]; then
    ossmix vmix0-outvol $1
else
    ossmix $(ossmix|grep $1|cut -d\  -f1) $2
fi

```

Starting the wireless network, trying to connect to different wireless networks in a list depending on signal strength (conditional execution, pipes, grep, egrep, sed, sort, tr, echo, for loops, setting the list delimiter ($IFS)) usage: [COLOR="Navy"]# lucon[/COLOR]
```
#!/bin/bash

echo lucon v.1

known="LU_unsecure_with_web_logon, NETLOGON, LU weblogon, netlogon, Netlogon"

if [[ $(whoami) != "root" ]]; then
        echo Fool! You need to be root to mess with the network settings.
        exit 1
fi
echo privileges ok

if [[ -z $(ifconfig|grep wlan0) ]]; then
        ifconfig wlan0 up
        sleep 10
fi
echo wlan0 up

if [[ -n $(ps aux | grep "dhcpcd wlan0" | grep -v grep) ]]; then
        dhcpcd -k wlan0
fi
echo dhcpcd killed

available=$(
        iwlist wlan0 scan                                                            |\
        egrep "Quality|Encryption|ESSID"                                             | \
        sed -n "N;N;s/.*Quality=\([0-9]\+\).*key:off.*ESSID:\"\(.*\)\".*/\1 \2/;T;p" |  \
        sort -r | sort -uk2 | sort -r | cut -d\  -f2                                 |   \
        egrep "^$(echo $known| sed "s/, /$|^/g")$"                                   |    \
        sed -n "s/^.\+$/&;/;T;p"                                                     |     \
        tr -d "\n"
)

if [[ -z $available ]]; then
        echo No known networks found
        exit 1
else
        IFS=';'
        for essid in $available; do
                echo Trying to connect to $essid
                iwconfig wlan0 essid $essid
                sleep 10
                if $(dhcpcd wlan0); then
                        echo Connected to $essid
                        exit 0
                fi
        done
        echo All attempts unsuccessful
        exit 1
fi
```

Also: _[sed?](http://solstorm.doesntexist.com/files/kiloseconds.txt)_ (...sed)

---

### Post by cariboo on 2010-03-27
This is not really a Cafe thread, moved to Programming Talk

---

### Post by TheLions on 2010-03-27
> **red_Marvin said:**
> ...

Thanks a lot!

---

### Post by TheLions on 2010-03-27
> **schauerlich said:**
> Explain how the forkbomb [here](http://ubuntuforums.org/announcement.php?f=11) works. (The one with all the colons and parentheses)

it is using functions

```
:(){};
``` is a function with name : 
```
:(){: | : &};
```inside function its recursivly calling itself twice and forking process outside terminal

and the last part : after; is running that : function

---

### Post by RabbitWho on 2010-03-27
> **schauerlich said:**
> ```
echo -e "\x5c\x64\x2e\x24\x6f\x40\x33\x20\x79\x5e\x26\x6f\x75\x40\x72\x20\x6f\x40\x28\x35\x77\x6e\x20\x24\x77\x21\x6f\x23\x72\x25\x6b" | sed 's/[\\\.\$\@3\^\(5\!\#\%\&]//g'
```

That's awesome.

---

