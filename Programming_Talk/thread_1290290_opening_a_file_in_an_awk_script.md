---
title: "opening a file in an awk script"
date: 2009-10-13
forum: Programming Talk
---

### Post by benj1 on 2009-10-13
just messing around abit with awk, and there doesnt seem to be a straight forward way of opening a file hardcoded within an awk script

if you use an awk script then you have to supply the file as an argument or use getline to load a file then loop over it by hand (which seems to me to be distinctly un-awkish)

yes you can make it a shell script so you can do awk'*foo bar do stuff*' file. but thats just a bit of a kludgy workaround

ive tried BEGIN{FILENAME="file"}
but that doesnt work

are these the only ways, or am i missing something very obvious? it seems like a major oversight if it is the only way.

---

### Post by DaithiF on 2009-10-13
umm, maybe i've misunderstood you, but an awk script is a set of instructions that you pass to the awk command when operating on a file, so:
```
awk -f script.awk somefile

```
I don't know why you would want to hardcode a particular file into the script itself.

---

### Post by benj1 on 2009-10-13
thanks DaithiF, awk is actually an entire scripting language in its own right, very good for text processing, this is the script for working out whats been install/removed from the base install,its quite good, mainly because you dont need to define the main loop for going through the lines in the file, its also smaller than a python file (my equivalent python script is 24 lines v 14 lines for this) and (for the speed freaks) runs twice as fast.
as you can see, the only file i would need to use is /var/log/dpkg.log so i dont really want to pass it as an option
```

#! /bin/sh                                                               
awk '                                                                   
$3 ~ /remove/ {                                                  
    if ($4 in install) {delete install[$4]}                         
    else {remove[$4]=$4}                      
}                                                                               
$3 ~ /install/{                                                  
    if ($4 in remove){delete remove[$4]}                        
    else {install[$4]=$4}                                               
}                                                                                                                              
END {   
    print "installed apps\n--------------"; for (entry in install){print entry}  
    print "removed apps\n------------"; for (entry in remove){print entry}                                                     
}'  /var/log/dpkg.log


```
you can write it as an awk script ie

