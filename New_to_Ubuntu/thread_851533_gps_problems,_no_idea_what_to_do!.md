---
title: "gps problems, no idea what to do!"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by iainr86 on 2008-07-06
hi, on saturday i'm setting off on a charity rally from london to mongolia. We've kindly been lent an Aleutia E2 computer (which is awesome btw) for our car, and one of the things i want to use it for is GPS.

I bought a zycast SG-949 usb gps receiver on ebay (specifically as it was listed as linux compatible) but am having trouble getting it to work.

So far i have installed GPSDrive and tangoGPS, but neither registered any GPS  as being connected. I then installed gpsd using synaptic and hoped it would magically work but it still wont.

Basically i haven't a clue what to do and desperately need help to get it up and running in time!

Iain

---

### Post by hansdown on 2008-07-06
Hi iainr86, I just did a quick google search, and it tells me that your model is meant to be used with a samsung oqo model 2 ultra "when used with navigator software". Maybe You should check that.

---

### Post by iainr86 on 2008-07-07
thanks for the reply. the model i've bought is this one [http://www.gpsforless.co.uk/product_details.php?id=11549](http://www.gpsforless.co.uk/product_details.php?id=11549) which claims to be linux compatible. The only instructions that come with it are for setting it up in xp and they tell you to install a usb driver from the cd. I had a look on the cd and couldn't see any obvious linux drivers but then i didn't really know what to look for. The instructions say to follow the same process for all os's but as we don't have a cd drive on our E2 i don't know what to do

---

### Post by Elfy on 2008-07-07
If you can open the cd and post the contents perhaps it might help.

---

### Post by iainr86 on 2008-07-07
Ok i'll do my best.

Starting from the root folder of the cd we have:

Acrobat R 5.0 > AR500ENU.exe
SG278 > Manual > several pdf files
             > Utility > zycast gps viewer.exe
             > Utility > Zycast PPC gps viewer > GPSLangRes.dll, GPSviewer.exe

this is repeated for several different model numbers including my one:

SG-949 > Manual > 3 pdf files
               > Utility > zycast gps viewer.exe
               > Utility > Zycast PPC gps viewer > GPSLangRes.dll, GPSviewer.exe

USB Driver > PL-2303 Driver Installer.exe

Thats all that seems to be on the cd

---

### Post by Elfy on 2008-07-07
I've tried to get some inf from the zyczst site but there doesn't appear to be much.

Firstly - what does the manual say about linux - or is it one of those completely nonsensical pidgin english jobs :)

When you plug it in to your box does it actually do anything?

Secondly - you could try running it with wine, or a vm - not sure about vmware but the puel virtualbox does have usb support.

---

### Post by iainr86 on 2008-07-07
The manual only gives instructions for windows xp then says to follow the same steps for other os's. Don't see how that could help since there appears to be no linux apps on there and there definitely aren't any mac programs/drivers.

when i run lsusb in terminal i get a list of usb devices connected. I've got a usb mouse, keyboard and also the gps unit all connected up. Its not clear which is which though

I was thinking that maybe if i could assign the gps module to a certain com port it might make the software be able to find it?

---

### Post by Elfy on 2008-07-07
paste the lsusb here - might help, but I think that you might find trying to run it with wine the best option as it is.

I know the few threads I've seen here about gps units usually head in either the win eor virtual machine direction.

---

### Post by MarcusBauer on 2008-07-07
Hello Iain, this should all be very easy to set up. The GPS mouse will occupy a /dev/ttyXX. You have to figure out the value of XX. And put it into /etc/defaults/gpsd into DEVICES="". Then restart gpsd with "sudo /etc/init.d/gpsd restart".

You can figure out the correct device with looking into /var/log/messages after plugging the mouse in. There will be some lines which tell you which device the gps mouse was asigned. If unsure post the lines here.

---

### Post by MarcusBauer on 2008-07-07
hello again. a good description is on:

