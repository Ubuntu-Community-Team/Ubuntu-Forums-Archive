---
title: "printer not working after update"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by lila on 2012-09-08
Hello,
I've just updated my computer to ubuntu 12.04 (it was working fine under 10.something, but the update programme insisted).  
Everything is fine, I'm getting used to the new environment, EXCEPT the printer isn't working.  It is there, the computer recognises the model (Canon MP520), but it says "sending data" and "printer inactive".  I've tried searching, but can't find this problem in any other thread.  Any ideas?
Thanks for your help! When I logged in, I was told that my last connection was on May 27th, 2010.  That means I've been turning 2,5 years under ubuntu without any problem whatsoever, both for my business and privatly.  That's pretty good going!:KS
Thanks to all those developers out there!  You people rock!
lila

---

### Post by anewguy on 2012-09-08
Well, I haven't used this as I don't have your printer, but I did find this link.  It is a private private source and not through the repositories, but here is the link:

[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html]("http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html")

---

### Post by lila on 2012-09-08
Hello,
I've just tried that iheartubuntu link.  It doesn't seem to want to install.  On the upside, I found the terminal...:lolflag:

Open for other suggestions!

lila

---

### Post by anewguy on 2012-09-08
I'll have to do some more scanning of the net and see if something pops up.

Glad you found terminal! ;)

---

### Post by ixtok on 2012-09-08
You can find the drivers for your printer at the Canon-Asia web site.

---

### Post by BicyclerBoy on 2012-09-08
A much easier way is to use a ppa.
Some canon sites only have rpm & some have deb..
When 12.04 was released (& months later) the canon rpm packages would not install because of dependency problems with libpopt package.

