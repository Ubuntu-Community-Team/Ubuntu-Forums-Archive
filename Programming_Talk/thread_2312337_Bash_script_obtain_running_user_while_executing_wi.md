---
title: "Bash script: obtain running user while executing with sudo previleges"
date: 2016-02-03
forum: Programming Talk
---

### Post by erotavlas on 2016-02-03
Hi,
I need to execute a script as sudo user and for this reason I wrote this code
```

#!/bin/bash

user=$USER
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root, use sudo "$0" instead" 1>&2
   exit 1
fi

```
I had a problem with the value of the variable $USER that is root instead of the current running user as if I had executed without sudo.
How can I obtain the current running user instead of root? Have I to pass the correct values during the calling of script?
Thank you

---

### Post by ian-weisser on 2016-02-03
The 'whoami' command will retunr the current user.

---

### Post by matt_symes on 2016-02-03
Hi

If a logged in user is running the script, this may help.

```

matthew-xu-16-04:/usr/share/X11/xkb:2 % sudo logname
matthew
matthew-xu-16-04:/usr/share/X11/xkb:2 % sudo whoami 
root
matthew-xu-16-04:/usr/share/X11/xkb:2 % 
```

EDIT:

...although I've had so many flu tablets today, I'm not actually sure if i understand your question.

Kind regards

---

### Post by erotavlas on 2016-02-03
> **ian-weisser said:**
> The 'whoami' command will retunr the current user.
This does not work.

---

### Post by erotavlas on 2016-02-03
> **matt_symes said:**
> Hi

If a logged in user is running the script, this may help.

```

matthew-xu-16-04:/usr/share/X11/xkb:2 % sudo logname
matthew
matthew-xu-16-04:/usr/share/X11/xkb:2 % sudo whoami 
root
matthew-xu-16-04:/usr/share/X11/xkb:2 % 
```

EDIT:

...although I've had so many flu tablets today, I'm not actually sure if i understand your question.

Kind regards

Yes sudo logname work. I need to know the current user in order to read some file from the home folder.
Thank you very much

---

### Post by matt_symes on 2016-02-03
Hi

You may also find SUDO_USER useful (maybe).
```

matthew-xu-16-04:/home/matthew/temp:2 % cat t 
#!/bin/bash

echo $USER
echo $EUID
echo $UID
echo $LOGNAME
echo $SUDO_USER
matthew-xu-16-04:/home/matthew/temp:2 % ./t
matthew
1000
1000
matthew

matthew-xu-16-04:/home/matthew/temp:2 % sudo ./t
root
0
0
root
matthew
matthew-xu-16-04:/home/matthew/temp:2 % 
```

Some ideas for you to play with.

If one of these fix your problem then please post back which one.

Kind regards

---

### Post by erotavlas on 2016-02-04
> **matt_symes said:**
> Hi

You may also find SUDO_USER useful (maybe).
```

matthew-xu-16-04:/home/matthew/temp:2 % cat t 
#!/bin/bash

echo $USER
echo $EUID
echo $UID
echo $LOGNAME
echo $SUDO_USER
matthew-xu-16-04:/home/matthew/temp:2 % ./t
matthew
1000
1000
matthew

matthew-xu-16-04:/home/matthew/temp:2 % sudo ./t
root
0
0
root
matthew
matthew-xu-16-04:/home/matthew/temp:2 % 
```

Some ideas for you to play with.

If one of these fix your problem then please post back which one.

Kind regards


Hi, I'm interested on executing my script with sudo previleges and for this reason I consider only this case.
Both these commands work well.
```

echo $(sudo logname)
echo $SUDO_USER

```
Although the first is the preferred one. I made a lot of search and I found this very useful thread [https://stackoverflow.com/questions/4598001/how-do-you-find-the-original-user-through-multiple-sudo-and-su-commands](https://stackoverflow.com/questions/4598001/how-do-you-find-the-original-user-through-multiple-sudo-and-su-commands).
The final answer is that there is no guarantee method even if the best commands that work in the majority of case are:
```

who am i | awk '{print $1}' 
logname

```
Thank you

---

### Post by matt_symes on 2016-02-04
Hi

Nice link ! Thanks for posting it.

I've had to do something similar in the past in a script, so it's not impossible that i stumbled across that link myself.

Kind regards

---

### Post by erotavlas on 2016-02-10
Hi,
I have another problem. I tried to use logname under lubuntu 15.10 64 bits and I get back
```

logname: no login name

```
Any idea?

Edit:
Even who i am does not work and returns blank row :(. I'm downloading ubuntu 15.10 64 bit in order to check...

Edit2:
$USER and $LOGNAME work well. Moreover, I found these two bugs [https://bugs.launchpad.net/terminator/+bug/1516440](https://bugs.launchpad.net/terminator/+bug/1516440) and [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1537645](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1537645)

---

### Post by matt_symes on 2016-02-10
Hi

From 

```
info logname
```

> ‘logname’ prints the calling user’s name, as found in a
system-maintained file (often ‘/var/run/utmp’ or ‘/etc/utmp’), and exits
with a status of 0.  If there is no entry for the calling process,
‘logname’ prints an error message and exits with a status of 1.

Does /var/run/utmp exist ?

> An exit status of zero indicates success, and a nonzero value
indicates failure.

Are you checking the exit status of logname ?

Can you use SUDO_USER instead or supplementary ?

I don't use Lubuntu at the moment so these are suggestions only.

Kind regards

---

### Post by erotavlas on 2016-02-11
> **matt_symes said:**
> Hi

From 

```
info logname
```



Does /var/run/utmp exist ?



Are you checking the exit status of logname ?

Can you use SUDO_USER instead or supplementary ?

I don't use Lubuntu at the moment so these are suggestions only.

Kind regards

I confirm that under lubuntu 15.10 both logname and who i am do not work. The /var/run/utmp exists. I solved by using
```

user=$(sudo logname)
if [ -z "$user"]; then
    user=$SUDO_USER
fi

```
While under ubuntu 15.10 both logname and who i am work well.
Thank you

---

