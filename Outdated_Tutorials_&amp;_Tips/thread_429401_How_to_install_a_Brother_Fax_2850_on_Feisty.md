---
title: "How to install a Brother Fax 2850 on Feisty"
date: 2007-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by winddummy on 2007-05-01
This info is on the Brother site but I thought I'ld distill it here for the Fax 2850

Download the drivers from the Brother web site.
LPR Driver: [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
Cups Wrapper: [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

From a terminal
```

sudo ln -s /etc/init.d/cups /etc/init.d/lpd
sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
sudo mkdir -p /var/spool/lpd

sudo dpkg -i fax2850lpr-1.1.2-1.i386.deb
sudo dpkg -i cupswrapperFAX2850-1.0.2-1.i386.deb

sudo rm /etc/init.d/cups /etc/init.d/lpd
sudo rm /etc/init.d/cupsys /etc/init.d/lpd
sudo rm -rf  /var/spool/lpd

```

From the menu
```

System > Administration > Printing
>> New Printer (My system detected the Fax 2850 on the USB port.)
> Forward
> Install Driver
Browser to /usr/share/cups/model
select the brfax2850_cups.ppd
> Forward
Fill out the description and location if you like
> Apply

```
With any luck you can print a test page

---

