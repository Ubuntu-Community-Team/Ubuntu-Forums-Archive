---
title: "Help with Bash Scripts"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by silark on 2008-07-03
I have an old laptop I installed xubuntu on and plan to use it as a picture frame. I have a few requirements:

1.I should be able to VNC in from my dual boot windows/ubuntu box

2. feh should start automatically on boot 

3.The laptop should automatically sync with pictures on another box

4. The laptop should shut down and wake itself up (Or at least the screen should.

If you have any input on how to do any of this that would be great but the area I am struggling with is number 3 and 4. I think I need to learn some bash scripting and how to use cron tab and I am totally clueless on both. I have tried to follow so guides online but get lost in the bash scripting because I just don't understand enough. If someone could offer a starting point (online guides etc...)that would be great.

Thanks in advance

---

### Post by pytheas22 on 2008-07-03
For #1, you just need to install a vnc server.  This should do it:
```

sudo apt-get install vnc4server
```

then as long as it's running all the time (which the installer should configure it to do), you'll be able to remote in whenever you want.

2. I don't know what feh is, but you can write a script and put it in /etc/init.d to start it at boot.  If you don't know how to do that, I can explain, but it's easy and there are plenty of guides online (make sure you follow one for Ubuntu or Debian, as other distributions do init.d stuff a little differently sometimes).

3. rsync would be a good way to do this.  It can keep your picture folder and the same folder on a remote machine in sync; in other words, it will copy over any new pictures.  It should already be installed on Xubuntu.  [This]("http://www.crucialp.com/resources/tutorials/server-administration/how-to-copy-files-across-a-network-internet-in-unix-linux-redhat-debian-freebsd-scp-tar-rsync-secure-network-copy.php") is a nice guide on using it.  Run it as a cron job every hour or day or whatever, depending on how often you're adding new pictures.  Keep in mind that the remote machine needs to have an ssh service running, which you can install easily with the command:

```
sudo apt-get install ssh
```

in Ubuntu.  ssh runs on any Unix system, including Macs.  I don't know what to do in Windows, but I'm sure there's a way to make rysnc work with a Windows machine.

4. You can write a cron job to shut the machine down at specified intervals, using shutdown -h or suspend commands.  Waking it up is harder; I can't think of a way to do it (maybe you could wake up via LAN but I don't know how to do that, and you'd have to have another machine set to send the signal).

As for the screen, you should be able to configure it to turn off at a set interval of inactivity.  I'm not familiar with Xubuntu so I don't know exactly where to tell you to click, but look through your preferences/administration menu and see if you can find something related to power options.  If you can't find it let me know; in a worst case, you could install the GUI that Gnome uses for power management.

As for editing crontab, take a look at this [guide]("http://ubuntuforums.org/showthread.php?t=102626").  Don't be intimidated; crontab is actually very simple, although I understand that it can be tough if you're not comfortable with bash scripting.  But for what you need to do, you don't need to know much about bash, really.

If you have more questions please feel free to ask.

---

### Post by silark on 2008-07-04
Firstly let me thank you for the quick response and the moral support...something I needed as I have had my fair share of struggles with this project. I am trying to move this project along in steps so have been trying to get feh to run at boot (Feh is a slideshow programme). This is important because I would like to have as little interaction with the frame as possible. I used the following script:

#!/bin/bash
# This file is located at /usr/local/bin/slideshow.sh
#
# Copyright 2004 Adam Franco
# Licensed under the GNU GPL v1.2+ ([http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html))

killall feh unclutter

unclutter &

feh -zZFr -D 1 /usr/share/xfce4/backdrops/


I made this executable and if I double click it it runs my slideshow fine. So I dropped my script into the init.d folder and checked I could run it from there also and it did. Only issue is that on restart the slideshow never started...what am I missing?

---

### Post by Martje_001 on 2008-07-04
Go to a terminal and do:
```
sudo update-rc.d -f name-of-script defaults
```
you haven't linked it to any startup-level yet. That's why it doesn't start.

---

### Post by unutbu on 2008-07-04
If your script is called slideshow.sh, edit 
/etc/rc.local and add
```

/etc/init.d/slideshow.sh
```

just above the last line which should read:

```
exit 0
```

Explanation: /etc/init.d is a repository of scripts, but the scripts only get run if there is a link to them in /etc/rc2.d. (The 2 is the default runlevel).

---

### Post by silark on 2008-07-04
I did try altering the file /etc/rc.local as you advised andeven made it executable as the details in the file say to but had no luck. It almost appears the scripts is running at shut down as I get a n error message relating to feh "Define your home directory it would really help me out" or words to that effect. Any ideas?

Also I notice you have a display of how many times you have been thanked...how do add to that.

---

### Post by pytheas22 on 2008-07-04
> I did try altering the file /etc/rc.local as you advised andeven made it executable as the details in the file say to but had no luck.

But did you run:

```
sudo update-rc.d -f name-of-script defaults
```

You need to do this before the system will run the script at boot.

Also maybe you could add a line to the script to make it do something that you would notice, like:
```

touch ~/Desktop/the_script_ran
```

It could be the case that the script is running but you don't realize it (because feh is dying for some other reason).  If you add the line above to your script and a file appears on your desktop called "the_script_ran," then you know at least that the script was executed successfully, and that the problem lies elsewhere.

Finally, how does feh work?  If it depends on X (the graphical server), then running it at boot might not work...you may need to wait a little longer, until you log into xfce (your desktop).  Also, you're running feh as root now, which could be another problem.

(does anyone know if xfce has an easy way to run commands at login à la Gnome Sessions?)

---

### Post by unutbu on 2008-07-04
How to turn your linux box into a digital picture frame:

Note: I learned this from [http://www.adamfranco.com/archives/3](http://www.adamfranco.com/archives/3) and [http://ubuntuforums.org/showthread.php?t=843646](http://ubuntuforums.org/showthread.php?t=843646)

1) Install the feh and unclutter packages
```

sudo apt-get install feh unclutter
```

2) Hook up a GRUB boot stanza to runlevel 3 

