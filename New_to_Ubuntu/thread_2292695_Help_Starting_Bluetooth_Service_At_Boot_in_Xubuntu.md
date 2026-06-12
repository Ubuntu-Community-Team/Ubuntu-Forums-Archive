---
title: "Help Starting Bluetooth Service At Boot in Xubuntu Vivid (amd64)"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by lambdafox on 2015-08-30
After boot, I can do the following in terminal:

```
sudo /etc/init.d/bluetooth start
[sudo] password for randyb: 
[ ok ] Starting bluetooth (via systemctl): bluetooth.service.

```

Then if I check the status, I see:

```
:~$ /etc/init.d/bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2015-08-30 10:33:33 EDT; 12s ago
 Main PID: 3536 (bluetoothd)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;3536 /usr/sbin/bluetoothd -n

Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: DIS cannot ...d
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Failed to i...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Failed to i...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Failed to i...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Failed to i...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Failed to i...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Failed to i...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: Failed to init gatt_example p...n
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: Bluetooth Management interfac...d
Aug 30 10:33:33 RandyDesktop bluetoothd[3536]: bluetoothd[3536]: Bluetooth M...d
Hint: Some lines were ellipsized, use -l to show in full.
```

But if I do this:

```
sudo update-rc.d bluetooth defaults
```

and reboot, blueman will not run and says bluetooth is not started

Checking the status shows this:

```
~$ /etc/init.d/bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
```

I can add the command* /etc/init.d/bluetooth start* to the session and startup list, but it asks for authentication if I do it that way.

---

### Post by Toz on 2015-08-30
Vivid has switched over to systemd. Try using systemctl instead:
```
sudo systemctl enable bluetooth
```

You'll also start wanting to get use to the systemd equivalents:
- systemctl status bluetooth
- systemctl start bluetooth
- systemctl list-units
...etc (see 'man systemctl')

---

### Post by lambdafox on 2015-08-30
> **Toz said:**
> Vivid has switched over to systemd. Try using systemctl instead:
```
sudo systemctl enable bluetooth
```

You'll also start wanting to get use to the systemd equivalents:
- systemctl status bluetooth
- systemctl start bluetooth
- systemctl list-units
...etc (see 'man systemctl')

Thank you.  My question though, was how to start bluetooth at boot.

---

### Post by Toz on 2015-08-31
> **lambdafox said:**
> Thank you.  My question though, was how to start bluetooth at boot.
By issuing: "**sudo systemctl enable bluetooth**"

After reboot, what does the following show:
```
sudo systemctl is-enabled bluetooth
```
```
sudo systemctl status bluetooth
```
```
sudo journalctl | grep -i bluetooth
```

---

### Post by lambdafox on 2015-08-31
> **Toz said:**
> By issuing: "**sudo systemctl enable bluetooth**"

After reboot, what does the following show:
```
sudo systemctl is-enabled bluetooth
```
```
sudo systemctl status bluetooth
```
```
sudo journalctl | grep -i bluetooth
```


```
sudo systemctl enable bluetooth
[sudo] password for randyb: 
Synchronizing state for bluetooth.service with sysvinit using update-rc.d...
Executing /usr/sbin/update-rc.d bluetooth defaults
Executing /usr/sbin/update-rc.d bluetooth enable

```

reboot

```
sudo systemctl is-enabled bluetooth
[sudo] password for randyb: 
enabled
randyb@RandyDesktop:~$ sudo systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
randyb@RandyDesktop:~$ sudo journalctl | grep -i bluetooth
Aug 31 08:41:29 RandyDesktop NetworkManager[658]: <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so
Aug 31 08:43:13 RandyDesktop sudo[3503]: randyb : TTY=pts/5 ; PWD=/home/randyb ; USER=root ; COMMAND=/bin/systemctl is-enabled bluetooth
Aug 31 08:43:34 RandyDesktop sudo[3510]: randyb : TTY=pts/5 ; PWD=/home/randyb ; USER=root ; COMMAND=/bin/systemctl status bluetooth
randyb@RandyDesktop:~$ 
```

The line that says Active: inactive (dead) seems to be the problem

---

### Post by Toz on 2015-08-31
To answer your initial question, the bluetooth daemon (service) is set to start at boot on your system. Unfortunately, it dies and doesn't leave any explanation as to why (which is strange). 

A couple of suggestions:

1. Is bluetooth blocked:
```
sudo rfkill list all
```

2. As root, can you edit the /lib/systemd/system/bluetooth.service file and add in the "[Service]" section the following directive:
```
Environment=SYSTEMD_LOG_LEVEL=debug
```
...save the file and reboot. Perhaps this will leave some extra info in your journal as to why its dying:
```
sudo journalctl -u bluetooth
```
...and
```
sudo journalctl -xb | grep -i bluetooth
```

