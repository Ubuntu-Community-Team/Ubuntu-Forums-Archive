---
title: "HOWTO: Tether a Verizon Q to Ubuntu - USB Cable"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by dark_harmonics on 2008-05-26
This is my very first howto which I am writing because it has taken me hours of research to figure out how to tether my Verizon Q to ubuntu. 

Install wvdial (if not already installed in your version of ubuntu)

```
sudo apt-get install wvdial
```

Next you need to turn on the "Modem link" on your Q. As soon as you plug the USB cable into your computer you need to type:
```
dmesg
```
You need to look for the line where it assigns a device ID to your modem. Mine was 4 lines up from the bottom and looked like this:
```
[  119.616081] cdc_acm 1-2:1.0: ttyACM0: USB ACM device
```
So according to this line ttyACM0 is the name of my Q's Modem.

Next we need to configure your /etc/wvdial.conf file properly. You will need to edit the ##########@vzw3g.com to reflect your phone number and the Modem to reflect the modem device name we just figured out. 

First backup the original copy of the /etc/wvdial.conf file with:

```
sudo cp /etc/wvdial.conf /etc/wvdial.original
```

Then edit your /etc/wvdial.conf 
```
 sudo gedit /etc/wvdial.conf
```
and replace the contents with the below:
```

# /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = vzw
Phone = #777
Modem Type = USB Modem
Stupid Mode = on
Baud = 921600
Modem = /dev/ttyACM0 #put your modem name here
Init = ATZ
ISDN = 0
Username = ##########@vzw3g.com #change the pound symbols to your number
Carrier Check = no
Auto Reconnect = on
[Dialer shh]
Init3 = ATM0

[Dialer pulse]
Dial Command = ATDP

```

Save and close the file after you fill in the needed information.

In this next part we will need to edit your /etc/ppp/options file so that your phone does not disconnect after 2.5 minutes and so lets make a backup copy of it with:
```
sudo cp /etc/ppp/options /etc/ppp/options.original
```

Now lets open it with ```
sudo gedit /etc/ppp/options
```
We are going to need to find two settings. In gedit click the find button and put "lcp-echo-interval" into the find box. 
Change the value of it to be:
```
lcp-echo-interval = 0
```
Next scroll down less than half a page to find the "lcp-echo-failure" setting and change it to:
```
lcp-echo-failure = 0
```

Save and close the file.


Now to connect simply execute wvdial with:
```
wvdial
```

Thats it folks!

References and credits go to the folks who posted at this thread (in particular corn13read who provided the information that allowed me to figure out the rest): [http://ubuntuforums.org/showthread.php?t=511257](http://ubuntuforums.org/showthread.php?t=511257)

---

