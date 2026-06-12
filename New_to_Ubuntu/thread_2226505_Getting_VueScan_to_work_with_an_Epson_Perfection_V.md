---
title: "Getting VueScan to work with an Epson Perfection V700 on 14.04 Trusty using Firewire"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by Digital_Man on 2014-05-27
[FONT=verdana]Well, it's been a long day, but I've made great progress in getting VueScan to work with an Epson Perfection V700 on 14.04 using Firewire, but I still have one lingering issue.

For starters in terminal I typed:[/FONT][SIZE=3]
[/SIZE][FONT=courier new]sudo sane-find-scanner[/FONT]

[FONT=verdana]sane recognized my scanner and came back with:[/FONT]
[FONT=courier new]found SCSI processor "EPSON GT-X900 1.07" at /dev/sgX[/FONT]

[SIZE=2][FONT=verdana]In my case, sgX is sg6 but your machine could give you a different number.

Then it was just a question of permissions. So, I went with:[/FONT][/SIZE]
[COLOR=#000000][FONT=Helvetica][FONT=courier new]sudo chmod ugo+r /dev/sg6
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Helvetica][FONT=courier new]sudo chmod ugo+w /dev/sg6[/FONT][SIZE=3]

[/SIZE][FONT=verdana]Then once again in terminal:[/FONT][SIZE=3]
[/SIZE][COLOR=#000000][FONT=Helvetica][FONT=courier new]scanimage -L[/FONT][/FONT][/COLOR][SIZE=3][COLOR=#000000][FONT=Helvetica]

[/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Helvetica]And that came back with:[/FONT][/COLOR][SIZE=3][COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Helvetica][FONT=courier new]device `epson2:/dev/sg6' is a Epson GT-X900 flatbed scanner[/FONT][/FONT][/COLOR][SIZE=3][COLOR=#000000][FONT=Helvetica]

[/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Helvetica]Again, fantastic. So, after that, I open VueScan and it is recognizing the v700 and making some truly gorgeous scans.

The one lingering issue is that VueScan does not remember this if the computer is shutdown or restarted.[/FONT][/COLOR] I have to go through the above steps again. What is it that I need to do in order to get VueScan to retain the settings forever?
[SIZE=3]
[/SIZE][/FONT][/COLOR]

---

### Post by cariboo on 2014-05-28
My scanner isn't supported by Vuescan, so I cant try it out, but does it create a configuration file in /etc. or any other directory?

---

### Post by Digital_Man on 2014-05-28
There's certainly a file in /etc/sane/epson.conf

I should say  that if the scanner itself is turned off, that also triggers the need to  go through all the steps again. In the scheme of things, I don't mind  doing that, but it just seems that there must be a way to make Ubuntu  remember the permissions.

---

### Post by rbmorse on 2014-05-31
Is your user a member of the scanner group?

---

### Post by Digital_Man on 2014-05-31
That's an excellent question/idea.
My user was not a member of the scanner group, but I just added him in response to your posting.
Alas, the problem persists.... but thank you.

---

### Post by bobblex on 2014-05-31
I wonder why you are even using sane or trying to configure sane?

I installed downloaded and installed VueScan following the instructions on the VueScan site and VueScan runs just fine with my Microtek i800.  I didn't do anything at all to sane.  My Microtek scanner, however, is connected via USB, not Firewire.

---

### Post by Digital_Man on 2014-05-31
I also have a Nikon CoolScan 4000 which I use with VueScan on my system. That is simply "plug and play" and works beautifully via Firewire without SANE or any further adjustments.

But per the instructions on the VueScan site, the Epson Perfection v700 does require adjustments:
[http://www.hamrick.com/vuescan/epson_perfection_v700.html](http://www.hamrick.com/vuescan/epson_perfection_v700.html)
> [COLOR=#333333][FONT=Helvetica Neue]You can use this scanner on Mac OS X and Linux without installing any other software.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]
On Linux, you need to [set up libusb device protections]("http://www.freecolormanagement.com/sane/libusb.html").[/FONT][/COLOR]

Though I perhaps naively tried, the Epson Perfection v700 does not "plug and play" with Ubuntu and VueScan.

Since I need to use Firewire and not USB, I searched the site that the VueScan instructions point to and arrived here:
[http://www.freecolormanagement.com/sane/ieee1394.html](http://www.freecolormanagement.com/sane/ieee1394.html)

Those instructions are quite old, but it seems that SANE is necessary, and I have been able to get as far as [my first post in this thread]("http://ubuntuforums.org/showthread.php?t=2226505&p=13034658#post13034658") in getting everything to work. The only missing piece with my setup is getting my computer to retain the settings after it or the scanner have been turned off and then on again.

But by all means, if there is some easier way to make my Epson Perfection v700 work with Ubuntu 14.04 using VueScan 9.4.32, then I would welcome hearing about it.

---

