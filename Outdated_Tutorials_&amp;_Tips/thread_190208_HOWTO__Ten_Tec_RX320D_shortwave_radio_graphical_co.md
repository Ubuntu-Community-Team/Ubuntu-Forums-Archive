---
title: "HOWTO:  Ten Tec RX320D shortwave radio graphical control"
date: 2006-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by troupa on 2006-06-06
The Ten Tec RX320D software-defined shortwave receiver can be controlled graphically on Ubuntu.  This has been tested with Breezy and Dapper.

1)  You'll need to download two packages.
```
wget http://shortwave.no-ip.org/xclass-0.9.1_0.9.1-1_i386.deb
wget http://shortwave.no-ip.org/rx320-0.6.1_0.6.1-1_i386.deb
```

2) install using dpkg.
```
sudo dpkg -i xclass-0.9.1_0.9.1-1_i386.deb
sudo dpkg -i rx320-0.6.1_0.6.1-1_i386.deb
```

3) Run the control software.
```
rx320
```

4) Right click on a blank space of the controller's window and choose "Configure" and put in the /dev entry for the serial port that the radio is connected to.  Mine, for example, is /dev/ttyS0.

The site hosting the packages should hopefully be available 24/7.

---

### Post by Don DeGregori on 2007-10-23
When will your site be back up so I can download for the RX320?
Don

---

### Post by gccradioscience on 2010-08-13
Question,   Why is this not available in the Software Center or the Synaptic Package Manager??     I need this soon for my next piece the RX-320D.   I am glad to hear the great news that the RX-320D is compatible with Linux Ubuntu,  it's too bad that Ten Tec did not come out with a wideband receiver with general coverage of HF/VHF and UHF frequencies from 10 kHz to 3 GHz excluding cellular.     I wish linux would be available in most professional communications equipment PC receivers, cause linux is more secure than Windows.  Still I am glad to hear thatI can add a SW receiver to my netbook now I need to get the receiver and find the software for it.    We need to make the downloads available via the Ten Tec site.    I will call them up tommorrow about this.


gccradioscience

---

