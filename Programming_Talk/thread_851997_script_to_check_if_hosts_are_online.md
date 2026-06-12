---
title: "script to check if hosts are online"
date: 2008-07-07
forum: Programming Talk
---

### Post by gurth4ng on 2008-07-07
Hello. I feel kinda rusty when it comes to shell scripts so i could use some help :)

I am trying to write a script that will ping a few hosts, and then tell me if they are online or not. I'm mostly doing it for the general know-how, so i can use it later in a more serious script. So, here's what i've got so far:
```
#!/bin/bash
HOSTS="192.168.2.2 192.168.2.3 192.168.2.4 192.168.2.6 192.168.2.7"

COUNT=4

for myHost in $HOSTS
do
	count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{print $2}' | awk '{print $1}')
	if $count
		then echo "Hosts down"
		else echo "Host up!"
	fi
done
```

now, when i run it (after giving it permitions ofc), i get the following error:
```
./check: line 9: 0: command not found
```

any ideas?

---

### Post by ghostdog74 on 2008-07-07
> **gurth4ng said:**
> Hello. I feel kinda rusty when it comes to shell scripts so i could use some help :)

I am trying to write a script that will ping a few hosts, and then tell me if they are online or not. I'm mostly doing it for the general know-how, so i can use it later in a more serious script. So, here's what i've got so far:
```
#!/bin/bash
HOSTS="192.168.2.2 192.168.2.3 192.168.2.4 192.168.2.6 192.168.2.7"

COUNT=4

for myHost in $HOSTS
do
	count=$(ping -c $COUNT $myHost | grep 'received' | awk -F',' '{print $2}' | awk '{print $1}')
	if $count
		then echo "Hosts down"
		else echo "Host up!"
	fi
done
```

now, when i run it (after giving it permitions ofc), i get the following error:
```
./check: line 9: 0: command not found
```

any ideas?

piping too much awk makes your code awk-ward. also, if you use awk, there's no need to use grep. also for your case, checking for return status may suffice. something like this
```

...
for myHost in $HOSTS
do
	result=$(ping -c $COUNT $myHost)
	if [ $result -ne 0 ];then
		then echo "Hosts down"
		else echo "Host up!"
	fi
done

```

---

### Post by weresheep on 2008-07-07
Hello,

The format for an if statement in Bash is

```

if [ expr ]
then
fi

```

so I would think you'd want something like...

```

if [ "$count" -gt 0 ]

```

I realise you're doing this for learning, but for completeness there is a simplier approach using the exit status of ping. The ping man page states that ping returns 1 if no replies are recived. So you could simplfy your script loop to something like...

```

ping -c 1 "$myHost" > /dev/null

if [ "$?" -eq 0 ] ; then
    echo "Hosts up"
else
    echo "Host down"
fi

```

Hope that helps.

-weresheep

---

### Post by geirha on 2008-07-07
As a one-liner:

```

for host in 192.168.2.{2,3,4,6,7}; do ping -c2 $host >/dev/null && echo $host is up || echo $host is down; done
```

---

### Post by gurth4ng on 2008-07-09
thx a lot everyone, you've been very helpful :)

---

### Post by dtmilano on 2008-07-09
You can also use this
```

s=(UP DOWN); for h in 192.168.2.{2,3,4,6,7}; do ping -nqc 3 $h >/dev/null; echo "$h is ${s[$?]}"; done

```

---

### Post by n~kf)}BW% on 2010-11-21
Hi! Here is link to script that uses ping and also one that uses nmap (multithreaded - faster). :popcorn:

[http://360percents.com/posts/bash-script-for-checking-online-hosts-in-domain/](http://360percents.com/posts/bash-script-for-checking-online-hosts-in-domain/)

Best regards

---

### Post by s.fox on 2010-11-22
[IMG]http://serial-coder.co.uk/blog/wp-content/uploads/2010/11/threadNecromancy.jpg[/IMG]

Closed.

---

