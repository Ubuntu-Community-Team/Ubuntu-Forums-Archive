---
title: "HOWTO: A quick way to connect to your bluetooth headset"
date: 2006-07-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Chrissss on 2006-07-11
Hi!

I think working with a bluetooth Headset is pretty annoying with linux. There's no way to quickly connect to your headset and get a visual feedback that the connection works. So here's a solution for that.

A small script which enables the connection and shows a popup via libnotify on your desktop. It will look like like this. 

[[img]http://img471.imageshack.us/img471/9301/bildschirmfoto5xv.png[/img]](http://imageshack.us)

Please note: This won't help you to solve problems with your BT headset. You need a already configured bluetooth setup for this how-to. So before trying to do this how-to, make sure your setup is OK. For help how to do this, look e.g. here

[https://help.ubuntu.com/community/BluetoothSkype](https://help.ubuntu.com/community/BluetoothSkype)

To get this working make sure **libnotify-bin** is installed on your system
```
sudo apt-get install libnotify-bin
```
After that, you create the script
```
sudo gedit /usr/local/bin/headsetconnect
```
and paste this content
```
#!/bin/bash

# HeadsetConnect 1.0 connect by Chrissss
# you need libnotify-bin to run this script

# Enter the bluetooth address of your headset here
MAC=xx:xx:xx:xx:xx:xx

# Localisation
TITLE="Bluetooth"
CONNECTED="Connection to headset established."
ALLREADYCONNECTED="Connection to headset already exists."
FAILED="Connection to headset failed!"
BTLOGO=/usr/share/icons/gnome/48x48/stock/io/stock_bluetooth.png

# Now the magic
PID=`pidof btsco`

if [ ! $PID ]
then
  btsco -v -s -f $MAC
  if [ -e /tmp/bt_headset_connected ]
  then
    notify-send -i $BTLOGO -t 3000 "$TITLE" "$CONNECTED"
  else
    notify-send -i gtk-dialog-warning -t 3000 "$TITLE" "$FAILED"
    killall btsco
  fi
else
  notify-send  -u critical -i gtk-dialog-info -t 3000 "$TITLE" "$ALLREADYCONNEC
fi
```
Make sure to replace the "xx"s with the correct BT address of your headset. After that make the script executable
```
sudo chmod 755 /usr/local/bin/headsetconnect
```
Well, you're done. Call 
```
headsetconnect
```
out of a terminal window, or even better, put a starter inside the gnome bar.

CU
 Christoph

---

### Post by blanny on 2006-11-02
I think the script got cut off.  Do you think you could attach it?

blanny

---

### Post by mikalh on 2006-11-03
My new headset's still charging, so I haven't been able to try the script properly yet, but I think the only thing that got cut off was
"$ALLREADYCONNEC
to 
"$ALLREADYCONNECTED"

---

### Post by dave_abrahams on 2007-05-08
FYI, this isn't working reliably for me.  It's much less slick (e.g. runs in foreground), but a script containing

```

sudo modprobe snd-bt-sco
dbus-send --system --dest=org.bluez /org/bluez/hci0 org.bluez.Adapter.SetMode string:discoverable
btsco -v  00:03:89:F1:7A:95

```

*does* work reliably for me.  I'd like to find a way to integrate the two.

---

### Post by joeashcraft on 2007-05-13
How did you find the MAC address of your headset? In the SkypeBluetooth howto it says to use kbluetoothd. I couldn't find that in the repos, and i'm using gnome. any ideas?

---

### Post by Aetherius on 2007-05-14
Didn't know where else to post this but I made something similar. This script will search and display all available bluetooth devices and allow you to pick one. Works great for me, but theres only 3 BT devices in range so it needs some real-world testing.

dependencies:

```
bluez-utils bluez-btsco zenity
```

please run 
```
sudo modprobe snd_bt_sco
```

if you haven't already ;)

```
#!/bin/bash
killall btsco
zenity --info --text="Click ok to search for your headset. Please ensure that your headset is in 'discoverable' mode."
results=`hcitool scan`
results=${results:13}
declare -a macaddresses
declare -a names
i=1
temp2=""

while [ -n "$results" ]; do
	temp=$results
	macaddresses[$i]=${temp:0:18}
	results=${results:18}
	temp=${results%00:*}
	names[$i]=$temp
	results=${results:${#temp}}
	i=$i+1;
done

if [ 0 -lt ${#macaddresses[@]} ]; then
	address=`zenity --text="Please select your headset from the following list.\
	\nIf your headset does not appear here click cancel." --list --column Address --column Name  ${macaddresses[1]} "${names[1]}"  ${macaddresses[2]} "${names[2]}"  ${macaddresses[3]} "${names[3]}"  ${macaddresses[4]} "${names[4]}"  ${macaddresses[5]} "${names[5]}"  ${macaddresses[6]} "${names[6]}"  ${macaddresses[7]} "${names[7]}"  ${macaddresses[8]} "${names[8]}"  ${macaddresses[9]} "${names[9]}"  ${macaddresses[10]} "${names[10]}" `
	if [ -n "$address" ]; then
		btsco -f -r -s $address
		if [ -a /tmp/bt_headset_connected ]; then
			zenity --info --text="Connection Successful!"
		else
			zenity --warning --text="Something's not right here, check the README and try again."
		fi
	else
		zenity --warning --text="Please ensure you device is discoverable and restart this program to search again."
	fi	
else
	zenity --warning --text="No bluetooth devices detected. Please ensure you device is discoverable and restart this program."
fi
```

Please criticize comment and bug-report, sorry if I'm stepping on toes Chrissss

---

### Post by hexo1125 on 2007-05-14
I installed bluez-utils bluez-btsco zenity already.
However, sudo modprobe btsco returns module not found.
I also tried using module-assistant to search for btsco and cannot find it.

Do I have to build that module somehow?

---

### Post by Aetherius on 2007-05-14
sorry

```
sudo modprobe snd_bt_sco
```


my bad :corrected

---

### Post by hexo1125 on 2007-05-14
Actually, I also tried snd_bt_sco and still I cannot find the module.
I did a quick google on it and found that
> 
For SCO (two-way voice quality audio) you need a kernel with the emu10k1 driver selected (this is one of the drivers that forces the inclusion of the implementation of "snd_hwdep_new")


It also has somethng to do with ALSA I think.
I'm using edgy with custom compiled 2.6.19 kernel. I might not have selected that.

.. or maybe it's something else...

---

### Post by glennric on 2007-05-15
> **hexo1125 said:**
> Actually, I also tried snd_bt_sco and still I cannot find the module.
I did a quick google on it and found that


It also has somethng to do with ALSA I think.
I'm using edgy with custom compiled 2.6.19 kernel. I might not have selected that.

.. or maybe it's something else...

You have to make sure CONFIG_HWDEP_NEW is set (as you mentioned above) and compile the kernel module for your custom kernel.  The source for this is included with the sources for btsco in a subdirectory called kernel.

---

### Post by jeremyrnelson on 2007-09-22
I've read forums and tips and tricks and a little bit of everything just trying to get my headset working for the purposes of Skype under Ubuntu 7.04 (Feisty).  I'm not trying to do anything else with my Bluetooth adapter.  I'm using a TrendNet  TBW-101UB adapter and a Jabra BT 350 headset.

I wrote this shell script in pieces to first completely reset my bluetooth stack, then to start each piece individually so I could tell where things were failing.  This is NOT a long term solution for you, is not user friendly, and does nasty things that are probably overkill like unload your Bluetooth, hcid, l2cap and other kernel modules.  It also deletes any stored information from your bluetooth module by doing an rm -rf on your /var/lib/bluetooth/ directory.

The goal of this script is to reset everything and start each piece individually so you can get it up and running.  I wanted to get to the point where I could get the headset working reliably every time I reboot the computer, even if that means re-pairing it, entering the PIN, etc., etc.

Note that I had to add "options hci_usb force_scofix=1" (without the quotes) to /etc/modprobe.d/bluez to get my Jabra BT350 working.  Before I did this, it was pairing and pretending to work, but all I got were the beeps indicating that it was connecting and disconnecting, with no audio from (or to) the headset.

You'll need the bluez-pin, bluez-utils and bluez-btsco drivers at a minimum.  I don't use any of the graphical utilities here.  WARNING - If you have other Bluetooth things going on, this will almost surely screw them up.  Use at your own risk!  You'll obviously want to put your headset's MAC address where I've got mine.

Here's the script:

read -p "Remove Bluetooth adapter and put headset into peering mode"
sudo killall skype
sudo /etc/init.d/bluetooth stop
sudo killall btsco 
sudo killall hcid
sudo killall passkey-agent
sudo rmmod snd_bt_sco
sudo rmmod rfcomm
sudo rmmod l2cap
sudo rmmod hci_usb
sudo rmmod bluetooth
sudo rm -rf /var/lib/bluetooth/*

read -p "Replace Bluetooth adapter"

sudo /etc/init.d/bluetooth start
sleep 3
sudo passkey-agent --default /usr/bin/bluez-pin &
sleep 3
sudo modprobe snd_bt_sco
sleep 3
sudo hciconfig hci0 voice 0x0060
sleep 3
sudo hcitool scan
sleep 3
sudo hcitool inq
sleep 3
sudo hcitool con
sleep 3
sudo hcitool cc 00:13:17:84:96:34
sleep 3
sudo hcitool con
sleep 3
sudo hcitool auth 00:13:17:84:96:34
sleep 3
sudo sdptool browse
sleep 3
sudo btsco -v -f -r -s 00:13:17:84:96:34
sleep 3
aplay -B 1000000 -D plughw:Headset /usr/share/sounds/generic.wav 
sleep 3
skype &

---

### Post by shadowh511 on 2008-01-21
i get:```

sam@sam-laptop:~$ sudo headsetconnect
/usr/local/bin/headsetconnect: line 21: btsco: command not found
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
btsco: no process killed

```

---

