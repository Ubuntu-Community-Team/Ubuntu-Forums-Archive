---
title: "HowTo: Beep internal PC speaker on usb hotplug"
date: 2008-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by chewearn on 2008-06-22
[B][SIZE=3]A. Introduction[/SIZE]
[/B]
I came upon this [page]("http://www.nslu2-linux.org/wiki/Info/USBSlotsAndBuses") when playing around with a Linksys NSLU2.  After understanding the script at the bottom of that page, it occurred to me that I could do something similar for an Ubuntu PC.  Wouldn't it be nice for the PC speaker to beep when you plug/unplug a USB device?  I went about modifying the script to make a simpler one for beeping the internal PC speaker in Ubuntu.

Note: I am referring to the internal PC speaker, not the audio output from the sound card.



[B][SIZE=3]B. Prerequisite[/SIZE]
[/B]
Tested OK in the following systems:
1. Ubuntu Intrepid 8.10 86_x64
2. Ubuntu Hardy 8.04 86_x64
3. Ubuntu Hardy 8.04 i386
4. Ubuntu Gutsy 7.10 i386

The following steps rely on the terminal.  Open a terminal window by:
Panel menu > Application > Accessories > Terminal

Then, copy/paste the codes for each of the steps.



[SIZE=3][B]C. Install
[/B][/SIZE]

[B]1. Install beep
[/B]
This will install the beep program, that will emit the sound from the PC speaker.
```
sudo apt-get install beep
```.

[B]2. Test beep
[/B]
```
beep
```You should hear a beep from the PC speaker.


[B]3. Create the script file
[/B]
```
cd ~

cat > usb-hotplug.sh << "EOF"
#!/bin/bash

LOCKFILE="/tmp/usb-hotplug.lock"

# Lock to convert multiple triggers to single run
if ( set -o noclobber; echo "$$" > "$LOCKFILE" ) 2> /dev/null; then
    trap 'rm -f "$LOCKFILE"; exit $?' INT TERM EXIT

    BEEP="/usr/bin/beep"
    STATFILE="/tmp/whatisinusb"
    CURR=`lsusb`
    PREV=`cat $STATFILE`

    if [ "${#CURR}" -gt "${#PREV}" ] ; then
        $BEEP -l 100 -f 2000 -n -l 150 -f 3000
    fi

    if [ "${#CURR}" -lt "${#PREV}" ] ; then
        $BEEP -l 100 -f 3000 -n -l 150 -f 2000
    fi

    if [ "$CURR" != "$PREV" ] ; then
        echo "$CURR" > $STATFILE
    fi

    rm -f "$LOCKFILE"
    trap - INT TERM EXIT
fi

EOF
```.

[B]4. Move the script to /bin
[/B]
```
sudo cp ~/usb-hotplug.sh /bin/usb-hotplug.sh
```.

[B]5. Make the script executable
[/B]
```
sudo chmod +x /bin/usb-hotplug.sh
```.

[B]6. Add udev rule to trigger the script upon an usb hotplug event
[/B]
```
echo BUS==\"usb\", RUN+=\"/bin/usb-hotplug.sh\" | sudo tee -a /etc/udev/rules.d/80-programs.rules
```.


[B][SIZE=3]C. End notes[/SIZE]
[/B]
That's it!  It should work immediately, without any reboot.



[SIZE=3][B]D. Uninstall
[/B][/SIZE]
If you find the beepings irritating after a while, you can remove it by:


[B]1. Remove the udev rule
[/B]
Fire-up a text editor with root privilege.  If you are using Ubuntu/gnome, run the command below:

```
gksudo gedit /etc/udev/rules.d/80-programs.rules
```Delete the line:
```
BUS=="usb", RUN+="/bin/usb-hotplug.sh"
```.

[B]2. Remove usb-hotplug.sh
[/B]
```
sudo rm /bin/usb-hotplug.sh
```.

[B]3. Optional: remove beep
[/B]
```
sudo apt-get remove beep
```.

.

---

