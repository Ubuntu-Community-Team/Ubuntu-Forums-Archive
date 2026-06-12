---
title: "How to stop streaming message about 'unable to enumerate usb'..."
date: 2013-03-31
forum: New to Ubuntu
---

### Post by KernowInExile on 2013-03-31
Hello all,
I will confess that despite being drawn to various Linux distributions on and off for years its taken me a while to actually get started. I am starting to use Ubuntu and wanted to try using the command line. I opened up tty1 from Ctrl-Alt-F1 which sure enough opened a command line interface however it started to stream repeatedly a message about being unable to enumerate USB port2. Not something I was particularly interested in at this stage and certainly something I only needed to be told once!

Can someone shed some light on how I could stop it from doing this so that I can go on to explore what the command line has to offer without being put off at the first hurdle?

Thanks,

---

### Post by robsablah on 2013-03-31
Just to get a background... what version are you using?
eg. 12.4 desktop amd64

If it is a desktop edition I would suggest opening terminal from Applications or by using ctrl + alt + T

in either case - can you make a note of the time that this occurs and record the exact error - it may be just a notification
 - open up syslog (# nano /var/log/syslog) - find the time and copy 20 -30 lines either side of the error so we can see whats going on

I think it would also help if we can see whats connected on your system

Can you run the following? "lsusb" and "lspci" (without quotes) in a terminal?
It should not be needed but the more information I have then the more I have to work with.

---

### Post by KernowInExile on 2013-04-02
Its 12.04 LTS on a Toshiba Satellite Pro Intel Celeron dual booting with Windows. When I open a terminal the way you suggest I dont get the same error. I've just tried opening tty1 again and this time the error isnt happening either so if it comes back I'll copy the system log as you suggested.

Running lsusb gives:

medved@AllPowerfulGentleman:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07ab:fcfe Freecom Technologies Hard Drive 80GB
Bus 002 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
medved@AllPowerfulGentleman:~$ 

While lspci gives:

medved@AllPowerfulGentleman:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07ab:fcfe Freecom Technologies Hard Drive 80GB
Bus 002 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 006 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
medved@AllPowerfulGentleman:~$ 

If I get the same problem again I'll try and copy a bit more to get you more to go with.

---