[http://myy.helia.fi/~karte/haicom_hi-204e_usb_gps_on_linux.html](http://myy.helia.fi/~karte/haicom_hi-204e_usb_gps_on_linux.html)

However, I wonder if the "sudo mknod..." is still necessary.

But /dev/ttyUSB0 sounds good, thus you may try:
$ sudo killall gpsd
$ sudo gpsd -N -n -D 2 /dev/ttyUSB0 &

And tell us about the output

---

### Post by iainr86 on 2008-07-07
Thanks for your help Marcus, it seems to be working after

$ sudo killall gpsd
$ sudo gpsd -N -n -D 2 /dev/ttyUSB0 &

awesome!! 

I downloaded the .deb file a while ago, i think its version 0.9.0.3, is there an easy way to upgrade it to the latest version? 

i now need to go through and figure out how to download all the maps we'll need for our route

cheers marcus, i'll send an email off to you in a minute

---

### Post by iainr86 on 2008-07-07
ok one final question, it looks like i have to go through this process after every restart. is it possible to write some sort of script that will automatically run the 2 lines of code without me having to use the terminal?

i need it to carry out:

$ sudo killall gpsd
$ sudo gpsd -N -n -D 2 /dev/ttyUSB0 &

---

### Post by james_vanb on 2008-07-07
Don't know if this will help, but I had a sound problem that required me to run 3 commands at every start.  I found that rc.local is a dummy script and added the commands - They ran at start up.  Try the following:

```
sudo gedit /etc/rc.local
```

Add the 2 commands (without sudo) after the last commented out line and before "exit=0" or in Hardy it will say "exit 0".  Save and exit.

```
killall gpsd
gpsd -N -n -D 2 /dev/ttyUSB0 &
exit 0
```

Restart and see if it worked.

---

### Post by achadwick on 2008-07-10
[QUOTE=iainr86;5333077]I bought a zycast SG-949 usb gps receiver on ebay (specifically as it was listed as linux compatible) but am having trouble getting it to work.

So far i have installed GPSDrive and tangoGPS, but neither registered any GPS  as being connected. I then installed gpsd using synaptic and hoped it would magically work but it still wont.[QUOTE]

I've just bought myself one of these, and it seems fine. The setup is a little non-graphical-user-friendly however: what I've done to get it working, or at least talking to gpsd is:

[INDENT]$ sudo apt-get install gpsd[/INDENT]

Or use synaptic. gpsd doesn't start automatically by itself, you need to configure it minimally before it'll start.

[INDENT]$ sudo dpkg-reconfigure gpsd[/INDENT]

And answer:

[LIST]
[*] Should gpsd start on boot? **<Yes>**
[*] Device your GPS receiver is attached to: **/dev/ttyUSB0**
[*] Options to gpsd: *leave blank - works for me*
[/LIST]

gpsd should then start, and will be running on next boot. I haven't got a lock yet because I'm buried deep indoors where I work, but sling the unit on a windowsill or out of a window or something and it should work. To test that data's being received over NMEA (= the serial protocol used for GPS devices), you can open a terminal and type:

[INDENT]
$ cgps
[/INDENT]

You should see something a line like:

[INDENT]
GPSD,I=SiRF binary GSW3.1.1TO_3.1.00.07-C23P1.00
[/INDENT]

in the scrolling output: that's the firmware revision number on the device, apparently; presumably seeing it indicates that all is well.

If you installed the gpsd-clients package. xgps is another of the clients in that package, as is a simple logger. You can do 'dpkg -L PACKAGENAME' to see the files inside an installed package - have fun investigating! Don't forget, the manual pages for all of these are installed too: "man PROGRAMNAME" for those.

You'll need to restart any gpsd clients if you unplug and replug the USB connection. However, you can connect as many clients as you need - loggers, map views, position indicators and compasses - to gpsd as you need. Which is nice.

I'll watch this thread, and let you know how I get on.

---

