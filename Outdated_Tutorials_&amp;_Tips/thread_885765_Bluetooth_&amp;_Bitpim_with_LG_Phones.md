---
title: "Bluetooth &amp; Bitpim with LG Phones"
date: 2008-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by quazi on 2008-08-10
For those of you who don't know, Bitpim is a great tool for transferring files back and forth between phones and your PC (ie. backing up contacts and making your own mp3 ringtones).  This tutorial will be given for a LG VX-8300 specifically, but it should work with later (maybe some earlier) models.

First, get bitpim from the repositories and make sure that bluetooth utilities are installed:
```
sudo apt-get install bitpim bluez-utils
```

Start bluetooth with the command:
```
sudo /etc/init.d/bluetooth start 
```

In your phone, go under the Main Menu -> Settings & Tools -> Bluetooth.  Then, highlight Add New Device and under settings select "discovery mode" (the location and name of this option may vary from model to model.  What this option does is enable your phone to be seen by your system for a few minutes.)

Then find out your phone's mac address and connect with the commands:
```
$ hcitool scan
$ sudo hcitool cc ##:##:##:##:##:##
$ sudo hcitool auth ##:##:##:##:##:##
```, where ##:##:##:##:##:## is the mac address of the phone.

This last line may or may not be necessary.  When I entered it, I got the output "Not connected."  However, I'd already previously connected my phone with the laptop through gnome-bluetooth in a previous failed attempt to get bluetooth working and had already authorized my phone for connection, so I ignored the message.

Now we need to find out what channel to connect rfcomm to, so enter ```
sdptool browse ##:##:##:##:##:##
```  
and find the section with "Service Name: BT DIAG."  Look under "Protocal Descriptor List" and find the Channel number:

```
Service Name: BT DIAG
Service RecHandle: 0x10005
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 16
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Serial Port" (0x1101)
```
Here it's 16.

Now run ```
rfcomm connect 0 ##:##:##:##:##:## ??
```
where ?? is the channel number.

At this point the phone should be connected via bluetooth with ubuntu and we can run bitpim.  Start it up with ```
bitpim
```

Click on settings (icon with wrench on screwdriver) and under Com Port select /dev/rfcomm0.  If you know your phone type select it under Phone Type.  Hit OK and click on the icon with the magnifying glass over the phone to detect your phone.  After doing this I get an error message ```
No phone detected/recognized.  
Run Settings?
```

After doing this your phone should be connected (regardless of what Bitpim tells you).  Try getting your phonebook data from your phone to verify that the connection works.

