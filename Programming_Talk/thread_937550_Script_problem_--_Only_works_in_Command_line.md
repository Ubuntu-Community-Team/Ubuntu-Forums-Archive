---
title: "Script problem -- Only works in Command line"
date: 2008-10-04
forum: Programming Talk
---

### Post by Scyron on 2008-10-04
I'm writing a extremely basic bash script that unmounts any current items in /media/cdrom, mounts an iso there, and then runs a executable on the mounted disk using wine. Here's the gist:

```

#!/bin/bash
# mount_and_run

sudo umount '/media/cdrom'
sudo mount -o loop -t iso9660 '/iso/location' '/media/cdrom'
wine '/media/cdrom/run.exe'

```

[LIST]
[*]When I run this script by typing "mount_and_run" in the terminal, it works perfectly.
[*]When I click the script and select "Run", it runs the executable (if the iso is already mounted) but does not unmount or mount.
[*]When I click the script and select "Run in terminal", it unmounts and mounts but does not run the executable.
[/LIST]

In practice, I have to open the script twice for it to work in the GUI. I surmise problem (a) is that the script will not run sudo commands from GUI choices, and problem (b) is that the script completes each command and quits, not leaving the program running.

I've tried workarounds involving launchers, but to no avail. Is there anyway I can get the script to run in the GUI like it does in the terminal?

---

### Post by dwhitney67 on 2008-10-04
Change the "wine" line to:
```
wine /media/cdrom/run.exe &
```
It looks like you were trying to "wine" a string, and not a program.  Also, it might be necessary to run the program in the background, thus allowing the script to end, yet your Windoze program to continue running.

P.S.  If you are expecting to be prompted to enter a sudo password, then setup your gnome applet to "Run in terminal".

---

### Post by Scyron on 2008-10-04
:confused:

For some reason, the program refuses to load adequately in the background with '&' and still closes when the script ends (also, the quotes weren't an issue it seems). Hm.

Ah well. I came up with a decent workaround of using a small non-terminating process on the last line (at the moment cpp) to prevent the script from ending. Your tips set me on the right path, so thank you for that.

---

### Post by dwhitney67 on 2008-10-04
Here's a simple way to keep a script from ending (unless the operator presses ctrl-C):
```
#/bin/sh

# ...

while [ true ]
do
    sleep 1
done
```

---

### Post by geirha on 2008-10-04
Replace sudo with gksudo and it will ask for the password graphically instead of through a terminal.

Secondly, I would add that iso to /etc/fstab, with a line like this:

```
/iso/location /media/cdrom iso9660 loop,user,noauto 0 0
```
The *user* option will allow you to mount and unmount it as a regular user (without sudo).

If you add the fstab-line, you could make the script into:
[php]
#!/bin/bash
# mount_and_run

mount '/iso/location'
wine '/media/cdrom/run.exe'
while pidof some.exe &>/dev/null; do
  sleep 5
done
umount '/iso/location'
[/php]

It sounds like the /media/cdrom/run.exe forks into a different process, so run it manually once, and run **ps -ef | grep exe** and identify the name of the new process it runs, then replace some.exe with that. The while loop should run untill that process disappears, and then unmount the iso again.

---

### Post by Scyron on 2008-10-04
Geirha's solution works perfectly. Thank you very much.

---

