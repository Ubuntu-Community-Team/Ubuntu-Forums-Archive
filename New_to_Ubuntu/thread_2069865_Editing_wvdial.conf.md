---
title: "Editing wvdial.conf"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by Polydorus on 2012-10-11
I'm tying to install dial up on Ubuntu 12.04 (64 bit).  I have managed to get wvdial installed and now I'm trying to configure it.  I ran:
sudo wvdialconf /ect/wvdial.conf 
and I got a few error messages.

I was hoping to fix most of the errors by editing wvdial.conf adding my ISP, user name, password and such.  When I tried to open wvdial.conf with gedit I get the error message:

Could not open: You do not have permission

Where do go now?

TIA

---

### Post by mikewhatever on 2012-10-11
Try ** gksudo gedit /ect/wvdial.conf **

---

### Post by Polydorus on 2012-10-11
Thanks.  What does the GK in front of sudo stand for?

---

### Post by mikewhatever on 2012-10-11
Explained [here.]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Polydorus on 2012-10-12
Thanks for the link, interesting explanation.

    Your suggestion to use, gksudo gedit /ect/wvdial.conf allowed me to edit the configuration without any problems.   However now wvdial is not able to read what I saved.  I get the following message:

--> Can't open '/etc/wvdial.conf' for reading: Permission denied
--> ...starting with blank configuration.
--> WvDial: Internet dialer version 1.61
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Did I miss something about permissions when I saved my edited wvdial.conf?

TIA

---

### Post by Polydorus on 2012-10-14
For some reason  the Dialer Defaults  came up with semicolons  in front of each item.  Removing the semicolons allowed me to get online today.  I guess this can be marked solved.  Thank you very much for the help mikewhatever.

---

### Post by mikewhatever on 2012-10-15
Thanks for the update. Glad you got it working.

---

### Post by ejoftiduttu on 2012-12-24
Re: reliance netconnect in ubuntu 12.04
When i tried to connect my reliance netconnect on ubuntu 12.04 i'm getting a msg likethis

ejofti@ejofti-ThinkPad-E420:~$ sudo wvdial netconnect
--> WvDial: Internet dialer version 1.61
--> Warning: section [Dialer netconnect] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Anyone plz help me solve this..

---

### Post by Polydorus on 2012-12-25
What type of modem (serial/USB) do you have?

---

