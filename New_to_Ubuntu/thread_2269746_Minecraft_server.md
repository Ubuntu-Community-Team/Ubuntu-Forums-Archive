---
title: "Minecraft server"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2015-03-17
Clearing up post. I posted in haste, my upstart script was fine. I found the trouble was with my script.

---

### Post by ian-weisser on 2015-03-17
Here's my own Upstart job for my Minecraft server. I hope it helps.
It uses a different uid and file location than yours, so don't cut-and-paste it.

```
# description "start and stop the minecraft-server"
start on network-device-up
stop on shutdown

setuid minecraft
chdir /srv/minecraft
exec /bin/sh -c '/usr/bin/java -Xms1024M -Xmx1024M -jar server.jar nogui 2>&1 | logger -t minecraft'

respawn
respawn limit 20 5
```

It runs totally headless. No window at all.

---

### Post by Tadaen_Sylvermane on 2015-03-18
Your example does help. I posted in frustration. The error was with 2 things in my script though. I am out right now, will post script when I get home. The server runs as a regular user now. The upstart job probably needs some clarification, but it does work. 

At this point it is ramdisk enabled, automatic ramdisk backups every 5 minutes. Backs up to file server every hour. I do need to figure a way to get it to stop cleanly on shutdown still.

---

### Post by ian-weisser on 2015-03-18
> **Tadaen_Sylvermane said:**
>  I do need to figure a way to get it to stop cleanly on shutdown still.
Have you tried structuring the job with a pre-start criteria? [http://upstart.ubuntu.com/cookbook/#pre-start](http://upstart.ubuntu.com/cookbook/#pre-start)
If you are able to push all the ramdisk creation and mounting into a pre-start script, the Upstart can start/stop the service for you.

```

start on <criteria>
stop on <criteria>
pre-start <create and mount ramdisk script>
post-stop <backup, unmount, and destroy ramdisk script>

```

---

### Post by Tadaen_Sylvermane on 2015-03-18
```
# /etc/init/minecraft.conf


start on runlevel [2345]
stop on runlevel [016]


pre-start exec /home/jason/bin/mcserver root
post-stop exec /home/jason/bin/mcserver stop

```

if I'm understanding correctly. Here is the script being called.

```
#!/bin/bash
#Tadaen Sylvermane
#Original source material - http://minecraft.gamepedia.com/Tutorials/Server_startup_script


##### variables #####


USERNAME=jason # username to run as on the server & username to ssh to for backups on the file server
MCSOURCE=/media/data/mcsource # source folder
MCRAMDISK=/media/data/mcramdisk # ramdisk mountpoint
SERVER=10.0.1.201 # file server location
SERVICE=$(ls "$MCSOURCE" | grep -i minecraft_server)
INVOCATION="java  -Xmx768M -Xms768M -jar $SERVICE nogui"


##### begin script #####


mc_ramdisk() { # loads the ramdisk on boot else backs up the ramdisk to the sourcefolder
    if [[ ! -f "$MCRAMDISK"/"$SERVICE" ]] ; then
        sudo chown "$USERNAME":"$USERNAME" "$MCRAMDISK"
        chmod 755 "$MCRAMDISK"
        rsync -aAX "$MCSOURCE"/* "$MCRAMDISK"
    else
        rsync -aAX "$MCRAMDISK"/* "$MCSOURCE"
    fi
}


mc_start() { # starts the server
    if pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
        echo "$SERVICE is running!"
    else
        echo "starting ${*********!"
        cd "$MCRAMDISK" && screen -dmS minecraft $INVOCATION
        sleep 7
        if pgrep -u "$USERNAME" -f "$SERVICE" ; then
            echo "$SERVICE is running!"
        else
            echo "couldn't start ${*********!"
        fi
    fi
}


mc_saveoff() { # changes server to read only for clean backup purposes
    if pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
        echo "$SERVICE is running. suspending saves..."
        screen -p 0 -S minecraft -X eval 'stuff \"save-off\"015'
        screen -p 0 -S minecraft -X eval 'stuff \"save-all\"015'
        sync
        sleep 5
    else
        echo "$SERVICE isn't running. not suspending saves."
    fi
}


mc_saveon() { # changes server back to read / write
    if pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
        echo "re-enabling saves now"
        screen -p 0 -S minecraft -X eval 'stuff "save-on"\015'
    else
        echo "$SERVICE isn't running. not resuming saves."
    fi
}


mc_stop() { # stops the server
    if pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
        echo "stopping $SERVICE"
        screen -p 0 -S minecraft -X eval 'stuff "say server shutdown in 10 seconds... saving map"\015'
        mc_saveoff
        sleep 10
        screen -p 0 -S minecraft -X eval 'stuff "stop"\015'
        sleep 10
    else
        echo "$SERVICE wasn't running."
    fi
    if pgrep -u "$USERNAME" -f "$SERVICE" > /dev/null ; then
        echo "error! $SERVICE couldn't be stopped!"
    else
        echo "$SERVICE has stopped."
    fi
}


mc_backup() { # backs up over ssh to file server
    echo "backing up to server now..."
    rsync -aAX --delete-after "$MCSOURCE"/* "$USERNAME"@"$SERVER":/media/data/MCSERVER
    echo "backup to server complete..."
}


case "$1" in
    root) # only to be called from the upstart script on boot
        su -c "/home/${USERNAME}/bin/mcserver start" "$USERNAME"
        ;;
    start)
        mc_ramdisk
        mc_start
        ;;
    stop)
        mc_stop
        ;;
    restart)
        mc_stop
        mc_start
        ;;
    rdbackup)
        mc_saveoff
        mc_ramdisk
        mc_saveon
        ;;
    srvbackup)
        mc_backup
        ;;
    *)
        echo "usage $0 {start | stop | restart | rdbackup | srvbackup}"
        exit 0
        ;;
esac


##### end script #####

```

i have no idea why those few variables are *******

---

### Post by ian-weisser on 2015-03-18
Looks like you wrote an entire sysvinit script there.
Why not just put it in /etc/init.d/ and let Upstart's sysvinit compatibility take it?

If you go the upstart-job route, you will need to break out the pre-start, post-start, pre-stop, and post-stop tasks into small scripts, each in a separate part of the Upstart .conf file.
You don't need to specify start and stop in an Upstart job; all services have start and stop already built-in to Upstart.

---

### Post by Tadaen_Sylvermane on 2015-03-19
it was originally a sysv script. i used it as a template. i changed it to be a normal script so that i could run it as a regular user. guess i can just change it to 755 so my user can activate it. i will go back to an init script. i had wanted to do it the new way as i'm not a fan of sysv. but it its easier then i guess that is why it is still there.

---

### Post by ian-weisser on 2015-03-19
Converting to Upstart is, sooner or later, going to be rather a dead end anyway. Starting with 15.04, Upstart is replaced with systemd.

Nevertheless, Upstart and systemd share a lot of concepts like replacing scripts with config files, and separate pre-start/post-start/pre-stop/post-stop hooks you can use, and using the 'service' command for proper control.

---

### Post by Tadaen_Sylvermane on 2015-03-19
my server distro will be 14.04 for a long time to come unless the whole server dies on me and i have no choice but to replace it. so i'm not worried about that to much. i will do some more reading, adjust my script and work up an upstart job for it. it just has to start the server and stop it at shutdown. nothing more. everything else i want to run as non root. i can add a couple custom upstart only options to my case construct, all with su.

*EDIT*

one reason i have no intention of replacing 14.04 is that is what the host is running. i have no desire to rebuild my kvm setup (not saying its hard, just why bother?). my host is hiding in closet and it's a bit of trouble to dig it out so i can connect a proper monitor & kb to it. and having all of my guests running 14.04 as well means they can all share the same /var/cache/apt/archives. i have a script set to run on the host every sunday at 3 am to upgrade packages on host, then run through the vms (file server & minecraft survival thus far) and do the same. just basic packages, whatever comes with apt-get upgrade. no kernels. saves bandwidth as i only have to download packages once.

---

