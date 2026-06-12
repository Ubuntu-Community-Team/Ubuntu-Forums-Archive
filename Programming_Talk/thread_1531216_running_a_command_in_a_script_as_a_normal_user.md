---
title: "running a command in a script as a normal user"
date: 2010-07-14
forum: Programming Talk
---

### Post by perky on 2010-07-14
G'day :)

Is it possible to run one line in a sh script as the current (unprivelaged) user when the script is run as root?

To explain better, a user called perky runs: sudo sh script.sh

And I'm wondering how to have one line in script.sh run as perky instead of sudo/root.

Cheers!

---

### Post by sgosnell on 2010-07-14
Sudo means Perky isn't running the script, root (superuser) is.  Sudo means "do as superuser", or root.  It's possible for Perky to do anything in a script that Perky has privileges for.  If the action requires root privileges, then sudo is required.

---

### Post by perky on 2010-07-14
> **sgosnell said:**
> Sudo means Perky isn't running the script, root (superuser) is.  Sudo means "do as superuser", or root.  It's possible for Perky to do anything in a script that Perky has privileges for.  If the action requires root privileges, then sudo is required.

The thing is, when I run the following as root it would be good to have the green/bold line to be run as the regular user.  This is because root has different gconf settings to the normal user.

```

#!/bin/sh
FN_MAIN=batteryStatus.py
FN_SERVER=battery_status.server
FN_SOUND=low_power.wav
DEST_MAIN=/usr/local/bin/
DEST_SERVER=/usr/lib/bonobo/servers/
DEST_SOUND=/usr/share/sounds/
FULL_MAIN=$DEST_MAIN$FN_MAIN
FULL_SERVER=$DEST_SERVER$FN_SERVER
FULL_SOUND=$DEST_SOUND$FN_SOUND
FN_OLD=$FN_MAIN.old.$(date +%Y-%m-%d-%T)
# backup older version
if [ -f $FULL_MAIN ]
then
  # DONT_RELOAD_GNOME_PANEL=true
  echo 
  echo Backing up older version...
  mv --verbose $FULL_MAIN $DEST_MAIN$FN_OLD
  if [ -f $FULL_MAIN ]
  then
    echo 
    echo Error backing up old version. Please run as root: "\033[1m"sudo sh $0"\033[0m"
    echo 
    exit 2
  else
    echo Resetting custom settings \(because of major internal changes\)...
    **[COLOR="DarkGreen"]gconftool --recursive-unset '/apps/battery-status-applet'[/COLOR]**
  fi
fi
# install
echo 
echo Copying files...
cp --verbose $FN_MAIN $DEST_MAIN
cp --verbose $FN_SERVER $DEST_SERVER
cp --verbose $FN_SOUND $DEST_SOUND
if [ -f $FULL_MAIN ] && [ -f $FULL_SERVER ] && [ -f $FULL_SOUND ]
then
  echo 
  if [ $DONT_RELOAD_GNOME_PANEL ]
  then
    echo \(skipping restarting Gnome Panel\)
  else
    echo Restarting Gnome Panel...
    killall gnome-panel
  fi
  echo 
  echo "\033[1m"Installation complete!"\033[0m" \(It is safe to remove this directory.\)
  echo 
  echo If you encounter any errors, please run the applet as:
  echo python $FULL_MAIN 1
  echo 
  echo This will output any debugging info.  Please post errors to:
  echo http://ubuntuforums.org/showthread.php?p=9271002
  echo \(or pm perky on Ubuntuforums.\)
  echo Thanks!!
  echo 
  exit 0
else
  echo 
  echo Error copying files. Please run as root: "\033[1m"sudo sh $0"\033[0m"
  echo 
  exit 1
fi

```

---

### Post by soltanis on 2010-07-15
Hi. Quick etymology lesson. "sudo" comes from "su" which originally meant *super user* but now is understood to mean *substitute user*. Sudo allows you to run commands as other users, not just root.

