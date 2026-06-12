---
title: "New Ipod ( Itouch ,nano video &amp; new classic ) support ! ( tested in amarok )"
date: 2007-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by rabanomen on 2007-11-24
The newest Ipod from Apple ( Ipod iTouch , Nano video and Classic ) doestn have support for Linux users but with a simple program we can solve this problema and hack the hash ofour  ipods databases.Just works


1. You need download this file : [http://main.wtbw.co.uk/hash_linux.zip](http://main.wtbw.co.uk/hash_linux.zip)
$ wget [http://main.wtbw.co.uk/hash_linux.zip](http://main.wtbw.co.uk/hash_linux.zip)

2. Unzip and cd it 
$ unzip hash_linux.zip 
$ cd hash_crack/

3. Connect your iPod and get the hex direction . Use this command : 

$ sudo lsusb -v | grep -i Serial

4. Open the file "main.cpp" and replace in line 15 the example serial line , with your own ipod serial :

[I]Between 2 numbers there is an " 0x" 
If your serial is  :   003B566097408C14  
you may convert in : " 0x00 0x3B 0x56 0x60 0x97 0x40 0x8C 0x14"[/I]
$nano main.cpp

5.  ¿Have you installed gcc ?  [  $ sudo install gcc ]  if dont , we need it !
Compile your main.cpp

$ make all

6. Now we have the crack ready . Just run replacing the "ROUTEOFIPOD" with your path to ipod ( /media/IPODRABANO ) for me 

$  ./gethash  /[PATH_TO_IPO]/iPod_Control/iTunes/iTunesDB
*For example ./gethash /media/IPODRABANO/iPod_Control/iTu.....*

7. The last version of Amarok bring support for the news iPods . Upgrade amarok if you dont have it ! . Mount the ipod in amarok , and ..... just run !!!!!

:guitar::)

---

### Post by euxneks on 2007-11-29
does this require the jailbreak/sshfs method as well?

---

### Post by elbioleg on 2008-01-12
Thank you very much, it runs perfectly with the Rhythmbox.

---

### Post by El Flavio on 2008-01-13
HI! I dont know how to get my ipod serial. where is it?

---

### Post by ldgregory on 2008-07-28
Hmmm. Does this work with the current iTouch (bought yesterday). My serial number is much longer than the eight (byte?) hex in this how-to. i.e in the example, you list:

If your serial is : 003B566097408C14

My serial number from lsusb is:
iSerial                 3 1238486cd169a1f1d0c0766e0c016ead356acf8d

Line 14 in main.cpp is:
unsigned char fwid[8] = {

with fwid[8] apparently sized for the eight (byte?) hex in the example serial. I suppose I could change it to fwid[20].

I would have tried that, but ls'ing my /media directory and I don't see the iTouch mounted anywhere.

dmesg shows the following when connecting the iTouch:
[ 2507.295883] usb 5-1: new high speed USB device using ehci_hcd and address 4
[ 2507.430563] usb 5-1: configuration #1 chosen from 3 choices

Given that it doesn't appear to have mounted (although DigiKam auto-starts when I plug in the iTouch), I'm not sure I can proceed with your next step of:

$ ./gethash /[PATH_TO_IPO]/iPod_Control/iTunes/iTunesDB

This is a jailbroken 1.1.4 iTouch initial config done on an Windoze box.

Thanks for any help.

---

### Post by myusername on 2008-07-29
the serial to the ipod touch (or any ipod) is on the back of the ipod. you can also find it on the original ipod box

---

### Post by ldgregory on 2008-08-05
Hmmm. Ultimately, I ended up following another tutorial and got everything working, but the serial number on the back of my iPod Touch is 1A8014ZX14D which is eleven characters rather than the 16 characters in his serial number. No biggie though, I've already got it working. Just trying to solve DigiKam and the Touch for photo transfers.

Thanks everyone.

---

### Post by Ghost175 on 2009-01-25
5. ¿Have you installed gcc ? [ $ sudo install gcc ] if dont , we need it !
Compile your main.cpp

what do you mean gcc? the command sudo install gcc get rejected by my terminal,

 install: missing destination file operand after `gcc'
Try `install --help' for more information.

and once that is fixed how do you compile main.cpp?

---

### Post by whin on 2009-01-25
wow this is really great!

---

### Post by IwarV on 2009-01-27
removed

---

### Post by clconway on 2009-01-30
> what do you mean gcc? the command sudo install gcc get rejected by my terminal

That should be ```
sudo apt-get install gcc
``` or ```
sudo apt-get install build-essential
```

But if you don't know how to use gcc, using this hack might be ill-advised.

---

### Post by mastermindg on 2009-02-09
In case you haven't figured it out:

The firewire id is the first 16 characters of the serial on line 3:

$ sudo lsusb -v | grep -i Serial
  iSerial                 0 
  iSerial                 1 0000:00:0b.0
  iSerial                 3 e8c99add6b763d2557d69853e2cc2bc529c4819f
  iSerial                 3 
  iSerial                 3 57442D574D41535930363630393836
  iSerial                 0 
  iSerial                 1 0000:00:0b.1

so, here it would be:

e8c99add6c763d25

---

