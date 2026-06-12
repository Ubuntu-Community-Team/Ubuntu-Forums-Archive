---
title: "3g usb modem...."
date: 2008-09-04
forum: New to Ubuntu
---

### Post by russty12 on 2008-09-04
hi i am a complete novice with linux/ubuntu and i need of advice with my 3 usb modem.i have an huawei e169g hspda usb modem, i have installed the software using the wine program but still cant get the software/modem to work. it just shows me the message "data modem invalid". so any suggestions on how i can get this to work would be appreciated thnx russell.....

---

### Post by GeorgeVita on 2008-09-04
Hi,
I thing that you don't need wine to use your modem. You may connect to your provider by using wvdial (dialer program) from a terminal window after fixing the file wvdial.conf (initialization parameters).

First EDIT the wvdial.conf by executing the terminal command:

sudo gedit /etc/wvdial.conf (give your password when asked)

then you must add the following parameters to the wvdial.conf (configuration file for the dialer program)

[Dialer hspa]
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = user
Password = pass
Phone = *99#
Stupid Mode =1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 =AT+CGDCONT=1,"IP","internet"

(possibly you have to check the Phone Number if it is different for your provider, and also the Init3 maybe you have to put another string in the place of "internet")

SAVE the file, insert your modem to the USB port, wait for 5 seconds and from a terminal window execute the command:

sudo wvdial hspa (give your password if asked)

After some messages including "CONNECT 7200000" comes the final "--> secondary DNS address ..." and you are connected. Minimize the terminal window and click on the Firefox shortcut, unselect the "work off line" option from "file" menu (if selected) and Browse!

To disconnect, press CTRL-C at the terminal window which you made the connection.

Note that the above worked with E170, E220 on Ubuntu 8.04 (full installation or Live CD). The SIM PIN check is disabled.

As references you can read the data given via the "man wvdial" and "man wvdial.conf" commands (from a terminal window).

Copy paste and post any 'bad' messages to fix them.
 
Regards,
George

---

### Post by russty12 on 2008-09-04
thanks for the help will let you know if it works ok :)

regards Russell

---

### Post by halitech on 2008-09-04
if that doesn't work, there is info here:

[http://samiux.wordpress.com/2008/04/23/huawei-e169g-on-ubuntu-804/](http://samiux.wordpress.com/2008/04/23/huawei-e169g-on-ubuntu-804/)

---

