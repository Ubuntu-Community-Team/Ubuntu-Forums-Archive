---
title: "Switch from superuser to $USER in bash script"
date: 2010-07-17
forum: Programming Talk
---

### Post by Cypher2 on 2010-07-17
Hello :)

In my endeavor to pursue and achieve the best custom distribution install ever, I have been mounting myself a self-install script tol load and install/configure all necessary packages and parameters to the desired system.

One little bug remains:

Since running the script requires calling su/sudo (Debian/Ubuntu), I would like to know if there is any way to exit the superuser status within the shell script without completely exiting command execution... Somewhat like typing "exit" in the terminal and exiting back to the normal "USER@HOST:~$"

The purpose of this question is to avoid using chown commands and extensive back and forth within command directories (cd) to copy and apply given parameters, or even create some files and folders where needed so that the permissions are already set for the normal $USER rather than root.

THank you very much for any help!

---

### Post by jbrown96 on 2010-07-17
su $USER or su - $USER

The - puts you into that user's environment (i.e. moving to their home directory, loading their .bashrc, etc.).

After you run your commands you can exit.

A better way may be to do [CODE/su - $USER -c 'COMMAND TO RUN'[/CODE]
Your script may stop execution if you switch users, so you may need to just specify commands to run as that user.

---

### Post by soltanis on 2010-07-17
More like this:

```

su - "$USER" -c "command; command; command;"

```

Without the -c switch it will just drop you into that user's shell.

You can also run a one-off command using sudo:

```

sudo -u "$USER" command;command;command

```

Either one works.

---

### Post by Zorgoth on 2010-07-17
I think you could also use sudo -i -u $USER

---

### Post by soltanis on 2010-07-18
If you open a login shell up, your script will not execute within the context of that shell; instead, the shell will just wait for input until it is terminated at which point your script will resume. Running sudo -i without any commands will do this.

---

### Post by Cypher2 on 2010-12-06
I end up digging the net and found something better which ends up going like this:

--------------------------------------------------------
ON_USER=$(echo ~ | awk -F'/' '{ print $1 $2 $3 }' | sed 's/home//g')
export $(grep -v "^#" ~/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)
if sudo -u $ON_USER test -z "$DBUS_SESSION_BUS_ADDRESS" ;
then eval `sudo -u $ON_USER dbus-launch --sh-syntax --exit-with-session`
fi
echo "Current user's name is: $ON_USER"
sleep 5
--------------------------------------------------------

call sudo commands as: 

sudo -u $ON_USER "DBUS_SESSION_BUS_ADDRESS="$DBUS_SESSION_BUS_ADDRESS command

---

