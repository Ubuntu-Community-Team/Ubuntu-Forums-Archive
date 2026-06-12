---
title: "HOWTO Modems and Ubuntu"
date: 2004-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by az on 2004-11-27
***This is not completely finished yet. I am editing it regularly***

If you are sure that your modem is supported by Linux without drivers, please continue.  Otherwise, download the scanmodem script and look at the /scan/ModemData.txt file it creates for you:

[http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

gunzip scanModem.gz
chmod +x scanModem
sudo ./scanModem

Read the HOWTO Linmodems Winmodems softmodems, as necessary.

If the setup of your modem failed using the Ubuntu metwork tools, you have at least two other options.
pppconfig
wvdial

pppconfig:

Open a terminal and do 
sudo pppconfig
Enter the information as needed.  Use the name provider for your default connection.  COM1 is /dev/ttyS0, COM2 is /dev/ttyS1, and so forth.
Add your user to the dip group using the advanced options.
Save and exit.
sudo pon
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on.  Post the result in your question to the forum.
sudo poff hangs up.
You need to log out and back in for your user/group settings to be updated.  You can then pon and poff without the sudo.  Now, right click on the panel and add an applet called modem lights.  It is already set up to use pon and poff.  Make sure that it is using the correct lock file to see your modem or you will not see the lights.

WVDIAL

Install wvdial if it is not already installed.  Some people have said that pppconfig worked better than wvdial while some have said that wvdial was the only utility that could get them on the net.  Go figure.

type
wvdialconf .wvdialrc

enter your info and type wvdial to get on the net.
You can also use pon.wvdial and poff.wvdial, too.


Post questions on the forums as needed.

---

