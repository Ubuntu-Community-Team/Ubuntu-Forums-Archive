---
title: "HOWTO: Install BitPim"
date: 2006-03-17
forum: Outdated Tutorials &amp; Tips
---

### Post by d351GuJu on 2006-03-17
For those who don't know what Bitpim is, check [here]("http://www.bitpim.org/")!

All right let's get started installing Bitpim for now.

-------------------------------------------------------

We will need to convert a RPM package to DEB package, so do this.
**sudo apt-get install alien**

Now download BitPim from the original website, yes the RPM version.
And convert the RPM to DEB, by entering the following:
**sudo alien -d bitpim*.rpm**

It will take a few seconds, to convert and it will notify when it finishes.

Now let's install it:
**sudo dpkg -i bitpim*.deb**

Once installed run it by entering bitpim on the console.

**ERRORS:**

libstdc++.so.5  -> if you receive this kind of error, do the following:
sudo apt-get install libstdc++5

libtiff.so.3 -> if you receive this kind of error, do the following:
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3

-------------------------------------------------------------------

[SIZE="3"]_**Devices that works so far:**_[/SIZE]
```
[LIST]
[*]None as of yet
[/LIST]
```

---

### Post by r3v3rs3pa on 2006-04-09
[http://www.bitpim.org/help/](http://www.bitpim.org/help/)

click the folder "troubleshooting"
then select "linux issues"
for the same info, which if the app n its docs change, it will support any changes.

and they also support USB recognition.
same link, [http://www.bitpim.org/help/](http://www.bitpim.org/help/)

click the "reference" folder
then the folder "usb"
then select "linux usb setup"


UPDATE:
the newest version, all i did was use the auto-detect phone and it found mine. i didnt need the usb support at all.
i have the rl-4920, which isnt exactly the most common phone.
anyways, some of the buttons like "phone info" dont say anything.
i went to the menu "EDIT"-->detect
and it found my phone, which, last i knew, was one of the lesser supported phones.

---

### Post by Didjit on 2006-05-17
Installed ok, can't seem to get connected w/Bluetooth. Anyone have any luck connecting BitPim w/Bluetooth? Appreciate any shared info.

Didjit

---

### Post by Paerez on 2006-05-18
I am testing out bitpim on my gf's razr, and it finds it, but when I try to grab data I get this:

```

BitPim version: 0.9.00-official
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "src/gui.py", line 275, in run
  File "src/gui.py", line 152, in __call__
  File "src/gui.py", line 1760, in getdata
  File "src/gui.py", line 1754, in getfundamentals
  File "src/phones/com_moto.py", line 226, in getfundamentals
  File "src/phones/com_motov710.py", line 118, in _get_ringtone_index
  File "src/phones/com_moto.py", line 161, in decode_utf16
LookupError: unknown encoding: utf_16le
```

---

### Post by hbj on 2006-06-27
I'm trying to run this in Dappr and the program would not start it unless I launched it with the kdesu command.  So there must be a permissions issue.  Any ideas on how to track this down?

---

### Post by d351GuJu on 2006-06-28
[QUOTE=hbj]I'm trying to run this in Dappr and the program would not start it unless I launched it with the kdesu command.  So there must be a permissions issue.  Any ideas on how to track this down?[/QUOTE]

Hmm...I just installed the latest version (0.9.03) and it launched just fine from the command line.  Could you run it from the command line by just typing "bitpim" and post here what the output is?

---

### Post by marlin on 2006-07-06
Sorry to break into your thread but I am having the same difficulty running BitPim in Kubuntu-Dapper and am asking for your assistance. 

I converted the RPM to .DEB (bitpim_0.9.04-1_i386.deb).

I then installed using dpkg -i bitpim_0.9.04-1_i386.deb . 
When I run "bitpim" from my home directory I receive the following error:

Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory. 

Upon seeing the reference to libtiff.so.3, I created the suggested link in my home directory and when I run bitpim I recieve the same error as above. Any help is much appreciated.

---

### Post by marlin on 2006-07-06
OK! I will crawl back under my rock where I belong. When one creates the LINK where told to create it (/usr/lib) then BitPim "fires up" as expected. Sorry for wasting your time!

---

### Post by ncappel1 on 2006-08-03
I also get a similar problem as Paerez, but my error is a bit longer:
```
BitPim version: 0.9.05-official
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "src/gui.py", line 276, in run
  File "src/gui.py", line 153, in __call__
  File "src/gui.py", line 1931, in getphoneinfo
  File "src/gui.py", line 1809, in setupcomm
  File "src/commport.py", line 68, in __init__
  File "src/commport.py", line 97, in _openport
  File "src/commport.py", line 129, in _openusb
  File "src/native/usb/usb.py", line 165, in openbulk
USBException: could not claim interface 1: Operation not permitted

Variables by last 8 frames, innermost last

Frame run in src/gui.py at line 269
              e =  <native.usb.usb.USBException instance at 0xb31aaa0c>
            res =  None
           self =  <WorkerThread(BitPim helper, started daemon)>
           item =  (<gui.Request instance at 0xb43bdaac>, <gui.Callback instance at 0xb43bd64c>)
           call =  <gui.Request instance at 0xb43bdaac>
             ex =  <native.usb.usb.USBException instance at 0xb31aaa0c>
       resultcb =  <gui.Callback instance at 0xb43bd64c>
          first =  0

Frame __call__ in src/gui.py at line 153
           self =  <gui.Request instance at 0xb43bdaac>
           args =  ()
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame getphoneinfo in src/gui.py at line 1931
           self =  <WorkerThread(BitPim helper, started daemon)>

Frame setupcomm in src/gui.py at line 1809
           name =  'usb::001::002::1'
           self =  <WorkerThread(BitPim helper, started daemon)>
       autofunc =  None
         comcfg =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
          klass =  <class commport.CommConnection at 0xb5b0ed7c>

Frame __init__ in src/commport.py at line 68
           baud =  115200
   autolistargs =  (<module 'phones.com_motoe815' from '/usr/lib/BitPim-0.9.05/bitpim/phones/com_mo
           self =  <commport.CommConnection instance at 0xb31aa04c>
   hardwareflow =  False
   autolistfunc =  None
        timeout =  3
      logtarget =  <WorkerThread(BitPim helper, started daemon)>
configparameters =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
   softwareflow =  False
           port =  'usb::001::002::1'

Frame _openport in src/commport.py at line 110
           baud =  115200
          dummy =  0
    description =  None
           self =  <commport.CommConnection instance at 0xb31aa04c>
   hardwareflow =  False
        timeout =  3
   softwareflow =  False
           port =  'usb::001::002::1'

Frame _openusb in src/commport.py at line 129
          iface =  <native.usb.usb.USBInterface instance at 0xb31aab0c>
      wantedbus =  '001'
           name =  'usb::001::002::1'
            bus =  <native.usb.usb.USBBus instance at 0xb31aa92c>
           self =  <commport.CommConnection instance at 0xb31aa04c>
      wanteddev =  '002'
        timeout =  3
         device =  <native.usb.usb.USBDevice instance at 0xb31aa94c>
    wantediface =  1
              _ =  'usb'

Frame openbulk in src/native/usb/usb.py at line 165
            res =  -1
           self =  <native.usb.usb.USBInterface instance at 0xb31aab0c>
           epin =  <native.usb.usb.USBEndpoint instance at 0xb31aab2c>
              v =  1
          epout =  <native.usb.usb.USBEndpoint instance at 0xb31aab4c>
             ep =  <native.usb.usb.USBEndpoint instance at 0xb31aab2c>
```

I am trying to get this to work with my brand new Motorola pebl!

could it be a usb permissions issue?

---

### Post by d351GuJu on 2006-08-05
If you are experiencing permission issues, then you may want to read [this]("http://www.bitpim.org/help/howto-linuxusb.htm").

I apologize I can not be of any help, but I am not very good at debugging.  :(  But please post here if you succeed in getting that permission issue resolved.  Thanks!

---

### Post by ncappel1 on 2006-08-05
d351GuJu, I tried doing what was written on the bitpim site before, i should have been more clear. my system uses udev (or so i surmise, as the folder /etc/hotplug isn't in my system)

Does anyone know about other ways to play with usb permissions? i've looked around the forums a bit but havn't found anything that really seems to address the issue at hand.

---

### Post by JerMe on 2006-08-12
I wrote this for another forum.  Do what the OP says, then continue from here.  This will get all the udev permissions running.  (You obviously will need to download the RPM from [www.bitpim.org](www.bitpim.org), convert the RPM to a DEB file using alien, and install the DEB file with dpkg.)  Next:

install libstdc++5:

```
sudo apt-get install libstdc++5
```

symlink:
```
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3
```

Then you need to make a bitpim group, and add yourself to the bitpim group.
([http://www.bitpim.org/help/howto-linuxusb.htm](http://www.bitpim.org/help/howto-linuxusb.htm))  Your_user_name is, well, your user name: 
```
sudo groupadd bitpim
sudo usermod -G bitpim -a *your_user_name*
```

Dont forget the **-a**, or else you'll screw up your permissions. ;)

Lastly, you need to make a USB rule to recognize your cellphone directly.  Connect your phone to the cable, and plug the cable into your USB port.  Then type:

```
lsusb
```

to list the USB devices connected to your computer.  You should see your phone.  Mine is listed as

```
Bus 002 Device 003: ID [color=red]1004:6000[/color] LG Electronics, Inc. VX4400/VX6000 Cellphone
```

Pay attention to the 1004:6000.  The 1004 is the Vendor ID, and the 6000 is the Product ID.  Write it down or keep it in mind.  1004 and 6000 is for a LG VX9800 cellphone.

Next, make a "udev" rule to detect your phone.  Create /etc/udev/rules.d/60-cell.rules using Nano:

```
sudo nano -w /etc/udev/rules.d/60-cell.rules
```

Then paste the following into the nano editor (highlight the text below, then middle click in terminal to paste):

```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
# LG Phone
SYSFS{idVendor}=="[COLOR="Red"]1004[/COLOR]", SYSFS{idProduct}=="[COLOR="Red"]6000[/COLOR]", GROUP="bitpim", MODE="0660"
LABEL="cell_rules_end"
```

The red sections correspond to the VendorID and ProductID of your phone.  Add it in accordingly.

Ctrl-X to to exit and save the file.  Type y to save and hit enter to confirm the file name.

Reboot. (Alternatively, you can log off, log back in, open terminal, type sudo /etc/init.d/udev restart, then log out and log back in.  At this point of your linux life, it's easier to just restart.)

When you're back into GNOME, hit Alt-F2 and type **bitpim**.  You'll be greeted with the bitpim splash.

In bitpim, click Edit > Settings to open the bitpim settings window.  In that window, choose your phone model from the dropdown menu.  Also, the com port should be set on AUTO.  Click OK to close the window.

Next, click Edit > Detect Phone.  Your phone should be detected by bitpim.

---

### Post by ncappel1 on 2006-08-12
This seems like excellent info, exactly what I needed. But--I just visited my family and forgot the phone cable at their house. They will mail it back soon. I will post the results as soon as I can!

---

### Post by alienseer23 on 2006-08-16
I get this using a samsung a840 phone, following your walk thru to the letter. Closer, but still nothing. First, no phone detected, then I select the interface, bitpim tells me to, then I get this. Help?


[PHP]Frame getdata in src/gui.py at line 1826
           self =  <WorkerThread(BitPim helper, started daemon)>
            req =  <guiwidgets.GetPhoneDialog; proxy of C++ wxDialog instance at _a0f87708_p_wxDial
           todo =  [(<bound method WorkerThread.rebootcheck of <WorkerThread(BitPim helper, started

Frame setupcomm in src/gui.py at line 1809
           name =  'usb::002::002::1'
           self =  <WorkerThread(BitPim helper, started daemon)>
       autofunc =  None
         comcfg =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
          klass =  <class commport.CommConnection at 0xb5abeddc>

Frame __init__ in src/commport.py at line 68
           baud =  115200
   autolistargs =  (<module 'phones.com_samsungspha840' from '/usr/lib/BitPim-0.9.06/bitpim/phones/
           self =  <commport.CommConnection instance at 0xb379bbac>
   hardwareflow =  False
   autolistfunc =  None
        timeout =  3
      logtarget =  <WorkerThread(BitPim helper, started daemon)>
configparameters =  Keys ['baud', 'hardwareflow', 'retryontimeout', 'softwareflow', 'timeout']
                   {'baud': 115200, 'hardwareflow': False, 'softwareflow': False, 'retryontimeout':
   softwareflow =  False
           port =  'usb::002::002::1'

Frame _openport in src/commport.py at line 110
           baud =  115200
          dummy =  0
    description =  None
           self =  <commport.CommConnection instance at 0xb379bbac>
   hardwareflow =  False
        timeout =  3
   softwareflow =  False
           port =  'usb::002::002::1'

Frame _openusb in src/commport.py at line 129
          iface =  <native.usb.usb.USBInterface instance at 0xb2971e4c>
      wantedbus =  '002'
           name =  'usb::002::002::1'
            bus =  <native.usb.usb.USBBus instance at 0xb297944c>
           self =  <commport.CommConnection instance at 0xb379bbac>
      wanteddev =  '002'
        timeout =  3
         device =  <native.usb.usb.USBDevice instance at 0xb2971aec>
    wantediface =  1
              _ =  'usb'

Frame openbulk in src/native/usb/usb.py at line 165
            res =  -16
           self =  <native.usb.usb.USBInterface instance at 0xb2971e4c>
           epin =  <native.usb.usb.USBEndpoint instance at 0xb2971c8c>
              v =  1
          epout =  <native.usb.usb.USBEndpoint instance at 0xb297116c>
             ep =  <native.usb.usb.USBEndpoint instance at 0xb297116c>[/PHP]

---

### Post by alienseer23 on 2006-08-16
It also likes to tell me that is cannot autodetect the port to use, it cannot detect a candidate?

---

### Post by TDogg on 2006-08-17
(Ubuntu Dapper)

I followed JerMe's steps, and it worked for my Samsung a660.  The port was called a "USB to Serial Converter", which confused me... but works.

---

### Post by alienseer23 on 2006-08-18
Ok, how do I roll back these changes, and start from scratch, then? It tells me there is no port available? I know it is in there, it shows up in my device manager. Ugh!

---

### Post by JerMe on 2006-08-18
alienseer23, which steps did you follow?  The OP then mine, or just mine?

---

### Post by alienseer23 on 2006-08-18
> **JerMe said:**
> alienseer23, which steps did you follow?  The OP then mine, or just mine?
first I did this (assuming OP was the original post of this thread)
> -------------------------------------------------------

We will need to convert a RPM package to DEB package, so do this.
sudo apt-get install alien

Now download BitPim from the original website, yes the RPM version.
And convert the RPM to DEB, by entering the following:
sudo alien -d bitpim*.rpm

It will take a few seconds, to convert and it will notify when it finishes.

Now let's install it:
sudo dpkg -i bitpim*.deb

Once installed run it by entering bitpim on the console.

ERRORS:

libstdc++.so.5 -> if you receive this kind of error, do the following:
sudo apt-get install libstdc++5

libtiff.so.3 -> if you receive this kind of error, do the following:
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3

-------------------------------------------------------------------


then I followed your post...(which I also found on bitpim's websight). 

Also, bitpim's websight sais I need some "ACM" driver??? I see no driver and I followed their instructions as to how to go about getting it or activating it, and nothing happens. Help? ((Posting in the right placenow, hehehe))

---

### Post by JerMe on 2006-08-18
[http://www.bitpim.org/help/phones-samsung-cables.htm:](http://www.bitpim.org/help/phones-samsung-cables.htm:)
> Samsung phones use the Linux "acm" driver. This driver will automatically install with most modern Linux distributions will show up as the device /dev/usb/ttyACM0 or similar. If the acm driver does not automatically get loaded, load it with /sbin/insmod acm while logged on as root.

Note that your Samsung SPH-A840 has limitations when using bitpim ([http://www.bitpim.org/help/phones-samsung-model-specific-notes.htm):](http://www.bitpim.org/help/phones-samsung-model-specific-notes.htm):)
> BitPim can read and write the phonebook and calendar. Wallpaper and ringers can be read and writen to the phone. For phones with cameras, pictures and videos are read with the wallpaper.

Many of these Samsung models are also available from carriers other than Sprint in the Americas. While these phones are not officially supported by BitPim, many of the capabilities may work. In many cases, the phonebook and calendar can be transferred, but media (photos, wallpaper, ringers) transfer does work.

These phones have a limit of 300 numbers, urls and emails. There is an internal counter of numbers, urls of emails. This counter can become corrupted (particularly in BitPim version 0.7.26), such that the phone thinks that there are more numbers on the phone than there actually are. This then limits how many numbers can be saved to the phone. The only way to reset this counter to a correct value is to wipe the phonebook and rewrite it. The phonebook can be wiped using an option in the phones security menu. Make sure you have good backup of the phonebook.

Ringer and wallpaper assignments for phonebook entries are not preserved when writing the phonebook to the phone.

---

### Post by alienseer23 on 2006-08-18
Yeah, I know all about that, but I have had it working before on my windows. I had no problems with it there, which makes it a bit confusing why this is happening here. I would love to try the drivers from my windows installs, but have no idea of their equivalent in linux...not ever too sure where I got them. I remember having different drivers for the cable, and the phone....but, still that linux "ACM" driver is absent from my system and apperently it is needed for this operations, so..any idas on how to acquire it?

---

### Post by JerMe on 2006-08-18
Plug in your phone and post the entire output of **lsusb**.

---

### Post by alienseer23 on 2006-08-18
no prob, if I can get the phone to realize it is plugged in. Usually, I have to reboot, then the phone will say "USB CONNECTED". If I unplug it for whatever reason, and then plug it back in, it doesn't connect for some reason, at all, at that poin...like now, running lsusb results in an eternal wait for a result. I am trying to find a way to resolve this. If I cannot, going to reboot, and try the plug again, and yes, I know I have the correct plug, got it from sprint...or at least, they said it was the right one?

um, apparently, lsusb hangs...every time. ugh

---

### Post by JerMe on 2006-08-18
Hmm.  Post the output of these then (highlight terminal, middle click here to paste):
```
grep usb /var/log/messages
```
```
dmesg | grep usb
```

---

### Post by alienseer23 on 2006-08-18
here is the output of grep usb /var/log/messages


>  Aug 16 02:51:57 localhost kernel: [17180508.492000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:52:13 localhost kernel: [17180524.060000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:52:21 localhost kernel: [17180532.032000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:52:44 localhost kernel: [17180555.348000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:53:01 localhost kernel: [17180572.800000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:53:19 localhost kernel: [17180590.148000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:53:24 localhost kernel: [17180594.952000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:53:33 localhost kernel: [17180604.584000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:53:41 localhost kernel: [17180612.172000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:53:58 localhost kernel: [17180629.448000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:54:13 localhost kernel: [17180644.592000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:54:24 localhost kernel: [17180655.760000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:54:32 localhost kernel: [17180662.984000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:54:45 localhost kernel: [17180676.212000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:54:52 localhost kernel: [17180683.976000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:55:22 localhost kernel: [17180713.480000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:55:31 localhost kernel: [17180722.844000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 02:55:51 localhost kernel: [17180742.696000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:01:10 localhost kernel: [17181061.684000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:01:26 localhost kernel: [17181077.424000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:01:32 localhost kernel: [17181082.980000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:01:39 localhost kernel: [17181090.616000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:01:51 localhost kernel: [17181102.536000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:01:56 localhost kernel: [17181107.516000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:02:34 localhost kernel: [17181145.336000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:05:08 localhost kernel: [17181299.180000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:05:15 localhost kernel: [17181306.588000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:05:30 localhost kernel: [17181320.996000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:05:39 localhost kernel: [17181330.804000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:05:46 localhost kernel: [17181336.316000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:05:54 localhost kernel: [17181345.468000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:06:06 localhost kernel: [17181356.628000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 03:06:30 localhost kernel: [17181381.412000] usb 2-2: USB disconnect, address 2
Aug 16 03:06:30 localhost kernel: [17181381.412000] Modules linked in: ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec af_packet nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs dm_mod md_mod sr_mod sbp2 lp tsdev arc4 ieee80211_crypt_wep snd_mpu401 snd_mpu401_uart analog floppy snd_ca0106 gameport parport_pc snd_rawmidi snd_seq_device snd_ac97_codec snd_pcm_oss snd_mixer_oss parport snd_pcm snd_timer psmouse usblp cdc_acm visor usbserial snd soundcore snd_ac97_bus bcm43xx serio_raw snd_page_alloc ieee80211softmac pcspkr ieee80211 ieee80211_crypt nvidia i2c_nforce2 i2c_core shpchp pci_hotplug nvidia_agp agpgart sg sd_mod evdev usb_storage ext3 jbd ide_generic ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tilebl
Aug 16 22:59:52 localhost kernel: [17179575.852000] usbcore: registered new driver usbfs
Aug 16 22:59:52 localhost kernel: [17179575.852000] usbcore: registered new driver hub
Aug 16 22:59:52 localhost kernel: [17179576.816000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 16 22:59:52 localhost kernel: [17179577.180000] usbcore: registered new driver usb-storage
Aug 16 22:59:52 localhost kernel: [17179577.564000] usb 1-2: new full speed USB device using ohci_hcd and address 3
Aug 16 22:59:52 localhost kernel: [17179578.176000] usb 2-2: new full speed USB device using ohci_hcd and address 2
Aug 16 22:59:52 localhost kernel: [17179588.536000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
Aug 16 22:59:52 localhost kernel: [17179588.536000] usbcore: registered new driver usblp
Aug 16 22:59:52 localhost kernel: [17179588.536000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Aug 16 22:59:52 localhost kernel: [17179588.864000] usbcore: registered new driver usbserial
Aug 16 22:59:52 localhost kernel: [17179588.864000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Aug 16 22:59:52 localhost kernel: [17179588.864000] usbcore: registered new driver usbserial_generic
Aug 16 22:59:52 localhost kernel: [17179588.864000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Aug 16 22:59:52 localhost kernel: [17179588.868000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Aug 16 22:59:52 localhost kernel: [17179588.868000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Aug 16 22:59:52 localhost kernel: [17179588.868000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Aug 16 22:59:52 localhost kernel: [17179588.868000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Aug 16 22:59:52 localhost kernel: [17179588.868000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Aug 16 22:59:52 localhost kernel: [17179588.872000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
Aug 16 22:59:52 localhost kernel: [17179588.872000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB3
Aug 16 22:59:52 localhost kernel: [17179588.872000] usbcore: registered new driver visor
Aug 16 22:59:52 localhost kernel: [17179588.872000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Aug 16 22:59:52 localhost kernel: [17179588.884000] usbcore: registered new driver cdc_acm
Aug 16 22:59:52 localhost kernel: [17179588.884000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug 16 23:14:47 localhost kernel: [17180527.720000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:15:31 localhost kernel: [17180571.680000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:15:47 localhost kernel: [17180587.720000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:16:04 localhost kernel: [17180604.796000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:17:48 localhost kernel: [17180709.240000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:18:01 localhost kernel: [17180721.612000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:19:47 localhost kernel: [17180827.832000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:26:58 localhost kernel: [17181258.776000] usb 3-3: usbfs: interface 0 claimed by usb-storage while 'bitpim' sets config #2
Aug 16 23:26:58 localhost kernel: [17181258.776000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:26:58 localhost kernel: [17181258.788000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:26:58 localhost kernel: [17181258.792000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:26:58 localhost kernel: [17181258.808000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:26:58 localhost kernel: [17181258.812000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:27:01 localhost kernel: [17181261.516000] usb 3-3: usbfs: interface 0 claimed by usb-storage while 'bitpim' sets config #2
Aug 16 23:27:01 localhost kernel: [17181261.520000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:01 localhost kernel: [17181261.560000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:01 localhost kernel: [17181261.564000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:01 localhost kernel: [17181261.576000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:01 localhost kernel: [17181261.584000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:27:20 localhost kernel: [17181280.476000] usb 3-3: usbfs: interface 0 claimed by usb-storage while 'bitpim' sets config #2
Aug 16 23:27:20 localhost kernel: [17181280.480000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:20 localhost kernel: [17181280.488000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:20 localhost kernel: [17181280.488000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:20 localhost kernel: [17181280.504000] usb 1-2: usbfs: interface 1 claimed by usblp while 'bitpim' sets config #1
Aug 16 23:27:20 localhost kernel: [17181280.508000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 16 23:45:57 localhost kernel: [17182397.912000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 17 00:28:10 localhost kernel: [17179575.680000] usbcore: registered new driver usbfs
Aug 17 00:28:10 localhost kernel: [17179575.680000] usbcore: registered new driver hub
Aug 17 00:28:10 localhost kernel: [17179576.880000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 17 00:28:10 localhost kernel: [17179577.628000] usb 1-2: new full speed USB device using ohci_hcd and address 3
Aug 17 00:28:10 localhost kernel: [17179578.240000] usb 2-2: new full speed USB device using ohci_hcd and address 2
Aug 17 00:28:10 localhost kernel: [17179587.912000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
Aug 17 00:28:10 localhost kernel: [17179587.912000] usbcore: registered new driver usblp
Aug 17 00:28:10 localhost kernel: [17179587.912000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Aug 17 00:28:10 localhost kernel: [17179587.920000] usbcore: registered new driver usb-storage
Aug 17 00:28:10 localhost kernel: [17179587.944000] usbcore: registered new driver usbserial
Aug 17 00:28:10 localhost kernel: [17179587.944000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Aug 17 00:28:10 localhost kernel: [17179587.944000] usbcore: registered new driver usbserial_generic
Aug 17 00:28:10 localhost kernel: [17179587.944000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Aug 17 00:28:10 localhost kernel: [17179587.952000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Aug 17 00:28:10 localhost kernel: [17179587.952000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Aug 17 00:28:10 localhost kernel: [17179587.952000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Aug 17 00:28:10 localhost kernel: [17179587.956000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Aug 17 00:28:10 localhost kernel: [17179587.956000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Aug 17 00:28:10 localhost kernel: [17179587.956000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
Aug 17 00:28:10 localhost kernel: [17179587.956000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB3
Aug 17 00:28:10 localhost kernel: [17179587.956000] usbcore: registered new driver visor
Aug 17 00:28:10 localhost kernel: [17179587.956000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Aug 17 00:28:10 localhost kernel: [17179587.964000] usbcore: registered new driver cdc_acm
Aug 17 00:28:10 localhost kernel: [17179587.964000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug 17 00:29:20 localhost kernel: [17179680.808000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 17 00:29:31 localhost kernel: [17179691.496000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 17 00:29:37 localhost kernel: [17179697.232000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 17 00:30:04 localhost kernel: [17179725.176000] usb 2-2: usbfs: interface 0 claimed by visor while 'bitpim' sets config #1
Aug 17 02:23:29 localhost kernel: [17186529.572000] usb 2-2: USB disconnect, address 2
Aug 17 02:23:29 localhost kernel: [17186529.572000] Modules linked in: ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec af_packet nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs sg sd_mod dm_mod md_mod sr_mod sbp2 lp arc4 ieee80211_crypt_wep tsdev cdc_acm visor usbserial usb_storage usblp bcm43xx snd_mpu401 snd_mpu401_uart snd_ca0106 snd_rawmidi snd_seq_device ieee80211softmac snd_ac97_codec snd_pcm_oss snd_mixer_oss ieee80211 ieee80211_crypt snd_pcm snd_timer snd soundcore snd_ac97_bus analog snd_page_alloc nvidia pcspkr floppy parport_pc parport gameport psmouse serio_raw i2c_nforce2 i2c_core shpchp pci_hotplug nvidia_agp agpgart evdev ext3 jbd ide_generic ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tilebl
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+947500246/1069171712] usb_serial_disconnect+0x56/0xd0 [usbserial]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944456002/1069171712] usb_unbind_interface+0x42/0x90 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944493064/1069171712] usb_disable_device+0xb8/0x130 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944467296/1069171712] usb_disconnect+0xb0/0x150 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944473376/1069171712] hub_port_connect_change+0x60/0x440 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944461191/1069171712] clear_port_feature+0x57/0x60 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944475121/1069171712] hub_events+0x2f1/0x480 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944475520/1069171712] hub_thread+0x0/0xf0 [usbcore]
Aug 17 02:23:29 localhost kernel: [17186529.572000]  [pg0+944475541/1069171712] hub_thread+0x15/0xf0 [usbcore]
Aug 17 13:11:00 localhost kernel: [17179576.104000] usbcore: registered new driver usbfs
Aug 17 13:11:00 localhost kernel: [17179576.104000] usbcore: registered new driver hub
Aug 17 13:11:00 localhost kernel: [17179577.180000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 17 13:11:00 localhost kernel: [17179577.544000] usbcore: registered new driver usb-storage
Aug 17 13:11:00 localhost kernel: [17179577.928000] usb 1-2: new full speed USB device using ohci_hcd and address 3
Aug 17 13:11:00 localhost kernel: [17179578.540000] usb 2-2: new full speed USB device using ohci_hcd and address 2
Aug 17 13:11:00 localhost kernel: [17179592.728000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
Aug 17 13:11:00 localhost kernel: [17179592.732000] usbcore: registered new driver usblp
Aug 17 13:11:00 localhost kernel: [17179592.732000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Aug 17 13:11:00 localhost kernel: [17179593.672000] usbcore: registered new driver usbserial
Aug 17 13:11:00 localhost kernel: [17179593.672000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Aug 17 13:11:00 localhost kernel: [17179593.672000] usbcore: registered new driver usbserial_generic
Aug 17 13:11:00 localhost kernel: [17179593.672000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Aug 17 13:11:00 localhost kernel: [17179593.688000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Aug 17 13:11:00 localhost kernel: [17179593.688000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Aug 17 13:11:00 localhost kernel: [17179593.688000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Aug 17 13:11:00 localhost kernel: [17179593.688000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Aug 17 13:11:00 localhost kernel: [17179593.688000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Aug 17 13:11:00 localhost kernel: [17179593.692000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
Aug 17 13:11:00 localhost kernel: [17179593.692000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB3
Aug 17 13:11:00 localhost kernel: [17179593.692000] usbcore: registered new driver visor
Aug 17 13:11:00 localhost kernel: [17179593.692000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Aug 17 13:11:00 localhost kernel: [17179593.712000] usbcore: registered new driver cdc_acm
Aug 17 13:11:00 localhost kernel: [17179593.712000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug 17 14:51:04 localhost kernel: [17185641.060000] usb 2-2: USB disconnect, address 2
Aug 17 14:51:04 localhost kernel: [17185641.060000] Modules linked in: jfs xfs exportfs reiserfs ext2 hfs hfsplus isofs udf ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec af_packet nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs dm_mod md_mod sr_mod sbp2 lp arc4 ieee80211_crypt_wep tsdev cdc_acm visor usbserial snd_ca0106 snd_ac97_codec snd_pcm_oss snd_mixer_oss bcm43xx analog snd_pcm snd_timer gameport ieee80211softmac ieee80211 ieee80211_crypt snd_mpu401 snd_mpu401_uart snd_rawmidi snd_seq_device snd_ac97_bus snd_page_alloc snd soundcore parport_pc parport pcspkr usblp psmouse serio_raw floppy nvidia nvidia_agp i2c_nforce2 i2c_core shpchp pci_hotplug agpgart sg sd_mod evdev usb_storage ext3 jbd ide_generic ohci1394 ieee1394 ehci_hcd ohci_hcd usbcore ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor f
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+947717334/1069171712] usb_serial_disconnect+0x56/0xd0 [usbserial]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944456002/1069171712] usb_unbind_interface+0x42/0x90 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944493064/1069171712] usb_disable_device+0xb8/0x130 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944467296/1069171712] usb_disconnect+0xb0/0x150 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944473376/1069171712] hub_port_connect_change+0x60/0x440 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944461191/1069171712] clear_port_feature+0x57/0x60 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944475121/1069171712] hub_events+0x2f1/0x480 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944475520/1069171712] hub_thread+0x0/0xf0 [usbcore]
Aug 17 14:51:04 localhost kernel: [17185641.060000]  [pg0+944475541/1069171712] hub_thread+0x15/0xf0 [usbcore]
Aug 18 02:41:23 localhost kernel: [17179577.112000] usbcore: registered new driver usbfs
Aug 18 02:41:23 localhost kernel: [17179577.112000] usbcore: registered new driver hub
Aug 18 02:41:23 localhost kernel: [17179578.084000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 18 02:41:23 localhost kernel: [17179578.344000] usbcore: registered new driver usb-storage
Aug 18 02:41:23 localhost kernel: [17179578.648000] usb 1-2: new full speed USB device using ohci_hcd and address 3
Aug 18 02:41:23 localhost kernel: [17179593.268000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
Aug 18 02:41:23 localhost kernel: [17179593.268000] usbcore: registered new driver usblp
Aug 18 02:41:23 localhost kernel: [17179593.268000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Aug 18 03:55:37 localhost kernel: [17179575.828000] usbcore: registered new driver usbfs
Aug 18 03:55:37 localhost kernel: [17179575.828000] usbcore: registered new driver hub
Aug 18 03:55:37 localhost kernel: [17179576.952000] usb 3-3: new high speed USB device using ehci_hcd and address 3
Aug 18 03:55:37 localhost kernel: [17179577.516000] usb 1-2: new full speed USB device using ohci_hcd and address 3
Aug 18 03:55:37 localhost kernel: [17179587.500000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
Aug 18 03:55:37 localhost kernel: [17179587.500000] usbcore: registered new driver usblp
Aug 18 03:55:37 localhost kernel: [17179587.500000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Aug 18 03:55:37 localhost kernel: [17179587.580000] usbcore: registered new driver usb-storage
Aug 18 04:36:22 localhost kernel: [17182052.188000] usb 2-2: new full speed USB device using ohci_hcd and address 2
Aug 18 04:36:22 localhost kernel: [17182052.776000] usbcore: registered new driver usbserial
Aug 18 04:36:22 localhost kernel: [17182052.776000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Aug 18 04:36:22 localhost kernel: [17182052.780000] usbcore: registered new driver usbserial_generic
Aug 18 04:36:22 localhost kernel: [17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Aug 18 04:36:22 localhost kernel: [17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Aug 18 04:36:22 localhost kernel: [17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Aug 18 04:36:22 localhost kernel: [17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Aug 18 04:36:22 localhost kernel: [17182052.784000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
Aug 18 04:36:22 localhost kernel: [17182052.788000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
Aug 18 04:36:22 localhost kernel: [17182052.792000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
Aug 18 04:36:22 localhost kernel: [17182052.796000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB3
Aug 18 04:36:22 localhost kernel: [17182052.796000] usbcore: registered new driver visor
Aug 18 04:36:22 localhost kernel: [17182052.796000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
Aug 18 04:36:22 localhost kernel: [17182052.812000] usbcore: registered new driver cdc_acm
Aug 18 04:36:22 localhost kernel: [17182052.812000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
Aug 18 04:37:17 localhost kernel: [17182107.072000] usb 2-2: USB disconnect, address 2
Aug 18 04:37:17 localhost kernel: [17182107.072000] Modules linked in: cdc_acm visor usbserial ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs sg sd_mod dm_mod md_mod sr_mod sbp2 lp arc4 ieee80211_crypt_wep tsdev snd_ca0106 pcspkr snd_ac97_codec snd_pcm_oss snd_mixer_oss bcm43xx parport_pc parport snd_mpu401 snd_mpu401_uart snd_pcm snd_timer snd_rawmidi snd_seq_device ieee80211softmac ieee80211 ieee80211_crypt snd nvidia floppy snd_ac97_bus usb_storage soundcore analog snd_page_alloc gameport usblp psmouse shpchp pci_hotplug serio_raw i2c_nforce2 i2c_core nvidia_agp agpgart evdev ext3 jbd ide_generic ehci_hcd ohci_hcd ohci1394 ieee1394 usbcore ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bi
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+951649494/1069171712] usb_serial_disconnect+0x56/0xd0 [usbserial]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944456002/1069171712] usb_unbind_interface+0x42/0x90 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944493064/1069171712] usb_disable_device+0xb8/0x130 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944467296/1069171712] usb_disconnect+0xb0/0x150 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944473376/1069171712] hub_port_connect_change+0x60/0x440 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944461191/1069171712] clear_port_feature+0x57/0x60 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944475121/1069171712] hub_events+0x2f1/0x480 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944475520/1069171712] hub_thread+0x0/0xf0 [usbcore]
Aug 18 04:37:17 localhost kernel: [17182107.072000]  [pg0+944475541/1069171712] hub_thread+0x15/0xf0 [usbcore]

---

### Post by alienseer23 on 2006-08-18
and here is the output of of dmesg | grep usb

>  [17179575.828000] usbcore: registered new driver usbfs
[17179575.828000] usbcore: registered new driver hub
[17179576.952000] usb 3-3: new high speed USB device using ehci_hcd and address 3
[17179577.516000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[17179587.500000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4911
[17179587.500000] usbcore: registered new driver usblp
[17179587.500000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179587.576000] usb-storage: device found at 3
[17179587.576000] usb-storage: waiting for device to settle before scanning
[17179587.580000] usb-storage: device found at 3
[17179587.580000] usb-storage: waiting for device to settle before scanning
[17179587.580000] usbcore: registered new driver usb-storage
[17179592.588000] usb-storage: device scan complete
[17179592.600000] usb-storage: device scan complete
[17182052.188000] usb 2-2: new full speed USB device using ohci_hcd and address 2
[17182052.776000] usbcore: registered new driver usbserial
[17182052.776000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17182052.780000] usbcore: registered new driver usbserial_generic
[17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
[17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
[17182052.780000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
[17182052.784000] usb 2-2: palm_os_4_probe - error -32 getting connection info
[17182052.784000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB0
[17182052.788000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB1
[17182052.788000] usb 2-2: palm_os_4_probe - error -32 getting connection info
[17182052.792000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB2
[17182052.796000] usb 2-2: Handspring Visor / Palm OS converter now attached to ttyUSB3
[17182052.796000] usbcore: registered new driver visor
[17182052.796000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[17182052.812000] usbcore: registered new driver cdc_acm
[17182052.812000] drivers/usb/class/cdc-acm.c: v0.23:USB Abstract Control Model driver for USB modems and ISDN adapters
[17182107.072000] usb 2-2: USB disconnect, address 2
[17182107.072000] Modules linked in: cdc_acm visor usbserial ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec nls_iso8859_1 nls_cp437 vfat fat nls_utf8 ntfs sg sd_mod dm_mod md_mod sr_mod sbp2 lp arc4 ieee80211_crypt_wep tsdev snd_ca0106 pcspkr snd_ac97_codec snd_pcm_oss snd_mixer_oss bcm43xx parport_pc parport snd_mpu401 snd_mpu401_uart snd_pcm snd_timer snd_rawmidi snd_seq_device ieee80211softmac ieee80211 ieee80211_crypt snd nvidia floppy snd_ac97_bus usb_storage soundcore analog snd_page_alloc gameport usblp psmouse shpchp pci_hotplug serio_raw i2c_nforce2 i2c_core nvidia_agp agpgart evdev ext3 jbd ide_generic ehci_hcd ohci_hcd ohci1394 ieee1394 usbcore ide_disk ide_cd cdrom generic amd74xx sata_nv libata scsi_mod thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[17182107.072000]  [<f8fea4d6>] usb_serial_disconnect+0x56/0xd0 [usbserial]
[17182107.072000]  [<f890e142>] usb_unbind_interface+0x42/0x90 [usbcore]
[17182107.072000]  [<f8917208>] usb_disable_device+0xb8/0x130 [usbcore]
[17182107.072000]  [<f8910d60>] usb_disconnect+0xb0/0x150 [usbcore]
[17182107.072000]  [<f8912520>] hub_port_connect_change+0x60/0x440 [usbcore]
[17182107.072000]  [<f890f587>] clear_port_feature+0x57/0x60 [usbcore]
[17182107.072000]  [<f8912bf1>] hub_events+0x2f1/0x480 [usbcore]
[17182107.072000]  [<f8912d80>] hub_thread+0x0/0xf0 [usbcore]
[17182107.072000]  [<f8912d95>] hub_thread+0x15/0xf0 [usbcore]

---

### Post by alienseer23 on 2006-08-18
i noticed that there is alot of mention of palm os devise visor or something like this...I have no palm os device, unless it means my mobile? Ids it incorrectly reading my device?

---

### Post by JerMe on 2006-08-18
Could possibly be.  I noticed that too, and was about to ask you if you owned any of these devices.  Obviously, the cdc_acm module is being loaded so you're fine with that.

---

### Post by alienseer23 on 2006-08-18
I saw that, too...the cdc_acm. I am wondering how to get the palm os out of there...any ideas?

---

### Post by JerMe on 2006-08-18
Sorry. :(  At this point, you should jump on the bitpim-user mailing list:
[https://lists.sourceforge.net/lists/listinfo/bitpim-user](https://lists.sourceforge.net/lists/listinfo/bitpim-user)

I can't figure why your phone would hang at the issue of **lsusb** or would connect and disconnect intermittently.  When things like that happen, I automatically assume bad hardware.  You said that your phone and cable works in Windows, so it's not the cable (hopefully).  Right now, you need to find out why your phone hangs upon connection.

I'd say for now, uninstall bitpim with **sudo dpkg --remove --purge bitpim**,then **rm -fr ~/.bitpim***, then jump on the mailing list.

---

### Post by alienseer23 on 2006-08-18
sorry, it isn't the phone that hangs, its the terminal at the lsusb command, there is no output, but the phone still works fine. It also does not connect and disconnect like all that. The phone will function fine in all instances as itself, a phone. When I plug the cable into the phone, it is supposed to say "usb connected" on the display of the phone, this only happens when I have the phone connected fresh from boot or reboot of the system, I don't know why. Then, if I manually disconect the cable from the phone, to say..take it to the store or something, and bring it back and reconnect the cable, there is no notification, I assume the phone or the comp is not responding in any way at all to the connection. This happens with my girl's phone, I tested it last night. What I think is happening is the cable driver (?) works from boot with the phone, but as soon as the system is up, the palm os visor mod (?) seems to be taking over the cable/usb connection(?), so the actual cable for the phone won't transmit any data, because the system thinks it is a palm/os 'visor' device. Or at leaste the palm os visor mod in the system is blocking communications. Does this seem like I am ANYWHERE near the bullseye? BEst shot here with this.

---

### Post by alienseer23 on 2006-08-20
I just thought I would post that this same thing happens on another computer with the samsung a840 phone and the sprint-supplied spsc cable. THe connection is good when connected from boot, but the phone does not get detected with bitpim. When I disconnect The cable, and reconect it, there is no connection at all with the phone and the computer. The cable itself on both systems is listed in bitpim as working adn all, but not available to access. weird. Help?

---

### Post by ramcosca on 2006-09-15
Hello. I have a question... how do I send an mp3 to the phone using BitPim? I tried doing it, reformatted the song to fit it (in the program) but it doesn't want to send it to the phone. What can I do?

---

### Post by JerMe on 2006-09-15
> **ramcosca said:**
> Hello. I have a question... how do I send an mp3 to the phone using BitPim? I tried doing it, reformatted the song to fit it (in the program) but it doesn't want to send it to the phone. What can I do?

What phone are you using?  Are you trying to upload the mp3 as a ringtone or as a song to be played in the phone's music player?  Which verison of bitpim are you using?  How did you install it?  Did you follow the original post, and the instructions from the bitpim website (that I summarized earlier in this thread)?  Details ;)

---

### Post by djin44 on 2006-09-16
Hm, I have the AMD64, I seem to be getting quite a few errors when converting the RPM to DEB.

Is there a 64-bit version of Bitpim?

---

### Post by Epperly on 2006-10-21
Hey all, can anybody tell me how to add BitPim to my Applications menu?
Also, what category would it go under?
It is located in /usr/lib/BitPim-0.9.07/ if that's any different..

---

### Post by d351GuJu on 2006-10-22
> **Epperly said:**
> Hey all, can anybody tell me how to add BitPim to my Applications menu?
Also, what category would it go under?
It is located in /usr/lib/BitPim-0.9.07/ if that's any different..

Epperly,

I would add BitPim to "Utilities" section of the menu.  Here's how to add it.

Hit Alt+F2 -> enter "kmenuedit" and you should see the "menu editor".
Go under "Utilities" section, and right click and click "New Item...", there you should enter the following:

Item Name:  BitPim
Icon (on right hand side):  Select an icon that you like the best.
Command:  This is where you tell where the program is, if you can enter bitpim on command line, then all u need to enter here is "bitpim"; otherwise, you will need to tell it where the program is located at.

See the picture for more detail.

---

### Post by Epperly on 2006-10-22
I don't have kmenuedit. I am in gnome if that makes a difference.
Also Alacarte now isn't here in Edgy I just upgraded from Dapper where I did have it..

---

### Post by lorddaddy84 on 2006-10-24
I can browse the file system on my E816 but when I try to backup my phone book, I get this error.
> BitPim version: 0.9.07-official
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "src/gui.py", line 1770, in OnCallback
  File "src/gui.py", line 177, in __call__
  File "src/gui.py", line 134, in __call__
  File "src/gui.py", line 1614, in OnProgressMinor
  File "src/guiwidgets.py", line 1277, in progressminor
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 928, in SetValue
PyAssertionError: C++ assertion "wxAssertFailure" failed in ../src/gtk/gauge.cpp(95): invalid value in wxGauge::SetValue()

Variables by last 8 frames, innermost last

Frame MainLoop in /usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py at line 7720
           self =  <gui.MainApp; proxy of C++ wxPyApp instance at _d0054f08_p_wxPyApp>

Frame MainLoop in /usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py at line 7153
           args =  (<gui.MainApp; proxy of C++ wxPyApp instance at _d0054f08_p_wxPyApp>,)
         kwargs =  Keys []
                   {}

Frame OnCallback in src/gui.py at line 1770
           self =  <gui.MainWindow; proxy of C++ wxFrame instance at _b0106408_p_wxFrame>
          event =  <gui.HelperReturnEvent; proxy of C++ wxPyEvent instance at _80f00209_p_wxPyEvent

Frame __call__ in src/gui.py at line 177
           self =  <gui.HelperReturnEvent; proxy of C++ wxPyEvent instance at _80f00209_p_wxPyEvent

Frame __call__ in src/gui.py at line 134
           self =  <gui.Callback instance at 0xb54ece6c>
           args =  (500, 10, 'Reading conatct entry 1 to 10')
              d =  Keys []
                   {}
         kwargs =  Keys []
                   {}

Frame OnProgressMinor in src/gui.py at line 1614
            max =  10
           self =  <gui.MainWindow; proxy of C++ wxFrame instance at _b0106408_p_wxFrame>
            pos =  500
           desc =  'Reading conatct entry 1 to 10'

Frame progressminor in src/guiwidgets.py at line 1277
            max =  10
           self =  <guiwidgets.MyStatusBar; proxy of C++ wxStatusBar instance at _60266408_p_wxStat
            pos =  500
           desc =  'Reading conatct entry 1 to 10'

Frame SetValue in /usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py at line 928
           args =  (<wx._controls.Gauge; proxy of C++ wxGauge instance at _78736e08_p_wxGauge>, 500
         kwargs =  Keys []
                   {}

Any Ideas?
Thanks.

---

### Post by Epperly on 2006-10-25
nevermind I figured it out... I forgot post #12, thanks

---

### Post by SmiLey497 on 2006-10-26
i followed the instructions on how to add a usb port but bitpim doesn't automatically detect my phone, i have to manually set it and for some reason there is another samsung port listed but it says its not available. and also when i transfer a ring tone to my phone it transfers fine but when the ring tone is in my phone it doesn't play:(

---

### Post by SmiLey497 on 2006-10-26
here is a pic 
[IMG]http://www.msprotege.com/members/-YellowMSP-/Screenshot3.jpg[/IMG]

---

### Post by lazyart on 2006-10-26
Doesn't work with the plain-vanilla Razr V3 (Cingular's original Razr).  Tried V3c V3cm and 710 but no luck. You can plug it into the USB port and use it as a phone charger. :D

---

### Post by SmiLey497 on 2006-10-29
i did everything but liek the guide syas but bitpim doesn't open, any suggestions???

---

### Post by qrm on 2006-10-29
why dont you install it from synaptic?

---

### Post by Pianoman72 on 2006-11-06
> **alienseer23 said:**
> i noticed that there is alot of mention of palm os devise visor or something like this...I have no palm os device, unless it means my mobile? Ids it incorrectly reading my device?

I sent you a PM.

Here is the solution for others.  This might just be an issue with SAMSUNG phones, but if you run lsmod and your machine is loading a module/driver named "visor" (when you connect your usb cable) you need to edit /etc/modprobe.conf and add the line "blacklist visor".

You might need to create modprobe.conf - don't worry about messing anything up by doing this.

Then, assuming you have followed all of the instructions in this thread so far I am going to add this:

In bitpim, manually select /dev/ttyACM0 as the port for your phone. I have a Samsung a640 but I selected a620 in order to add music (this posted on the bitpim.org site).

That should work.

Oh, also I always have to "sudo bitpim" in order for it to load correctly...also try this if you are having problems.

---

### Post by d351GuJu on 2006-11-07
Everyone, please if you have your device working with bitpim, post here and I will make changes to the original post so that others like you won't have to spend so much time browsing through the thread.

Thanks,

d351GuJu

---

### Post by lorddaddy84 on 2006-11-07
I can start bitpim with my e815 plugged in and it will say No phone recognized but I can click on file system and browse the file system.
Can someone help me get it to work with all the features?
Thanks.

---

### Post by Epperly on 2006-11-09
oops! I ran "sudo usermod -G bitpim -a your_user_name" without the -a and now when I go to users and groups I get an error:
Failed to run users-admin.

Help please! =\

---

### Post by pooslinger on 2006-11-29
```
# apt-get install alien
```

Then convert it (this needs to be run as root) and then install the resulting deb:
```
# alien bitpim*.rpm
# dpkg -i bitpim*.deb
```

Then we need to create a symlink due to bitpim's use of libbtiff version 3:
```
# cd /usr/lib
#ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

If needed
```
# apt-get install libstdc++5
```

**Must run as root or USB device will be unavailable**

Set to auto detect.  VX9900 USB cable.

[http://www.quietearth.us/articles/2006/09/11/Ubuntu-Installing-bitpim](http://www.quietearth.us/articles/2006/09/11/Ubuntu-Installing-bitpim)

---

### Post by PokerFacePenguin on 2006-12-24
> **marlin said:**
> Sorry to break into your thread but I am having the same difficulty running BitPim in Kubuntu-Dapper and am asking for your assistance. 

I converted the RPM to .DEB (bitpim_0.9.04-1_i386.deb).

I then installed using dpkg -i bitpim_0.9.04-1_i386.deb . 
When I run "bitpim" from my home directory I receive the following error:

Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory. 

Upon seeing the reference to libtiff.so.3, I created the suggested link in my home directory and when I run bitpim I recieve the same error as above. Any help is much appreciated.

You probably have libtiff.so.4 so set the link appropriately.  Hope this helps.

---

### Post by nynoah on 2007-02-01
when I try to install this I run into a problem.  after I install alien, I try to convert the RMP file but for some reason the RPM file can not be found.  I downloaded it and I can see the file on my desktop.....whats going on?

Noah

---

### Post by SmiLey497 on 2007-02-02
when you open the terminal write 

> sudo alien -k then drag the rpm file to the terminal then press enter

---

### Post by tribeone on 2007-02-09
Ok guys I followed the sreps outline at the begining on installing alien and it is installed but I am now having prob converting the rpm. I dwn loaded the bitpim file and it is on my comp i see it on my desktop. This is what I get


```
:~$ sudo alien -d bitpim*.rpm
File "bitpim*.rpm" not found.

```

---

### Post by lollikerwin on 2007-02-11
Have to post this so that others don't waste 2 days on it like I did (idiot!): set up bluetooth dongle (this a nightmare in itself - install bluez-passkey-gnome and add bt-applet to startup for easy pairing*), installed BitPim 0.9.11 on Edgy, connected my vx9900 (enV) and ran rfcomm connect according to [http://www.quietearth.us/vx9800.htm](http://www.quietearth.us/vx9800.htm) (thanks pooslinger!).  

No matter what, the phone is not detected.  :mad:  I reinstall BitPim a million times: from the repos, from Debian, older versions from BitPim site; I install it on my virtual WinXP (POS dongle repeatedly crashes it so no help here)... all to no avail.  I had clicked on different items in BitPim, but it wasn't until I accidentally click on "View>>View Filesystem" and then later click on "Filesystem" in the main BitPim window that I realize that the phone is actually connected but just not displaying as detected because the phone's file directory shows up!  DOH!  I click on "Get Phone Data" and retrieve the rest of the phone's info.  This is where I am now, so wish me luck with actual file transfer...

So for anyone else connecting an enV to Edgy with bluetooth...  Hope I saved you some time!

*In Feisty use bluez-gnome and bluetooth-applet instead.

---

### Post by TheBandit181 on 2007-02-13
USER@ubuntu:/usr/lib$ ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
ln: creating symbolic link `/usr/lib/libtiff.so.3' to `/usr/lib/libtiff.so.4': File exists
USER@ubuntu:/usr/lib$ bitpim
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 20, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory

I get this error when trying to run.  I think correctly set the link, I posted the past to steps to maybe pinpoint the spot where I went wrong.

---

### Post by usererror on 2007-02-17
This how to worked perfectly for me according to the directions on post #1...I had to do the #2 option under errors.

Now i can see files in / of my phone alltel v3c but i cannot see /motorola/system I have GOT to get rid of these awful startup/shutdown mp3s and get a silence ones on there instead.

---

### Post by 13east on 2007-05-14
> **tribeone said:**
> Ok guys I followed the sreps outline at the begining on installing alien and it is installed but I am now having prob converting the rpm. I dwn loaded the bitpim file and it is on my comp i see it on my desktop. This is what I get


```
:~$ sudo alien -d bitpim*.rpm
File "bitpim*.rpm" not found.

```

make sure you're in the correct directory when trying to convert from rpm to deb...
if you're using firefox, the browser would normally save your files to the Desktop by default... and if this is where you have the rpm file, you need to redirect terminal to the Desktop... terminal starts off in your home directory by default and you have "cd" to change the folder you're viewing...
the following command will change terminal directory to the Desktop: ```
cd ~/Desktop
```

... hope this helps

---

### Post by 13east on 2007-05-14
> **pooslinger said:**
> ```
# apt-get install alien
```

Then convert it (this needs to be run as root) and then install the resulting deb:
```
# alien bitpim*.rpm
# dpkg -i bitpim*.deb
```

Then we need to create a symlink due to bitpim's use of libbtiff version 3:
```
# cd /usr/lib
#ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

If needed
```
# apt-get install libstdc++5
```

**Must run as root or USB device will be unavailable**

Set to auto detect.  VX9900 USB cable.

[http://www.quietearth.us/articles/2006/09/11/Ubuntu-Installing-bitpim](http://www.quietearth.us/articles/2006/09/11/Ubuntu-Installing-bitpim)

got bitpim to recognize my lg cu500 (cingular) using this guide... just had to create the symlink...  the only issue is the bitpim always refuses to close cleanly stating a busy status, its really annoying... i assume i have to eject the phone manually from the program before i close it, but if anyone knows for sure thanks in advance for any help you can provide...

---

### Post by AJI on 2007-05-22
**NOTE TO 64-BIT USERS:**

I fixed my libtiff.so.3 issue by running:

```
ln -s /usr/lib32/libtiff.so.4 /usr/lib32/libtiff.so.3
```

---

### Post by DiZASTiX on 2007-06-12
I followed OP's instructions, then JerMe's instructions on page 2 but bitpim still wasn't detecting my phone. Then, I ran it as root (sudo bitpim in a terminal) and it auto detected it! My phone is a LG enV (aka VX9900)

Thanks!

---

### Post by r0bby1982 on 2007-08-01
Running bitpim as root allows you to access the phone; translation: either su to root or use sudo :)

Hope this helps somebody :)

---

### Post by PhutterMan on 2007-08-05
I installed the version from Synaptic and it does funny things with my phone (ie, when I connect to the phone it dials a number on the phone and then resets it).  Now, I'm using it over Bluetooth on rfcomm0.  I believe the weirdness with the phone arises from the older version of the program, as the newest test version works fine with the same phone over Bluetooth with Windows.  The phone is an LG vx8600.

Therefore, I want to install the newest version for Linux, but I'm on AMD64.  The .deb package doesn't work because of the architecture, and the .rpm method described in this thread gives off an impressive list of errors, starting with a bunch of dependency-related ones and finally making a snide remark (well, an error) about it being the wrong architecture, also.

Is it possible to install bitpim at all on amd64??  I assume it is, but I didn't see that come up in this discussion, and I wondered if anyone knew.

Thanks!

---

### Post by JerMe on 2007-08-05
> **PhutterMan said:**
> I installed the version from Synaptic and it does funny things with my phone (ie, when I connect to the phone it dials a number on the phone and then resets it).  Now, I'm using it over Bluetooth on rfcomm0.  I believe the weirdness with the phone arises from the older version of the program, as the newest test version works fine with the same phone over Bluetooth with Windows.  The phone is an LG vx8600.

Therefore, I want to install the newest version for Linux, but I'm on AMD64.  The .deb package doesn't work because of the architecture, and the .rpm method described in this thread gives off an impressive list of errors, starting with a bunch of dependency-related ones and finally making a snide remark (well, an error) about it being the wrong architecture, also.

Is it possible to install bitpim at all on amd64??  I assume it is, but I didn't see that come up in this discussion, and I wondered if anyone knew.

Thanks!

You could try installing the i386 .deb file with the --force-architecture flag and see if it installs in the 64-bit environment.  I haven't tried it with bitpim, but
sometimes it works with other deb files.

```
sudo dpkg -i --force-architecture bitpim-version.deb
```

---

### Post by PhutterMan on 2007-08-07
Thanks, I'll try that.  I'll post the results once I get a chance to do it.

---

### Post by LobbyDizzle on 2007-11-04
jared@jared-laptop:~$ sudo dpkg -i --force-architecture bitpim-version.deb
dpkg: error processing bitpim-version.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 bitpim-version.deb




This is the error that I get. I know there is a simple solution to this since I have only had Ubuntu for about 3 days now...

oh yea, I did download and save bitpim.

---

### Post by MaindotC on 2008-01-21
I've been monitoring this thread for some time because I installed bitpim from the repos on my T60 a while ago and it didn't detect my phone.  

However, I just installed the test release .deb and it found my vx-9800!  Wo0t - closer and closer to being rid of winblows forever!

---

### Post by wile_e8 on 2008-03-13
OK, I'm having some weird issues, and this seemed like the best place to ask.  I've been using BitPim on and off since like last August for installing ring tones on both my phone and my wife's phone.  It's worked well up through the last time I used it, about a month ago.  However, now my wife wants a new ring tone on her phone, but for some reason BitPim is failing to recognize her phone anymore (or mine for that matter, tried that out too).  When I run the settings and try to choose the com port, BitPim says "You do not have any com/serial ports on your system."  I've tried lsusb, the phone is not shown on there either.  Would there be some reason that BitPim would have stopped seeing my com ports in the last month?  I started out on version 1.02 from the repository, but got the same errors upon upgrading to 1.05 and 1.06.20080304.

---

### Post by Martym on 2008-04-16
After struggling for two days this post was the answer, I thank you.  All my data is now being imported into Bitpim and I am one step closer to removing my XP partition :)

---

### Post by Steve.G on 2008-05-05
Alright, following the instructions here I was able to connect my Voyager to my machine. Bitpim sees it fine and can manipulate it with ease. Great Thread!

---

### Post by osweetbeans on 2008-06-01
> **DiZASTiX said:**
> I followed OP's instructions, then JerMe's instructions on page 2 but bitpim still wasn't detecting my phone. Then, I ran it as root (sudo bitpim in a terminal) and it auto detected it! My phone is a LG enV (aka VX9900)

Thanks!

this solved my detection problems as well- same phone too.

i installed my phone using the built in synaptic packet manager... i didnt have to do any RPM converting.

  thnanks for this thread :)

---

### Post by Jokermage on 2008-08-18
I am trying to install the latest bitpim (I have a VX9100) using the .deb file available from SourceForge. When I use the command:

```
sudo dpkg -i --force-architecture bitpim*.deb
```

I get the following result:
```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 136762 files and directories currently installed.)
Preparing to replace bitpim 1.0.6 (using bitpim_1.0.6_i386.deb) ...
Unpacking replacement bitpim ...
Setting up bitpim (1.0.6) ...
cp: cannot stat `/usr/lib/BitPim-1.0.6/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bitpim
```

I tried some of the procedures mentioned earlier, but I always end up at the "60-bitpim.rules" error. Can anyone tell me what I am doing wrong?

Thanks for your time!

---

### Post by Jokermage on 2008-08-19
Okay, I went back and installed the 1.0.5 version and it worked fine on the first try. Could there be a file missing or corrupted in the 1.0.6 package?

Anyway, it looks like I still need 1.0.6 since the LG VX9100 doesn't seem to be supported by 1.0.5.

---

### Post by Jokermage on 2008-08-19
Final Update: I installed the 1.0.6 test release from 8/11/08 (instead of the official 1.0.6 release) and everything worked fine. If anyone is having trouble installing the 1.0.6 version, I recommend trying to install the test release instead.

---

### Post by johnc@crosslink.net on 2008-10-07
looks like where I'm at w/ 1.0.6 including the setup for env2 (teh phone 4 kids today, don't ya know).
I extracted /usr/lib/BitPim-1.0.6/resources/60-bitpim.rules file (sometimes these little hacks work) but no go. My line:
root@john-laptop:/usr/lib/BitPim-1.0.6/resources# dpkg --force-architecture -i bitpim_1.0.6_i386.deb
dpkg: error processing bitpim_1.0.6_i386.deb (--install):
 cannot access archive: No such file or directory

& now my voyager doesn't work ...

I think just 1.0.7 & see...

& yes, 1.0.7 (which is still in testing) works just fine & now can see my voyager again. next test is the env2 on my son's phone.

---

### Post by rickle on 2008-12-01
I also could not install 1.06, 1.05 installed, but doesn't do lg vx9100.
I tried to install the current 1.07 got a missing libdb4.4, used synaptic package manager to install libdb4.4, and now get the same error as follows.

 sudo dpkg -i --force-architecture bitpim*.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 129299 files and directories currently installed.)
Preparing to replace bitpim 1.0.7.20080908 (using bitpim_1.0.7.20080908_i386.deb) ...
Unpacking replacement bitpim ...
Setting up bitpim (1.0.7.20080908) ...
cp: cannot stat `/usr/lib/BitPim-1.0.7.20080908/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bitpim

---

### Post by rickle on 2008-12-01
I removed bitpim 1.0.5 and the bitpim helper library
and tried installing again and the install finished OK.
Haven't checked to see that it works yet, that will have to wait a bit.

---

### Post by rickle on 2008-12-02
Still not working! I have tried both the 1.0.7 & 1.0.6 installing and completely removing the 1.0.5 in between so the install looks like it works, (with the warning about forcing it from Intel to AMD64)
When I run it from terminal I get wrong ELF class for libgio stuff, and then 8 gtk_widget_size_allocate warnings.(see below)
Ignoring the warnings, when I plug the phone in bitpim shows ports as a modem interface and diagnostic interface both in use, and a modem (/dev/ttyACMO) available, the available port times out when I try to use it and bitpim shows an error because the in use ones are in use.

I installed the libgio-fam package from Synaptic package manager, but that doesn't seem to make any difference either.

rick@NobilisUbuntu:~/Desktop$ bitpim
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(bitpim:6972): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -5 and height 17

---

### Post by rickle on 2008-12-02
HMMM! It's working  (Ubuntu IBEX, AMD64, Bitpim 1.0.6)
 I Tried it again tonight, and this time the LG USB Diagnostic interface is available, and it looks like it is working, I up/down loaded phonebook and ringer information! Don't know what changed, maybe a reboot.
I'm still wondering about the ELF errors and GTK warnings in the Terminal window, they are still showing up.

---

### Post by rickle on 2008-12-05
It seems the ports both show up as in use, unless I run bitpim as super user! sudo bitpim.

---

### Post by Saghaulor on 2008-12-23
Could you please provide more specific instructions on how exactly you have managed to get the i386deb of bitpim to work on your amd64 architecture?

I also have the Voyager and would like to manage it within Hardy amd64.

I've never really messed around with cross architecture installs, so I'm a bit new to the whole process.

---

### Post by booyabazooka on 2009-02-10
I couldn't get 1.0.6 to install on my amd64 system, but the 1.0.7 test release does.

sudo dpkg --force-architecture -i bitpim_1.0.7.20081215_i386.deb

Also worth noting that I seem to have to change permissions on the usb device, which I do lazily by:

chown -R $USER /dev/bus/usb

---

### Post by antipuls3 on 2009-03-23
> **d351GuJu said:**
> For those who don't know what Bitpim is, check [here]("http://www.bitpim.org/")!

All right let's get started installing Bitpim for now.

-------------------------------------------------------

We will need to convert a RPM package to DEB package, so do this.
**sudo apt-get install alien**

Now download BitPim from the original website, yes the RPM version.
And convert the RPM to DEB, by entering the following:
**sudo alien -d bitpim*.rpm**

It will take a few seconds, to convert and it will notify when it finishes.

Now let's install it:
**sudo dpkg -i bitpim*.deb**

Once installed run it by entering bitpim on the console.

**ERRORS:**

libstdc++.so.5  -> if you receive this kind of error, do the following:
sudo apt-get install libstdc++5

libtiff.so.3 -> if you receive this kind of error, do the following:
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3

-------------------------------------------------------------------

[SIZE="3"]_**Devices that works so far:**_[/SIZE]
```
[LIST]
[*]None as of yet
[/LIST]
```

Can't convert the rpm package for some reason... This is what I got
--------------------------------------------------------------------
Warning: Skipping conversion of scripts in package bitpim: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
Unpacking of 'bitpim-1.0.6-0.i386.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 155.


Where should I go from here? Why can't I just use the DEB package?

---

### Post by Bakon Jarser on 2009-04-09
Because you are trying to follow instructions from 2006 before bitpim had a .deb package.  bitpim is now in the (jaunty) repositories.

---

### Post by djuniah on 2009-04-10
After upgrading to jaunty, bitpim can no longer access my phone via the USB cable.  When i look at the phone connection screen i see this error:

```

active   True   Your operating system shows this driver and port is correctly configured and a device attached 
available   False   It was not possible to open this port 

```

I have tried all the listed chown tricks, and even tried running it as root, but nothing seems to work.  I dug into some of the configuration files for udev (don't worry, i didnt edit anything) and everything there seemed ok.

Anyone have any suggestions?
(yes, it did work just fine in hardy/intrepid)

---

### Post by sanelson on 2009-04-12
> **djuniah said:**
> After upgrading to jaunty, bitpim can no longer access my phone via the USB cable.  When i look at the phone connection screen i see this error:

```

active   True   Your operating system shows this driver and port is correctly configured and a device attached 
available   False   It was not possible to open this port 

```

I have tried all the listed chown tricks, and even tried running it as root, but nothing seems to work.  I dug into some of the configuration files for udev (don't worry, i didnt edit anything) and everything there seemed ok.

Anyone have any suggestions?
(yes, it did work just fine in hardy/intrepid)
I'm having the same problem here.  Running Jaunty x86_64 beta.

---

### Post by sanelson on 2009-04-12
> **sanelson said:**
> I'm having the same problem here.  Running Jaunty x86_64 beta.

I noticed that network manager is now giving me the option to use this phone as a modem, which I don't think it was doing before.  Could this be an issue with network manager not releasing the port?  It still seems to happen if I disable networking, but I imagine it could still be holding the port open.

---

### Post by bedhead75 on 2009-04-25
> **sanelson said:**
> I'm having the same problem here.  Running Jaunty x86_64 beta.


    I can confirm I'm having the same problem in 64-bit Jaunty (fresh install, not an upgrade), with the Bitpim offered in the repositories.  Even when run as root, in Bitpim, the port is not listed as available, even though it is listed as active.
    It worked fine in Hardy/Intrepid.  I also notice that when I plug in the cell phone for the first time, it's listed in the "lsusb" output, but if I unplug the phone and plug it back in, it no longer lists and I have to reboot in order to see it again.  Could this be regression with the cell phone driver in Jaunty rather than a problem in Bitpim?

---

### Post by ugmoe2000 on 2009-04-28
I can confirm this issue as well ...  will not let me use the Voyager; I've tried every trick I can think of /w no success.

I'm a 8.10 -> 9.04 upgrade. This is yet another reason why I always recommend people do a fresh install-- there are always problems but I'll surely keep trying with every new release until one day it actually works. Upgrading from Hardy to Intrepid left me without a graphical display (lost my video drivers), upgrading from Intrepid to Jaunty only left me with an obscure cell phone problem... not too shabby, there's improvement every time. I'm sure it'll just work /w Koala!

---

### Post by ugmoe2000 on 2009-04-29
So I just got done doing a fresh image of 9.04 on my machine only to find that the problem still persists. I ended up using a custom live cd from my old 8.10 system. Everything worked like a charm on that one... which leads me to believe it's not the phone's firmware... but Jaunty that's causing the problem... wonder what it is.

---

### Post by djuniah on 2009-04-30
I'm fairly positive that it is related to udev's permission settings for the device.  

NOTE: I did try to do it over a BT COM connection the other day, and i had the same exact issue.  I do BT development in linux, so i know that my adapter is fine and compatible. I'm beginning to think this issue is related to bitpim's interaction with udev, not with udev's interaction with the devices themselves.

---

### Post by Polygon on 2009-05-02
hmm, yeah bitpim is not working here either. I had a script to automatically set the udev permissions, and it shows up in lsusb:

Bus 003 Device 003: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone


and network manager also sees it and is able to create a cdma connection, but bitpim says the port is busy?

---

### Post by wizard10000 on 2009-05-03
I purged the 1.0.6 installation from Jaunty and installed v1.05 from Soureforge and my phone connected first time on /dev/ttyACM0 - wouldn't connect at all with the version of bitpim that comes with Jaunty.

Link to sourceforge archive:

[http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636](http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636)

---

### Post by bedhead75 on 2009-05-06
Does anyone know where you can find a deb for Bitpim v1.0.5 for Jaunty 64-bit?  Installing the i386 version using the sudo dpkg --force-architecture -i command, after satisfying the dependencies didn't work.  Running bitpim in the terminal gave errors about files in non-existant folders.

---

### Post by alexjohnc3 on 2009-05-20
> **wizard10000 said:**
> I purged the 1.0.6 installation from Jaunty and installed v1.05 from Soureforge and my phone connected first time on /dev/ttyACM0 - wouldn't connect at all with the version of bitpim that comes with Jaunty.

Link to sourceforge archive:

[http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636](http://sourceforge.net/project/showfiles.php?group_id=75211&package_id=75636)
This didn't work for me. The only reason I can think of is because I didn't fully purge 1.0.6? I uninstalled it, that's enough, right?
Is there anyway to connect to the phone on /dev/ttyACM0 (Filesystem on BitPim didn't work either)?

---

### Post by danatup on 2009-05-28
I had success by removing the ubuntu-provided package and downloading/installing the 1.06 deb package (both 1.05 and 1.06 worked for me)

Prior to this I had also followed the steps here:
[https://bugs.launchpad.net/ubuntu/jaunty/+source/udev/+bug/374782]("https://bugs.launchpad.net/ubuntu/jaunty/+source/udev/+bug/374782")
to give permissions to my user for "dialout"

---

### Post by jawamboldt on 2009-06-22
Hi, sorry to resurrect an old thread, but it's the exact issue I'm having. I'm running Jaunty and trying to connect to a Voyager. It shows up when I run lsusb however BitPim won't detect it. I've gone through this whole thread and followed all instructions with no luck. Just to rule out any sort of permission issue, I tried it as root also with no difference. I'm not getting any error message to point me in the right direction either, it's simply not being detected. Any help would be much appreciated. 

I'm going to hold off another day or two, but I'd hate to have to reboot into Windows to get some pictures off of my phone.

Thanks in advance,
Justin

---

### Post by mjbauer95 on 2009-07-26
> **jawamboldt said:**
> Hi, sorry to resurrect an old thread, but it's the exact issue I'm having. I'm running Jaunty and trying to connect to a Voyager. It shows up when I run lsusb however BitPim won't detect it. I've gone through this whole thread and followed all instructions with no luck. Just to rule out any sort of permission issue, I tried it as root also with no difference. I'm not getting any error message to point me in the right direction either, it's simply not being detected. Any help would be much appreciated. 

I'm going to hold off another day or two, but I'd hate to have to reboot into Windows to get some pictures off of my phone.

Thanks in advance,
Justin

Yeah I've got this problem too, does anyone have any answers?

---

### Post by cross157 on 2009-08-09
I want to add my experience with Bitpim in Ubuntu Jaunty because I struggled getting it working like many people on this thread. I ended up learning a lot about udev and hotplugging and udev rules files so overall I'm happy for the journey, but frustrated by the way I got it to work.

To make a long story short after weeks of trying and re-trying things I noticed that the bpudev file from the source code was written a bit differently than what was installed on my computer from the repositories through Synaptic.

So, I removed all traces of Bitpim downloaded the deb file from here: [http://www.bitpim.org/#download](http://www.bitpim.org/#download)

Installed it, ignoring the warning about a later verison from the software channels and Bitpim worked like a charm. It auto detected my LG voyageur phone right way without sudo access. In the end I don't actually know what the problem is but I have it working now and that's all I really care about.

**FYI**: Update manager will attempt to update Bitpim with the repositories version, if you do that **it will go back to not working**. I hope this helps someone.

---

### Post by merlin666 on 2009-09-09
Good thread. I am having the same persisting problem with jaunty (64-bit) and bitpim 1.0.6. connecting to LG Dare.

I have tried  

sudo chown -R $USER /dev/bus/usb 

and starting bitpim as root and nothing helps. I can access the mass storage and the phone is detected as 

Bus 003 Device 004: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone

But this is not in BitPim. Hope there will be a solution soon.

---

### Post by XanTrax on 2009-10-14
I'm under the impression that BitPim on Linux/Ubuntu does not work with the newest Voyagers Firmware of VX10KV11.  The manual says it was built and tested with VX10KV03 and I remember that when the firmware upgraded for the Voyager that it took them a little while to upgrade bitpim for Windows to work with the newest.

Could anyone confirm or deny that the Voyager with firmware VX10KV11 on Ubuntu works and if so, that did they do to get it to work?  My phone isnt auto detected and trying to select the port to read through manual detection doesnt seem to yield anything but a traceback.

EDIT:  

Heres the traceback.  I'm gonna toy around with some stuff to see if I can get it work since the traceback reports that the device is busy (when its not).

```

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 284, in run
    res=call()
  File "/usr/share/bitpim/code/gui.py", line 159, in __call__
    return apply(self.method, self.args+args, d)
  File "/usr/share/bitpim/code/gui.py", line 1883, in getdata
    self.setupcomm()
  File "/usr/share/bitpim/code/gui.py", line 1866, in setupcomm
    configparameters=comcfg)
  File "/usr/share/bitpim/code/commport.py", line 68, in __init__
    self._openport(self.port, *self.params)
  File "/usr/share/bitpim/code/commport.py", line 97, in _openport
    self.ser=self._openusb(port, timeout)
  File "/usr/share/bitpim/code/commport.py", line 129, in _openusb
    return _usbdevicewrapper(iface.openbulk(), timeout)
  File "/usr/lib/bitpim/native/usb/usb.py", line 172, in openbulk
    raise USBException()
**_USBException: could not claim interface 2: Device or resource busy_**

```

EDIT 2:

Also, this appears in the log as soon as I start the program

```
16:58:24.840 Failed to open dir /var/run/bitpim
```

I know stuff in /var/run is supposed to be created by the applications for runtime information so I dont want to just touch it or create some arbitrary file.

---

### Post by cross157 on 2009-10-14
> **XanTrax said:**
> I'm under the impression that BitPim on Linux/Ubuntu does not work with the newest Voyagers Firmware of VX10KV11.  The manual says it was built and tested with VX10KV03 and I remember that when the firmware upgraded for the Voyager that it took them a little while to upgrade bitpim for Windows to work with the newest.

Could anyone confirm or deny that the Voyager with firmware VX10KV11 on Ubuntu works and if so, that did they do to get it to work?  My phone isnt auto detected and trying to select the port to read through manual detection doesnt seem to yield anything but a traceback.


I can verify that BitPim works automagically with firmware VX10KV11, that's what I have on my Voyager. But the version of BitPim in the Ubuntu repositories does **NOT** work. I only had success when I downloaded the deb directly from bitpim.org. Good luck

P.S. Lock the version or update will try to replace it once you've installed.

---

### Post by XanTrax on 2009-10-14
> **cross157 said:**
> I can verify that BitPim works automagically with firmware VX10KV11, that's what I have on my Voyager. But the version of BitPim in the Ubuntu repositories does **NOT** work. I only had success when I downloaded the deb directly from bitpim.org. Good luck

P.S. Lock the version or update will try to replace it once you've installed.

I tried both.  When I tried the one from the BitPim website, it did the exact same thing as the one from the repositories.  The only thing I can think of is that I did not run the one from the bitpim website as sudo or with su.  

The picture/attachment below is what it says for my phone.  This is from the one from the repositories.  I'll reinstall the one from the bitpim website and see what it says.

Please note where it says 

```

Available              False          It was not possible to open this port

```

As well as how it states that libusb is in use and that it is active.  Again, I'll try the one from the bitpim website but I am 98% sure it said the exact same information.

---

### Post by cross157 on 2009-10-14
> **XanTrax said:**
> I tried both.  When I tried the one from the BitPim website, it did the exact same thing as the one from the repositories.  The only thing I can think of is that I did not run the one from the bitpim website as sudo or with su.  

The picture/attachment below is what it says for my phone.  This is from the one from the repositories.  I'll reinstall the one from the bitpim website and see what it says.

Please note where it says 

```

Available              False          It was not possible to open this port

```

As well as how it states that libusb is in use and that it is active.  Again, I'll try the one from the bitpim website but I am 98% sure it said the exact same information.


Sorry, I'm not sure what the issue is then. Once I installed the deb from bitpim.org it worked without sudo.

---

### Post by XanTrax on 2009-10-14
> **cross157 said:**
> Sorry, I'm not sure what the issue is then. Once I installed the deb from bitpim.org it worked without sudo.

Weird.  Didn't work for me.  I'll try it again and maybe toy with that one a bit more.

---

### Post by Logan 1229 on 2009-10-17
> **cross157 said:**
> I want to add my experience with Bitpim in Ubuntu Jaunty because I struggled getting it working like many people on this thread. I ended up learning a lot about udev and hotplugging and udev rules files so overall I'm happy for the journey, but frustrated by the way I got it to work.

To make a long story short after weeks of trying and re-trying things I noticed that the bpudev file from the source code was written a bit differently than what was installed on my computer from the repositories through Synaptic.

So, I removed all traces of Bitpim downloaded the deb file from here: [http://www.bitpim.org/#download](http://www.bitpim.org/#download)

Installed it, ignoring the warning about a later verison from the software channels and Bitpim worked like a charm. It auto detected my LG voyageur phone right way without sudo access. In the end I don't actually know what the problem is but I have it working now and that's all I really care about.

**FYI**: Update manager will attempt to update Bitpim with the repositories version, if you do that **it will go back to not working**. I hope this helps someone.


Cross157 is correct.  I just spent better part of 2 days troubleshooting Jaunty to get my LG Voyager working. Do not install Bitpim via synaptic (doesn't detect phone because of - for me - port issues/permissions, which I couldn't resolve using any of previous posts here or guides from Bitpim site).  However followed his advise  got somewhere finally!

Wasn't able to detect phone properly but was able to detect "other CDMA phone..." Bitpim lists voyager as VX10000 but my lsusb lists it as:  "Bus 004 Device 011: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone"

1)  Downloaded & installed Bitpim using Linux DEB file from [http://bitpim.org/#download](http://bitpim.org/#download)
2)  Start Bitpim as sudo
3)  Plug in phone.  (Auto-detects as "other CDMA...") but may need to "Detect phone" at this point
4)  In Bitpim settings, choose phone type "LG-VX10000 (Voyager)" *** DO NOT RE-DETECT PHONE ***
5)  In Bitpim, highlight "filesystem" then choose "Get phone data"
6)  In filesystem, go to /root/brew/shared/ringtone
7)  Can now go into right box screen (mine was empty) & right click mouse to add ringtones via "New File".  Add as many as you want then right click again to choose "Reboot Phone".
8)  Give phone time to restart, then disconnect, & you have your new ringtones!
   * Lastly, note, a couple of times the filesystem didn't pull up, but if I re-detected phone & continued from step 4, it would work.

Otherwise , specific to Voyager - for Canada , if you're just desperate to get new ringtones & don't care how, follow the simple steps for using "Rumkin" (instructions about 1/2 way down page) via: 
  [http://www.voyager-lg.com/canadian-voyager-guidestutorials/how-to-install-drivers-and-transfer-files-(canadian-version)/](http://www.voyager-lg.com/canadian-voyager-guidestutorials/how-to-install-drivers-and-transfer-files-(canadian-version)/)
Tested & works, no charge.  Note this link is to another forum with tons of info on Voyagers for everyone/where. 

Hope this helps someone other than me.  Thanks to all previous posters as well!  Cheers!

---

### Post by XanTrax on 2009-10-18
Oh sweet, it worked.  I guess I probably didnt remove my .bitpim directory (or some other files) when I installed the one from the bitpim website.

Thanks guys!

---

### Post by mactheburger@gmail.com on 2009-10-18
Holy cow. Start Bitpim with sudo... not being able to access my LG keybo with bitpim was the only thing keeping me from using kubuntu full time... good bye M$. yes i'm a linux noob.. but the ubuntu community is awesome and helps me since i have no idea what to do.

---

### Post by e.m.fields on 2009-11-03
> **Logan 1229 said:**
> Cross157 is correct.  I just spent better part of 2 days troubleshooting Jaunty to get my LG Voyager working. Do not install Bitpim via synaptic (doesn't detect phone because of - for me - port issues/permissions, which I couldn't resolve using any of previous posts here or guides from Bitpim site).  However followed his advise  got somewhere finally!

Wasn't able to detect phone properly but was able to detect "other CDMA phone..." Bitpim lists voyager as VX10000 but my lsusb lists it as:  "Bus 004 Device 011: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone"

1)  Downloaded & installed Bitpim using Linux DEB file from [http://bitpim.org/#download](http://bitpim.org/#download)

...

Augh.  Any luck for users running Ubuntu x64? Looks like I'm S.O.L. as the DEB file is i386.

Doh!

---

### Post by ironmark on 2009-11-07
Hey everyone! I tried to do this on my laptop so that i could run bitpim with my ENV touch. I know that the 1.06 version will not work with the ENV touch, so I tried to install the 1.07 beta. however this is the message that I am getting after installing and using the both 'sudo bitpim' and 'bitpim'

Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.3/initscripts/ConsoleSetLibPath.py", line 35, in <module>
  File "src/bp.py", line 20, in <module>
  File "src/bp_cli.py", line 21, in <module>
  File "src/bp_config.py", line 19, in <module>
  File "src/guihelper.py", line 23, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
  File "ExtensionLoader_wx__core_.py", line 12, in <module>
ImportError: libexpat.so.0: cannot open shared object file: No such file or directory

I have tried to get the libexpat.so.0 library but it states that my libraries are upto date. Any ideas how to fix this. btw the 1.06 version runs fine, except I cannot access my phone. 1.06 states that the usb port is inaccessible, but does see my phone connected.

---

### Post by oldgeekster on 2009-11-08
Hi Folks,

Running Karmic on my older Toshiba notebook and just purchased a LG enV3 from Verizon.  Installed the older version of bitpim via the Ubuntu Software Center yesterday then (after reading this thread) opened a terminal and did a "sudo bitpim" - sure enough it was able to detect my phone on the "Other" setting after running it as root. (Won't work, but at least it talked to my enV3). I will overcome having to do that "sudo thang" later on, but there is another solution.

What I would like to do now is upgrade to the latest test version 1.0.7* of bitpim from bitpim.org which reportedly *does* cover the enV3 cell phone along with a ton of the newer phones out there.  Unfortunately, there isn't a .deb package available there, nor anyplace else I looked.  Tried/failed converting/installing their RPM version using alien multiple times.

Anybody know where I might find a bitpim-1.0.7.20090805.deb version of that package?  Other suggestions?

TIA!
-=dave=-

---

### Post by Njall on 2010-02-15
Having just gotten the LG env Touch I installed [**[COLOR="Blue"]BitPim v1.0.7[/COLOR]** ]("http://www.bitpim.org/") on Kubuntu Karmic (9.10).  Here's what I did to finally get BitPim to start.  YMMV.

1. Download the BitPim v1.0.7 RPM file [**[COLOR="Blue"]bitpim-1.0.7-0.i386.rpm[/COLOR]**]("http://prdownloads.sourceforge.net/bitpim/bitpim-1.0.7-0.i386.rpm?download").  While you're at it donate $5 to the BitPim project to say thanks!

2. In a terminal session:

```
[INDENT]sudo apt-get install alien
sudo alien -d bitpim*.rpm
sudo dpkg -i bitpim*.deb
cd /usr/lib
sudo ln -s libtiff.so.4.2.1 libtiff.so.3
cd /lib
sudo ln -s libexpat.so.1.5.2 libexpat.so.0
bitpim[/INDENT]
```

3. You can add the BitPim link and icon to your KDE menu.  However, KDE doesn't work with Windows ICO format.  So I went to [[COLOR="Blue"]**http://converticon.com/**[/COLOR]]("http://converticon.com/") and converted a copy of /usr/lib/BitPim-1.0.7/resources/bitpim.ico to a PNG which I then copied back to the BitPim resources directory.

The path for the bitpim program is: /usr/bin/bitpim

Have fun!

Nelson

---

### Post by mohaned_nj on 2010-02-20
thank's
i convert it to deb

---

### Post by kittybrat on 2010-03-05
> **Njall said:**
> Having just gotten the LG env Touch I installed [**[COLOR="Blue"]BitPim v1.0.7[/COLOR]** ]("http://www.bitpim.org/") on Kubuntu Karmic (9.10).  Here's what I did to finally get BitPim to start.  YMMV.

1. Download the BitPim v1.0.7 RPM file [**[COLOR="Blue"]bitpim-1.0.7-0.i386.rpm[/COLOR]**]("http://prdownloads.sourceforge.net/bitpim/bitpim-1.0.7-0.i386.rpm?download").  While you're at it donate $5 to the BitPim project to say thanks!

2. In a terminal session:

```
[INDENT]sudo apt-get install alien
sudo alien -d bitpim*.rpm
sudo dpkg -i bitpim*.deb
cd /usr/lib
sudo ln -s libtiff.so.4.2.1 libtiff.so.3
cd /lib
sudo ln -s libexpat.so.1.5.2 libexpat.so.0
bitpim[/INDENT]
```

3. You can add the BitPim link and icon to your KDE menu.  However, KDE doesn't work with Windows ICO format.  So I went to [[COLOR="Blue"]**http://converticon.com/**[/COLOR]]("http://converticon.com/") and converted a copy of /usr/lib/BitPim-1.0.7/resources/bitpim.ico to a PNG which I then copied back to the BitPim resources directory.

The path for the bitpim program is: /usr/bin/bitpim

Have fun!

Nelson

This didn't work for me. :(
I'm on Karmic, if that makes a difference.

---

### Post by ShadowGazer on 2010-03-19
Followed all directions in post, didn't work, when trying to run bitpim, I get this error:

```
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.3/initscripts/ConsoleSetLibPath.py", line 35, in <module>
  File "src/bp.py", line 20, in <module>
  File "src/bp_cli.py", line 21, in <module>
  File "src/bp_config.py", line 19, in <module>
  File "src/guihelper.py", line 23, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
  File "ExtensionLoader_wx__core_.py", line 12, in <module>
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
```

I am using version 10.04 (beta 2 I think)

---

### Post by thelunchboxosu on 2010-04-07
When I convert the rpm with alien I get this message in the terminal:

```
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/bitpim
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: error: couldn't find library libpython2.5.so.1.0 needed by debian/bitpim/usr/lib/BitPim-1.0.7/pyexpat.so (ELF format: 'elf32-i386'; RPATH: '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: dpkg-shlibdeps returned exit code 2
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `bitpim-1.0.7': No such file or directory

```

Any ideas? I'm new to Linux so I have no idea what any of this means.

---

### Post by bpettis on 2010-06-23
Okay, I followed OP instructions, and then JerMe's instructions on page 2. When I run "bitpim" or even "sudo bitpim" I receive this error:


Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.3/initscripts/ConsoleSetLibPath.py", line 35, in <module>
  File "src/bp.py", line 20, in <module>
  File "src/bp_cli.py", line 21, in <module>
  File "src/bp_config.py", line 19, in <module>
  File "src/guihelper.py", line 23, in <module>
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/__init__.py", line 45, in <module>
    from wx._core import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
  File "ExtensionLoader_wx__core_.py", line 12, in <module>
ImportError: libexpat.so.0: cannot open shared object file: No such file or directory


In case it helps, heres the results of lsusb:


Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e8:6640 Samsung Electronics Co., Ltd Usb Modem Enumerator
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by bpettis on 2010-06-23
Good News!

I was able to solve the problem and get bitpim to launch by downloading "compat-expat" as a rpm (from [here]("http://www.rpmfind.net/linux/rpm2html/search.php?query=compat-expat1")), use alien to convert to a .deb, and installed it.

Then, when I ran "bitpim" again, the program ran without a hitch!

---

### Post by dougs510 on 2010-10-28
I also had problems with "libexpat.so".  I just replicated the softlink and now all is well.

---

### Post by Punkristo on 2010-11-02
This is the error I'm getting:

> pag@pag-laptop:~/Desktop/bitpim$ sudo alien -d bitpim-1.0.7-0.i386.rpm
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package bitpim: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `bitpim-1.0.7': File exists
unable to mkdir bitpim-1.0.7:  at /usr/share/perl5/Alien/Package.pm line 257.

---

### Post by hellop on 2011-02-01
Njall's instructions worked.  Thanks dude!   You guys need to follow these steps he posted:

```

sudo apt-get install alien
sudo alien -d bitpim*.rpm
sudo dpkg -i bitpim*.deb
cd /usr/lib
sudo ln -s libtiff.so.4.2.1 libtiff.so.3
cd /lib
sudo ln -s libexpat.so.1.5.2 libexpat.so.0
bitpim

```When you get this error:
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory

It means you do not have that file.  If you're running ubuntu 10.04, you probably have version 4.2.1 of libtiff, instead of version 3.  So, if bitpim wants version 3, you can trick it by creating a symlink called libtiff.so.3 that points to your version, libtiff.so.4.2.1...  OR whatever version you do have. So, follow the above steps to create the symlink.

What also might help if you're getting python, or script errors when converting the rpm, is to install the previous version of bitpim (1.06) from the repositories, so that it will install all the dependencies.  Then just remove bitpim, leaving the dependencies.   Like this:

```

aptitude install bitpim
apt-cache remove bitpim

```Then follow Njall's instructions to install the latest version of bitpim.

@Punkristo:  it can't create the directory because it exists.  so remove it: rm -f bitpim-1.0.7

p.s.  I had to run bitpim as root in kde in order to get it to detect my port and phone, from terminal like this: gksu bitpim

Samsung Convoy S/W V u640.DJ28 working with bitpim in Linux Kubuntu 10.04.

---

### Post by letank on 2011-06-09
Reviving an old thread.

Still using Ubuntu 9.10, on a samsung N210, LG VX9700 -Dare- version 05

bitpim 1.0.7 did not work, Uninstalled, Downloaded 1.0.6 via synaptic, did not work... updated the lib from the first few posts, still no detection of the phone but could connect to the correct usb port.

sudo bitpim was the key, and increased time out to 4.0, at the default it stopped the download, not sure if it was relevant or not.

cheers

---

### Post by tgrantt on 2011-07-12
> **Njall said:**
> Having just gotten the LG env Touch I installed [**[COLOR="Blue"]BitPim v1.0.7[/COLOR]** ]("http://www.bitpim.org/") on Kubuntu Karmic (9.10).  Here's what I did to finally get BitPim to start.  YMMV.


2. In a terminal session:

```
[INDENT]
sudo ln -s libexpat.so.1.5.2 libexpat.so.0
bitpim[/INDENT]
```



This is what I needed! Thanks!

---

### Post by cams-scripts on 2011-07-12
[COLOR=#000000][FONT=Times New Roman][FONT=arial]It helped me Thanks![/FONT][/FONT][/COLOR]

---

