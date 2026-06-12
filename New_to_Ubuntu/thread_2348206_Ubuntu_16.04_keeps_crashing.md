---
title: "Ubuntu 16.04 keeps crashing"
date: 2017-01-01
forum: New to Ubuntu
---

### Post by Ribar on 2017-01-01
Hello guys,

Happy new years! :) Few days ago I installed Ubuntu 16.04 on my desktop. Since the install i have been getting system crashes, mainly the system will run for a day or so and it will completely freeze for me. That is i have no mouse/keyboard input. 

I am new to linux and i am not sure where to begin troubleshooting. Couple of other things perhaps might be worth mentioning, before i installed Ubuntu i had Linux Mint distribution installed. I was experiencing same issue there, that is system crashing. I decided to install Ubuntu in hopes for better system stability but no luck. Rather then moving onto another distro i want to resolve this as i think the issue will persist no matter what Linux Distro i load, but i am not sure.

I hope you can help me diagnose this issue. 

Best Regards,
Pasha

---

### Post by ian-weisser on 2017-01-01
Start with your logs: Look at /var/log/dmesg and /var/log/syslog for the time around a freeze.

---

### Post by Ribar on 2017-01-02
> **ian-weisser said:**
> Start with your logs: Look at /var/log/dmesg and /var/log/syslog for the time around a freeze.

Hi Ian,

I have been digging through the syslog and this is what i found. This is from around the time system crashed, what got my attention is the "config_get_device_record: failed to read" and that goes for a while it just continues i have only included a few here. And also another interesting is 

> Jan  1 11:27:22 linux ModemManager[1028]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.1': not supported by any plugin

It appears that there might be a device that is not supported? How do  I find out more what this device is? It looks like its connected to USB port, is there a command that allows me to see in detail what is connected to /usb3/3-10/3-10.1  ? I have multiple USB devices connected, mouse, keyboard, webcam, external sound card. I am not sure which is having a conflict with the system.

```
Jan  1 11:27:20 linux org.gtk.vfs.GPhoto2VolumeMonitor[1823]: (process:2198): GVFS-GPhoto2-WARNING **: device (null) has no BUSNUM property, ignoring
Jan  1 11:27:20 linux org.gtk.vfs.GPhoto2VolumeMonitor[1823]: message repeated 3 times: [ (process:2198): GVFS-GPhoto2-WARNING **: device (null) has no BUSNUM property, ignoring]
Jan  1 11:27:20 linux gnome-session[1980]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Jan  1 11:27:20 linux org.gtk.vfs.AfcVolumeMonitor[1823]: creating volume for device uuid 'b3051f9c658c7ec6cebbbdc7e912228020064a0e'
Jan  1 11:27:20 linux usbmuxd[23125]: [11:27:20.806][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:21 linux usbmuxd[23125]: [11:27:21.828][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:22 linux ModemManager[1028]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.1': not supported by any plugin
Jan  1 11:27:22 linux usbmuxd[23125]: [11:27:22.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:23 linux gnome-session[1980]: (gnome-software:2283): Gs-WARNING **: failed to get updates: no results to show
Jan  1 11:27:23 linux usbmuxd[23125]: [11:27:23.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:24 linux usbmuxd[23125]: [11:27:24.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:25 linux usbmuxd[23125]: [11:27:25.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:26 linux usbmuxd[23125]: [11:27:26.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:27 linux usbmuxd[23125]: [11:27:27.826][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:28 linux usbmuxd[23125]: [11:27:28.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:29 linux usbmuxd[23125]: [11:27:29.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:30 linux usbmuxd[23125]: [11:27:30.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:31 linux usbmuxd[23125]: [11:27:31.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:32 linux usbmuxd[23125]: [11:27:32.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:33 linux usbmuxd[23125]: [11:27:33.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:34 linux usbmuxd[23125]: [11:27:34.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:35 linux usbmuxd[23125]: [11:27:35.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:36 linux usbmuxd[23125]: [11:27:36.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:37 linux usbmuxd[23125]: [11:27:37.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:38 linux usbmuxd[23125]: [11:27:38.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Jan  1 11:27:39 linux usbmuxd[23125]: [11:27:39.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
```

Also under the var/crash i found this output but this looks like its mostly related to application crashes? 

