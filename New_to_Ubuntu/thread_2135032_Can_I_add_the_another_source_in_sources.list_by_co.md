---
title: "Can I add the another source in sources.list by command line?"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by goddesschi on 2013-04-13
If I don't want to edit the sources.list file by vi(m), could I  add the source by command line to import the specific source  in the sources.list file
I want to add the command to the sell script, please give me the suggestion...thanks

for example:
Could I add below sources into sources.list by one line command 
> deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) precise main 
 deb-src [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) precise main

---

### Post by papibe on 2013-04-13
Hi goddesschi.

I see a couple of alternatives:

Using sed:
```
#!/bin/bash
sed -i '$ a\
\
# Inserted by this because of that.\
deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main\
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main' /etc/apt/sources.list

```
Or using bash's echo:
```
#!/bin/bash
echo "" >> /etc/apt/sources.list
echo "# Inserted by this because of that." >> /etc/apt/sources.list
echo "deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main" >> /etc/apt/sources.list
echo "deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main"  >> /etc/apt/sources.list

```
Since you are appending content to a root's owned file you would need to run this using sudo:
```
sudo either_script.sh
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by rrich1974 on 2013-04-13
actually, there is no need to add the source by editing the source list. instead, you can add a PPA by add a line in source of "software source"
so: ubuntu software center--> edit-->software source-->other software-->add

---

### Post by jorok_tupur on 2013-04-13
One line:

```
echo -e '\ndeb http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main\ndeb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main ' | sudo tee -a /etc/apt/sources.list
```

Explanation:
The command above can be divided into two parts: the 'echo' and the 'tee'.
[LIST=1]
[*]The 'echo' will send your sources to the stdout. The -e switch will make it interpret escape sequences - such as \n - correctly. 
[*]The result of 'echo' above is piped to 'tee' below. 
[*]The 'tee' will copy sources lines from the pipe, and write that into /etc/apt/sources.list. The -a switch will make it append the lines into the file, instead of overwriting it. 
[/LIST]

---

### Post by sisco311 on 2013-04-13
Instead of editing the main sources.list file you should create your own .list file in /etc/apt/sources.list.d

For adding multiple lines, I'd probably use a here string:
```

cat << EOF > /etc/apt/sources.list.d/my-ppa-repo.list
# short description

deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main
deb-src http://ppa.launchpad.net/shiki/mediainfo/ubuntu precise main
EOF
```

---

### Post by goddesschi on 2013-04-13
Thanks a lot, every friends.
Could I ask another question about sed

if I want to replace the sentence **'/'** to **'/home'**, how to type the command

I try to type the below command, but it can't work...:(
> sed -i 's/"'"\/"'"/"'"\/home\/"'"/g' config.php

---

### Post by steeldriver on 2013-04-13
imo the easiest way is to avoid escaping or quoting the slash altogether by using a different separator for the sed substitution command e.g. with | as separator

```
$ echo '/my/dir' | sed 's|/|/home/|'
/home/my/dir
```

---

