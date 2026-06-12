---
title: "Bash shell script help - editing a text file, variables &amp; more"
date: 2012-12-20
forum: Programming Talk
---

### Post by josiahrulez on 2012-12-20
Hey all, so i'm trying to make a batch script to automatically install and config some apps.

I have the installing bit done, but i want these apps to auto start when the user logs in, for that i need to edit 

/etc/default/sabnzbdplus
i need to edit line 12, i need to add the current users user name after the "USER=". 
```
# This file is sourced by /etc/init.d/sabnzbdplus
#
# When SABnzbd+ is started using the init script, the
# --daemon option is always used, and the program is
# started under the account of $USER, as set below.
#
# Each setting is marked either "required" or "optional";
# leaving any required setting unconfigured will cause
# the service to not start.

# [required] user or uid of account to run the program as:
USER=

# [optional] full path to the configuration file of your choice;
#            otherwise, the default location (in $USER's home
#            directory) is used:
CONFIG=

# [optional] hostname/ip and port number to listen on:
HOST=
PORT=

# [optional] extra command line options, if any:
EXTRAOPTS=
```

How would i do this? would i need to add a variable and get the user to manually input his username or is there a command to find out the current users username? and how would i edit a text file automatically with no user input?

Any help would be appriciated, I'm new to all this scripting stuff.

---

### Post by Habitual on 2012-12-20
n/m
user variable in startup script? no.

---

### Post by josiahrulez on 2012-12-20
> **Habitual said:**
> n/m
user variable in startup script? no.

A little more information please?

---

### Post by greenpeace on 2012-12-20
You could use **sed** to update it?

```
gp@gpm:~/test$ **cat eg-config.cfg **
# This file is sourced by /etc/init.d/sabnzbdplus
#
# When SABnzbd+ is started using the init script, the
# --daemon option is always used, and the program is
# started under the account of $USER, as set below.
#
# Each setting is marked either "required" or "optional";
# leaving any required setting unconfigured will cause
# the service to not start.

# [required] user or uid of account to run the program as:
USER=

# [optional] full path to the configuration file of your choice;
#            otherwise, the default location (in $USER's home
#            directory) is used:
CONFIG=

# [optional] hostname/ip and port number to listen on:
HOST=
PORT=

# [optional] extra command line options, if any:
EXTRAOPTS=
gp@gpm:~/test$ **sed -i 's/USER=/&greenpeace/' eg-config.cfg **
gp@gpm:~/test$ **cat eg-config.cfg **
# This file is sourced by /etc/init.d/sabnzbdplus
#
# When SABnzbd+ is started using the init script, the
# --daemon option is always used, and the program is
# started under the account of $USER, as set below.
#
# Each setting is marked either "required" or "optional";
# leaving any required setting unconfigured will cause
# the service to not start.

# [required] user or uid of account to run the program as:
USER=greenpeace

# [optional] full path to the configuration file of your choice;
#            otherwise, the default location (in $USER's home
#            directory) is used:
CONFIG=

# [optional] hostname/ip and port number to listen on:
HOST=
PORT=

# [optional] extra command line options, if any:
EXTRAOPTS=
```

---

### Post by josiahrulez on 2012-12-20
> **greenpeace said:**
> You could use **sed** to update it?

```
gp@gpm:~/test$ **cat eg-config.cfg **
# This file is sourced by /etc/init.d/sabnzbdplus
#
# When SABnzbd+ is started using the init script, the
# --daemon option is always used, and the program is
# started under the account of $USER, as set below.
#
# Each setting is marked either "required" or "optional";
# leaving any required setting unconfigured will cause
# the service to not start.

# [required] user or uid of account to run the program as:
USER=

# [optional] full path to the configuration file of your choice;
#            otherwise, the default location (in $USER's home
#            directory) is used:
CONFIG=

# [optional] hostname/ip and port number to listen on:
HOST=
PORT=

# [optional] extra command line options, if any:
EXTRAOPTS=
gp@gpm:~/test$ **sed -i 's/USER=/&greenpeace/' eg-config.cfg **
gp@gpm:~/test$ **cat eg-config.cfg **
# This file is sourced by /etc/init.d/sabnzbdplus
#
# When SABnzbd+ is started using the init script, the
# --daemon option is always used, and the program is
# started under the account of $USER, as set below.
#
# Each setting is marked either "required" or "optional";
# leaving any required setting unconfigured will cause
# the service to not start.

# [required] user or uid of account to run the program as:
USER=greenpeace

# [optional] full path to the configuration file of your choice;
#            otherwise, the default location (in $USER's home
#            directory) is used:
CONFIG=

# [optional] hostname/ip and port number to listen on:
HOST=
PORT=

# [optional] extra command line options, if any:
EXTRAOPTS=
```

Thanks it works,

sed -i 's/USER=/&greenpeace/' Edit /etc/default/sabnzbdplus

but what command can i use to set the current user instead of "greenpeace? $USER doesnt really work?

Also if i run a python script via the shell script,
```
python ~/CouchPotatoServer/CouchPotato.py
sleep 15

```
how can i close it? i know ctrl z works if i manually input it, but how can i get it to close itself after it waits the 15 seconds?