---

### Post by lambdafox on 2015-09-03
> **Toz said:**
> To answer your initial question, the bluetooth daemon (service) is set to start at boot on your system. Unfortunately, it dies and doesn't leave any explanation as to why (which is strange). ...

```
~$ sudo rfkill list all
[sudo] password for randyb: 
~$ 

```

edit bluetooth.service and reboot

```
~$ sudo journalctl -u bluetooth
[sudo] password for randyb: 
-- Logs begin at Thu 2015-09-03 10:07:35 EDT, end at Thu 2015-09-03 10:13:29 EDT
lines 1-1/1 (END)

sudo journalctl -xb | grep -i bluetooth
Sep 03 10:07:43 RandyDesktop NetworkManager[632]: <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so
Sep 03 10:13:29 RandyDesktop sudo[3502]: randyb : TTY=pts/3 ; PWD=/home/randyb ; USER=root ; COMMAND=/bin/journalctl -u bluetooth
randyb@RandyDesktop:~$ 
```

---

### Post by lambdafox on 2015-09-04
I found [this thread ]("http://unix.stackexchange.com/questions/137028")on stackexchange. I tried this on Saturday, September 5, 2015 to see if it works for my bluetooth problem.

The bluetooth. service file originally set the Type=dbus.  Changing the type to forking (or any of the other values does not change the behavior.). [URL="http://unix.stackexchange.com/questions/137028/why-is-my-systemd-unit-loaded-but-inactive-dead"]


[/URL]

---

### Post by Geoffrey_Arndt on 2015-09-04
OR, have you tried another approach entirely - - purchasing an inexpensive usb-bluetooth dongle with good history of Linux compatibility?  I've had good luck with Panda wireless and bluetooth 4.0 dongles (avail on amazon, egghead, etc.).   Just search for bluetooth+ubuntu or panda+ubuntu.

---

### Post by lambdafox on 2015-09-05
> **Geoffrey_Arndt said:**
> OR, have you tried another approach entirely - - purchasing an inexpensive usb-bluetooth dongle with good history of Linux compatibility?  I've had good luck with Panda wireless and bluetooth 4.0 dongles (avail on amazon, egghead, etc.).   Just search for bluetooth+ubuntu or panda+ubuntu.

My dongle is a Soundbot SB340.  I searched amazon before buying it and found this:

[http://www.amazon.com/review/R1OJS8YBDL6GPH](http://www.amazon.com/review/R1OJS8YBDL6GPH)

Unfortunately, I am not having the same experience with Xubuntu Vivid (amd64)...

---

### Post by lambdafox on 2015-09-05
> **Geoffrey_Arndt said:**
> OR, have you tried another approach entirely - - purchasing an inexpensive usb-bluetooth dongle with good history of Linux compatibility?  I've had good luck with [COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000]Panda[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR] [COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000]wireless[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR] and bluetooth 4.0 dongles (avail on amazon, egghead, etc.).   Just search for bluetooth+ubuntu or [COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000][COLOR=#000]panda[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]+ubuntu.

I looked at the device on Amazon, but could not find a list of supported Bluetooth profiles.  Nor is there one listed on the [COLOR=#000]Panda[/COLOR] [COLOR=#000]Wireless[/COLOR] web site.  I posted a question on Amazon and sent an email to support at [COLOR=#000]panda[/COLOR]...

---

### Post by jeremy31 on 2015-09-06
What does ```
lsusb
``` Tell us about the device?

---

### Post by lambdafox on 2015-09-06
> **jeremy31 said:**
> What does ```
lsusb
``` Tell us about the device?

It does not show at all:

```
lsusb
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 0e8d:1887 MediaTek Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

and[I] I also wanted to add the full status output to the conversation:

[/I]```
sudo systemctl status bluetooth -l
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor preset: enabled)
   Active: active (running) since Sun 2015-09-06 10:42:17 EDT; 15s ago
 Main PID: 17487 (bluetoothd)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;17487 /usr/sbin/bluetoothd -n

Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: DIS cannot start: GATT is disabled
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Failed to init deviceinfo plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Failed to init proximity plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Failed to init time plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Failed to init alert plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Failed to init thermometer plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: Failed to init gatt_example plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: Bluetooth Management interface initialized
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Failed to init gatt_example plugin
Sep 06 10:42:17 RandyDesktop bluetoothd[17487]: bluetoothd[17487]: Bluetooth Management interface initialized

```

I did find references to the error "DIS cannot start: GATT is disabled" with reference to other bluetooth devices, but the solution to that was to patch and rebuild the kernel.  They pointed out that if the kernel were later updated the patch would be overwritten.

---

