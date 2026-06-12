---
title: "chown / ownership problems in bash"
date: 2011-05-06
forum: Programming Talk
---

### Post by CaptainMark on 2011-05-06
How would I go about fixing this changing ownerships problem?
In a script i tried to use the this command```
chown -R $USER $HOME/.config/homesync
``` to change the owner of the directory homesync to the currently logged in user, all well and good, however this script needs to be run with sudo so instead of 
$HOME= /home/mark
$USER= mark

they become 
$HOME= /root
$USER= root

any ideas how to run a script with sudo but still have the constants for user and home still equal what they would without sudo??

My only workaround is to make the permissions of the directory 777, which is not an ideal option

---

### Post by Arndt on 2011-05-06
> **CaptainMark said:**
> How would I go about fixing this changing ownerships problem?
In a script i tried to use the this command```
chown -R $USER $HOME/.config/homesync
``` to change the owner of the directory homesync to the currently logged in user, all well and good, however this script needs to be run with sudo so instead of 
$HOME= /home/mark
$USER= mark

they become 
$HOME= /root
$USER= root

any ideas how to run a script with sudo but still have the constants for user and home still equal what they would without sudo??

My only workaround is to make the permissions of the directory 777, which is not an ideal option

Is this a solution?

```
sudo USER=$USER HOME=$HOME yourscript
```

---

### Post by CaptainMark on 2011-05-06
it works ok, but i needed something in the script itself, this is to be passed onto complete terminal-phobes and i dont want to add anything out of the ordinary to the commands they have to type

---

### Post by Drenriza on 2011-05-06
Give the files a sticky bit, that makes it possible for a normal user to run a file as the root user.

---

### Post by Arndt on 2011-05-06
> **CaptainMark said:**
> it works ok, but i needed something in the script itself, this is to be passed onto complete terminal-phobes and i dont want to add anything out of the ordinary to the commands they have to type

sudo sets SUDO_USER to the name of the original user. Can you use that?

---

### Post by DaithiF on 2011-05-06
Hi, why rely on environment variables?  pass in parameters to the script instead ...

```
sudo yourscript $USER $HOME

```

bash will expand the variables before passing them into the script, so you will get your user's details rather than roots.

then in your script access these as $1, $2 etc positional params.
```
user=$1
home=$2
...
```

---

### Post by CaptainMark on 2011-05-06
> **Arndt said:**
> sudo sets SUDO_USER to the name of the original user. Can you use that?
this works perfectly, thanks so much
if i sudo su, then echo $SUDO_USER still prints mark, not root.

whats odd is that i was wrong on the fact that running with sudo changes the user but not the home, 
make a script ```
#!/bin/bash

echo $USER
echo $HOME
```run it as normal user to get ```
mark
/home/mark
```run it as root and you get```
root
/home/mark
```odd but oh well, thanks for your help

one last question, its not too important, but if i wanted to send this script to non-ubuntu users or to any distro that doesnt use the sudoers system, im presuming this wouldnt work??
can anyone confirm?

---

