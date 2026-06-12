---
title: "Help get G25 + Driving Force Pro support into Linux"
date: 2008-03-19
forum: Programming Talk
---

### Post by Rich43 on 2008-03-19
I want to get full support for the Logitech G25 under Linux, I am almost there!

If you have or understand Linux, can program C, own or have a friend with a G25 or DFP please read on :-)

The Driving Force Pro could also apply to this thread but since I own a G25, I will talk about that. The two wheels have some similarity's.

Recently a developer got some inside info from a logitech employee. Someone has nicely made a command line tool to configure the G25 wheel. When the wheel is first turned on, it is in a special backwards compatibility mode, some of the buttons are disabled and limited to 11 buttons and the clutch is disabled.

The tool is available here:
[http://vdrift.net/Forum/viewtopic.php?t=866](http://vdrift.net/Forum/viewtopic.php?t=866)
To save time, heres a precompiled version (32bit binary!): [http://richieward.com/files/usbtool-0.1-compiled.tar.gz](http://richieward.com/files/usbtool-0.1-compiled.tar.gz)
You may need swig, libusb, python for it to work.

To use it, I use these commands on ubuntu:
#List all usb devices to get device id for the next set of commands
sudo ./usbtool -l
#Disable the built in compatibility mode and switch to normal g25 mode (Enables clutch + more buttons)
sudo ./usbtool -d <device id here> g25-set-extended-mode
#Enable 900 degrees
sudo ./usbtool -d <device id here> g25-set-range-wheel-900

I found an extensive list of commands by typing: ./usbtool --list-commands

**Much technical information on the wheel that got leaked from logitech is available at:** [http://vdrift.net/Forum/viewtopic.php?t=866](http://vdrift.net/Forum/viewtopic.php?t=866)

**There is currently one problem, when the G25 is set to 900 degrees, the wheel dissappears from /dev/input.**
The kernel driver needs to be modified to fix this and this is why I need your help.

You should download the linux kernel and look in /drivers/hid/ and work out how to get the wheel working with full 900 degrees and then we can move onto looking to see if we can make force feedback work.

Once we have it all working with the command line tool, I shall make a gtk gui that can configure your wheel (Similar to the windows logitech software).

---

