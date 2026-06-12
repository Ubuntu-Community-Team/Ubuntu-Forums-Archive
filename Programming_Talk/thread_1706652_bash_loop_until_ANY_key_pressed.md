---
title: "bash loop until ANY key pressed?"
date: 2011-03-14
forum: Programming Talk
---

### Post by janmartin on 2011-03-14
Hi,

I need to write a loop that loops until ANY key is pressed.

However this lops only IF a key is pressed.

How to change this?

```
#!/bin/bash

# /home/me/DIY-streetview/synch/synch.sh

count=0
while : ; do

# dummy action
echo -n "$a "
let "a+=1"

read -n 1 keypress
echo $keypress

done
echo "Thanks for using this script."
exit 0
```

---

### Post by Arndt on 2011-03-14
> **janmartin said:**
> Hi,

I need to write a loop that loops until ANY key is pressed.

However this lops only IF a key is pressed.

How to change this?

```
#!/bin/bash

# /home/me/DIY-streetview/synch/synch.sh

count=0
while : ; do

# dummy action
echo -n "$a "
let "a+=1"

read -n 1 keypress
echo $keypress

done
echo "Thanks for using this script."
exit 0
```

Can you use "read -t 0"?

---

### Post by janmartin on 2011-03-14
Hi Arndt,

when I replace 

read -n 1 keypress

by 
read -t 0
or 
read -t 0 keypress

it does not react to keys at all.

Jan

---

### Post by Arndt on 2011-03-14
> **janmartin said:**
> Hi Arndt,

when I replace 

read -n 1 keypress

by 
read -t 0
or 
read -t 0 keypress

it does not react to keys at all.

Jan

I didn't mean that you should replace the existing arguments, only that -t 0 is part of the solution. Look in the manual page what -t does.

---

