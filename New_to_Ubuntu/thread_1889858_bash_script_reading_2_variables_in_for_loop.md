---
title: "bash script reading 2 variables in for loop"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by chomezski on 2011-12-02
hi guys - was wondering if anyone can help me

my goal is to write a script that SCPs files to different IPs based on the info from a file "version2";

example of info from version2:

J9088A 2610-48, R.11.54, R.10.06 | 10.19.128.91
J9137A 2520-8-PoE, S.14.30, S.14.03 | 10.19.128.92

i'm having trouble inserting 2 variables in the for loop - 1 to take the 'type' from each verse and 1 to take the 'ip'

this is what i have so far:

#!/bin/bash

type=$(awk '{print $1}' version2)
ip=$(awk '{print $6}' version2)

for a in $type; do
    if [[ $a == *J9088A* ]]; then
       scp /home/Procurve/2610/primary scripts@$ip:/os/primary
       ??send password?
    elif [[ $a == *J9137A* ]]; then
       scp /home/Procurve/2520/primary scripts@$ip:/os/primary
       ?send password?
    fi
done


i also still need to fit in the password somehow... i think i'm a bit over my head - but can anyone help me???

---

### Post by Lars Noodén on 2011-12-02
Use keys and a key agent to manage authentication.  That way you only have to enter the password once.

---

### Post by chomezski on 2011-12-02
thanks lars - but i first need to find out how to tie in the $ip variable

---

### Post by surfer on 2011-12-02
expect might help.

here's a thread about it:
[http://ubuntuforums.org/showthread.php?t=192929](http://ubuntuforums.org/showthread.php?t=192929)

---

### Post by chomezski on 2011-12-02
hi surfer - thanks! 

i am planning on using an expect script to actually perform the scp file transfer but my main problem is still using 2 variables in the for loop (maybe i am using the wrong kind of loop??)

i need both the IP and the TYPE variables

i have the iplist and the type variables in 2 files but i still can't seem to tie them in together

i'm imagining the bash script like this...

#!/bin/bash

for type in $(version); do
if [[ $type == *J9088A* ]]; then
    ??ip=$(iplist)?? <<???
    scpscript.exp /home/ProcurveFirmware/2610/primary $ip
elif [[ $a == *J9137A* ]]; then
    ??ip=$(iplist)?? <<???
    scpscriptip.exp /home/ProcurveFirmware/2520/primary $ip
fi
done

---

### Post by surfer on 2011-12-02
are you restricted to using bash? it can certainly be done in bash but it would hurt a lot less if you used a higher level language.

personally, i'd do it in python; there's even a python-expect module.

---

### Post by Lisiano on 2011-12-02
```
#!/bin/bash
old_IFS=$IFS
IFS=$'\n'
for line in $(cat version2); do
if [[ $line == J9088A* ]]; then
scp /home/Procurve/2610/primary scripts@$(echo $line | cut -f6 '-d '):/os/primary
elif [[ $line == J9137A* ]]; then
scp /home/Procurve/2520/primary scripts@$(echo $line | cut -f6 '-d '):/os/primary
fi
done
IFS=$old_IFS
```
I understand you wish to send only certain files to certain hosts, host based on the 6th field and the folder based on the 2nd minus the "-*". This snippet will be a lot better if you wish to do this with more hosts.
```
#!/bin/bash
old_IFS=$IFS
IFS=$'\n'
for line in $(cat version2); do
scp /home/Procurve/$(echo $line | cut -f1 '-d ' | cut -f1 '-d-')/primary scripts@$(echo $line | cut -f6 '-d '):/os/primary
done
IFS=$old_IFS
```
In both cases we change IFS so that the for loop will work on lines instead of fields, cut doesn't care about IFS since we tell it our own separator. Later if you wish to use awk or anything that relies on IFS, you'll have to restore it, otherwise you can just drop both instances of old_IFS which will result in even less code
```
#!/bin/bash
IFS=$'\n'
for line in $(cat version2); do
scp /home/Procurve/$(echo $line | cut -f1 '-d ' | cut -f1 '-d-')/primary scripts@$(echo $line | cut -f6 '-d '):/os/primary
done
```

---

