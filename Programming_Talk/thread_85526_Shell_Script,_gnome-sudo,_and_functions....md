---
title: "Shell Script, gnome-sudo, and functions..."
date: 2005-11-02
forum: Programming Talk
---

### Post by audax321 on 2005-11-02
Hello,

   I'm writing a shell script right now that needs to run a command as root using gnome-sudo. This one line is executed in a function and its execution is to be followed by another function. The problem I have is that the first function is exiting as soon as gnome-sudo runs instead of waiting for the command that gnome-sudo is running as root to finish. So the function following the first one is not working.

e.g.

```

MOUNT_ISO()
{
	gnome-sudo -m "Enter password for root access." -t "Got r00t?" "mount -r -o loop "$1" /media/Filesystem\ Image" &
}


PROCESS_ISO()
{
	#do stuff
}


# MAIN SCRIPT CODE
MOUNT_ISO "$1"
PROCESS_ISO

```

So, in the above, MOUNT_ISO is being called, but the function exits and calls PROCESS_ISO before the ISO file has even finished mounting.

What I need it to do is completely mount the iso before calling PROCESS_ISO.

Thanks for any help with this. :???:

---

### Post by audax321 on 2005-11-03
I came up with this as an alternative in the MOUNT_ISO function, but I'm not sure if this is less secure than gnome-sudo.

```

	root_password=$(zenity --title "Enter root password..." --entry --hide-text --text "Enter root password to mount image:")
	sudo mount -r -o loop "$1" /media/Filesystem\ Image
	echo "$root_password"

```

---

### Post by audax321 on 2005-11-03
Okay I just read the sudo man page and it says that sudo can be used to get the password from stdin. Is there a way to redirect stdin to the root_password variable rather than echo the variable? Or can stdin only be redirected to files?

---

### Post by audax321 on 2005-11-04
I'm surprised no replies! I thought this would be a pretty basic question. Oh well, I guess you're all to busy with C to mess with shell scripts :)

Anway, I just read that using sudo -S causes the password to show up on 'ps -auxww' (I have no idea what this is), and it allows any user on the system to view the password. So, I guess the best way is to just use echo as I did above. Oh well, it works, I'm happy.

Now, when I mount an ISO I can have it do things to the files in the ISO :)

---

### Post by Retrix on 2005-11-04
In your original script, remove the & at the end of the gnome-sudo line... it is causing that process to be backgrounded and letting the rest continue. Your other approaches look like incredibly insecure ways of doing what you want.

---

### Post by audax321 on 2005-11-04
Yup, thought that was insecure as well. Thanks, removing the & fixed it. I got that line from someone and had no idea why that & was even there. Thanks. :)

---

