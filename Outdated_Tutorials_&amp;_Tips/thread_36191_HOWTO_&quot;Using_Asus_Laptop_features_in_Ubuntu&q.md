---
title: "HOWTO &quot;Using Asus Laptop features in Ubuntu&quot;"
date: 2005-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by f.prisson on 2005-05-22
This howto contains nothing really new,but I have tried to write a simple guide for not so much experienced users.

Some of the Asus laptops (or even all, I don't know) have different hotkeys and Status LEDs. This howto describes how to use them in Ubuntu.

**Installation**

You need the kernel module asus_acpi which is included in the default kernel. Check whether it's loaded with ```
lsmod | grep asus
``` If it isn't loaded do this with ```
sudo modprobe asus_acpi
```and add the module in /etc/modules with ```
sudo gedit /etc/modules
``` so that it will be loaded automatically on next reboot.

You need the normal linux acpi daemon running. On the top of it you need the asus_acpi daemon which you have to compile yourself. Get the source at [http://sourceforge.net/projects/acpi4asus/](http://sourceforge.net/projects/acpi4asus/).
Copy the archive in a temporary directory of your choice and uncompress it with```
tar -xvjf acpi4asus-0.xx.tar.bz2
``` change the directory with
```
cd ./acpi4asus-0.xx/asus_acpid/
``` As you already have the kernel module you only need to compile the asus_acpi daemon. You need the kernel source, kernel headers, make and gcc for this. For compiling the daemon type ```
make
``` For installing it type ```
sudo make install
``` You now have to copy the directory "samples" to .asus_acpi in your home directory: ```
cp -r ../samples /home/user/.asus_acpi
``` Start the daemon as normal user with ```
asus_acpid &
``` The basic installation is finished now.

**Configuration**

Go to the just copied .asus_acpi directory in your users home directory. In the "events" directory you can define which skript or action should be taken on which event. There are some predefined events, for the four little buttons below of the display which start a browser, mutt and two other application. For changing this behaviour, edit the skripts in the .asus_acpi directory. The Vol up / down keys are also predefined, but you need aumix installed for this.```
sudo apt-get install aumix
``` For getting the right event codes of all ofAutostart of the asus_acpid daemon the special keys, you have to stop the ACPI daemons first: ```
killall asus_acpid
``` and ```
sudo /etc/init.d/./acpid stop
``` Have a look at the "/proc/acpi/events" file with ```
sudo cat /proc/acpi/events
``` By pressing the special keys now, you can see the appropiate event codes. If you have finished leave with ```
Ctrl + C
``` Take a look at 	the examples, for the syntax of your new events. You also can activate the LEDs in the right corner by doing the following (replace 1 with 0 for deactivating): ```
echo 1 > /proc/acpi/asus/mled
``` or ```
echo 1 > /proc/acpi/asus/wled
``` 
[B]
My configuration as an example[/B]

I use the four little buttons for starting applications, no special things here.

The powergear button (event code 5c) is used for activating or deactivating my wireless LAN interface. I use the following skript:```
# module already loaded?
mod=`/bin/lsmod | /bin/grep ipw2100; echo $?`
case "$mod" in
        1) /sbin/modprobe ipw2100
        ;;
esac

# activate or deactivate
stat=`cat /proc/acpi/asus/wled`
case "$stat" in
        0) sudo ifup eth1
           echo 1 > /proc/acpi/asus/wled
           ;;
        1) sudo ifdown eth1
           echo 0 > /proc/acpi/asus/wled
           ;;