These directions were adopted from instructions for an LG VX-9800: [http://www.quietearth.us/vx9800.htm](http://www.quietearth.us/vx9800.htm)

---

### Post by lightenup on 2008-08-17
Sweet worked like a champ! Also I would like to add that folks might want to go to the BitPim web site and get the latest version as it adds support for newer phones:

[http://www.bitpim.org/#download](http://www.bitpim.org/#download)

You can just download the deb and install it and then run `bitpim` from a console window (ie. lightenup@neutron:~$ bitpim )

---

### Post by HyperHacker on 2009-05-23
I've been trying to get this to work and it just doesn't want to cooperate. When I run "sdptool browse" there is no BT DIAG section. Bitpim shows "This port is active but not available for use" and "It was not possible to open this port."

---

### Post by asuastrophysics on 2009-05-26
i followed the entire guide and it doesnt work. BT DIAG is not in the console.

this is ridiculous. yet another complete waste of my time. in windows, it works immediately without any flaws. in ubuntu, it doesnt work period. what a stupid OS.

im going back to windows. what a waste of half an hour for NOTHING. 

there is absolutely no hardware support in linux. period. somebody needs to axe this entire project and do us all a favor.

---

### Post by quazi on 2009-05-27
I tried these instructions in Jaunty and they still work for me (although I need to use an older version of Bitpim than the one in the repos).

My linux machine is broken currently (literally, the video card is fried), so I can't really be of any help.  Make sure you follow all instructions correctly and make sure you have the right Mac address.  Also what make are your phones?

---

### Post by agenthex on 2009-10-26
I tried this method, and everything worked including the rfcomm command, but when I tried BitPim, it failed to detect my phone.  I was finally able to get it working by using the -r (for RAW mode) command with rfcomm.

I had created a blank rfcomm file in /etc/bluetooth/ and edited the rfcomm.conf file to add an entry for my phone.

rfcomm -r connect 4

This established a raw mode connection to my phone and allowed BitPim to finally see it.  Thanks to quazi for the first post and the rfcomm man pages for the -r switch.

---

### Post by maxcomx on 2009-11-02
i followed step by step, everything went well until.. i cant get the phonebook or anything else from the phone, 

here is the error Bitpim gived me.

> BitPim version: 1.0.6-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 284, in run
    res=call()
  File "/usr/share/bitpim/code/gui.py", line 159, in __call__
    return apply(self.method, self.args+args, d)
  File "/usr/share/bitpim/code/gui.py", line 1884, in getdata
    results=self.getfundamentals()
  File "/usr/share/bitpim/code/gui.py", line 1878, in getfundamentals
    self.commphone.getfundamentals(results)
  File "/usr/share/bitpim/code/phones/com_lgvx4400.py", line 96, in getfundamentals
    results['uniqueserial']=sha.new(self.get_esn()).hexdigest()
  File "/usr/share/bitpim/code/phones/com_lgvx8300.py", line 85, in get_esn
    return self.get_brew_esn()
  File "/usr/share/bitpim/code/phones/com_brew.py", line 335, in get_brew_esn
    p_brew.ESN_resp).esn
  File "/usr/share/bitpim/code/phones/com_lg.py", line 1711, in _sendbrewcommand
    return func(*args, **kwargs)
  File "/usr/share/bitpim/code/phones/com_brew.py", line 755, in sendbrewcommand
    self.setmode(self.MODEBREW)
  File "/usr/share/bitpim/code/phones/com_phone.py", line 114, in setmode
    res=getattr(self, func)()
  File "/usr/share/bitpim/code/phones/com_brew.py", line 693, in _setmodebrew
    self.sendbrewcommand(req, respc, callsetmode=False)
  File "/usr/share/bitpim/code/phones/com_lg.py", line 1711, in _sendbrewcommand
    return func(*args, **kwargs)
  File "/usr/share/bitpim/code/phones/com_brew.py", line 757, in sendbrewcommand
    request.writetobuffer(buffer, logtitle="sendbrewcommand")
  File "/usr/share/bitpim/code/phones/p_brew.py", line 2536, in writetobuffer
    self.__field_header=requestheader(**{'command': 0x0c})
  File "/usr/share/bitpim/code/phones/p_brew.py", line 42, in __init__
    super(requestheader,self).__init__(**dict)
TypeError: object.__init__() takes no parameters

Variables by last 8 frames, innermost last

Frame _sendbrewcommand in /usr/share/bitpim/code/phones/com_lg.py at line 1714
           self =  <phones.com_lgvx8700.Phone object at 0xc071f6c>
           args =  (<phones.p_brew.ESN_req object at 0xc071d2c>, <class 'phones.p_brew.ESN_resp'>)
           func =  <bound method Phone.sendbrewcommand of <phones.com_lgvx8700.Phone object at 0xc0
         kwargs =  Keys []
                   {}

Frame sendbrewcommand in /usr/share/bitpim/code/phones/com_brew.py at line 755
    callsetmode =  True
        request =  <phones.p_brew.ESN_req object at 0xc071d2c>
           self =  <phones.com_lgvx8700.Phone object at 0xc071f6c>
  responseclass =  <class 'phones.p_brew.ESN_resp'>

Frame setmode in /usr/share/bitpim/code/phones/com_phone.py at line 116
    desiredmode =  'modebrew'
           self =  <phones.com_lgvx8700.Phone object at 0xc071f6c>
        strmode =  'none'
 strdesiredmode =  'brew'
           func =  '_setmodebrew'
              v =  'writeobject'

Frame _setmodebrew in /usr/share/bitpim/code/phones/com_brew.py at line 696
           self =  <phones.com_lgvx8700.Phone object at 0xc071f6c>
            req =  <phones.p_brew.memoryconfigrequest object at 0xc0719ac>
          respc =  <class 'phones.p_brew.memoryconfigresponse'>

Frame _sendbrewcommand in /usr/share/bitpim/code/phones/com_lg.py at line 1714
           self =  <phones.com_lgvx8700.Phone object at 0xc071f6c>
           args =  (<phones.p_brew.memoryconfigrequest object at 0xc0719ac>, <class 'phones.p_brew.
           func =  <bound method Phone.sendbrewcommand of <phones.com_lgvx8700.Phone object at 0xc0
         kwargs =  Keys ['callsetmode']
                   {'callsetmode': False}

Frame sendbrewcommand in /usr/share/bitpim/code/phones/com_brew.py at line 757
         buffer =  <prototypes.buffer object at 0xc07192c>
    callsetmode =  False
        request =  <phones.p_brew.memoryconfigrequest object at 0xc0719ac>
           self =  <phones.com_lgvx8700.Phone object at 0xc071f6c>
  responseclass =  <class 'phones.p_brew.memoryconfigresponse'>

Frame writetobuffer in /usr/share/bitpim/code/phones/p_brew.py at line 2536
            buf =  <prototypes.buffer object at 0xc07192c>
        autolog =  True
       logtitle =  'sendbrewcommand'
           self =  <phones.p_brew.memoryconfigrequest object at 0xc0719ac>

Frame __init__ in /usr/share/bitpim/code/phones/p_brew.py at line 42
           self =  <phones.p_brew.requestheader object at 0xc0718ac>
           args =  ()
           dict =  Keys ['command']
                   {'command': 12}
         kwargs =  Keys ['command']
                   {'command': 12}


I use Ubuntu Jaunty and a Cell phone LG10000 voyager from Telus in canada.

thanx for help.

---

### Post by greyfox1 on 2009-11-05
Hi maxcomx,

Does your BT port show as available in Bitpim? Mine does not (it is listed under "Ports not available") and I get the same problem as you. This is in spite of the ability I have to transfer pictures back and forth between my laptop and the phone via BT using Nautilus. Strange.

Anyone have suggestions?

---

### Post by greyfox1 on 2009-11-09
I figured out how to gracefully resolve the errors some of us are running into in newer versions of Ubuntu and will be posting a new how-to shortly.

EDIT: [enjoy]("http://ubuntuforums.org/showthread.php?t=1320844").

---

### Post by cesarsalles on 2009-11-17
thanks a lot for your help. I have a Samsung phone and following your instructions was able send files to it.

---

### Post by Buttons840 on 2010-07-31
I've fallowed this guide and I can send data to my phone, and retrieve phone info.  All indications are that the connection is working properly.

However, BitPim will not "Find Phone," and the button to send info to the phone is disabled.  I'm wondering if BitPims failure to find the phone arbitrarily disables the ability to write to the phone?

But again, I do know I can retrieve information from the phone, such as the model, contacts, and ringtones.  Just can't write to it.

---

### Post by quazi on 2010-11-27
As a brief update, this also works with the Samsung Alias 2 (I haven't tried writing to it).

There's another (better) guide that automates this process:
[http://ubuntuforums.org/showthread.php?t=1320844](http://ubuntuforums.org/showthread.php?t=1320844)

---