```
_opt_google_chrome_chrome.1000.crash
_opt_google_chrome_chrome.1000.upload
_opt_google_chrome_chrome.1000.uploaded
_opt_viber_Viber.1000.crash
_opt_viber_Viber.1000.upload
_opt_viber_Viber.1000.uploaded
_usr_bin_compiz.1000.crash
_usr_bin_compiz.1000.upload
_usr_bin_compiz.1000.uploaded
_usr_bin_python2.7.1000.crash
_usr_bin_python2.7.1000.upload
_usr_bin_python2.7.1000.uploaded
_usr_bin_unity-scope-loader.1000.crash
_usr_bin_unity-scope-loader.1000.upload
_usr_bin_unity-scope-loader.1000.uploaded
_usr_lib_x86_64-linux-gnu_unity-scope-home_unity-scope-home.1000.crash

```


var/log/dmesg is empty 

Thanks,
Ribar

---

### Post by ian-weisser on 2017-01-02
> **Ribar said:**
> var/log/dmesg is empty
Sorry,, my mistake. (It changed in 16.04).
Look for clues in the systemd and kernel logs using the command
```
journalctl
```


> **Ribar said:**
> Jan  1 11:27:22 linux ModemManager[1028]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.1': not supported by any plugin
Jan  1 11:27:22 linux usbmuxd[23125]: [11:27:22.825][1] config_get_device_record: failed to read '/var/lib/lockdown/b3051f9c658c7ec6cebbbdc7e912228020064a0e.plist': No such file or directory
Use the command 'lsusb' to list all the USB devices attached to your system. There may be a lot of them - USB is used internally for wireless cards, webcams, and more.
See if you can identify which devlice corresponds to bus 3, device 10.
Then use the lsusb -v and -vv flags to get more information on just that device.

---

### Post by Ribar on 2017-01-02
> **ian-weisser said:**
> Sorry,, my mistake. (It changed in 16.04).
Look for clues in the systemd and kernel logs using the command
```
journalctl
```



Use the command 'lsusb' to list all the USB devices attached to your system. There may be a lot of them - USB is used internally for wireless cards, webcams, and more.
See if you can identify which devlice corresponds to bus 3, device 10.
Then use the lsusb -v and -vv flags to get more information on just that device.


After running lsusb i get the output bellow, that said i do not see any device 10 on Bus 3. 

Here is the output: lsusb
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 002: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF
Bus 003 Device 004: ID 1532:0043 Razer USA, Ltd 
Bus 003 Device 002: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 007: ID 1235:8016 Focusrite-Novation 
Bus 003 Device 006: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by ian-weisser on 2017-01-02
That would explain why the error is device-not-found.
Moving on....

Is there anything you can do to reliably cause the freeze?

In the log you posted above, 'usbmuxd' is a daemon for communicating with Apple products - iPhones and iPods. Are you plugging one of those in?
Is the time in that log accurate? That 's what was happening _during_ a freeze?

Next time it freezes, do CTRL+ALT+F1. does a text login appear? Can you login to it? Use CTRL+ALT+F7 to return to the frozen GUI interface. Can you toggle back and forth while the GUI is frozen?

---

### Post by Ribar on 2017-01-02
I do plug in my iphone when i charge it. That said that set me of with an idea to identify the port thats Bus3 Devcie 10. What i ended up doing is plugging in my iphone on available physical USB ports and runing the lsusb command after each connect and sure enough i came a cross USB port that corresponds to Bus 3 device 10. The good thing is that i dont have anything plug in that port at the moment. But as  you can see bellow i was able to identify which physical port that is with iphone. The particular port is on the back of the computer and i dont connect my phone there to charge it.


```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 002: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 003 Device 005: ID 046d:0994 Logitech, Inc. QuickCam Orbit/Sphere AF
Bus 003 Device 004: ID 1532:0043 Razer USA, Ltd 
Bus 003 Device 002: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 007: ID 1235:8016 Focusrite-Novation 
Bus 003 Device 006: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 003: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


When it froze last time i was not able to do anything, with keyboard or mouse. The time is correct. I tried few short cuts but no luck. I can try CTRL+ALT+F1 and CTRL+ALT+F7 next time.

---

