---
title: "I don't get it"
date: 2008-10-02
forum: Programming Talk
---

### Post by akvino on 2008-10-02
What does this do? 

cat << EOF >> /etc/sysctl.conf

I understand the 'cat' and /etc/sysctl.conf, but this syntax - what does ti do? How does shell interpret this?

---

### Post by Bachstelze on 2008-10-02
Where did you see this? It's most likely not a shell command.

---

### Post by akvino on 2008-10-02
> **HymnToLife said:**
> Where did you see this? It's most likely not a shell command.

I saw it in the clustering configuration email list:
[i]
I believe you just need to force all nodes to "speak" IGMPv2. Do this:

for iface in /proc/sys/net/ipv4/conf/*; do
 echo '2' > $iface/force_igmp_version
done

On each node and probably it will work after. Cisco switches generally
speak IGMPv2 and Linux defaults to IGMPv3. RHCS depends on multicast
to work properly and multicast depends on IGMP.

You will need to set this in /etc/sysctl.conf to make it persistent
between reboots. Do this:

cat << EOF >> /etc/sysctl.conf
net.ipv4.conf.all.force_igmp_version = 2
net.ipv4.conf.default.force_igmp_version = 2
EOF

Let us know if this resolve your problem.[/i]

---

### Post by dribeas on 2008-10-02
> **akvino said:**
> What does this do? 

cat << EOF >> /etc/sysctl.conf

I understand the 'cat' and /etc/sysctl.conf, but this syntax - what does ti do? How does shell interpret this?

Its used in scripting, and can be used on the command line. >> means redirect output to the end of /etc/sysctl.conf, which is the easy part.

Then the << EOF means use STDIN for input up to and not including EOF. EOF can be any word:

```

$ cat << my_end_of_file > file.txt
This is a text
my_end_of_file
$ cat file.txt
This is a text
$

```

---

### Post by unutbu on 2008-10-02
Save this into a file called something like test.sh
```
#!/bin/bash
cat << EOF >> ~/output
net.ipv4.conf.all.force_igmp_version = 2
net.ipv4.conf.default.force_igmp_version = 2
EOF

```
Make it executable: ```

chmod +x test.sh

```
Run it:```

./test.sh

```
And then look inside ~/output.

The "cat << EOF" idiom sends all subsequent lines to cat until an EOF is found on a line by itself. The ">> ~/output" appends the output of cat to ~/output.

---

### Post by Bachstelze on 2008-10-02
What they said ;) Don't forget to give all the relevant information when asking for help.

---

### Post by akvino on 2008-10-03
Thank you all.

:D

---

