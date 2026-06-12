---
title: "Looking for a printer driver or help getting one from disk"
date: 2016-10-20
forum: New to Ubuntu
---

### Post by msmith1138 on 2016-10-20
Hey gang!

I am looking for the specific driver for the Epson ET-16500. All I have been able to find so far is the generic driver and the printer is coming out much too dim to be of use. Being new to Linux I am uncertain how to proceed. I read that it might be possible to get the ppd file from the disk that came with it, but have so far, been unsuccessful in my attempts to figure it out on my own. Any help would be greatly appreciated!

Thanks!!

---

### Post by Kris_M on 2016-10-20
Hi and welcome to the forums!
I googled for  ubuntu driver Epson ET-16500
and saw this:  looks like there's a deb. Yay!  same idea as what I used to install my Canon MX7520.  Give it a shot and holler if you hit stumbling blocks!

[http://tutorialforlinux.com/2016/10/09/epson-et-16500-driver-for-ubuntu-16-04-xenial-how-to-get-install-quickstart-scanning/](http://tutorialforlinux.com/2016/10/09/epson-et-16500-driver-for-ubuntu-16-04-xenial-how-to-get-install-quickstart-scanning/)


edit: at the bottom of that one you'll see a link for the scanner install instrs (another deb).
I did same thing when I was a noob so don't be scared by it. - still a noob![URL="http://tutorialforlinux.com/2016/10/09/epson-et-16500-driver-for-ubuntu-16-04-xenial-how-to-get-install-quickstart-scanning/"]
[/URL]

---

### Post by colmax on 2016-10-21
You could be printing in draft mode if text is faint
I use a brother printer & have found ota install seems to work better than downloading the file then running it
I'm so ugly i had a job where they pushed my face in the dough to make gorilla biscuits lol :)

---

### Post by msmith1138 on 2016-10-21
Thank you for the welcome!

I think this is the driver that I have, as it has the same limited options available and the printer is still producing very dim copies. It only happens when printing from Xubuntu and not from the printer itself. I have the install disk from Epson but it is only for win/mac.

I just got this printer for free for beta testing it, and I would really hate to not use the $900 device I was given for a two paragraph review :D

---

### Post by msmith1138 on 2016-10-21
> **colmax said:**
> You could be printing in draft mode if text is faint
I use a brother printer & have found ota install seems to work better than downloading the file then running it
I'm so ugly i had a job where they pushed my face in the dough to make gorilla biscuits lol :)


The generic driver utility doesn't even give me an option for how to print. It gives me the ability to turn on/off greyscale, and change the paper type is really all there is

---

### Post by Kris_M on 2016-10-21
so when you go to system settings / printers, what do you get? My orig is MG7500-series, the one created by the driver is MG7500USB.  The second one is checked default. Look for settings in there.

---

### Post by msmith1138 on 2016-10-21
I get the two printers I have, the ET-16500 and the XP-610. The XP-610 shows ESC/P Driver (full feature) , but the 16500 shows it is running off of the ESC/P-R (generic). I am unable to find anything else for the 16500 other than the site that doesn't really explain a noob version of how to pull a ppd file from an install disk

---

### Post by colmax on 2016-10-21
Haven't found any linux driver for your printer (nice looking machine tho)
Maybe update cups
Cheers

---

### Post by Kris_M on 2016-10-21
forget cups.  I can only suggest that you run that link I gave you and see if anything different shows up .  I'm heading to bed. will check in tomorrow.

---

### Post by Geoffrey_Arndt on 2016-10-21
OK . . . click on links below.    If any problems, please provide info on what steps you've taken.

Note:   the driver link below handles MANY epson printer including yours (EVEN THOUGH it's not listed - - it's just too new and the site maintainers haven't updated the web page)

Here is the specific driver you need (64 bit **espson-inkjet-printer-escpr OR just 1.4.1 Deb as listed on the download page**) from openprinting.org . . . install it via the "gdebi" installer (install gdebi first from Synaptic or Ubuntu Software first).   If all these instructions seem more complex than needed . . you're right . . . just remember they were written/updated by engineers.

Once gdebi (that stands for "gnome deb installer") is installed, go to the /downloads folder (or wherever you actually downloaded the deb file to - - then right click it, and select gdebi from the popup window.  Then just read the gdebi installer gui and click on install.

Here is the page with the download file (above driver):   [http://www.openprinting.org/driver/epson-escpr/](http://www.openprinting.org/driver/epson-escpr/)

[URL="http://tutorialforlinux.com/2016/10/09/epson-et-16500-driver-for-ubuntu-16-04-xenial-how-to-get-install-quickstart-scanning/"]http://tutorialforlinux.com/2016/10/09/epson-et-16500-driver-for-ubuntu-16-04-xenial-how-to-get-install-quickstart-scanning/


[/URL]

---

### Post by msmith1138 on 2016-10-23
These for some reason are still showing as a generic driver without the full options for the printer itself. The 610 give me all the standard options the printer has available to it, the 16500 is very bare bones. [IMG]http://i53.photobucket.com/albums/g47/msmith1138/1d25f244-e2e5-4cb7-a1fe-241d9c5d8675_zpsusppw89d.png[/IMG]

---

### Post by msmith1138 on 2016-10-23
[IMG]http://i53.photobucket.com/albums/g47/msmith1138/Screenshot_2016-10-23_16-26-22_zps5l1errqf.png[/IMG]

---

### Post by Kris_M on 2016-10-23
Those may be about all the options you get.
I wouldn't select bright paper.  Mine just says
plain paper
letter
duplex off
600dpi

---