Would this work

python ~/CouchPotatoServer/CouchPotato.py && sleep 15 && kill

also how do i kill by process name and not ID?

---

### Post by Bachstelze on 2012-12-20
> **greenpeace said:**
> You could use **sed** to update it?


No, sed is the Stream EDitor, it should be used to edit streams, not files. To edit files, use ed. Yes, I know the GNU folks have added the redundant -i flag to their version of sed, that doesn't make it right.

To get the value of USER, just use grep and cut.

---

### Post by JKyleOKC on 2012-12-20
> **josiahrulez said:**
> but what command can i use to set the current user instead of "greenpeace? $USER doesnt really work?What previous posts haven't made clear is that there **isn't** a current user (in the sense that you're using the phrase) at the time this script runs. No such "current user" exists until someone has logged in.

Actually, there's always a current user -- but during the boot sequence that user is "root" and you probably don't want the program to run as root. That would defeat many of the principles on which system security depends.

I'm not familiar with the package to which this script belongs, but it's likely that these environment variables are intended to "wall off" the program for use by the system. As part of /etc/init.d, the script will be run with root privileges when the named service starts, not when a user program associated with the service executes...

---

### Post by Bachstelze on 2012-12-20
> **JKyleOKC said:**
> What previous posts haven't made clear is that there **isn't** a current user (in the sense that you're using the phrase) at the time this script runs. No such "current user" exists until someone has logged in.

In understood "current user" as "the user specified by the USER variable in the script", but I may be wrong...

---

### Post by josiahrulez on 2012-12-20
thanks to the last few ppl who posted, ill have to test it tomorrow, its like 4am here lol.

but one last question before i go to bed. How can i add an application to the start up applications from the command line?

i found this online but it doesnt seem to work?
```
cat << EOF >> ~/.config/autostart/name.desktop
[Desktop Entry]
Type=Application
Exec=command
Name=name
Comment=whatever 
EOF
```

> **Bachstelze said:**
> To get the value of USER, just use grep and cut.
you lost me there, could you explain a bit further?

> **JKyleOKC said:**
> What previous posts haven't made clear is that there **isn't** a current user (in the sense that you're using the phrase) at the time this script runs. No such "current user" exists until someone has logged in.

Actually, there's always a current user -- but during the boot sequence that user is "root" and you probably don't want the program to run as root. That would defeat many of the principles on which system security depends.

I'm not familiar with the package to which this script belongs, but it's likely that these environment variables are intended to "wall off" the program for use by the system. As part of /etc/init.d, the script will be run with root privileges when the named service starts, not when a user program associated with the service executes...
Its a script to install and configure some applications, so it has to be manually run by a user. I want a way to use the username of the user running the script to be added to the file.

---

### Post by JKyleOKC on 2012-12-20
> **josiahrulez said:**
> thanks to the last few ppl who posted, ill have to test it tomorrow, its like 4am here lol.

but one last question before i go to bed. How can i add an application to the start up applications from the command line?

i found this online but it doesn't seem to work?
```
cat << EOF >> ~/.config/autostart/name.desktop
[Desktop Entry]
Type=Application
Exec=command
Name=name
Comment=whatever 
EOF
```

(snipped)

Its a script to install and configure some applications, so it has to be manually run by a user. I want a way to use the username of the user running the script to be added to the file.For the script, you might try commenting out that line in the script by adding "#" at the start of the line, and trying it. There will be a USER variable in the environment already, with the name of the current user, if this is only run after logging in and is never run during the boot process. However if the install is run via "sudo" then USER will contain "root" and that won't be good.

That bit you posted for adding it to autostart is a generic template and requires lots of editing to actually be usable. The "name" and "command" strings have to be replaced by what you want. The idea is to create a launcher, something similar to what Windows calls a shortcut, and add it to the list of things started when logging in. The two "name" instances are different; the first can be anything unique but preferably without any blank spaces, while the second will be exactly how it's listed in file displays. The "command" instance must be exactly what the user would type in a terminal window to start the application.

---

### Post by josiahrulez on 2012-12-21
> **Bachstelze said:**
> No, sed is the Stream EDitor, it should be used to edit streams, not files. To edit files, use ed. Yes, I know the GNU folks have added the redundant -i flag to their version of sed, that doesn't make it right.

To get the value of USER, just use grep and cut.

So i ended up doing this, but it doesn't work, sed doesn't like $variables. Will it work with ed and i tried playing around with ed earlier and couldnt get it to edit the file.
```

#!/bin/bash

echo -e "\e[1;32m" "What is your username?" "\e[0m" & read -p "  : " username
	echo ""
	echo $username

sed -i 's/USER=/&$username/' '/home/josiah/Desktop/Untitled Document'
```

edit** i found a fix, if i used " instead of ' it worked, it also will not work with $USER when running with sudo because it uses the root user.
```

#!/bin/bash

echo -e "\e[1;32m" "What is your username?" "\e[0m" & read -p "  : " username
	echo ""
	echo $username

sed -i "s/USER=/&$username/" '/home/josiah/Desktop/Untitled Document'

```

---

