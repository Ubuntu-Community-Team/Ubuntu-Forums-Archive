---
title: "HOWTO: Sagem F@st 800 with ueagle-atm on Ubuntu 10.10"
date: 2011-03-01
forum: Outdated Tutorials &amp; Tips
---

### Post by jwdonal on 2011-03-01
Hello all.  I thought I would post my solution for Sagem F@st 800 on ubuntu as the tutorial found here ([https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)) did not work for me.  I also scoured Google high and low and didn't find any suggestions for the errors I was seeing.

Background: I've been a Gentoo user for...well...ever.  Believe it or not it was the very first linux distro that I ever got my hands on - yeah, it's def not for the faint of heart.  But I've honestly become tired of the incredibly time consuming maintenance required to keep the box up to date with the latest packages.  Don't get me wrong portage is pretty good but it quickly becomes a mess of endless dependencies/reverse-dependencies/package-conflicts/etc.  And I honestly don't care anymore about compiling _every_single_package_ from scratch on my system - I know how source code gets compiled. LOL.  Long story short, I was looking for a change and Ubuntu seemed pretty rockin so I decided to switch my entire web/cvs/file server over to Ubuntu 10.10.

My biggest hurdle to overcome in doing this switch was to get my Sagem DSL modem up and running on Ubuntu.  When getting this working for the first time on Gentoo (about 5 years ago) it was an incredibly painful experience - compiling all the firmware, drivers, etc, etc from scratch was a mess and confusing.  Ubuntu made things much easier but it still didn't work right off the bat, hence this HOWTO.

First, if you're using a recent version of Ubuntu you should _NOT_ be using the eagle-usb kernel module.  The eagle-usb kernel module is as old as dirt.  You should now be using the ueagle-atm module instead (along with the obligatory usbatm module).  What is super cool about Ubuntu 10.10 is the ueagle-atm kernel module and (more importantly) the Eagle firmware is now automatically included in the default install!  You can verify this my running the following:

```
# locate ueagle-atm
/lib/firmware/ueagle-atm
/lib/firmware/ueagle-atm/930-fpga.bin
/lib/firmware/ueagle-atm/CMV4p.bin.v2
/lib/firmware/ueagle-atm/CMV9i.bin
/lib/firmware/ueagle-atm/CMV9p.bin
/lib/firmware/ueagle-atm/CMVei.bin
/lib/firmware/ueagle-atm/CMVeiWO.bin
/lib/firmware/ueagle-atm/CMVep.bin
/lib/firmware/ueagle-atm/CMVepES.bin
/lib/firmware/ueagle-atm/CMVepES03.bin
/lib/firmware/ueagle-atm/CMVepFR.bin
/lib/firmware/ueagle-atm/CMVepFR04.bin
/lib/firmware/ueagle-atm/CMVepFR10.bin
/lib/firmware/ueagle-atm/CMVepIT.bin
/lib/firmware/ueagle-atm/CMVepWO.bin
/lib/firmware/ueagle-atm/DSP4p.bin
/lib/firmware/ueagle-atm/DSP9i.bin
/lib/firmware/ueagle-atm/DSP9p.bin
/lib/firmware/ueagle-atm/DSPei.bin
/lib/firmware/ueagle-atm/DSPep.bin
/lib/firmware/ueagle-atm/adi930.fw
/lib/firmware/ueagle-atm/eagleI.fw
/lib/firmware/ueagle-atm/eagleII.fw
/lib/firmware/ueagle-atm/eagleIII.fw
/lib/firmware/ueagle-atm/eagleIV.fw
/lib/modules/2.6.35-25-generic/kernel/drivers/usb/atm/ueagle-atm.ko
/usr/share/doc/linux-firmware/licenses/LICENCE.ueagle-atm4-firmware
```If you see the above then you're in really good shape.  If not, find another tutorial.  Haha.

Next, plug in your Sagem modem and run 'less /var/log/messages'.  Keep hitting 'G' on the keyboard to keep refreshing the screen with the latest content from the file.  Eventually you should see something very similar to the following output:

