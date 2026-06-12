---
title: "Fix Ubuntu idling in boot"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Zyl on 2012-10-26
Hello,

albeit being a complete newbie to Ubuntu and Linux in general I need to do fairly advanced stuff with it. This is specifically because of programming libraries I am required to use in my college course (Robot Operating System (a meta OS)) and the target platform, which is a KUKA YouBot running Ubuntu.

I am running Ubuntu 11.10 Oneiric on my Laptop.

I eventually had most stuff set up, but then noticed I needed to install a proper graphics card driver to use the program for robot simulation (Gazebo). I downloaded the driver from nvidia.com but it prompted me that it could not run while "X Server" was running. To my understanding "X Server" is a program or service related to managing communication between graphics card and screen hardware. (?)

So I did top command, killed the xorg program and got kicked out of my session. "Ubuntu apparantly more hard hearted than Windows, ok."

I then looked up an actual tutorial to do this, which as the first step advised to add the "nomodeset" parameter to the Ubuntu boot menuentry in /boot/grub/grub.cfg. Done that, rebooted, selected that entry in Grub. Problem: Ubuntu does not finish booting anymore. It stops either right after initializing "Pulse Audio" or a few step after failing to configure "Network Interface Security" (approximate wording).

I managed to remove the "nomodeset" parameter through recovery mode, but still no luck. I am also not sure if what I did is even related to the boot failure.

Any suggestions for how to tackle such problem? Would need to redo ~5 hours of work otherwise - rather tell me to reinstall than let me sit and wait for 2 days.
More info:
Graphics card: NVidia GeForce GT540M
NVidia Optimus for hardly reliable GPU switching set up on hardware - cannot be disabled.

Thanks in advance,
Zyl

---

### Post by danielbauwens on 2012-10-26
To get nvidia driver open terminal and type:
```
sudo apt-get install nvidia-current
```
and then reboot.

Daniel

---

### Post by Zyl on 2012-10-26
> **danielbauwens said:**
> To get nvidia driver open terminal and type:
```
sudo apt-get install nvidia-current
```and then reboot.

Daniel
Tried this. It says it is already up to date.

My main concern is that it won't boot properly anymore, as in get to the Desktop.

Graphics drivers are a secondary problem.

---

### Post by danielbauwens on 2012-10-26
Maybe you should update, sometimes helps.

```
sudo apt-get update
```
then:
```
sudo apt-get dist-upgrade
```

Daniel

---

### Post by Zyl on 2012-10-26
> **danielbauwens said:**
> Maybe you should update, sometimes helps.

```
sudo apt-get update
```then:
```
sudo apt-get dist-upgrade
```Daniel
Done. sudo apt-get dist-upgrade took about 5 minutes. Downloaded a lot of stuff. Problem not fixed however.

I noticed the following: Upon boot, it says the following in the first line:
```
could not write bytes: Broken pipe
```I read elsewhere ( [http://forum.ubuntuusers.de/topic/anmeldung-could-not-write-bytes-broken-pipe/](http://forum.ubuntuusers.de/topic/anmeldung-could-not-write-bytes-broken-pipe/) ) that this indicates a mount problem and Ubuntu handling the disk as read-only. 
I then did this command:
```
mount -o remount,rw,errors=remount-ro /
```Also, to reset a broken login session (?):
```
cd /home/zyl
sudo rm .ICEauthority
sudo rm .Xauthority
```

I then chose to continue normal boot from within the recovery mode menu.
It said the following:
```
* Starting load fallback graphics devices             [[COLOR=Red]fail[/COLOR]]
```I tried to reboot again. The broken pipe message is gone, but it now only prints the following discomforting message:
```
* Starting automatic crash report generation          [[COLOR=Red]fail[/COLOR]]
```

Any clues? "Starting load fallback graphics devices [fail]" sounds related to my problem.

---

### Post by Zyl on 2012-10-26
After further research I was able to fix the problem entirely.
Here is how I did it (These instructions are for laptops with NVidia Optimus):
```
**sudo rm /etc/X11/xorg.conf**
**sudo reboot**
**sudo /etc/init.d/lightdm stop** [COLOR=Silver]#note: this throws you out of your current session[/COLOR]
[COLOR=DarkOrchid]Hit Ctrl + Alt + F1 and log in with your account data[/COLOR]
**sudo apt-get purge nvidia-current**
**sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**
**sudo add-apt-repository ppa:bumblebee/stable**
**sudo apt-get update**
**sudo apt-get install acpi-call-tools acpi-call-source bbswitch-dkms bumblebee virtualgl**
**sudo reboot**
```

Bumblebee specifically is the one thing to support NVidia Optimus.

Sources:[list][*][http://www.moonlitdog.com/nvidia_ubuntu](http://www.moonlitdog.com/nvidia_ubuntu)[*]Some russian forum which magically disappeared from my history after dist-upgrade.[/list]

Thanks for your time.

---

