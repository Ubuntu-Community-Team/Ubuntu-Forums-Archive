---
title: "Can detect WIFI  but cannot connect to Wifi under 11.10"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Herojam on 2012-01-30
I use a  Aztech Wifi adaptor to connect to the WIFI in my house. Under 10.10  Ubuntu , i have no problems to detect and connect to the WIFI network in my house. But when i use 11.10 version, the USB Aztech adaptor  can detect the networks available  but when i key in the Key to connect  which is   WEP  40/128 bit code   i don't seem to be able to get a connection.

But with the 10.10  this is not a problem. I don't seem to understand why.

I'm new in Ubuntu and would appreciate any help.

Thanks.

Herojam

---

### Post by rgreener25 on 2012-01-30
Could your router have a button you need to press before connecting

---

### Post by Herojam on 2012-01-30
Thanks for reply. Appreciate you taking the time to help.  My router has no button as you mentioned.
All the other computers can connect except for this one running 11.10.   The funny thing is when i am in 10.10   there is no problem to connect.

Herojam

---

### Post by grahammechanical on 2012-01-30
What did you do in 10.10 to set up this connection that you have forgotten to do in 11.10?

Try clicking on the network icon and selecting Edit Connections. Click the Wireless tab and then select your wireless connection and click Edit. Go to the Wireless Security tab and make sure that Security is set to WEP 40/128-bit key and not WPA & WPA2 Personal or something else.

You can also check that you are using the correct pass phrase or wireless key.

Please confirm that these settings are correct. You can also set the connection to connect automatically.

You do not explain the manner in which 11.10 does not seem to make a connection. What messages does the system give you as the desktop loads? 

Regards.

---

### Post by Herojam on 2012-01-30
Thanks for reply.  Basically i have two computers running on Ubuntu.
One computer is a  netbook running on UBUNTu 9.10 the other is  a desktop which was running on 9.10 and then there was a message asking me to upgrade to 11.10  as 9.10 is no longer supported.

When the desktop was on 9.10  i was able to connect to the Internet quite easily. At the top righthand corner , i would click on the wireless connection and it would show me various wireless connections that were available. As my router is security locked by a 40/128 bit Hex key, at first login i was required to key in the  security key.  Subsequently  since it is set for automatic connection , every time i start up it would automatically  detect and get a connection. 

But after the upgrading to 11.10, it would try to connect but it could not.  I tried to connect manually by  using edit connections  and deleting all the connections and then keying in all the settings  like eg. shared or open, 40/128 bit security key etc  but to no avail.  

I don't think it has got to do with the USB security adaptor i'm using as it can detect the WI FI networks available and it shows me what is available.  Then when i click the one i'm using it a message pops up asking me the key. I key in the key and and press connect but after i while ite message pops up again and requests for the key  again and again.  I tied another live distro  Pear OS and the same thing happens. But on 9.10  on live mode   there is no problem to connect . I have checked all my settings and both 9.10 and 11.10 are exactly the same.

What have i done wrong?  Hope to have sufficiently given you an idea of my predicament.

Would appreciate any help.


Thanks

Herojam

---

### Post by Herojam on 2012-01-30
Hope someone can help as i am running out of ideas to get 11.10 connected to my home network.

Cheers

Herojam.

---

### Post by anewguy on 2012-01-31
Post back the outputs of:

lspci

lsusb

lshw -C network

ifconfig

iwconfig

lsmod


Dave ;)

---

### Post by Herojam on 2012-01-31
How to i do these ?  Do  I key this at the terminal?

Sorry but i am really  new to all this.

Herojam

---

### Post by dolphin194 on 2012-01-31
> **Herojam said:**
> How to i do these ?  Do  I key this at the terminal?

Sorry but i am really  new to all this.

Herojam

Yes. Run those commands in the terminal.

---

### Post by Herojam on 2012-02-01
Managed to solve the problem.  I had to unplug and remove the wireless USB  Adaptor and installing  back again  and then it managed to make a connection after accepting my key .
It was like a reboot of the USB Wireless adaptor.  

Thank you for all  who helped and really appreciate the spirit of helping one another on this site.

Cheers

Herojam

---