2A) Tell your linux box what to do if it encounters the word "runlevel3" in its boot command:
```
gksu gedit /etc/event.d/rc-default
```
Change this:
```
	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif [ -r /etc/inittab ]; then
```

to
```
	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
 	[B]elif grep -q -w -- "runlevel3" /proc/cmdline; then
	    telinit 3[/B]
	elif [ -r /etc/inittab ]; then
```

Save and Quit gedit.

2B) Put "runlevel3" in a new GRUB boot stanza:


```
gksu gedit /boot/grub/menu.lst
```

About 2/3 of the way down the file you will find a line that says
```

## ## End Default Options ##
```

Below that line you will find your boot stanzas. My first boot stanza looks like this:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```
Yours will be different, so don't just copy mine. Make a duplicate copy of your boot stanza, and then modify the duplicate changing the title to Slideshow, and adding "runlevel3" to the end of the kernel line:

```
title		**Slideshow**
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro **runlevel3**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed ro 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

3) Make runlevel 3 the default boot option
Go back up to the top of menu.lst. You will see a line that says

```
default		0
```

0 means the first boot stanza since GRUB starts count at 0. If you placed Slideshow as your first boot stanza, then there is nothing here that needs to be changed. If your default number is different, or if you placed the Slideshow boot stanza in some place other than as your first boot stanza, then change the number here appropriately.

For most machines, there is nothing here that needs to be changed.
Save and Quit gedit.

4) Make /etc/init.d/slideshow part of the runlevel 3 boot sequence
4A) Make the slideshow boot script
```
gksu gedit /etc/init.d/slideshow
```
Put this in the empty file:
```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
. /lib/lsb/init-functions

case "$1" in
    start)
	echo -n "Starting pictureframe"
	/usr/bin/X11/xinit /home/**USERNAME**/bin/slideshow.sh -- :1
        ;;
    restart|reload|force-reload)
        ;;
    stop)
	killall feh unclutter X
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```
Change USERNAME to your own username! 

Save and Quit gedit

4B) Make the script executable:
```
sudo chmod 755 /etc/init.d/slideshow
```

4C) Link the slideshow script to /etc/rc3.d:
```
sudo ln -sf /etc/init.d/slideshow /etc/rc3.d/S99slideshow
```

5) Make the /home/USERNAME/bin/slideshow.sh script that is called by /etc/init.d/slideshow

5A) I keep all my scripts in a directory called bin. If you wish to put your script somewhere else, by all means feel free to do so. Just be sure to edit /etc/init.d/slideshow so it will call slideshow.sh with the right path.