[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

You would prob need to install & use synaptic package manager to add this ppa as "software centre" is a bit too dumbed down. 
Synaptic makes it easy to select the correct package for your printer (from the ppa) & the scanner driver (scangearmp) .

---

### Post by anewguy on 2012-09-09
I think that's what the thread I posted was doing.

---

### Post by lila on 2012-09-09
Hello again,

I've tried those lines.  The canon asia website has the install problems mentioned above.
I've retried the micael gruz repository.  During the update stage, I get this error: 

W: Impossible de récupérer [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Impossible de récupérer [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.

(sorry it's in French - the last paragraph says : the down load of some files failed, they were ignored or the old ones were used in their place.  The first two paragrphs detail those files)

I'll now try again to run the actual driver install.  Will post what I get in a bit.

:popcorn: lila

---

### Post by anewguy on 2012-09-09
Hopefully, by > I'll now try again to run the actual driver install. Will post what I get in a bit. 

you don't mean the Windows driver - that won't install and it won't work.

---

### Post by lila on 2012-09-09
Nope, that's not working.  I tried using synaptic (thanks for the scangear hint as well).  It has installed the packeges.  It's just not printing...:(  
And I do need to urgently print out a document (it was due Friday...).

If all else fails, I'll need to e-mail it to a friend with a working printer.  But that would delay another day at least, due to working hours and all...  So any help in the next hour or so (before I have to go to bed if I want to be able to face myself in the mirror tomorrow...) would be really welcome!
Thanks for all your efforts!
lila

---

### Post by lila on 2012-09-09
> **anewguy said:**
> Hopefully, by 

you don't mean the Windows driver - that won't install and it won't work.

... 'course not.  I don't think I even have that.  I always chuck out those CDs that come with things...;)

---

### Post by lila on 2012-09-10
Hello,
I'm still no further with this.  
Anyone else any ideas?
lila

---

### Post by BicyclerBoy on 2012-09-10
The ppa I provided is not the same as the one you used...

The old michael-gruz ppa does not work in precise (YMMV)..

2 solutions:
- Hack the old ppa definition to use 11.10 packages (was working).. 
- use the new ppa

[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

That ppa is up-to-date..

---

### Post by lila on 2012-09-14
Thanks Bicycler Boy. I did use that ppa you gave, and I just re-checked.  I re-did the whole process, terminal told me it chaged nothing on existing packages. 
Then with synaptic I installed all the drivers for the MP series (not just the 520), just to be sure.  It still doesn't work.  
Getting increasingly desperate... I'm running a small business and need the printer...

Any other ideas?

lila

---

### Post by BicyclerBoy on 2012-09-14
So synaptic shows you have packages installed from michael-gruzs ppa?
You should something **similar** to attached pic with the addition of scangear*.

Maybe you need to open "printers/printing" & remove the installed printer & then click/run add printer again..
Possible you need to reboot with printer disconnected..

---

### Post by bayouoldguy on 2012-09-14
I had a problem after the upgrade to 12.04.1, could not get my Canon MP500 to print. Similar response. I had earlier established printing using a USB stick test run of the upgrade version. My system installed the CUPS printer driver way back on 10.04 LTS & has used that driver here. I had to Re-install the CUPS driver using Synaptic, then a sub-menu opened up to allow me to select the MP500. Look into if you are using the correct driver.....good luck...."G"


[ATTACH]224146[/ATTACH]

---

### Post by BicyclerBoy on 2012-09-14
@bayouoldguy
Yours is not the CUPS printer driver but rather a driver from the gutenprint open source printer driver project.

The Michael Gruzs ppa is a driver from the (partly?) open source Canon printer/scanner driver.

Both use CUPS.

The Canon drivers (print/scan) work very well. (mp272).

---

### Post by bayouoldguy on 2012-09-15
I stand corrected....thanks...."G"

---

### Post by BicyclerBoy on 2012-09-15
Guess nobody is that bothered what the drivers are called anyway, if they work.

The OP might have thought they needed both..
The gutenprint stuff never worked for mp272 on my PC running 11.04.

---

### Post by pdc on 2012-09-15
lila: help us to be clear what you have done ...

...if I were starting from the beginning, ..

I would go here

[http://support-sg.canon-asia.com/contents/SG/EN/0100083403.html](http://support-sg.canon-asia.com/contents/SG/EN/0100083403.html)

and download and install the common driver first..

....then I would go here ...

[http://support-sg.canon-asia.com/contents/SG/EN/0100083901.html](http://support-sg.canon-asia.com/contents/SG/EN/0100083901.html)

and install the MP520 driver

........they are both .deb packages

can you show us a screenshot from synaptic of your cnij installations?

I enclose one of mine: I have the MG3160 canon printer that works fine

---

### Post by lila on 2012-09-18
Hi guys,

thanks so much!  I never got round to looking again the last few days, just working too much...

I do not know how to do a screenshot, and right now don't feel like learning it....
But according to synaptic I have installed:
cnijfilter-mp520series  3.70.1-0~23~precis 
and also
cnijfilter-common of the same version.

I have rebooted several times with and without disconnecting the printer.  I've also tried the printer on our newly aquired laptop that had 12.04 pre-installed (from a very nice computer shop in Paris, they are ubuntu-specialists).  I get the same problem there.  We hadn't tried that yet, as we hadn't tried to print with that laptop.

It's getting late right now, but I'll see tomorrow, if installing the drivers on the laptop will work - in that case on this one I would need to uninstall and re-install the printer (on the laptop it has never been installed).
Else I'll take another look at those canon-asia websites.

I'll report back tomorrow!!
lila

---

### Post by bayouoldguy on 2012-09-18
lila, sad to hear your MP520 printer problem. Way back in Ubuntu  10.04 LTS I could only get my MP500 working by using the gutenprint driver, etc., for better or worse. I was only to get it working in Ubuntu 12.04.1 by updating the driver & reinstalling it, I am sending screenshots of what is shown installed on my Dell D620 laptop. You may want to make a list of the "cups" & drivers & install them  just to see if your printer will wake up. You may have to uninstall existing drivers first...then if cups does not work, remove &start over.....good luck...."G"
[ATTACH]224344[/ATTACH]
[ATTACH]224345[/ATTACH]

---

### Post by pdc on 2012-09-18
bonjour lila, mon brave ami!

I would suggest deleting the cnij.......drivers you have already installed;

.....using synaptic .........also called package manager........

then start afresh.........

......go to ..

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083403.html)

and download this IJ Printer Driver Ver. 2.80 for Linux(debian **_Common package_**)...

.if gdebi jumps and offers to install.......let it do so..

now go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083901.html)

IJ Printer Driver Ver. 2.80 for Linux(**debian Package for the MP520 series**)

again, let gdebi install............

that should be it......

c'est pas tres difficile pour vous? peut-etre facile je pense........

---

### Post by lila on 2012-09-19
Hi guys,
I'm getting there!  This is written on my laptop.  When I turned it on, it wanted an insane amount of updates (we normally use it ounconnected to the internet).  I ran them, it took almost an hour.  Some of them had "cups" in the name, so that gave me hope.
I then installed the printer, it asked a few questions as to what I wanted to call the printer and if I wanted the default driver choice (yes).  And it just printed me a beatifully colouful testpage!

Now I'll try to uninstall and reinstall everything on the desktop.  See you in a bit (we use a wired connection and have only one cable for that, so while I run things like updates on one computer, I can't follow the forum at the same time on the other one).

lila

---

### Post by lila on 2012-09-19
Yes! :p

The printer works on both computers!

What finally did it on the computer that I originally posted about: 

1. I uninstalled the cnijfilters using synaptic.  
2. I uninstalled the printer through "paramètres système" (the red icon with the cogwheel and the spanner on it, I don't know its English name) --> printers
3. reinstalled the printer in the same program. (Just needed to click uninstall and reinstall, followed by a few very simple verifications.)

... I don't know if that would have done it from the start, because here as well I just received a bunch of updates with "cups" in them.  It will remain a mystery, I guess.

So, thank you all a lot!
... I can print out some invoice forms now.  It's all full well working a lot, but I was running out of invoices to bill my customers... ;)  And a couple of urgent letters as well.

Keep up the good work, you guys are amazing!
lila

---

### Post by pdc on 2012-09-19
bonnes felicitations!

fantastique! 

you can also use it as a scanner:

you need to download ScanGear MP Ver. 1.10 for Linux(debian Common package)

.......from here............

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100084701.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100084701.html)

(naturellement, one installs the above..............)

et apres ca ...ScanGear MP Ver. 1.10 for Linux(debian Package for MP520series) 

........from here.......

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100085001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100085001.html)

and test it works by typing into a terminal

> scangearmp

.........if that is good, and you need a launcher..post back

---

### Post by lila on 2012-09-19
Thanks pdc,

the scanner worked before the update, and I was hoping... so I just tried putting in a document and scanning it.  It works.  It even has scangear and x-sane an another program that come up to choose from.  No need to install anything.

btw., I live in France, but I'm German.  And I've lived in France a lot less long (6 years) than I lived in England (11 years, before moving to France).  So, no need to translate for me... but thanks anyway!;)  The only time I get lost is with program names and other computer terms being translated for the French version.  I have learned that the easiest thing is to memorize the icon - except when you are searching for something, in which case you need to know the name or at least the first letter.  AND I've just figuerd out why I found synaptic so much less useful than I used to:  I need to put in the search terms in French!  :lolflag:  I was still doing it in English...
I would be very much in favour of bi- or tri-lingual computers!

Lila

---

### Post by BicyclerBoy on 2012-09-19
Altho I applaud Cannon for providing packages for linux & very good build instructions..
I won't advise people to go outside of package management system unless absolutely necessary & they understand the risks/problems/errors.
But each to their own..

The Canon supplied printer drivers were at version 3.2 Jan 2012 (from Aus or NZ sites).
The previous posted links were to version 2.8.
I would be surprised if they install on 64 bit 12.04..
Each countries Canon website seems to have diff versions/selections & some have rpm & some have debs but all seem to be 32 bit.

YMMV But I found problems with converting 64 bit rpm to deb  (12.04) & the 32 bit deb package would not install on 64bit 12.04.
Problems were incompatible libpopt & incompatible multi-arch support.

The Michael Gruz ppa is the latest Canon source "ubuntuized" so it works with the current Ubuntu distro. You can **not** state the same for external debs & rpm packages especially old ones...

---

