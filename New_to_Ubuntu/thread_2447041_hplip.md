---
title: "hplip"
date: 2020-07-11
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2020-07-11
I have a hp desktop all in one printer,copier and scanner. I don't use it that often but yesterday I wanted to scan something and I got message of communication device error 5012. So i removed hplip 3.20.5 and downloaded newest release of 3.20.6 I followed the instructions some error messages were on the terminal but i continued on. The program recognized my printer but still got the 5012 error. How can this be fixed.  Can anyone provide step by step instructions to fix this problem? **_Any help would be appreciated._                                                                                                                                                                                         **

---

### Post by daniewicz on 2020-07-11
Try reinstalling and post the terminal error messages.

---

### Post by tuesdaybarrett on 2020-07-12
i followed these instructions. to reinstall hplip. 1.[COLOR=#1983A6][FONT=Roboto]wget [https://nchc.dl.sourceforge.net/project/hplip/hplip/3.20.6/hplip-3.20.6.run](https://nchc.dl.sourceforge.net/project/hplip/hplip/3.20.6/hplip-3.20.6.run)
[/FONT][/COLOR]2.[COLOR=#1983A6][FONT=Roboto]chmod -R 755 hplip-3.20.6.run
[/FONT][/COLOR]3.[COLOR=#1983A6][FONT=Roboto]./hplip-3.20.6.run
[/FONT][/COLOR]error: Device busy: hp:/usb/Deskjet_2540_series?serial=CN3C12FKC80604error: Device not found
error: Device busy: hp:/usb/Deskjet_2540_series?serial=CN3C12FKC80604
error: Device not found

---

### Post by tuesdaybarrett on 2020-07-12
also saw this error message
POST-BUILD COMMANDS
-------------------
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xf0 in position 0: invalid continuation byte


The above exception was the direct cause of the following exception:


Traceback (most recent call last):
  File "./install.py", line 241, in <module>
    text_install.start(language, auto, test_depends, test_unknown, assume_network, max_retries, enable, disable)
  File "/home/michael/hplip-3.20.6/installer/text_install.py", line 1405, in start
    cups.getSystemPPDs()
  File "/home/michael/hplip-3.20.6/prnt/cups.py", line 291, in getSystemPPDs
    ppd_dict = cupsext.getPPDList()
SystemError: <built-in function getPPDList> returned a result with an error set

---

### Post by tuesdaybarrett on 2020-07-12
should i enable QT5 via this?[COLOR=#333333][FONT=HPSimplifiedLight][h=2]How to install HPLIP with qt5[/h][/FONT][/COLOR]
[COLOR=#333333][FONT=HPSimplifiedRegular]**Notes:**[/FONT][/COLOR]
[COLOR=#333333][FONT=HPSimplifiedRegular]**HPLIP supports Qt5 from 3.16.5 and above**[/FONT][/COLOR]
[COLOR=#333333][FONT=HPSimplifiedLight]To enable qt5 support:

[LIST=1]
[*]You need to install the following dependencies
[LIST]
[*]PyQt5
[*]python-qt5-dbus
[/LIST]

[*]Go to source of hplip. By default it is in ~/Downloads.
[*]Run the following commands
[LIST]
[*]./configure --prefix=/usr --enable-qt5 --disable-qt4
[*][FONT=HPSimplifiedRegular]make[/FONT]
[*][FONT=HPSimplifiedRegular]"make install"[/FONT] as root user
[/LIST]
[/LIST]

[/FONT][/COLOR]

---

### Post by daniewicz on 2020-07-12
Always better to use the ubuntu package manager to install software rather than an internet site like sourceforge. Which version of ubuntu are you running? I have 20.04 and using the synaptic package manager I see that hplip 3.20.3 is available. Using synaptic would be the preferred way to install hplip.

---

### Post by tuesdaybarrett on 2020-07-13
I'm using ubuntu 20.04/ Installed synaptic package manager & then installed hplip but still get communication device error 5012

---

### Post by daniewicz on 2020-07-13
Try removing the printer, uninstall hplip, reinstall hplip[FONT=monospace][COLOR=#333333].[/COLOR][/FONT]

---

### Post by tuesdaybarrett on 2020-07-13
in my research i found that a driver is missing which is '/usr/lib/cups/-filter/hpcups.How can this be added to my system? i tried sudo apt install but that didn't work. Any answer would be helpful. hx again

---

### Post by daniewicz on 2020-07-13
install *printer-driver-hpcups*

---

