---
title: "Basic Bash scripting help"
date: 2008-11-07
forum: Programming Talk
---

### Post by derelict888 on 2008-11-07
I'm not a programmer but the need for a script has arised. I've got a script started and working, but there are a few improvements I want to make but I'm stuck. Here is what my script looks like;

```


#!/bin/bash

  for j in $(cat /[place]/list.txt); do (
  echo Now pulling data from $j - `date +%c`
  echo >> /[place]/inventory.txt     # Blank Space
  echo >> /[place]/inventory.txt \|~~~~~~~~~~~~~~~\>"$j"\<~~~~~~~~~~$
  ssh root@$j ls /etc/vifs  >> /[place]/inventory.txt
  echo >> /[place]/inventory.txt
)

#mv /[place]/inventory.txt \
#/[place]/inventory_`date +%F_%Hh_%Mm`.txt

done


```

If I uncomment the last 2 lines of code, I get the date post-fixed to the file's name, but I might get 2 - 3 files. If it takes 3 minutes to run through the list I get 3 files, and each are populated with data during the minute it completed. When I leave these lines commented out, it all goes in the same inventory.txt file.

How do I get all the information in one text file AND have a time stamped to it?

Also I've got another bit of information I want dumped in this text document; I want the first 16 characters of the first line of every file that is getting ls'd into this text document, but what code do I use to do that? Cat?

Thanks for any help

PS -> I'm sure my coding is pretty sorry and ugly, any suggestions for added elegance is welcome.  :)

---

### Post by raf_kig on 2008-11-07
Not absolutely shure what you want it to do.

Do you want a timestamp for every run? or do you want a timestamp for every item?
This does include a timestamp for every item:
```
for line in $(cat /tmp/list);
do
    echo "Timestamp: `date +%c`" >> /tmp/target
    echo "im a command to be run using $line as argument" >> /tmp/target
done;
mv "/tmp/target" "/tmp/target_`date +%F_%Hh_%Mm`"
```

/edit use ```
head -n1 | cut -c-16 $filename
``` to show the first 16 characters of a file (assuming those are ascii containing text files)

and btw, you should not allow root login via ssh, not ever


Regards

raf

---

### Post by derelict888 on 2008-11-07
Timestamp for every run, the script connects to several servers (from the list) lists a directory and then sends what it finds to a text file. Here is what it looks like now;
```

|~~~~~~~~~>Server1<~~~~~~~~~~~|
junk1
junk2
junk4
|~~~~~~~~~>Server2<~~~~~~~~~~~|
junk8
junk5
junk22

```
and so on till the end of the server list. This gets dumped into **inventory.txt**. What I want it to look like now is;
```

|~~~~~~~~~>Server1<~~~~~~~~~~~|
junk1 Has x.x.x.x IP block
junk2 Has x.x.x.x IP block
junk4  Has x.x.x.x IP block
|~~~~~~~~~>Server2<~~~~~~~~~~~|
junk8 Has x.x.x.x IP block
junk5 Has x.x.x.x IP block
junk22 Has x.x.x.x IP block

```
and then at the end change the name inventory.txt to **inventory_[date]_[time].txt** to indicate when the "inventory" check was ran (and to have unique files instead of 1 long text file).

The x.x.x.x will be the first 16 (or less) characters in the junk[x] files

Thanks for your help

As for the root part of the ssh command, its only after I've su'd into a different account that has RSA keys in place which I don't control.

---

### Post by derelict888 on 2008-11-07
As far as the naming convention goes, the inventory.txt file could have the timestamp put on from the very onset, but I didn't have any luck doing it that way.

---

### Post by geirha on 2008-11-10
Not sure I quite understand what you want. Is /etc/vifs a directory that contains files name junkX? if so, you could probably do something like this
```

list=/[place]/list.txt
inventory=/[place]/inventory.txt
destfile=/[place]/inventory_`date +%F_%H_%M`.txt

for host in ` < "$list" `; do
  echo "|~~~ $host ~~~|" >> "$inventory"
  ssh root@$host '
    for file in /etc/vifs/*; do 
      echo "$file has `head -c 16 "$file"` IP block" 
    done
  ' >> "$inventory"
done

mv -v "$inventory" "$destfile"

```

