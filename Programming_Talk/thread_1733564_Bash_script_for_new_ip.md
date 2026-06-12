---
title: "Bash script for new ip"
date: 2011-04-19
forum: Programming Talk
---

### Post by Evilware on 2011-04-19
what am i missing here

#####################
#!/bin/bash

NETWORK="192.168.3."
START="10"
END="30"
PAUSE="2"
MISSED="0"
PATH=/bin/:usr/bin:/sbin:/usr/sbin:/usr/local/sbin

####Start Script

#take the start ip, make sure its less than end ip else add one
for (($START < $END; $START+=1))
#for ((n=10 ; n <= 100 ; n++ ))
        do
        $NETWORK$START
                if ping -c 1 -w 1 $NETWORK > /dev/null;
        then
                echo "${$NETWORK$START} is in use"
        else
        if ! ping -c 1 -w 1 $NETWORK$START > /dev/null;
                then
                ((MISSED++)
if [$MISSED -eq 1]; then
        sudo /sbin/ipfconfig eth0:1 $NETWORK$START

fi
fi

done







~
~

---

### Post by gmargo on 2011-04-19
> **Evilware said:**
> what am i missing here

You are missing a description of what the script is supposed to do, what you are observing, and why you think that result is wrong.

> 
```

#####################
#!/bin/bash

```Probably the main problem, since your script requires bash.

The #!/bin/bash MUST be the first line; you cannot have a comment line above it.  Therefore, your script is being interpreted as a /bin/sh (or **dash(1)**) script.

Remove that first line of hash marks, and all or most of your problems will go away.



> 
```

for (($START < $END; $START+=1))

```This for statement is not valid even in bash.
a. **dash(1)** does not support this type of the **for** statement.
b. **bash(1)** requires three expressions in the **for** - you have only two, and the second is invalid.

Try this instead:
```

for (( ; $START < $END ; START += 1))

```> 
```

((MISSED++)

```presumably a typo.

> 
```

if [$MISSED -eq 1]; then

```You initialised $MISSED outside of the loop, so only the first miss will trigger.

---

### Post by Evilware on 2011-04-19
the whole point of this script is to ping a class c network, find the first available non pinagable address, and assign the adapter alias that address

still getting a loop error

---------begin--------


!/bin/bash

NETWORK="192.168.3."
START="10"
END="30"
PAUSE="2"
MISSED=0
PATH=/bin/:usr/bin:/sbin:/usr/sbin:/usr/local/sbin

####Start Script

#take the start ip, make sure its less than end ip else add one
for (( ; $START < $END ; START += 1))
do
$NETWORK$START
if ping -c 1 -w 1 $NETWORK > /dev/null;
then
echo "${$NETWORK$START} is in use"
else
if ! ping -c 1 -w 1 $NETWORK$START > /dev/null;
then
        MISSED=+1
fi
if [$MISSED -eq 1]; then
sudo /sbin/ipfconfig eth0:1 $NETWORK$START

fi
fi

done

---

### Post by Fire_Chief on 2011-04-19
> sudo /sbin/ipfconfig eth0:1 $NETWORK$START

The command is ifconfig to bring up an interface. You need to remove the p.

> if ping -c 1 -w 1 $NETWORK > /dev/null;
Also, it appears your first ping command is only pinging the first 3 octets? (unless I'm reading it wrong).
Maybe should be "if ping -c 1 -w 1 $NETWORK$START > /dev/null;" ?

:)

---

### Post by Vaphell on 2011-04-19
```
if [$MISSED -eq 1]
``` will fail

you need to separate [ and ] from parameters
```
if [ $MISSED -eq 1 ]
```

---

### Post by Evilware on 2011-04-20
Actually, I was making this far more difficult than I thought
the issue is, I'm used to RHEL and RHEL based distros.  for Ubuntu shell is handled differently, even as root.
sudo bash ./yourscriptname

I ended up getting the script working, which is great for the LTSP folks who find themselves needing to assign ip addresses to multiple networks on the same LAN who may not have the hardware needed to either install dozen nics, dedicate a dhcp server, or just want a nice fall back should the DHCP service not be available.

---

