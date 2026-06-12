---
title: "Connecting to my School's WPA Wifi"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by HamHamT on 2013-04-30
Hello, I have been having quite a bit of trouble with this.  I am able to connect to my school's open-wifi channel, but when I try and connect to my WPA, I get asked for a user name and password, and I am certain I am entering the information correctly.  I am able to connect to the WPA using my MacBook and the same exact information.

What I have tried so far:

1.) Asked the IT person at my school and suggested this:
>  If you are computer savvy you can try connection to WPA through your network adapter software that seems to work with Window 7 machines that have the same issues you have described.
but I don't understand what exactly he is saying.

EDIT:

Actually I have just found out what he means. I need to use this;

[http://www.smc.edu/AcademicAffairs/Library/Documents/Windows_WPA_instructions.pdf](http://www.smc.edu/AcademicAffairs/Library/Documents/Windows_WPA_instructions.pdf)

Could someone help me configure this for Ubuntu?

---

### Post by HermanAB on 2013-05-01
There is WPA and then there is WPA...

WPA-Enterprise uses RADIUS and EAP, not just a simple password.

You need to set up the certificate etc.  Some googling is required.

---

### Post by HamHamT on 2013-05-01
Thank you for your response Herman.  I am very new to configuring networking, and I am just learning about what a certificate is.  I found out i am using the PEAP, and I tried using  AddTrust_External_Root.pem which i got from following this guide for another school in Texas (not my school) but to no avail.  [http://hdc.tamu.edu/Connecting/Wireless/TAMULink_for_Linux/Connecting_Ubuntu_To_TAMULink.php](http://hdc.tamu.edu/Connecting/Wireless/TAMULink_for_Linux/Connecting_Ubuntu_To_TAMULink.php)

Could you point me in the direction of what exactly I need to google?

---

