---
title: "Ubuntu 11.04+Canon LBP 2900 - installation issue"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by jaimohan on 2012-10-25
Hi,

I'm new to ubuntu. Installation of Canon LBP 2900 seems to be not working on ubuntu. After going through various posts I've come to notice that this is a teething issue for many ubuntu users. 

I've downloaded a driver *raducotescuCanonCAPTDriverRelease 2.4-0-* and installed the same. The installation was successful, the printer is recognized by the system. Print Jobs are being pushed to the queue. But nothing is getting printed. The readme file along with driver says it is installing CAPT v2.00 driver. But printer properties show that the capt driver version is 1.5 

Please help..

---

### Post by pdc on 2012-10-25
**I suggest you delete the printer drivers that you have installed with the radonescu script**

If I offer the advice below:

Ubuntu make good help available

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)

the essence is

1) [COLOR="SeaGreen"]download and install the drivers[/COLOR]

 ...........go here........

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900772424.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900772424.html)

to download the package that is [COLOR="Blue"]CAPT Printer Driver for Linux Version 2.40[/COLOR]

....the package comes down as [COLOR="Green"]Linux_CAPT_PrinterDriver_V240_uk_EN.tar.gz[/COLOR]

I suggest to [COLOR="Red"]SAVE[/COLOR] the file to your downloads directory; and then open the directory; when you click on the file it should offer to open with ARCHIVE MANAGER; let it;

go to the Debian folder; open 32bit or 64bit depending on which you have installed.....

....now the action............. install the drivers ......

.........first install the [COLOR="Red"]common driver[/COLOR] (cndrvcups-common.deb)...........and [COLOR="Red"]then the capt driver[/COLOR] (cndrvcups-capt.deb).....***make sure you do it in that order***

2) [COLOR="SeaGreen"]tell the system where to find the necessary bits[/COLOR]:

which for you would be

**[COLOR="Green"]Register the printer[/COLOR]**

    > [COLOR="Red"]sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]



............................in Ubuntu 12.04 it is said ........"Ubuntu 12.04 has again blacklisted the usblp module"..........I didn't find this to be so with Mint, so my printer works by ignoring this ubuntu-specific advice...........



In post #4 of this thread

[http://ubuntuforums.org/showthread.php?t=1982917](http://ubuntuforums.org/showthread.php?t=1982917)

Sivella, who is very good on the LBP continues the story that I have described above:

3) [COLOR="Green"]**Register the printer with ccpd daemon**[/COLOR]:

    > [COLOR="Red"]sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0[/COLOR]



4) [COLOR="Green"]**Start ccpd daemon**[/COLOR]:

    > [COLOR="Red"]sudo /etc/init.d/ccpd start[/COLOR]



[COLOR="Green"]**Test install:**[/COLOR]

    > [COLOR="Red"]captstatusui -P LBP2900[/COLOR]



will open the Statusmonitor window. If the message "[COLOR="Blue"]Ready to print[/COLOR]" is displayed --> [COLOR="Blue"]all is OK[/COLOR].

[COLOR="Green"]**Try to print something**[/COLOR].

a) I have tried to put in quotes all the things you should copy and paste into a terminal............. you know how to open a terminal ?? ...... I use the menu command in the terminal as copy-c etc does not work in a terminal............

b) if you get printing, as above; [B][COLOR="Magenta"]you need to automate the process: Sivella tells how in post #6 of the thread above
[/COLOR][/B]
have a read through it; please post back for help if it all looks tricky; I can try to help you through it

---

### Post by jaimohan on 2012-11-01
Thank you Pdc for your elaborate reply. I followed your advise and did the following things.

[LIST=1]
[*]Removed the existing raducotescu drivers
[*]downloaded the gz file from canon
[*]opened the gz with archive manager
[*]installed the common and cups debs in that order
[*]connected the printer
[*]registered the printer as suggested
[*]ccpd start
[*]checked the status
[/LIST]

When checked the status it did open the status window, but there was no message. It was blank. what to do now?

by the by, went thru seville's post. Think the instructions given are manageable, even if i do not understand many of them. But i have to reach that stage.

pl help..

---

### Post by pdc on 2012-11-01
> but there was no message. It was blank. what to do now?


did you try 

> Try to print something.

---

### Post by jaimohan on 2012-11-02
> Try to print something.

Yes..I tried to print a file from the text editor. Incidentally, the setup has created another printer "LBP2900-2" and has marked it as default printer. Initially, I tried printing keeping this as the default printer. Since the printing did not work out, I changed the default printer to "LBP2900" (did not delete the other printer) and tried printing again. In both cases, it shows that the job is being processed. Meanwhile, the "captstatusui -P LBP2900" command from terminal after passing the file to print still displays the status window blank.

what to do now?

---

