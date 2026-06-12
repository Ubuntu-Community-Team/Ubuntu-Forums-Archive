---
title: "'if' condition to add new PPA always produces a one sided result"
date: 2014-04-28
forum: Programming Talk
---

### Post by octius4u on 2014-04-28
Greetings, 

I trying to write a bash script to add ppas and then run *apt-get update* .
How ever I'd like the new ppa to added only after a list of existing ppa's has been made.
In oder to check if the new ppas are not already installed. 

This first part of code I found a while ago on a ubuntu forum I believe,
and it was very instructional and works properly.
The first part is:
```

ExistingPPAs=$(tempfile)
for APT in `find /etc/apt/ -name *.list`; do
    grep -o "^deb http://ppa.launchpad.net/[a-z0-9\-]\+/[a-z0-9\-]\+" $APT | while read ENTRY ; do
        USER=`echo $ENTRY | cut -d/ -f4`
        PPA=`echo $ENTRY | cut -d/ -f5`
        PPAlink="ppa:$USER/$PPA"
        echo "$PPAlink" >> $ExistingPPAs
    done
done
cat $ExistingPPAs  ## For my own testing purposes to verify content
```

The next part however is the somewhat confusing and a bit frustrating.
Here I am trying to add the new PPA from a list in $MyPPAs, but only if $?, the result from grep is not 0.
The problem is the that if condition finds all results to be 0 even the echo above shows them to be 1.
So basically whether PPAx exists in the tempfile or not all are found to be existing. :confused:
```

for PPAx in $MyPPAs; do
    echo
    echo "Current ppa to be added is: $PPAx"
    sleep 0.5
    #GrepResult=$(grep -oqs $PPAx $ExistingPPAs)  ## I considered using a variable but the produced even more problems.
    grep -oqs $PPAx $ExistingPPAs
    echo "grep sais: $?"           #check the correct respons is given, and it always is correct.
    if [ "$?" == "0" ]; then
            echo "*** $PPAx has been FOUND and will be skipped."
    else 
            echo "*** $PPAx does currently NOT exist."
            add-apt-repository -y $PPAx
    fi
done
apt-get update

```

PLEASE HELP. I have searched for help with if condition inside for do loops but I can't find any solution after hours of trying.

---

### Post by steeldriver on 2014-04-28
Are you not testing the exit status of the echo command, rather than the grep?

```

    grep -oqs $PPAx $ExistingPPAs
[COLOR=#ff0000]**    echo "grep sais: $?" **[/COLOR]          #check the correct respons is given, and it always is correct.
    if [ "$?" == "0" ]; then

```

---

### Post by octius4u on 2014-04-28
Yes indeed! I can't believe I didn't see that for hours. A second set of eyes is great! **THANKS A LOT**. 
I works great now and does what it is supposed to. Thanks again.

---

### Post by steeldriver on 2014-04-28
... it *might* be better to do an integer comparison (rather than a string comparison)

```

    if [ $? -eq 0 ]; then

```

I don't really know for sure, just something to consider. You could also consider just testing the grep directly

```

    if grep -oqs $PPAx $ExistingPPAs; then
      .
      .
      .
    fi

```

---

### Post by octius4u on 2014-04-28
You're right. Checking grep directly seems to be a more direct approach. I tested it and it does work properly.

---

### Post by octius4u on 2014-04-28
If I may ask. What do you think of the following approach I have considered?

```

ExistingPPAs=$(tempfile)
for APT in `find /etc/apt/ -name *.list`; do
    grep -o "^deb [http://ppa.launchpad.net/](http://ppa.launchpad.net/)[a-z0-9\-]\+/[a-z0-9\-]\+" $APT | while read ENTRY ; do
        USER=`echo $ENTRY | cut -d/ -f4`
        PPA=`echo $ENTRY | cut -d/ -f5`
        PPAlink="ppa:$USER/$PPA"
        echo "$PPAlink" >> $ExistingPPAs
    done
done

function addit {
for PPAx in $1; do
    if ! grep -oqs $PPAx $ExistingPPAs; then echo "add-apt-repository $PPAx"; fi
    sleep 0.5
done
}
addit "ppa:noobslab/themes"
addit "ppa:noobslab/icons"
addit "ppa:nilarimogard/webupd8"
addit "ppa:webupd8team/y-ppa-manager"
addit "ppa:webupd8team/themes"
addit "ppa:ubuntu-wine/ppa"
addit "ppa:libreoffice/ppa"
addit "ppa:ehoover/compholio"
addit "ppa:skunk/pepper-flash"
```