---

### Post by derelict888 on 2008-11-11
That looks pretty good, I'll try the naming part of it first. Thanks.

---

### Post by derelict888 on 2008-11-11
Is that syntax correct? I'm getting an error from these lines;
```

      echo "$file has `head -c 16 "$file"` IP block"
    done
  ' >> "$inventory"

```
The error is;
```

./new_test.sh: line 26: unexpected EOF while looking for matching `"'
./new_test.sh: line 27: syntax error: unexpected end of file

```

---

### Post by geirha on 2008-11-11
I've looked over it several times, and I can't see any missing " quotes. It's possible it is one of the lines further up that lacks an ending " quote.

---

### Post by derelict888 on 2008-11-12
Here is all the code (minus comment block)

```

####################################################
# xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx                 #
#                                                  #
#       xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx       #
#  xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx    #
#  xxxxxxxxxxxx                                    #
#                                                  #
####################################################

#!/bin/bash

list=/[place]/list.txt
inventory=/[place]/inventory_test.txt   # inventory_test while in dev
destfile=/[place]/inventory_`date +%F_%H_%M`.txt

for host in ` < "$list" `; do
  echo "Now pulling data from $host - `date +%c`"
  echo "|~~~~~~~~~~> $host <~~~~~~~~~~|" >> "$inventory"
  ssh root@$host ls /etc/vifs >> "$inventory"
    for file in /etc/vifs/; do 
      echo "$file has `head -c 16 "$file"` IP block"
    done
  ' >> "$inventory"
done

mv -v "$inventory" "$destfile"

```
I was missing a " and I added it, but I'm still getting this error;

```
./new_test.sh 
./new_test.sh: line 23: unexpected EOF while looking for matching `''
./new_test.sh: line 27: syntax error: unexpected end of file

```

Thanks for your help :guitar:

---

### Post by geirha on 2008-11-12
> **derelict888 said:**
> 
```

  ssh root@$host ls /etc/vifs >> "$inventory"

```


There's the problem. You are only running ls on the server here, instead of the for loop, so the for-loop is run locally instead. And the problem comes when it gets to the closing ' quote which doesn't have a starting ' quote.

---

### Post by derelict888 on 2008-11-12
Ok how do I fix that? Sorry I really don't know enough about scripting/programming to do this on my own.

---

### Post by geirha on 2008-11-12
Try this. I put the for-loop to be run on the remote server on one line instead of several this time, and I also use the basename command so the full path isn't printed
```

####################################################
# xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx                 #
#                                                  #
#       xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx       #
#  xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx    #
#  xxxxxxxxxxxx                                    #
#                                                  #
####################################################

#!/bin/bash

list=/[place]/list.txt
inventory=/[place]/inventory_test.txt   # inventory_test while in dev
destfile=/[place]/inventory_`date +%F_%H_%M`.txt

for host in ` < "$list" `; do
  echo "Now pulling data from $host - `date +%c`"
  echo "|~~~~~~~~~~> $host <~~~~~~~~~~|" >> "$inventory"
  ssh root@$host 'for file in /etc/vifs/; do echo "`basename "$file"` has `head -c 16 "$file"` IP block"; done' >> "$inventory"
done

mv -v "$inventory" "$destfile"

```

---

### Post by derelict888 on 2008-11-12
Sweet this is working how I need it, thanks for your help :)

This thread can be marked as resolved.

---

### Post by geirha on 2008-11-13
> **derelict888 said:**
> Sweet this is working how I need it, thanks for your help :)

This thread can be marked as resolved.

Glad to hear! :) 

You mark your thread solved yourself. It's an option under "Thread Tools", just above the first post of the page.

---