```
kernel: [  314.156381] usb 3-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9022) Rev (0X5000): Eagle II
kernel: [  314.270031] usb 3-2: reset full speed USB device using uhci_hcd and address 2
kernel: [  314.424024] usb 3-2: [ueagle-atm] pre-firmware device, uploading firmware
kernel: [  314.424076] usb 3-2: [ueagle-atm] loading firmware ueagle-atm/eagleII.fw
kernel: [  314.424123] usbcore: registered new interface driver ueagle-atm
kernel: [  315.122010] usb 3-2: [ueagle-atm] firmware uploaded
kernel: [  315.290059] usb 3-2: USB disconnect, address 2
kernel: [  317.750029] usb 3-2: new full speed USB device using uhci_hcd and address 3
kernel: [  317.973382] usb 3-2: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9021) Rev (0X500B): Eagle II
kernel: [  318.090067] usb 3-2: reset full speed USB device using uhci_hcd and address 3
kernel: [  318.307282] usb 3-2: [ueagle-atm] using iso mode
kernel: [  318.307432] usb 3-2: [ueagle-atm] (re)booting started
kernel: [  319.960258] usb 3-2: [ueagle-atm] ATU-R firmware version : 44e2ea17
kernel: [  319.962617] usb 3-2: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
kernel: [  319.987526] usb 3-2: [Ueagle-atm] use deprecated cmvs version, please update your firmware
kernel: [  320.022252] usb 3-2: [ueagle-atm] modem started, waiting synchronization...
kernel: [  331.044054] usb 3-2: [ueagle-atm] modem operational

```The very last line that states "modem operation" will only appear if you _also_ plug in the phone line to the modem and it is able to properly sync with the carrier signal.

If you see all of the above then half the battle is already won! Congratulations!

Now here is where my howto differs from [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm).  I could not (no matter what or how hard I tried) get the pon/poff/plog drivers to work (specifically, I kept getting "LCP: timeout sending Config-Requests" messages and the DSL link would never establish).  I tried for 2 days but to no avail.  If you can get them to work then use them (as that is the preferred method for Ubuntu), but if you can't then read on.

I finally tried to get it working how I originally had it working on my Gentoo server and that was by using the Roaring Penguin and 'br2684ctl' driver packages.  These packages can be easily installed using the synaptic package manager. See the attached packages.png file.  The 'ppp' package is a required dependency of roaring-penguin so make sure you select it as well (although synaptic should ensure that all dependencies are installed correctly automagically).

Once you've got all that installed you need to create a virtual Ethernet-to-ATM bridge (RFC2684) interface that the roaring penguin driver can latch onto when it starts the communications link on the modem.  To do this you will need to simply run:

```
# br2684ctl -b -c 0 -e 0 -a 0.32
br2684ctl[5271]: Interface "nas0" created sucessfully
br2684ctl[5271]: Communicating over ATM 0.0.32, encapsulation: LLC
br2684ctl[5271]: Interface configured
```0.32 = VPI.VCI (you will need to get these from your DSL service provider or look them up online)

'-e 0' = My ISP (i.e. Qwest in Albuquerque, NM uses LLC encapsulation for 7Mb+ DSL and VC-mux encapsulation for anything <7Mbit).  Just in case that helps anyone.

If you don't see the above then it's most likely that the modem is not plugged in to the USB cable.  The above command will be successful even if the RJ-11 phone line is not plugged into the modem (since br2684ctl is not directly responsible for the ADSL communication).  If the modem is not connected via USB (or recognized) you will likely get the following error message:

```
br2684ctl[5210]: Fatal: failed to connect on socket; No such device
```If all is well then you should see the following interface:

```
# ifconfig -a
nas0      Link encap:Ethernet  HWaddr 00:60:4c:47:ed:dc
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```If you've got that then your in the home stretch!

Now run pppoe-setup and enter the required information.  When asked to specify the interface to use be sure to type in "nas0" (which is the virtual RFC2684 bridge that we created).  Also enter your personal username and password for the connection.

Now run pppoe-start! After a few moments it should say "Connected". And you're done!

Pz!

Jonathon

---

### Post by usuf on 2011-03-08
Hi i would to tank u for ur solution its but just one thing when i ru pppoe-start he tell me TIMED OUT can help me plzz ;)

---