esac
```For getting this work, I had to make ifup and ifdown executable for my normal user without requesting a password. I did it that way (better solutions are welcome).

Edit the /etc/sudoers file with ```
export EDITOR=gedit && sudo visudo
``` Add a line ```
myuser ALL = NOPASSWD: /sbin/ifup eth1, /sbin/ifdown eth1
``` 
Test if you are able to activate / deactive the network as normal user without giving password:```
sudo ifup <WLAN interface>
``` ```
sudo ifdown <WLAN interface>
``` I now deactived the auto activation of my wireless interface by commenting the line "auto eth1" in /etc/network/interfaces

If you create the correct event which calls the script above you can activate and deactive your WLAN interface by the powergear button now. The status is shown by the amber LED.

**Getting audiokeys working with xmms**

Create four files named xmms_play, xmms_stop, xmms_forward and xmms_back. Best way is to copy one of the sample event, in that case you only have to change the event code and skript name. The event codes are

stop		43
play		45
back		40
forward		41

Create four skripts in "/home/user/.asus_acpi/" corresponding to the names you used in the events. The commands for xmms are

stop		xmms -s
play		xmms -t
back		xmms -r
forward		xmms -f

**Autostart of the asus_acpid daemon**

I made a simple skript that only includes the line "asus_acpid &" and is called at gnome startup time (set it in System -> Settings -> Session). Don't forget to make the skript executable with```
chmod a+x <skriptfile>
``` 
**I hope this howto was helpful for you. Any kind of questions or feedback is welcome.**

---

### Post by Sam on 2005-05-22
[QUOTE=f.prisson]For getting this work, I had to make ifup and ifdown executable for my normal user without requesting a password. I did it that way (better solutions are welcome).

Make /etc/suders writeable to root ```
sudo chmod 540 /etc/suders
``` Set a root password```
sudo passwd root
``` Become root```
su -
``` Open the file /etc/sudoers```
vi /etc/sudoers
``` Add the following line (press "i" for going in insert mode, replace myuser by your user 	and eth1 by your wlan interface):```
myuser ALL = NOPASSWD: /sbin/ifup eth1, /sbin/ifdown eth1
``` Leave insert mode by pressing Escape and quit the file with "wq!"

Restore the original permissions and exit your root login. This is important, otherwise it would be a security risk. You shouldn't edit this file normally, only if you know what you are doing!
```
chmod 440 /etc/sudoers
``` ```
exit
```[/QUOTE]
Ouch ! What a bad mistake !!!

First, do ask the user to set his root password, sudo do the job very well
Secondly, do NOT change the sudoers permissions
Third, do NOT (read ABSOLUTLY NOT !) use vi to edit your sudoers file !!! Use ONLY visudo instead, it checks for a syntax failure before saving. (or use "export EDITOR=<your favorite editor> && sudo visudo")

---

### Post by f.prisson on 2005-05-22
> Ouch ! What a bad mistake !!!

First, do ask the user to set his root password, sudo do the job very well 

I don't think it's that problem if you know that you have to use root account carefully. I prefer it then using sudo. I wrote it that way because I didn't success with```
sudo gedit /etc/sudoers
``` 
> Secondly, do NOT change the sudoers permissions 
I know that I have to be very careful with that. But is allowing a certain user enabling /  disabling a network interface on a desktop system really a big problem?
> Third, do NOT (read ABSOLUTLY NOT !) use vi to edit your sudoers file !!! Use ONLY visudo instead, it checks for a syntax failure before saving. (or use "export EDITOR=<your favorite editor> && sudo visudo" Sorry, for that, I didn't know its that problem. I will change that.

---

### Post by Sam on 2005-05-22
[QUOTE=f.prisson]I don't think it's that problem if you know that you have to use root account carefully. I prefer it then using sudo. I wrote it that way because I didn't success with```
sudo gedit /etc/sudoers
``` 

I know that I have to be very careful with that. But is allowing a certain user enabling /  disabling a network interface on a desktop system really a big problem?

Sorry, for that, I didn't know its that problem. I will change that.[/QUOTE]
Allowing a certain user enabling/disabling a network interface is not a problem, it's the way you took. For the three points I said, you can avoid this by "export EDITOR=<your favorite editor> && sudo visudo".

You enabled the root account, but you didn't disable it (!). If someone prefers using su instead of sudo, he probably knows how to adapt you guide. And it's a security hole having the root account enabled (IMHO).

Then changing the permissions of the sudoers, that's a bad habit. With this point of view, some users will chmod 777 something just for doing a small update (ok I exaggerate, but it's better to do things in a clean way).

---

### Post by f.prisson on 2005-05-22
> You enabled the root account, but you didn't disable it (!). If someone prefers using su instead of sudo, he probably knows how to adapt you guide. And it's a security hole having the root account enabled (IMHO).

Then changing the permissions of the sudoers, that's a bad habit. With this point of view, some users will chmod 777 something just for doing a small update (ok I exaggerate, but it's better to do things in a clean way) I already changed and that and I agree with you, no nice way. :? > For the three points I said, you can avoid this by "export EDITOR=<your favorite editor> && sudo visudo" I will use this in my howto, easier to edit by this way.

Thank you for feedback.

---

### Post by Sam on 2005-05-22
[QUOTE=f.prisson]I already changed and that and I agree with you, no nice way. :?
I will use this in my howto, easier to edit by this way.

Thank you for feedback.[/QUOTE]
You're welcome !
It looks good now. :wink:

---