```
cd
mkdir bin
gedit bin/slideshow.sh
```

Put this in slideshow.sh:
```
#!/bin/bash
unclutter &
HOME=/home/**USERNAME** feh -zZFr -D 3 /path/to/your/images
```

Again, change USERNAME to your real username.
"-D 3" means display each picture for 3 seconds. Change 3 to fit your taste.

5B)  Make the script executable:
```
chmod 755 bin/slideshow.sh
```
Reboot and enjoy.

---

### Post by silark on 2008-07-08
Sorry it has been a couple of days will try these suggestions in the order they are presented when I get home. Could someone please give me a breakdown of what each portion of this command does.

sudo update-rc.d -f name-of-script defaults

Also I presume I would use:
sudo update-rc.d -f slideshow.sh defaults

is this correct.

---

### Post by unutbu on 2008-07-08
sudo update-rc.d -f name-of-script defaults
sudo means "Give me root powers"

update-rc.d is the name of the command. It creates symlinks from /etc/rc#.d to /etc/init.d. These symlinks control what scripts are run at boot time.

"-f" means force removal of symlinks. Since the rest of this command is only starting and stopping services, and not removing anything, the -f flag is meaningless in this context.

name-of-script refers to the script /etc/init.d/name-of-script

defaults means update-rc.d will make symlinks to start the service on runlevels 2,3,4,5, and stop the service on runlevels 0,1,6.

In the instructions I posted in post #8 I made the symlinks manually, with the command
```
sudo ln -sf /etc/init.d/slideshow /etc/rc3.d/S99slideshow
```
so there is no need to use update-rc.d if you want to follow post #8.

Post #8 allows your computer to boot into runlevel 3 (as default) and make it into a digital picture frame without you having to type anything. But it also allows you to use the GRUB menu to select a normal boot, so if you wanted to, your computer can be used like a normal computer.

If you run 
```
sudo update-rc.d -f slideshow.sh defaults
```

Then you will be setting up symlinks which will tell the computer to run the slideshow.sh script no matter if you boot into runlevel 2,3,4 or 5. In my opinion, that's not the best way. (That would conflict with post #8).

Some posters have been suggesting 
sudo update-rc.d -f slideshow.sh defaults
and they are right -- it could work, it's just not the way I chose to do things in post #8. If you have used this command, then there is a bit of cleanup necessary:

```
sudo rm -i /etc/rc0.d/*slideshow*
sudo rm -i /etc/rc1.d/*slideshow*
sudo rm -i /etc/rc2.d/*slideshow*
sudo rm -i /etc/rc3.d/*slideshow*
sudo rm -i /etc/rc4.d/*slideshow*
sudo rm -i /etc/rc5.d/*slideshow*
sudo rm -i /etc/rc6.d/*slideshow*
```

Perhaps the easiest way to manage these symlinks is to use the sysv-rc-conf package. (See attachment)
You can turn on/off scripts (services) simply by using arrow keys to select the service and pressing the spacebar to toggle.

You'll get a better idea what's going on with the runlevels and services here: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Brief summary is:
runlevel 0: shutdown
runlevel 1: single user mode
runlevel S: executed on every boot
runlevel 6: computer reboot
runlevel 2--5: Custom levels. Default is 2.

Most users never use runlevel 3,4 or 5. 

Finally, I mentioned in post #5 that if you put /etc/init.d/slidshow.sh in /etc/rc.local, then it will run at boot. While that is true, the complete solution is in post #8, so please remove /etc/init.d/slidshow.sh from /etc/rc.local.

---

### Post by silark on 2008-07-20
Ok I have been going in circles trying to do what you have all suggested and I decided to try and follow another tutorial I found and have installed Damn Small Linux. Another reason for this was Xubuntu was really slow on this old laptop and DSL seems to be a lot more zippy...it wouldn't matter once on the wall but when i'm working on it like this it helps make the failed attempts at getting this working a little more bearable. That being said I have a question about one of the steps in the tutorial i have been following. They have me edit my bash profile and I have little idea what they are actually having me do. What I do know is that before i changed this DSL booted up into xwindow now it stops at a cli after it starts sshd. Whilst this is useful in it's own way just like my original question i want it to start the slideshow automatically. Can someone help me decipher what the edit to the bash file actually does...i kinds get that there is an if statement in there defining whether or not to startx but do understand enough. I believe the answer to my problem is here because if i am at the machine and I type startx and xserver? starts and then the slideshow starts. Thanks again for the support.


