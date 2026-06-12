---
title: "HP printer unable to connect"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Jan Greeff on 2012-05-04
Since upgrading to 12.04 Precise Pangolin, my HP Officejet all-in-one does not work. After trying many options, I now get "unable to connect to CIFS host." Printers that lose contact have been my main hassle ever since Ubuntu 3 tears ago, but I have always managed to somehow get them going again, but this time seems like 12.04 has managed to take it out of my reach. One of my dead ends has been when I get to the stage where I try to purge the installations and the system refuses access, asking whether I am root. That freaks me out, when I get blocked from my own system and asked something I have no idea about - am I root? 

Is there someone who is patient enough to help a weary old computer illiterate out of his misery?

---

### Post by Ms. Daisy on 2012-05-08
I assume that the printer is plugged directly into the computer. 

First thing is you need the correct driver.  You can check for drivers by typing "driver" into the dash. That will start a search for drivers.  You may find the correct one that way.  I have an all-in-one HP, and the driver that ubuntu found never quite worked properly.  I ended up downloading the driver from the HP website.  If you post the model of your printer I can help you find it.

Second, have you installed HPLIP?  That's the Linux version of the HP software that allows you to use all the functions of the printer.  Here's a guide for HPLIP:

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

---

### Post by Jan Greeff on 2012-05-08
Thanks Ms Daisy, I have had drivers and hplip working for a long time, problem is upgrade to 12.04 seems to have messed up my network so now neither computer is able to communicate with the printer.

---

### Post by Ms. Daisy on 2012-05-08
hmm.. did you reinstall cups?

---

### Post by Bucky Ball on 2012-05-08
Perhaps need to fix the internet before tackling the printer. Perhaps you need to post a thread to work that out ...

If you need to download HPLip or any other driver/software you are going to have some issues without a connection to the outside world. ;)

---

### Post by Bucky Ball on 2012-05-08
Sorry, the forum did something odd and duplicated my last post. This one in error. ;)

---

### Post by Jan Greeff on 2012-05-08
No problem with Internet whatsoever.

---

### Post by jerome1232 on 2012-05-08
I'm going to mention the obvious first then let's go from there, How exactly are you connected to this printer? Is it a network printer (wireless or ethernet?) is it connected to another computer and shared from that computer? or is it directly connected to your Ubuntu box.

By way of diagnostics, does this command return anything?
```
hp-probe
```

---

### Post by anewguy on 2012-05-08
Also - the "are you root" question - does it actually ask if you are root, or does it say it needs root permissions?  Does it ask for a password at the time?  Are you running this from a terminal or from the GUI?  What command gives you the request?

---

### Post by Jan Greeff on 2012-05-08
Jerome1232 and anewguy, replies to your questions in seriatim:

Ethernet connection via the router, shared from the other computer.

hp-probe result:  warning: No devices found on the 'net' bus. If this isn't the result you are expecting,
warning: check your network connections and make sure your internet
warning: firewall software is disabled.

I ran "apt-get purge hplip" in a terminal and access was denied (are you root Question) but then I ran "sudo apt-get purge hplip" successfully, then reinstalled hplip. 

Currently, if I click on the black printer icon in the top toolbar, it shows four printers one of which is shown in the "power/printers" menu, but the hp toolbox shows no printers are installed.  

I have also installed cifs but this has had no effect.

When trying to connect to Localhost, a username and password is being requested by [http://localhost:631](http://localhost:631). The site says: "CUPS" and I have no idea what username and password is required.

The Ubuntu scheduled backup feedback is that backup is delayed until a network connection can be established.

---

### Post by jerome1232 on 2012-05-08
From the hp's control panel, print out a network status report. (mine has the feature, I'm assuming yours does too)

What is it's ip, hostname etc...

---

### Post by Bucky Ball on 2012-05-08
CUPS username and password is same as machine's; it's your login username and pass.

---

### Post by Jan Greeff on 2012-05-09
Thanks Bucky Ball, but it is not accepting my username and password. Have I gone wrong somewhere with the username which has never been used before, the system always asks for the password only?

---

### Post by Bucky Ball on 2012-05-09
Open a terminal and you will see it there, the one before the name of the machine. For instance:

```
jan@yourmachinename
```

---

### Post by Jan Greeff on 2012-05-09
Is it the whole jan@jan-etc? I have tried all combinations, the whole thing and just the part after "@" but same result: 

A username and password are being requested by [http://localhost:631](http://localhost:631). The site says: "CUPS"

---

### Post by Bucky Ball on 2012-05-09
Well, not sure what's happening there because it is your username, the one before the @ in the terminal, and your regular password for CUPS admin at  [http://localhost:631]("http://localhost:631/").

jan@jan = 'username@machine name'

---

