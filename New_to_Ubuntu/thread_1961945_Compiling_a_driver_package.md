---
title: "Compiling a driver package"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by traditionalist on 2012-04-20
Ubuntu 11.04.  I need to compile a tar.gz file so that it runs a driver. But nothing I have tried works. I have read reams of documentation but I can't find anything that shows how to do it, at least nothing I can understand.  The instructions in the package are;

** Ubuntu 8.10 **
- install the package 'build-essential'
- install the kernel headers package for your currently running kernel
  (usually 'linux-headers-generic')
- install the kernel source package for your currently running kernel
  ('linux-source')
- open a command shell and get root access
- go to the '/usr/src' directory and unpack the linux-source package
    e.g. 'cd /usr/src; tar xjf linux-source-2.6.27.tar.bz2'
- create a symbolic link from the 'drivers' directory in your linux sources
  to your linux headers
    e.g. 'ln -sfn /usr/src/linux-source-2.6.27/drivers /usr/src/linux-headers-`uname -r`/drivers'
- let the '/usr/src/linux' link point to your linux headers
    e.g. 'ln -sfn /usr/src/linux-headers-`uname -r` /usr/src/linux'

( Note on above. The problems start with "open a command shell and get root access". I just don't know how to do this. I have tried quite a few things but nothing works.)


Once you have a working build environment, just do the following:  ( I have a build environment it seems, the "Build essential" is installed)

- open a command shell and get root access
- go to the directory where you found this instructions file
- run 'make' and then 'make install'
- either reboot linux or execute the following commands:
    modprobe tvsat
    /etc/init.d/tvsatd start
- install a DVB viewer (Kaffeine, VDR, MythTV, etc.)
- make sure your user has the necessary rights to watch tv (e.g. on Ubuntu
  you have to be in the 'video' group)


can somebody please translate that into usable step-by-step instructions?

Regards...Trad

---

### Post by Paqman on 2012-04-20
> **traditionalist said:**
> 
** Ubuntu 8.10 **


Looks like instructions for a very old version of Ubuntu. Are you sure you need to compile your own driver on newer versions? Generally hardware support gets better with every version. 

What hardware is the driver for? A tuner card?

---

### Post by traditionalist on 2012-04-20
> **Paqman said:**
> Looks like instructions for a very old version of Ubuntu. Are you sure you need to compile your own driver on newer versions? Generally hardware support gets better with every version. 

What hardware is the driver for? A tuner card?

It is for a devolo TV sat plug.  I recently moved to Ubuntu from Windows, and I would like to get this running.

This is included in the package;

QUOTE

*** KNOWN ISSUES ***

- Because this driver is still based on the old DVB API, it does not support DVB-S2.
- The driver always reports a fixed SNR value, because the DVB API does not define a specific unit of measurement.
- When using VDR, it is possible that there are regular audio/video glitches when watching transponders with a large number of programs on them.
- There may be short audio/video glitches in the first five seconds after switching channels. This also affects simultaneous recordings from the same transponder.
- Only tested with VDR, MythTV, Kaffeine and szap (with dvr output), but other programs might work as well.
- Disconnecting the device for more than 30 seconds and then closing the DVB viewer will crash the driver, so always close your DVB viewer before disconnecting the device.

UNQUOTE

This is the newest package apparently.

Regards....Trad

---

### Post by Paqman on 2012-04-20
OK, that's quite an obscure piece of kit and not one that I'm at all familiar with. The first thing I would do is plug it in and see if it works without having to build your own drivers. Since they only mention support for old versions of Ubuntu it may be that you don't need to install the drivers manually any more. It's reasonably common on Linux for hardware to work without needing to install drivers yourself.

If you decide you do need to install manually:
> ( Note on above. The problems start with "open a command shell and get root access". I just don't know how to do this. I have tried quite a few things but nothing works.)

Those instructions were obviously written by someone not very familiar with Ubuntu. You generally don't use root terminals on Ubuntu, just prefix any commands that require root with "sudo". For example, instead of "make install", you'd use "sudo make install".

---

### Post by traditionalist on 2012-04-20
OK. Thanks a lot. The hardware itself works OK, I can test it, but I can't use it.  After a lot more enquiries, ( the hardware firm is not very good at answering queries), it seems it is not going to work anyway.

Regards....Trad

---