These PPA's are just some quick picks a an example.

---

### Post by Vaphell on 2014-04-29
```
USER=`echo $ENTRY | cut -d/ -f4`
```

this line is extremely bad. You've just overwritten a shell variable that is supposed to point to your username. Don't use all caps names for your user variables.

either way, first part done in cleaner way

```
#!/bin/bash

shopt -s globstar

pattern='^deb http://ppa.launchpad.net/[a-z0-9-]+/[a-z0-9-]+'
ExistingPPAs=$( tempfile )

while IFS='/' read _ _ _ user ppa
do 
    echo "ppa:$user/$ppa"
done < <( grep -Eho "$pattern" /etc/apt/**/*.list ) > $ExistingPPAs
```

and your addit function should loop over "$@" not $1 so it's possible to feed more ppas to it at once. Looping over 1 elem doesn't even make sense.

---

### Post by octius4u on 2014-04-30
First, I'm sorry for the delayed response, so THANK YOU for your answer. 
Second, since I'm not familiar with the "*shopt -s globstar*" line, I will try to understand and use your suggestion to improve my script.
Thirdly, the reason for the one liners were the comments I would add next to each ppa such as version (13.10, 14.04, etc) and purpose for adding them. Previously I had all ppas in a single variable.
What I am trying to do is write the script in a way that allows me to easily update ppas and packages to adapt the script to a new version say 14.10, by maybe just exchanging the some variable values.
Vaphell, Thanks again.

---

### Post by Vaphell on 2014-04-30
*shopt -s globstar* enables **. It is a bash feature that matches any sequence of directories, including 0

/etc/apt/[COLOR="#0000FF"]**[/COLOR]/*.list is equivalent to
/etc/apt/*.list +
/etc/apt/*/*.list +
/etc/apt/*/*/*.list +
...
in other words it's a native bash equivalent of recursive *find*.

Either way, if i remember correctly, these PPA list files are stored at most 1 level below, so */etc/apt/*.list /etc/apt/*/*.list* would be enough, assuming no globstar. I would even risk saying that PPAs are exactly 1 level below. Using *find* is a bit of an overkill in such a predictable situation.

> Thirdly, the reason for the one liners were the comments I would add next to each ppa such as version (13.10, 14.04, etc) and purpose for adding them.

No problem with that, but the code didn't indicate that intent and i saw no problem adding support of multiple params in kosher way
```
addit ppa:something/something ppa:something_else/something_else
```
Looping over "$@" is how the support for multiple params is done.


so you want something that supports both
```
addit ppa:x/y
addit ppa:x/y "this is a comment"
```
?

---

### Post by octius4u on 2014-04-30
Then this would be the first part, but cleared up.
```
#!/bin/bash

shopt -s globstar

pattern='^deb http://ppa.launchpad.net/[a-z0-9-]+/[a-z0-9-]+'
ExistingPPAs=$( tempfile )

while IFS='/' read _ _ _ user ppa
do 
    echo "ppa:$user/$ppa"
done < <( grep -Eho "$pattern" /etc/apt/**/*.list ) > $ExistingPPAs
```

At the moment this would have been the old way:
```
function addit {                          # Adds ppa if it doesn't exist.
    for PPAx in $1; do if ! grep -oqs $PPAx $ExistingPPAs; then add-apt-repository -y $PPAx; fi; done
}

addit "ppa:nvbn-rm/ppa"                       # Everpad | 13.10 14.04
addit "ppa:ubuntu-wine/ppa"                   # Wine Team | 13.10 14.04
addit "ppa:libreoffice/ppa"                    # Libreoffice | 13.10 14.04

```

Updated this way. Correct?
```

function addit {                          # Adds ppa if it doesn't exist.
    for PPAx in "$@"; do if ! grep -oqs $PPAx $ExistingPPAs; then add-apt-repository -y $PPAx; fi; done
}

addit "ppa:something/something ppa:something_else/something_else ppa:etc_app/etc_app"
```

---

### Post by Vaphell on 2014-04-30
you are doing it wrong ;) just feed the ppas as nice separate params, without these quotes spanning everything.

```
addit [COLOR="#0000FF"]ppa:something/something[/COLOR] [COLOR="#006400"]ppa:something_else/something_else[/COLOR] [COLOR="#800080"]ppa:etc_app/etc_app[/COLOR] 
```
$1 = ppa:something/something
$2 = ppa:something_else/something_else
$3 = ppa:etc_app/etc_app

"$@" will take them one by one which is what you wanted to achieve with word splitting on single continuous $1. The difference is $@ way is the proper one ;)

---