```

#! /usr/bin/awk

foobar etc etc

```
doing it that way theres no way of hardcoding the file(/var/log/dpkg.log), you need to pass the file as a command line argument, or use getline and then manually loop over the lines, which to me doesnt seem very awkish(as you can see with the full script you don't need to define a loop at all), the only other way is

```

#! /bin/sh
awk'
foobar etc etc
' file.txt

```
which is what im doing but isn't the most elegant solution.
it just suprises me that there doesnt seem to be a better way to do it

---

### Post by ghostdog74 on 2009-10-13
i am a bit confused about what you actually want to do. Ways to "open" a file in awk
```

1) awk -f test.awk <file>
2) awk '{print}' <file>
3) awk 'BEGIN{
        file="myfile";     
        while(( getline line < file ) > 0 ) {
           print line
        }
}' 

```

---

### Post by benj1 on 2009-10-13
> **ghostdog74 said:**
> i am a bit confused about what you actually want to do. Ways to "open" a file in awk
```

1) awk -f test.awk <file>
2) awk '{print}' <file>
3) awk 'BEGIN{
        file="myfile";     
        while(( getline line < file ) > 0 ) {
           print line
        }
}' 

```

its the script in my second post, i dont need to define the file from the command line so suggestions 1 and 2 aren't really relevant (unless i wrap them up in a shell script) and i know i can do 3 but it just seems un awkish, considering if i were to write an awk script with a text file to be handed to it from the command line at invocation way 3 would only need the equivalent of 
```
print $0
```
just seems strange to me that if you want to invoke awk with a file from the command line to print all lines you can do
```

#! /usr/bin/awk -f
{print $0}

```
but if you are only ever going to use one file, thats defined in the script you need to do
```

#! /usr/bin/awk
BEGIN{
    file="myfile";     
    while(( getline line < file ) > 0 ) {
       print line
    }
}

```
or
```

#! /bin/sh
awk '{print $0}' myfile

```
i was just wondering if there was a more elegant way

---

### Post by ghostdog74 on 2009-10-13
seriously, i must go for english/grammar class. I still do not know what you are talking about. Making up a real example would be nice. If you are not going to give awk an input file, then the only other way data are going into awk is from STDIN.

---

### Post by benj1 on 2009-10-13
```

#! /bin/sh                                                               
awk '                                                                   
$3 ~ /remove/ {                                                  
    if ($4 in install) {delete install[$4]}                         
    else {remove[$4]=$4}                      
}                                                                               
$3 ~ /install/{                                                  
    if ($4 in remove){delete remove[$4]}                        
    else {install[$4]=$4}                                               
}                                                                                                                              
END {   
    print "installed apps\n--------------"; for (entry in install){print entry}  
    print "removed apps\n------------"; for (entry in remove){print entry}                                                     
}'  /var/log/dpkg.log

```
this is my actual script, the file it reads is /var/log/dpkg.log to work out what packages have been installed or removed from the default install.
i have no need to give it any other files so

```

#! /usr/bin/awk -f  
$3 ~ /remove/ {                                                  
    if ($4 in install) {delete install[$4]}                         
    else {remove[$4]=$4}                      
}                                                                               
$3 ~ /install/{                                                  
    if ($4 in remove){delete remove[$4]}                        
    else {install[$4]=$4}                                               
}                                                                                                                              
END {   
    print "installed apps\n--------------"; for (entry in install){print entry}  
    print "removed apps\n------------"; for (entry in remove){print entry}                                                     
}

```
would be silly because i would have to remember to call it as
```
awk-script /var/log/dpkg.log
```
every time.
the only other option i can think of is something like
```

#! /usr/bin/awk
{
    file="/var/log/dpkg.log";     
    while(( getline line < file ) > 0 ) {
        $3 ~ /remove/ {                                                  
            if ($4 in install) {delete install[$4]}  
            else {remove[$4]=$4}                      
        }               
        $3 ~ /install/{                                                  
            if ($4 in remove){delete remove[$4]}                        
            else {install[$4]=$4} 
        }
    }
}                                                      
END {   
    print "installed apps\n--------------"; for (entry in install){print entry}
    print "removed apps\n------------"; for (entry in remove){print entry}
}

```
which yes you could say is fine, but isnt as straight forward as when you supply a file from the command line, and seems like a bit of a dodgy hack.

---

### Post by ghostdog74 on 2009-10-13
> **benj1 said:**
> [CODE]
which yes you could say is fine, but isnt as straight forward as when you supply a file from the command line, and seems like a bit of a dodgy hack.

i will pose the question back to you another way. If those methods of specifying a file name to awk are not  what you want, then show what is your ideal awk code look like.

---

### Post by benj1 on 2009-10-13
```

#! /usr/bin/awk  

BEGIN{FILENAME="/var/log/dpkg.log"}

$3 ~ /remove/ {                                                  
    if ($4 in install) {delete install[$4]}                         
    else {remove[$4]=$4}                      
}                                                                               
$3 ~ /install/{                                                  
    if ($4 in remove){delete remove[$4]}                        
    else {install[$4]=$4}                                               
}                                                                                                                              
END {   
    print "installed apps\n--------------"; for (entry in install){print entry}  
    print "removed apps\n------------"; for (entry in remove){print entry}                                                     
}

```
well the above would be sensible, FILENAME is already an awk variable for the file being read, added to the fact that the file isn't read until after the BEGIN block, this could be possible, and its more obvious and in keeping with awk than the other methods.

is the next post going to be "learn C and post a patch" per chance?

---

### Post by ghostdog74 on 2009-10-14
that's just how the way awk works. Note, FILENAME is undefined inside BEGIN block (read the man page). Therefore, if you are going to set FILENAME inside the BEGIN block like in your case, its just another ordinary awk variable. If you want to roll your own magic, then yes, you are quite correct, go look at the source, modify yourself and rebuild awk. Otherwise, why bother. It doesn't matter if its awkish or un-awkish, just use what's available since that's just how awk works.

---

### Post by benj1 on 2009-10-14
i know
it just seems an obvious oversight thats all

---

### Post by DaithiF on 2009-10-14
hmm, i don't agree.  awk -f script.awk somefile is the obvious way to me.  hardcoding a filename in the script would be like creating a screwdriver that can only be used on one particular screw...  :)

---

### Post by benj1 on 2009-10-14
> **DaithiF said:**
> hmm, i don't agree.  awk -f script.awk somefile is the obvious way to me.  hardcoding a filename in the script would be like creating a screwdriver that can only be used on one particular screw...  :)

yes but the option would be nice, its a bit silly having to define a file name when you are only going to be using the same one every time, when you launch an app you don't need to define the config file, only when you are using a non standard config file.
anyway ive found a setup that im somewhat more happy with

```
BEGIN {ARGV[1] = "/var/log/dpkg.log"; ARGC = 2}
```

---