-------EDIT-------

Also I can type startx at in my ssh session and it starts does the same thing as when i type it into the machine...but if I close my ssh session the slidshow stops, which is obvisously not what I want.

#!/bin/bash
export IRCNICK=DSL
export DISPLAY=:0
SSH=`env | grep SSH_CONNECTION`
RUNLEVEL=`runlevel|cut -f2 -d' '`
if [ -z &#8220;$SSH&#8221; ]; then
   if [ $RUNLEVEL -eq 5 ]; then
       startx
   fi
fi
cd /home/dsl/frame


-----UPDATE-----------

I figured it out I had copied and pasted from the tutorial I was working from and somehow the " had been turned into . so the line if [ -z &#8220;$SSH&#8221; ]; then became if [ -z .$SSH. ]; then  so now my laptop boots directly into the slideshow...some progress at last. I know I am using DSL and this is an Ubuntu forum but will likely keep updating in case this helps soomeone else.

---

### Post by bishounen on 2008-10-21
I apologize for resurrecting this older thread, but this seems to be the only thread dedicated to using xubuntu for a digital picture frame.

I have been following unutbu's great directions from post #8, but for some reason, my xubuntu 8.04 install keeps booting to the login screen, rather than starting the slide show.  I know the slide show works, I can double click it and off it goes.  But for some reason my system will just not display the slide show on boot.

Can anyone help?

EDIT:

I suspect the problem may be the rc-default file.  here is mine:

> # rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif grep -q -w -- "runlevel3" /proc/cmdline; then
	    telinit 3
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script

I not certain, but i think it&#347; defaulting to runlevel2, even though I specifying runlevel3.  Not sure how to fix this without breaking my ability to log in regularly.

---

### Post by unutbu on 2008-10-21
bishounen, would you please post your 
/boot/grub/menu.lst ?

Also please post the output of 
```

ls -l /etc/rc3.d
```

---

### Post by bishounen on 2008-10-21
No problem.  Here&#347; my menu.lst

> ## ## End Default Options ##

title		Slideshow
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0d162af9-e480-4de5-b03e-66ec207ab6a3 ro quiet splash runlevel3
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0d162af9-e480-4de5-b03e-66ec207ab6a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0d162af9-e480-4de5-b03e-66ec207ab6a3 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d162af9-e480-4de5-b03e-66ec207ab6a3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0d162af9-e480-4de5-b03e-66ec207ab6a3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


and the output of that command:

> ~$ ls -l /etc/rc3.d
total 4
-rw-r--r-- 1 root root 556 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-10-20 16:20 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-10-20 16:09 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-10-20 15:35 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-10-20 15:30 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-10-20 15:47 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-10-20 15:30 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-10-20 16:20 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  22 2008-10-20 16:20 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  14 2008-10-20 16:09 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2008-10-20 16:12 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-10-20 15:53 S20cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  22 2008-10-20 16:16 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  23 2008-10-20 15:34 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  19 2008-10-20 16:17 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-10-20 16:08 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  16 2008-10-20 16:20 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-10-20 16:20 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-10-20 16:20 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  13 2008-10-20 16:15 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-10-20 16:08 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-10-20 16:07 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-10-20 16:07 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  17 2008-10-20 16:18 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-10-20 16:09 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-10-20 16:09 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-10-20 15:27 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-10-20 15:27 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  21 2008-10-21 14:10 S99slideshow -> /etc/init.d/slideshow


---

### Post by unutbu on 2008-10-21
Okay bishounen, thanks for the output.
Please post the output of 
```

runlevel
```

Also, do you get the slideshow if you run
```

sudo /etc/init.d/slideshow start
```

---

### Post by bishounen on 2008-10-21
Actually, I found a way around the issue.

I simply added the script to the autostart menu, and then set the system to autologin.  Since it's not going to have a network connection, I'm not worried about the insecurity of that setup, and it works just great!

Admittedly, that doesn't fix my original issue, but it gets me the same result, which is more important to me right now.  thanks for all your help, I'll post when I have it all finished and let you know how it all worked out.

---

