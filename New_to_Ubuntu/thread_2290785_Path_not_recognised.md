---
title: "Path not recognised"
date: 2015-08-15
forum: New to Ubuntu
---

### Post by perthstuff on 2015-08-15
Hello, I wish to use Hadoop on a virtual machine and I am trying to configure the .bashrc file.

If I enter the following from the prompt:

ls /usr/local/hadoop/etc/hadoop/hadoop-env.sh

I get an error - no such file or directory but if I enter a ~ in front

ls ~/usr/local/hadoop/etc/hadoop/hadoop-env.sh

it works as one expects.

Do I need to put ~ in front of paths in my .bashrc file?


Thanks John

---

### Post by The Cog on 2015-08-15
I've not used hadoop so I'm guessing a bit, but...
It looks to me as though you have managed to get hadoop installed in the wrong place. /usr/local/hadoop looks like a sensible place to have hadoop installed - somewhere reachable by all users and clearly a local install. 
The leading ~ means your home directory. I would not expect hadoop to be installed in a user's home directory, especially in /home/$username/usr/local/hadoop.

---

### Post by perthstuff on 2015-08-15
The installation is from the web so the person who wrote it is probably unaware of that. I will modify it to take care of that
Cheers.

---

