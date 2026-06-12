---
title: "Ubuntu lost connection? with Logitech Bluetooth keyboard K810"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by momoZ on 2013-05-27
Hi there!

Thank you in advance for reading this thread. Any help will be much appreciated.

I am just troubleshooting to make Ubuntu work with my Logitech Bluetooth Illuminated keyboard K810, trying to have a permanent bluetooth connection.

Here are the highlights; First, I was able to make it work perfectly fine following these instructions:


    set keyboard discoverable
    "hcitool scan" and copy mac address XX:XX:XX:XX:XX:XX
    "sudo bluez-simple-agent hci0 XX:XX:XX:XX:XX:XX"
    which will hopefully return somthing like:
    "DisplayPasskey (/org/bluez/537/hci0/..., 123456)"
    the number at the end of the string represents the PIN you need to enter for pairing. enter those numbers on your bluetooth device and confirm with return
    on success you should get "Release" and "New device (/org/bluez/..."
    now set device as trusted "sudo bluez-test-device trusted XX:XX:XX:XX:XX:XX yes"
    you might have a connection now, but i still needed to:
    "sudo bluez-test-input connect XX:XX:XX:XX:XX:XX"
    now reboot and hope for the best!

 original instructions found at:
[http://devasive.blogspot.com/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html](http://devasive.blogspot.com/2012/11/ubuntu-1204-persistent-bluetooth-pairing.html)

Now, my Desktop is a somewhat old MoBo P4C800-e with dual boot to 2 SATA hard drives (Ubuntu 12.04 and Windows XP 32bit respectively) which perfectly works with any other wired (either ps/2 or USB) keyboard, but after I booted/switched between both Operative Systems a couple of times Ubuntu just doesn't "see" my Bluetooth keyboard anymore.

I got an error message in Ubuntu saying:
 
Your bug report will be processed in few seconds.
If you can reproduce it, please follow the next steps:
    - Open a new terminal
    - Run the command "sudo hcidump -XYt > $HOME/hci.log"
    - Reproduce the actions until the error happens
    - On the terminal, press Ctrl+C to stop hcidump.
    - Attach the file hci.log to the bug report.

...so I did, but this is what I got:

sudo: hcidump: command not found

I searched this forum and found 4 posts:

[http://ubuntuforums.org/showthread.php?t=2139018&highlight=logitech+k810](http://ubuntuforums.org/showthread.php?t=2139018&highlight=logitech+k810)
[http://ubuntuforums.org/showthread.php?t=1897905&highlight=logitech+k810](http://ubuntuforums.org/showthread.php?t=1897905&highlight=logitech+k810)

...but none were particularly helpful to me. So I tried hcitool scan and I got:

Scanning ...
    00:1F:20:75:D3:68    Logitech K810
yo@yo-desktop:~$ sudo bluez-simple agent hci 00:1f:20:75:D3:68 repair
Traceback (most recent call last):
  File "/usr/bin/bluez-simple-agent", line 102, in <module>
    path = manager.FindAdapter(args[0])
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.bluez.Error.NoSuchAdapter: No such adapter

I guess my question is if I can revert to a previous status in Ubuntu where it was no Bluetooth device set up, or MAC address scanned, or something like that so I can at least start over and see what happens.

Thank you in advance.

---

