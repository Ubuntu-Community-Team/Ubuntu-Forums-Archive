---
title: "HowTo: Xilinx and Spartan 3E"
date: 2009-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Wipster on 2009-10-30
Hey all,
There are quite a few resources about the Xilinx software suite and how to get setup about on the internet however they are either patchy or out of date.
So this is my little howto to get a fully up to date Xilinx webpack ISE with a Spartan 3E development kit (Digilent) working with a USB programming cable in Ubuntu 9.10. Hopefully it will be of some use :)

Ok so start out with downloading the Xilinx ISE 11.1, I used the web installer but the tar ball probably works well too.
[http://www.xilinx.com/support/download/](http://www.xilinx.com/support/download/)

Extract it and navigate to the directory and run
```
sudo ./xsetup
```
I personally keep everything as defaults on the installer, only turning off webtalk. (Dont check install cable driver as the USB is inbuilt)
Once it has installed I let the auto update run and get all the updates so I end up with 11.3

So plugin the Spartan dev kit and power it on, leave it for a sec then do
```
lsusb
```
There should be an entry starting 03fd this is the Xilinx board, if yours ends with 0008 then you can skip this next stage. Mine ended with 000d so I need to tell udev to load the correct firmware with fxload.

```
sudo apt-get install fxload
sudo cp /opt/Xilinx/11.1/ISE/bin/lin/xusbdfwu.rules /etc/udev/rules.d
sudo cp XilinxISE/11.1/ISE/bin/lin/xusb*.hex /usr/share/

```
This will put the rules file in place and the firmware where it expects it.
With the changes to udev you will need to open the rules file and change $TEMPNODE to $tempnode.

Unplug the board and restart udev with,
```
sudo service udev restart
```
Plug the kit back in and run lsusb, and the entry should now read 03fd:0008.

Now we need to make a softlink to libusb because impact cant pickup the default Ubuntu one.
```
sudo ln -s /lib/libusb-0.1.so.4.4.4 /lib/libusb.so
```

So there we go impact should now work, happy programming.

---

### Post by bpwilliams on 2010-09-12
> Unplug the board and restart udev with,
```
sudo service udev restart
```Plug the kit back in and run lsusb, and the entry should now read 03fd:0008.



So when I get to the part above, my Spartan 3E board does not show up as 03fd:0008!

Some other tutorials have showed me how to manually load the board with the corresponding firmware, or whatever? Then is does sow up correctly, but Impact still doesn't like it.

Any suggestions?

---

