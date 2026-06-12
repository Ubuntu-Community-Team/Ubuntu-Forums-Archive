---
title: "Can't figure out how to Uncab..."
date: 2008-09-04
forum: New to Ubuntu
---

### Post by AardvarkSagus on 2008-09-04
I am trying to install a US Robotics MaxG USR5421 USB wireless card.  All the documentation points me to obtaining the .inf and using ndiswrapper to install it, but I can't figure out how to extract the file from the Data . exe where it is supposedly found.  I keep getting the response 
```
bash: uncab: Command not found
```

I'm kind if a Linux newbie though not that green with PC's.  Where am I going wrong?

---

### Post by Pro-reason on 2008-09-04
> **AardvarkSagus said:**
> I am trying to install a US Robotics MaxG USR5421 USB wireless card.  All the documentation points me to obtaining the .inf and using ndiswrapper to install it, but I can't figure out how to extract the file from the Data . exe where it is supposedly found.  I keep getting the response 
```
bash: uncab: Command not found
```

I'm kind if a Linux newbie though not that green with PC's.  Where am I going wrong?

There is no such command as “uncab” for Ubuntu.  I think that you are running some sort of script designed for another system.

There is a command called “cabextract” which you can install in Synaptic, but I don't know if there is an easy way to make it work with the thing you are using.

In any case, what documentation are you following?  This talk of “.exe” makes me think we're talking about Windows files here.  Windows drivers will not work on Ubuntu.

---

### Post by AardvarkSagus on 2008-09-04
I am speaking of the windows drivers here.  This particular piece of hardware doesn't have Linux drivers so I am following the advice found [HERE](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsUsRobotics#USB) under the "MAXg 5421" heading saying:
> Necessary to follow instructions for USR805421 on ndiswrapper page. On Feisty, the udev rule should be: SUBSYSTEM=="usb", ATTR{idProduct}=="011b", ATTR{idVendor}=="0baf", ATTR{bConfigurationValue}="1". Value 011b depends on product (use lsusb command). Works fine with networkmanager.

That page tells me:
> Driver: Official U.S. Robotics [http://www.usr.com/support/5421/5421-files/5421-na.exe](http://www.usr.com/support/5421/5421-files/5421-na.exe). Unpack it and install driver with USR5421X.inf. This doesn’t copy the .sys files (.sys files for RNDIS driver are part of Windows, so they are not needed in Windows; however, driver for USR5421 distributes .sys files but they are not installed by .inf file); so copy RNDISMPK.sys and usb8023k.sys files into /etc/ndiswrapper/usr5421x directory as rndismpk.sys and usb8023k.sys respectively).
I use the Archive manager to extract the downloaded file and end up with a Data.exe and a Setup.exe that I cannot open to get the .inf supposedly contained therin.  Every place I have checked for infomation how to unpack that file tells me to uncab it.  This doesn't make any sense to me since that command doesn't seem to exist.

---

### Post by Pro-reason on 2008-09-04
> **AardvarkSagus said:**
> 

I use the Archive manager to extract the downloaded file and end up with a Data.exe and a Setup.exe that I cannot open to get the .inf supposedly contained therin.  Every place I have checked for infomation how to unpack that file tells me to uncab it.  This doesn't make any sense to me since that command doesn't seem to exist.

I've just done the following, and it worked.
```

sudo apt-get install **cabextract**
wget **http://www.usr.com/support/5421/5421-files/5421-na.exe**
unzip **5421-na.exe**
cabextract **Data.exe**
less **Disk1/*inf**

```

You'll be able to skip some steps that you have already done.  I hope that helps.

You can also make &#8220;uncab&#8221; a synonym for &#8220;cabextract&#8221; if you like.

```

echo "alias uncab=cabextract" >> ~/.bashrc 
bash

```

---

### Post by AardvarkSagus on 2008-09-04
Thanks for the help so far.  Is there any chance that I can get a little help with the rest of the run?  I am running into so many walls with this that I am about to re-enact the scene from Office Space...

---

### Post by Pro-reason on 2008-09-05
What other problems have you had?

---

### Post by AardvarkSagus on 2008-09-05
Well, even doing what you prescribed I can't seem to find the .inf file or the 2 .sys files to install using ndiswrapper.  Once I find those and get this thing running I will have a computer up and running completely.

---

### Post by Pro-reason on 2008-09-05
> **AardvarkSagus said:**
> Well, even doing what you prescribed I can't seem to find the .inf file or the 2 .sys files to install using ndiswrapper.  Once I find those and get this thing running I will have a computer up and running completely.

Hmmm.  Try copying and pasting exactly those commands into the terminal.  It will surely work.  (The last command displays the contents of the .inf file.)

In the event of any errors, post them here in detail.

Edit:  When I do &#8220;cabextract Data.exe&#8221;, I get this output:

```

Extracting cabinet: Data.exe
  extracting Disk1/data1.cab
  extracting Disk1/data1.hdr
  extracting Disk1/data2.cab
  extracting Disk1/ikernel.ex_
  extracting Disk1/layout.bin
  extracting Disk1/pnpchk.exe
  extracting Disk1/pnpinfo.inf
  extracting Disk1/Setup.bmp
  extracting Disk1/Setup.exe
  extracting Disk1/Setup.ini
  extracting Disk1/setup.inx

All done, no errors.

```

---

### Post by AardvarkSagus on 2008-09-05
Hopefully I'll get time to try tonight and let you know what happens.  Working now.

---

### Post by AardvarkSagus on 2008-09-06
I got as far as cabextract and everything worked with no errors and then I tried running ndiswrapper and installing the .inf (though I couldn't seem to find the inf with the file name that was specified on [THIS PAGE](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/#u) and when I tried, I got:
```
$ sudo ndiswrapper -i /home/matt/Disk1/pnpinfo.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing pnpinfo ...
couldn't get manufacturer section - installation may be incomplete

```
I'm getting frustrated.  I just want this to work.](*,)

---

### Post by AardvarkSagus on 2008-09-07
I may have found the actual file I am looking for and I got this:

```
matt@main-desktop:~/Documents$ sudo ndiswrapper -i /home/matt/Documents/USR5421X.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing usr5421x ...
forcing parameter IBSSGMode from 0 to 2

```
I don't know if this worked or not but it doesn't look promising.  Now to find the .sys files.  Any suggestions?

---

