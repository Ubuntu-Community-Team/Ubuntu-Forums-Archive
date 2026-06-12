---
title: "Iterate bash script over a list"
date: 2015-05-20
forum: Programming Talk
---

### Post by Robing Goodfellow on 2015-05-20
I am setting up to use ansible, need to set up ssh keys on numerous servers to receive playbooks (updates and scripts) using a key instead of a password to initiate the ssh session. I've written a bash script that copies the public key into the destination server, and it works well, once that is done I am able to ssh in without a password. I'd like to write into the script that it executes this on numerous IP's (which are not consecutive). Any suggestions on how to set that up? Here's psuedo code for what I'm trying to do:

List of IP addresses:
IP1
IP2
IP3
...
IP500

bash script:
x=1
for IPx:
do foo
when done
 x=x+1
go back to for IPx line
If x not on list (all IP addresses done)
 exit

regards, Richard

---

### Post by TheFu on 2015-05-20
Loops ... an example.

```
#!/bin/sh
#
# This is for really simple XVID conversion, use
#
for filename in "$@"; do
  DO SOMETHING with $filename .... 
done
```
So - if you pass in a list of IPs, space-separated ...

OTOH, why not use ansible to push the keys? That's how I do it. 
```
action: lineinfile dest=/home/{userid}/.ssh/authorized_keys
```

---

### Post by Vaphell on 2015-05-21
arrays (lists) go like this:

```
#!/bin/bash

ip_list=( 1.1.1.1. 2.2.2.2
          3.3.3.3  4.4.4.4
          etc etc )

for ip in "${ip_list[@]}"
do
    echo "$ip"
done
```

you could also read the list from the file.

```
#!/bin/bash

while read ip
do
    echo "$ip"
done < ip_list.txt
```

---

