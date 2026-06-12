---
title: "How to mount ramdisk upon startup"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by tckotb on 2011-09-22
Whats the easiest way to mount a ramdisk upon startup? Preferably answer with directions for terminal.

---

### Post by Lisiano on 2011-09-22
No need. It's already there in /dev/shm. It has 50% of your RAM as possible space, by default (Don't worry, unused shm space is not lost unlike in Windows). Also once Ubuntu 11.10 hits the scene you will also find it in /run/shm

---

### Post by tckotb on 2011-09-22
**Edit*** Oh, I see.

--And I have ubuntu 10.04.

---

### Post by tckotb on 2011-09-22
What was that about unused shm space?

---

### Post by Lisiano on 2011-09-22
No. /dev/shm is a mountpoint so you see it as a folder and can do stuff inside it like in any other mountpoint or folder.
And by auto copying you could tell your PC to do that but could you say what exactly you need to copy there? I could show you how to do that later (Eg: File, files (Both never move), folder (Files inside might change)


When you put something inside /dev/shm, some space in RAM get's allocated to that file, if you delete it, it get's freed. In Windows if you create a RAMDisk, the RAM is permanently allocated for the whole RAMDisk.
As in, in your RAM, /dev/shm never uses more than it needs to.

---

### Post by tckotb on 2011-09-22
Well I need all files and sub directories in /home/user/temp/ to go into /dev/shm/, then at shutdown go back into /home/user/temp/.

---

### Post by tckotb on 2011-09-22
and the files need to be copied over to /dev/shm before a specific init script runs.

---

### Post by Enigmapond on 2011-09-22
You realize that the information/data you move there is volatile and can get wiped or corrupted if there is a loss of power. Just saying this isn't such a great idea.

---

### Post by tckotb on 2011-09-22
Dont worry about the data being wiped, I already set up a cronjob to back it up every hour.

---

### Post by Enigmapond on 2011-09-22
I wasn't worrying...it's your data and you failed to mention the cronjob to backup...

---

### Post by tckotb on 2011-09-22
K, but can you tell me how I can have the data moved into the ramdisk at boot, and taken out on shutdown?

---

### Post by Lisiano on 2011-09-22
Okay, to copy on the files on boot. You could set cron to auto copy the files on boot.
Open a terminal and type the following
```
export EDITOR=nano
crontab -e
```
Now add this line
```
@reboot cp -rpf /home/user/temp /dev/shm
```
(Correct me if I'm wrong but I think user crontabs work even when the user is not logged in)
(@reboot works on boot as well, not just reboots)
Now press Ctrl+O -> Enter -> Ctrl+X

For the shutdown, this is a bit tricky and risky.
As a AI known to some people would say:
"Federal regulations require me to inform you that this next step is... looking pretty dangerous"
So. This step is dangerous, might eat your cat, break your flowerpot, take all your money, point fingers at you and laugh.
To minimize the risk we will edit a system file that is responsible for unattended upgrades.
Type this
```
gksudo gedit /etc/rc0.d/S10unattended-upgrades
```
Or if you really liked nano
```
sudo nano /etc/rc0.d/S10unattended-upgrades
```
Add this line```
cp -rpf /dev/shm/temp /home/user/
``` right after the comments end (The ones with #) and the PATH, NAME and DESC lines. So it should look like this (Might be different since I'm on 11.04)
[PHP]#! /bin/sh
#
### BEGIN INIT INFO
# Required-Start:
# Required-Stop:
# Provides:          unattended-upgrade-shutdown-check
# Default-Start:     
# Default-Stop:      0 6
# Short-Description: Check if unattended upgrades are being applied
# Description:       Check if unattended upgrades are being applied
#                    and wait for them to finish
### END INIT INFO


PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=unattended-upgrades
DESC=unattended-upgrades

cp -rpf /dev/shm/temp /home/user/

set -e

case "$1" in
  start|stop)
        echo -n "Checking for running $DESC: "
        python /usr/share/unattended-upgrades/unattended-upgrade-shutdown
        ;;
  restart|force-reload)
        # nothing
        ;;
  *)
    N=/etc/init.d/$NAME
    echo "Usage: $N {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0
[/PHP]Don't edit anything else. Save the file and now manually copy the temp folder to /dev/shm (Not contents, the folder)

---

### Post by Enigmapond on 2011-09-22
You would need to write a small copy/move script and place it in /etc/init.d/  directory and chmod +x to make it executable. I'm not sure where the reverse script would go for shutdown. I'm only guessing as that directory is the boot...

---

### Post by Lisiano on 2011-09-22
Oh. Didn't notice about a init script, just add this at the beginning of the script instead of crontab
```
cp -rpf /home/user/temp /dev/shm
```

Also you can just add this on the stop rule in the init script instead of editing /etc/rc0.d/S10unattended-upgrades
```
cp -rpf /dev/shm/temp /home/user/
```

---