Normally you'd need to either login as another user (using the **su -c** command) or give your own password (using the **sudo** invocation) to do this, but since your script is running as root anyways, running **sudo** will be allowed without needing any passwords (that's the beauty of root).

Long story short, doing this:

```

sudo -u porky "sh script.sh"

```

Will work.

---

### Post by rnerwein on 2010-07-15
> **perky said:**
> G'day :)

Is it possible to run one line in a sh script as the current (unprivelaged) user when the script is run as root?

To explain better, a user called perky runs: sudo sh script.sh

And I'm wondering how to have one line in script.sh run as perky instead of sudo/root.

Cheers!

hi
the way i want to solve problems like yours i use a liitle C-program ( i know long time ago there was i s-bit
available in shell too )
-->
include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

main(int ac, char **av)
{
uid_t uid_back;

uid_back = getuid();
setuid(0);
fprintf(stderr,"my uid now is: %d\n",getuid());
system("./y.sh");
setuid(uid_back);
fprintf(stderr,"my uid is back to: %d\n",getuid());
exit(0);
}

this program has to be compiled and then you have to run the command: chown root your_program
chmod 4555 your_program.
here is y.sh -->#
#!/bin/sh
echo "i will start the script:` id `"
# next commands ....
exit 0

this script will as as root. what you want is to run the script as a normal user - check the user-id and
change it in my little C-program to your behavior.
may be this helps you a little bit.
but be very, very careful with stuff like this.
ciao

---

### Post by renkinjutsu on 2010-07-15
```
echo 
    exit 2
  else
    echo Resetting custom settings \(because of major internal changes\)...
    [COLOR="Lime"]su perky -c "gconftool --recursive-unset '/apps/battery-status-applet'"[/COLOR]
  fi
fi
# install
echo 
```

---

### Post by perky on 2010-07-15
Thanks!

I wasn't aware of the switches available with sudo and su; they will do the job nicely - thanks again for the help :) :)

---

### Post by hannaman on 2010-07-18
Also, so you don't have to hardcode a username in your script, in case you want multiple users to use it, the "who am i" command will show the user you are logged in as.
```
$ whoami
michael
$ sudo whoami
root
$ who am i
michael  pts/0        2010-07-18 23:56
$ sudo who am i
michael  pts/0        2010-07-18 23:56 (:0.0)
```
You can just grab the first field and store it in a variable.
```
user=`who am i | awk '{ print $1 }'`
su - $user -c "gconftool --recursive-unset '/apps/battery-status-applet'"
```
Oh, and su originally meant **s**witch **u**ser, but if run without any username, it switches to root (superuser) so the meaning changed over the years.

---

### Post by soltanis on 2010-07-18
IMHO the extra awk invocation is not needed. Oh, and also, if you invoke the script as root, then asking "whoami" will tell you root, not the original user which invoked the script. There are two ways to figure this out. First, if your invocation of the whole script is this:

```

sudo sh script.sh

```

Then the environment variable $USER will not be changed (tested this under Ubuntu 10.04, Xfce environment, dash) and you can use the value of that variable. You can do this:

```

sudo -u "$USER" "command"

```

If your concern is portability though, I don't see this specified by POSIX or any other standard, so I expect that it varies depending on platform. If you plan on using this script elsewhere (doubtful, but maybe) then the better method would be to pass your current username as an argument to the shell script. Invoke it like this:

```

sudo sh script.sh `whoami`

```

And in the script you would do

```

user=$1
sudo -u "$user" "command"

```

There is more than one way to do it.

---

### Post by perky on 2010-07-20
Thanks, yeah finding the current user was the next hurdle :)

The `who am i` | awk.. method seems to work well, and `who` is part of coreutils which is part of every distro (well it would be safe to assume every distro that has Gnome installed).

$USER also seems to work in Ubuntu and in Archlinux, but seeing it's not a spec I might go with `who am i` (from the man pages $1 and $2 can be anything; eg `who mom likes`)

---

