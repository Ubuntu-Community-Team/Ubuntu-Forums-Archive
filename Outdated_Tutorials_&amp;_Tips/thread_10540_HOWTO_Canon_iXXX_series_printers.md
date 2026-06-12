---
title: "HOWTO: Canon iXXX series printers"
date: 2005-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by punkass on 2005-01-09
For anyone who has a Canon i550 or similar.

Steps to get your printer up and running...and printing nicely.

1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
    (they cover i550, i560, i850,i860,i950, i990)

    You need:
    bjfilterpixusXXXi-X.X-X.i386.rpm 
    AND the corresponding cups driver:
    bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
    $ sudo alien <rpm package>

3. $dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
    $dpkg -i bjfiltercups-X.X-X.i386.deb

4. $apt-get install libtiff3g
    $apt-get install libpng2

5. Then use the gnome gui for adding a new printer
     System > System Settings > Printing
     And you will now see your new driver in the list as PIXUS XXXi verX.X

6. And thats it,  happy high quality printing from your canon.

**Update:**

Well I just tried this on my laptop with Feisty and the drivers still work fine.
Step 4 has to be changed to libtiff4 and libpng3 but other than that, everything should work.

---

### Post by drmagoo on 2005-01-10
Thanks for the how-to. Which repository/where can I find libtiff3g?
apt-get yields:  E: Couldn't find package libtiff3g

magoo

---

### Post by punkass on 2005-01-10
no prob.

libtiff3g is in the universe repository, on a side note i am using hoary, but since libtiff3g is an old package it should be there for warty to.

hope that helps.

---

### Post by landotter on 2005-03-11
I have drivers for the following printers, send me a personal msg if you need me to email you one. :)

Brother_HL1250.ppd    Canon_S330.ppd             Epson_StylusPhoto950.ppd
Brother_HL1270N.ppd   Canon_S400.ppd             Epson_StylusPhoto960.ppd
Brother_HL1450.ppd    Canon_S4500.ppd            Epson_StylusPhotoEX.ppd
Brother_HL1470N.ppd   Canon_S450.ppd             Epson_StylusPhoto.ppd
Brother_HL1650.ppd    Canon_S500.ppd             Epson_StylusPhotoR200.ppd
Brother_HL1670N.ppd   Canon_S520.ppd             Epson_StylusPhotoR300.ppd
Brother_HL1850.ppd    Canon_S530.ppd             Epson_StylusPro.ppd
Brother_HL1870N.ppd   Canon_S600.ppd             Epson_StylusProXL.ppd
Brother_HL5140.ppd    Canon_S6300.ppd            HP_ColorLaserJet4500.ppd
Brother_HL5150D.ppd   Canon_S630.ppd             HP_ColorLaserJet5.ppd
Brother_HL5170DN.ppd  Canon_S750.ppd             HP_ColorLaserJet8500.ppd
Brother_HL6050.ppd    Canon_S800.ppd             HP_DeskJet112xC.ppd
Brother_HL7050.ppd    Canon_S820.ppd             HP_DeskJet122xC.ppd
Brother_HL8050.ppd    Canon_S830.ppd             HP_DeskJet2500C.ppd
Canon_BJ30.ppd        Canon_S9000.ppd            HP_DeskJet381x.ppd
Canon_BJC1000.ppd     Canon_S900.ppd             HP_DeskJet382x.ppd
Canon_BJC150.ppd      Epson_StylusC20UX.ppd      HP_DeskJet500C.ppd
Canon_BJC2000.ppd     Epson_StylusC40UX.ppd      HP_DeskJet515x.ppd
Canon_BJC2100.ppd     Epson_StylusC42.ppd        HP_DeskJet550C.ppd
Canon_BJC210.ppd      Epson_StylusC44.ppd        HP_DeskJet555x.ppd
Canon_BJC240.ppd      Epson_StylusC60.ppd        HP_DeskJet565x.ppd
Canon_BJC250.ppd      Epson_StylusC62.ppd        HP_DeskJet585x.ppd
Canon_BJC3000.ppd     Epson_StylusC64.ppd        HP_DeskJet600C.ppd
Canon_BJC4000.ppd     Epson_StylusC70.ppd        HP_DeskJet612x.ppd
Canon_BJC4100.ppd     Epson_StylusC80.ppd        HP_DeskJet6xxC.ppd
Canon_BJC4200.ppd     Epson_StylusC82.ppd        HP_DeskJet81xC.ppd
Canon_BJC4300.ppd     Epson_StylusC84.ppd        HP_DeskJet82xC.ppd
Canon_BJC4400.ppd     Epson_StylusColor1160.ppd  HP_DeskJet83xC.ppd
Canon_BJC4550.ppd     Epson_StylusColor1520.ppd  HP_DeskJet84xC.ppd
Canon_BJC4650.ppd     Epson_StylusColor200.ppd   HP_DeskJet850C.ppd
Canon_BJC6000.ppd     Epson_StylusColor3000.ppd  HP_DeskJet870C.ppd
Canon_BJC600.ppd      Epson_StylusColor400.ppd   HP_DeskJet88xC.ppd
Canon_BJC6100.ppd     Epson_StylusColor440.ppd   HP_DeskJet890C.ppd
Canon_BJC610.ppd      Epson_StylusColor460.ppd   HP_DeskJet895C.ppd
Canon_BJC6200.ppd     Epson_StylusColor480.ppd   HP_DeskJet92xC.ppd
Canon_BJC620.ppd      Epson_StylusColor500.ppd   HP_DeskJet93xC.ppd
Canon_BJC6500.ppd     Epson_StylusColor580.ppd   HP_DeskJet94xC.ppd
Canon_BJC7000.ppd     Epson_StylusColor600.ppd   HP_DeskJet95xC.ppd
Canon_BJC70.ppd       Epson_StylusColor640.ppd   HP_DeskJet96xC.ppd
Canon_BJC7100.ppd     Epson_StylusColor660.ppd   HP_DeskJet97xC.ppd
Canon_BJC800.ppd      Epson_StylusColor670.ppd   HP_DeskJet98xC.ppd
Canon_BJC8200.ppd     Epson_StylusColor680.ppd   HP_DeskJet99xC.ppd
Canon_BJC8500.ppd     Epson_StylusColor740.ppd   HP_DeskJet.ppd
Canon_BJC85.ppd       Epson_StylusColor760.ppd   HP_LaserJet1100.ppd
Canon_i250.ppd        Epson_StylusColor777.ppd   HP_LaserJet1200.ppd
Canon_i320.ppd        Epson_StylusColor800.ppd   HP_LaserJet1300.ppd
Canon_i350.ppd        Epson_StylusColor850.ppd   HP_LaserJet2100.ppd
Canon_i450.ppd        Epson_StylusColor860.ppd   HP_LaserJet2200.ppd
Canon_i455.ppd        Epson_StylusColor880.ppd   HP_LaserJet2300.ppd
Canon_i470D.ppd       Epson_StylusColor900.ppd   HP_LaserJet3.ppd
Canon_i475D.ppd       Epson_StylusColor980.ppd   HP_LaserJet4000.ppd
Canon_i550.ppd        Epson_StylusColorII.ppd    HP_LaserJet4100.ppd
Canon_i560.ppd        Epson_StylusColorIIs.ppd   HP_LaserJet4200.ppd
Canon_i6500.ppd       Epson_StylusColor.ppd      HP_LaserJet4L.ppd
Canon_i70.ppd         Epson_StylusPhoto1200.ppd  HP_LaserJet4plus.ppd
Canon_i80.ppd         Epson_StylusPhoto1270.ppd  HP_LaserJet4.ppd
Canon_i850.ppd        Epson_StylusPhoto1280.ppd  HP_LaserJet4Si.ppd
Canon_i860.ppd        Epson_StylusPhoto1290.ppd  HP_LaserJet4V.ppd
Canon_i865.ppd        Epson_StylusPhoto2100.ppd  HP_LaserJet5000.ppd
Canon_i905D.ppd       Epson_StylusPhoto2200.ppd  HP_LaserJet5100.ppd
Canon_i9100.ppd       Epson_StylusPhoto700.ppd   HP_LaserJet5.ppd
Canon_i950.ppd        Epson_StylusPhoto750.ppd   HP_LaserJet5Si.ppd
Canon_i960.ppd        Epson_StylusPhoto790.ppd   HP_LaserJet6.ppd
Canon_i965.ppd        Epson_StylusPhoto810.ppd   HP_LaserJet8000.ppd
Canon_i9900.ppd       Epson_StylusPhoto820.ppd   HP_LaserJet8100.ppd
Canon_i990.ppd        Epson_StylusPhoto830.ppd   HP_PhotoSmart1000.ppd
Canon_i9950.ppd       Epson_StylusPhoto870.ppd   HP_PhotoSmart11xx.ppd
Canon_MP360.ppd       Epson_StylusPhoto875.ppd   HP_PhotoSmart12xx.ppd
Canon_MP370.ppd       Epson_StylusPhoto890.ppd   HP_PhotoSmart13xx.ppd
Canon_MP390.ppd       Epson_StylusPhoto895.ppd   HP_PhotoSmart71xx.ppd
Canon_S100.ppd        Epson_StylusPhoto900.ppd   HP_PhotoSmart73xx.ppd
Canon_S200.ppd        Epson_StylusPhoto915.ppd   HP_PhotoSmart75xx.ppd
Canon_S300.ppd        Epson_StylusPhoto925.ppd

---

### Post by neshaug on 2005-04-12
I`ve done everything you said and everything worked out without any errors. The only problem is that the driver does not get listed... Neither can I find the ppd or ppd.gz file for it.

---

### Post by kuleali on 2005-04-12
Thank's this helped .

---

### Post by krash on 2005-04-18
Will this work when the printer is shared on a Windows machine?
I got the thing installed and the PIXUS-560i is there and ready in the printers config, but nothing happens when I print.

---

### Post by Toddy on 2005-04-18
It works just fine shared from a windows machine.  I just recently setup my Canon i850 following these how to instructions.  I created a Windows SMB network printer in System - Administration - Printing.  Did a Test Page, and voila!

---

### Post by azumi on 2005-04-19
where i should find driver for canon i550

url: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/) is down :(  ](*,) 

THX !

---

### Post by Turin Turambar on 2005-04-19
Most of Canon iXXX is not supported.... Turboprint 1.89 does the job perfectly... Try tornetting a bit....

---

### Post by echoz on 2005-04-26
I managed to get the driver to install and list.

Now the problem is that the print job doesn't seem to reach the printer at all.

The Status of the printer keeps on repeating that the printer is not connected, despite the fact that lsusb shows that the device is connected.

Any ideas?

btw, i'm using hoary.

---

### Post by echoz on 2005-04-26
Used the suggested BJC-7000 drivers and it work fine.

Would love to use the native canon drivers though.

---

### Post by pelikan on 2005-04-27
[QUOTE=echoz]Used the suggested BJC-7000 drivers and it work fine.

Would love to use the native canon drivers though.[/QUOTE]

Thanks for mentioning this. This guide didn't work for me. But I tried the BJC-7000 drivers on my i850 and they worked!

---

### Post by Seth on 2005-04-27
[QUOTE=pelikan]Thanks for mentioning this. This guide didn't work for me. But I tried the BJC-7000 drivers on my i850 and they worked![/QUOTE]
 I too use the 7000 drivers for my i560. Works fine.

---

### Post by manxego on 2005-04-27
Could you send me Canon-i560.ppd driver please? 
[email]manxego@gmail.com[/email]     ](*,)

---

### Post by woland on 2005-04-27
I have i550
At first I struggled to intall the pixus driver (i550), followed the guide but at the end the driver wanst listed. I tried again the next day and the list refreshed, so I was able to install it with this driver. The test page worked out fine, but most of the programs wouldn't print, including xpdf firefox thunderbird and so, ooo would print in A5 setting and be stuck there. The only programs that would print are kpdf (intalled it becouse of this bug) and gedit. 
Changed it to bjc7000 and it works fine for all the listed programs, at least for now.

---

### Post by vague- on 2005-04-28
[QUOTE=Seth]I too use the 7000 drivers for my i560. Works fine.[/QUOTE]

Which set of BJC-7000 drivers do you use?  (I appear to have two).  The GimpPrint version seems to print very aliased, the other without using black whenever it uses another colour.  That is printing from Firefox (1.0.2).

---

### Post by godot67 on 2005-04-28
krash, echoz > try to run: bjfilterpixusXXXi (from command line) and see if you get an error message.
If you get something like this : "bjfilterpixus860i: error while loading shared libraries: libcnbpcmcm187.so: cannot open shared object file: No such file or directory" then update your system by typing "ldconfig" as root

---

### Post by echoz on 2005-04-28
[QUOTE=godot67]krash, echoz > try to run: bjfilterpixusXXXi (from command line) and see if you get an error message.
If you get something like this : "bjfilterpixus860i: error while loading shared libraries: libcnbpcmcm187.so: cannot open shared object file: No such file or directory" then update your system by typing "ldconfig" as root[/QUOTE]
 I got the following.

```

BJLSTART
ControlMode=Common
SetTime=20050429094207
BJLEND


```

---

### Post by godot67 on 2005-04-29
[QUOTE=echoz]I got the following.

```

BJLSTART
ControlMode=Common
SetTime=20050429094207
BJLEND


```[/QUOTE]
 I'm not at home, so I can't check, but I think I get something similar, which means your problem  is probably elsewhere.

Before installing the pixus driver, I had the BJC 8200 driver working for my i865 (but when I printed, the position on the page was not that good). You can compare this one to the BJC 7000. Don't sure it's better, just in case.

---

### Post by Seth on 2005-04-29
[QUOTE=vague-]Which set of BJC-7000 drivers do you use?  (I appear to have two).  The GimpPrint version seems to print very aliased, the other without using black whenever it uses another colour.  That is printing from Firefox (1.0.2).[/QUOTE]
 The gimp-print ones seem to work fine for me.

---

### Post by Maikel on 2005-05-07
I set up my i550 as you told me to do with with little Howto at the beginning of this thread.
It works, but my problem so far is that i can't print in black.

Someone with the same problem?

---

### Post by wasynyt on 2005-05-08
Have to just say thank you...

you erased my last reason to use windoss for anything

---

### Post by vague- on 2005-05-13
I had a similar issue with nothing happening, until I started reading around in other HOWTOs.  It seems, as noted in [http://www.teaser.fr/~amajorel/howto/CANON-I850-CUPS](http://www.teaser.fr/~amajorel/howto/CANON-I850-CUPS), that you need to use the "-c" option to Alien when dealing with the file with the printer name in.  Mine worked fine after that.  I did find that link on these forums for a Canon i860 topic (I think it was i860), so thanks to whoever that was.

**EDIT:**  Since it was not mentioned in the first post, and in case other people have the same issue.  I had to restart CUPS before the drivers showed up in the printer configuration program.  I did this with:

```
$ sudo /etc/init.d/cupsys restart
```

---

### Post by ferrill on 2005-05-15
I got it working very well here is what I had to do:

1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
(they cover i550, i560, i850,i860,i950, i990)

You need:
bjfilterpixusXXXi-X.X-X.i386.rpm
AND the corresponding cups driver:
bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
sudo alien -c <rpm package>

3.
dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
dpkg -i bjfiltercups-X.X-X.i386.deb

4.
apt-get install libtiff3g
apt-get install libpng2

5. sudo /etc/init.d/cupsys restart

6. Then remove BJC-7000 driver.  System > System Settings > Printing, right click on the printer and select remove.  If you do not delete other driver referencing the printer when print from an application it will never get sent to the printer.

7. Then use the gnome gui for adding a new printer
System > System Settings > Printing
And you will now see your new driver in the list as PIXUS XXXi verX.X

---

### Post by eyerish on 2005-05-19
many thanks to all. Have an i560 and simply added a new default printer as a bjc7000 and it worked fine. Great coloring.

---

### Post by Ozitraveller on 2005-05-27
Is this similar to Canon i550? I use Bjc-7100 or Bjc-80 if that's any help.

---

### Post by jerrykenny on 2005-06-17
Excellent   !!!!

My canon i550 is now printing a treat !   I'm using it on printer port & cable rather than usb, which probably simplifies matters.

Am I the only only noob who didnt realise Open Office has a separate "Printer Administartion" GUI  ? . . . used to drive me demented by constantly reverting to US letter paper type.  In fact I dont think it would print any Opennoffice-word docs at all.

Fine now 'though.

---

### Post by nalgene on 2005-06-20
thanks for this howto, i can finally print correctly, the old bjc7000 didnt print dark enough however witht he correct driver it works perfectly..

ps

i think the 5. 

sudo /etc/init.d/cupsys restart

needs to be added to front page, i couldnt get it until i read this page...

---

### Post by fsman on 2005-06-20
can you check the ink levels or clean the ink heads with this method? if so how?
I know that turboprint provides this functionality

---

### Post by Jiilik on 2005-06-30
I also got my Canon i560 working using the above instructions.  However, I needed to regenerate the printer listing for the Cups manager in KDE (kubuntu).  To do this, I deleted ~/.kde/share/apps/kdeprint/printerdb_cups.txt and restarted KDE.

---

### Post by javamdk on 2005-07-13
[QUOTE=neshaug]I`ve done everything you said and everything worked out without any errors. The only problem is that the driver does not get listed... Neither can I find the ppd or ppd.gz file for it.[/QUOTE]

You may need to restart cups daemon. You can do this in number of ways, I normally do the following: 
```
sudo killall cupsd <-- terminate cupsd
sudo /user/sbin/cupsd  <-- starts cupsd back

```
Load the Printer GUI and it should show. This will also help refresh your printer if it's connected but CUPS doesn't recognize it.

---

### Post by songzi on 2005-08-07
I've installed my i950 successfully, but have the following problems:
1. I cannot print files with Adobe Reader and i950
2. In OpenOffice Wordprocessor, the default page paper format was set to A5 and cannot be reset to A4.

Any suggestions?  Thanks.

---

### Post by miq on 2005-08-07
With my canon i560 under kubuntu on my USB2 connexion, I've done everything except step 7 but I've done the kde equivalent

Detection is Ok, configuration is OK, but no page test printed, no page printed at all.
I receive the message (on my french system): 

"La page de test a été envoyée correctement à l'imprimante. Patientez jusqu'à ce qu'elle soit complètement imprimée, puis cliquez sur le bouton « OK »"
which can be translated in english ;
"test page has been send to the printer. Wait until it was print, then press « OK »"

No printer reaction.

KJobViewer catch and send the printing, Tells me it's printed.

The first time I try to install my printer, i've had apt-get errors on step 4 :
libtiff3g unknown
libpng2 unknown but proposing me to install a newer libpng10 (something like that)
which i've made. 

I've already corrected this problem and had finally installed libtiff3g and libpng2 with apt-get, and redo all the steps, but always the same problem. 

I've tried to killall cupsd and restart too, same problem.

please help.
MiQ.

---

### Post by SaCeR on 2005-08-11
I have a Canon connected to my windows Machine.. and im jusing the SBM, and enter the windows machine's IP and printer name.. and no login.. 
then i can find the printer driver, after i had installed it.. 
but why i try to print there is nothing printing.. its just in queue on the ubuntu machine.. not on the windows machine.. anyone who knows how to fix that?

---

### Post by ChrisTheGeek on 2005-08-17
I have a Canon i550 and am trying to get it to work with Hoary via the parallel port.

I followed the instructions here and installed the pixus drivers downloading:

- bjfiltercups-2.4-0.i386.rpm
- bjfilterpixus550i-2.2-1.i386

And converting them to debs with alien.  They installed fine and after restarting cups they appeared in the printer list but I only got driver options for  560i, 860i and 990i.  I tried the 560i but it doesn't work (no test page, no printer noises, nothing).

I'm sure I had this working on Warty - I think by using the 7000 driver but this doesn't work on Hoary for me (although I was able to make it print a single blank page before it got confused and hung!)

Any ideas for what I should try next?  Any log files/debug commands I can try? Many thanks in advance.

---

### Post by cmcanulty on 2005-08-21
I have a Canon i350, any drivers available for i? I am new to Ubuntu so need easy directions to follow, thanks

---

### Post by yhan on 2005-10-08
For those who have the problem with OpenOffice, which only want to print with A5 paper, I've found a simple solution. 

Simple follow this 
[INDENT]
sudo vi /usr/share/cups/model/canonpixus550i.ppd
[/INDENT]

*Note that you could use yr favorite text editor instead of vi*

Under the lines

[INDENT]
*DefaultPageSize: A4
*OpenUI *PageSize/Paper Size: PickOne
[/INDENT]
 Cut and paste the definition of the letter paper (or the format you currently use). It has to be the first of the list. 
For letter this is :
[INDENT]
*PageSize letter/Letter: "<</CNPageSizeName(letter)/PageSize[612 792]/ImagingBBox null>>setpagedevice"
[/INDENT]

save and quit vi (esc :wq)


Remove the driver and reinsert it in the printer definitions. 

It will print as a charm in the format you want :) 

I don't know exactly what's going on, but there is a bug with Cups or with OpenOffice, OpenOffice will only choose the first format of the list in the printer driver properties files (.ppd) 

I hope this could help someone !!!

It worked for me. 

Have a good day and good luck 

Yhan

---

### Post by yhan on 2005-10-08
By the way, if someone could tell me how I could get the printer status, it could be nice :) 

I mean by printer status : out of paper, status of the cartridges, cleaning, etc.
All the stuff you have by default with the other commercial popular OS. 

Thanks 

Yhan

---

### Post by crockettoo on 2005-11-04
Following the howto at the top of this thread for my Canon i550 I found libtiff3g not available in Breezy Universe, and despite installing every possible thing in Synaptic containing "libtiff", the test print was slow & faint. 
I downloaded libtiff3g into my Home directory from [here]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fupdates%2Fmain%2Ft%2Ftiff%2Flibtiff3g_3.5.5-7_i386.deb&md5sum=76f340590aa4a0546d810a7e7c7691a8&arch=i386&type=security")
Jan 2006: packages.debian is down so try [here]("http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/t/tiff3g/libtiff3g_3.6.1-2_i386.deb") 

Then in terminal "sudo dpkg -i libtiff3g_3-1.5.5-7_i386.deb" or (Jan 2006) "sudo dpkg -i libtiff3g_3.6.1-2_i386.deb"

... followed the rest of the howto, and it works brilliantly! Thanks !

---

### Post by nalgene on 2005-11-04
[QUOTE=crockettoo]Following the howto at the top of this thread for my Canon i550 I found libtiff3g not available in Breezy Universe, and despite installing every possible thing in Synaptic containing "libtiff", the test print was slow & faint. 
I downloaded libtiff3g into my Home directory from [here]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fupdates%2Fmain%2Ft%2Ftiff%2Flibtiff3g_3.5.5-7_i386.deb&md5sum=76f340590aa4a0546d810a7e7c7691a8&arch=i386&type=security") 

Then in terminal "sudo dpkg -i libtiff3g_3-1.5.5-7_i386.deb"

... followed the rest of the howto, and it works brilliantly! Thanks ![/QUOTE]
Thank you for this, i was able to get my printer running again, buy installing libtiff manually..

is there a way to allign, i think the allignment on printer is off

---

### Post by crockettoo on 2005-11-05
You could check the default paper type matches your paper size.

Right click your printer in System...Administration...Printing, pick the Paper tab and choose correct paper.

HTH

---

### Post by Georgie-o on 2005-11-08
I'm trying to get this to work with no success.  I installed alien and donwloaded the two files (drivers)  Am I supposed to "unpack" them in some way before using alien?


This is what I got:

$ sudo alien bjfilterpixus860i-2.4-0.i386.rpm
File "bjfilterpixus860i-2.4-0.i386.rpm" not found.


It seems strange that its not found when it's sitting on my desktop...  
I copied the file title by selecting Properties and copying it from the file name cell.

Any thoughts that a newb could follow?

---

### Post by crockettoo on 2005-11-09
You need to change directory to your desktop (>CD Desktop *note folder names are case sensitive*), or move the file to your home directory, or spell out the path to the file in full. For some reason the Desktop subdirectory is not in the default path.

---

### Post by yabbadabbadont on 2005-11-09
Has anyone gotten an i900D to work nicely?

I can get it to work with oss drivers, but the output pretty much sucks.

---

### Post by purplefeltangel on 2005-12-23
I have tried everything listed on this thread and still when I send to the printer, it says it is printing but the printer itself does not respond.

Canon i560 -- any help?

---

### Post by Trizik on 2006-01-03
Ubuntu 5.10, Canon i560 shared by a Windows machine

I installed the drivers as instructed by this thread.

When I try to print, the status of my print job says:> Printing: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR:  Connection failed with error NT_STATUS_ACCESS_DENIEDAny idea?

Other Windows machines can access the printer just fine.

---

### Post by joseph20 on 2006-01-08
I am running debian 'etch' but I can't seem to locate the packages for libtiff3g or libpng2.

---

### Post by crockettoo on 2006-01-08
packages.debian is down for some reason.

I managed to find libtiff3g [here]("http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/t/tiff3g/libtiff3g_3.6.1-2_i386.deb")

libpng2 was in Synaptic (Breezy repository) if I remember right.

HTH

---

### Post by legolas on 2006-03-22
Hey guys, I don't know if you have tried this guys drivers but I installed them and the seem to print a whole lot better than the BJ7000!  Give it a whirl.
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus.html)

---

### Post by frogotronic on 2006-05-19
[QUOTE=punkass]For anyone who has a Canon i550 or similar.

Steps to get your printer up and running...and printing nicely.

1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
    (they cover i550, i560, i850,i860,i950, i990)

    You need:
    bjfilterpixusXXXi-X.X-X.i386.rpm 
    AND the corresponding cups driver:
    bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
    $ sudo alien <rpm package>

3. $dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
    $dpkg -i bjfiltercups-X.X-X.i386.deb

4. $apt-get install libtiff3g
    $apt-get install libpng2

5. Then use the gnome gui for adding a new printer
     System > System Settings > Printing
     And you will now see your new driver in the list as PIXUS XXXi verX.X

6. And thats it,  happy high quality printing from your canon.[/QUOTE]

Followed your directions and do not see the driver listed.  Is it under the Canon drivers?  Or in the list of manufacturers?

---

### Post by crockettoo on 2006-05-19
These are the ones you need for the i550:

[ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus550i-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus550i-2.2-1.i386.rpm)
[ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm)

good luck

---

### Post by CameronCalver on 2006-05-19
Can some1 tell me what i type after url the computer i am trying toconnect to ip is 192.168.1.100

---

### Post by frogotronic on 2006-05-20
[QUOTE=crockettoo]These are the ones you need for the i550:

[ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus550i-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus550i-2.2-1.i386.rpm)
[ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm)

good luck[/QUOTE]

Hi,

Yep, had those...after a reboot I can now see them.  I just printed a PDF journal article on my Canon i550.

Thankyou very much for this HOWTO!

CH

---

### Post by frogotronic on 2006-05-20
[QUOTE=CameronCalver]Can some1 tell me what i type after url the computer i am trying toconnect to ip is 192.168.1.100[/QUOTE]

**From the first post:**

For anyone who has a Canon i550 or similar.

Steps to get your printer up and running...and printing nicely.

1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
(they cover i550, i560, i850,i860,i950, i990)

You need:
bjfilterpixusXXXi-X.X-X.i386.rpm
AND the corresponding cups driver:
bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
$ sudo alien <rpm package>

3. $dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
$dpkg -i bjfiltercups-X.X-X.i386.deb

4. $apt-get install libtiff3g
$apt-get install libpng2

5. Then use the gnome gui for adding a new printer
System > System Settings > Printing
And you will now see your new driver in the list as PIXUS XXXi verX.X

6. And thats it, happy high quality printing from your canon.
[B]
And from "Rachael's Blog" on howto print to an XP box:[/B]

[URL="http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/"]http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/
[/URL]
Enable &#8220;Print Services for Unix&#8221; on Windows XP machine and share printer. (I&#8217;m not actually sure that this is necessary, it might be a red herring&#8230;)

When you add the printer in Ubuntu,

   1. Choose &#8220;Network Printer&#8221; and &#8220;Windows Printer (SMB)&#8221;
   2. put your Workgroup in the Host field
   3. Put &#8220;guest@<host>/<printer>&#8221; in the Printer field (replacing <host> and <printer> with your host & printer names)

So, for example, if your Windows machine was called &#8220;Dozer&#8221; and your printer was called &#8220;LaserPrinter&#8221;, you would put &#8220;guest@Dozer/LaserPrinter&#8221;.

You should not need a name and password for the Windows machine for this to work. 

------------------------------------

This worked for me.  Make sure you get the dependencies for the tiff and png libraries.  You can get these via the synaptic package manager, if you're not versed in the apt-get command line fuction.

- CH

---

### Post by VFiend on 2006-06-01
Just in case anyone running Dapper searches the forums for this and is frustrated because the libpng2 and libtiff3g are deprecated (I know I was):

For the i550, the included Canon BJC-7100 Foomatic/bjc800 driver works great.

---

### Post by Ozitraveller on 2006-06-02
[QUOTE=VFiend]Just in case anyone running Dapper searches the forums for this and is frustrated because the libpng2 and libtiff3g are deprecated (I know I was):

For the i550, the included Canon BJC-7100 Foomatic/bjc800 driver works great.[/QUOTE]

Correct, I'm using this too.

---

### Post by Georgie-o on 2006-06-04
Does this BJC 7100 work for the i860 as well?  I've always used the BJC 7000 as recommended in the earlier posts and it does a good job of all regular printing except it _cannot_ print high quality pctures (the color is all off and they look awful).  Does this 7100 do high quality pics as well?

Thanks

---

### Post by aias on 2006-06-05
I followed this process and selected my 860.  However, I can't even print the test page anymore!  worked well in Breezy.  I get a message that a test page has been sent to the printer but nothing happens after that (it used to blink when it received data - doesn't even do that anymore).  can anyone help?

Thank you.

---

### Post by cafn8ed on 2006-06-09
[QUOTE=aias]I followed this process and selected my 860.  However, I can't even print the test page anymore!  worked well in Breezy.[/QUOTE]

I had the same experience.  Following advice given elsewhere about installing png and tiff libraries, and after doing a little reasearch online, I found that there's another png library which is functionally equivalent to libpng.so.2.  Equivalent enough that it got my Canon i860 working again.  Here are the commands you'll need:

First, make sure you're really missing libpng.so.2:

1) ```
ls /usr/lib/libpng.so.2
```

If you see this: "ls: /usr/lib/libpng.so.2: No such file or directory", then proceed.  If ls actually finds the library on your system, you should stop now and go looking for another solution.

2) ```
sudo apt-get install libpng10-0
```
(Ubuntu may say you already have this installed.  That's ok.)

3) ```
sudo ln -s /usr/lib/libpng10.so.0 /usr/lib/libpng.so.2
```

That should do it.  Try printing another page.  In my case, it worked right away, with no need to restart CUPS or anything else.

---

### Post by jabeez on 2006-06-09
Same thing here aias, my printer doesn't respond at all to anything, no matter what driver I select. It says it's online and accepting jobs but when I try to print a test page-----nada. What a joke, just booted back into windows cuz I had to print something and it worked fine, but alas linux always has some stupid nagging little problem that forces me back to XP. I've searched all over for days, and followed instructions on this thread and can see the PIXi550 drivers, but they do nothing. And to the above poster, all I could find is libpng12-0, which is already installed but apparently doing nothing. Sorry for the poor attitude, just a VERY frustrating experience. My specs for anyone with a suggestion......

Kubuntu Dapper (Fresh Install)
Canon I550 (works great in XP

---

### Post by cafn8ed on 2006-06-09
Those are the same symptoms I had before I got the png and tiff libraries installed: The printer seemed to be working, and when I sent a job to it the job would "complete", but the printer never printed anything.  If you already followed the instructions from the beginning of this thread to install the Pixus drivers, and installed the tiff libraries using apt-get, then all that should remain is the png driver.

When you say you can only find libpng12-0, do you mean you can only find that in the repositories (via synaptic, for example)?  You may need to add other repositories to your system to get the old libpng10-0.  Assuming you're using synaptic for this (I like it better than KDE's package manager)...

1) Run Synaptic

2) Click on the "Settings" menu and choose "Repositories"

3) In the popup, turn on all the checkboxes you can find.  You may not need them all, but it's easiest that way.

4) you can do a search for libpng10-0 and install it from synaptic, or you can exit the program and do these two commands:
```
sudo apt-get update
sudo apt-get install libpng10-0
```

Good luck.

---

### Post by bettermentflux on 2006-06-09
I was able to find Libpng 10 here: [http://packages.ubuntulinux.org/breezy/allpackages]("http://packages.ubuntulinux.org/breezy/allpackages")

Hope this helps you. I'll be trying to install my Canon i860 later today and will report on how I do.

---

### Post by cafn8ed on 2006-06-09
If you're using Breezy (Ubuntu 5.whatever), you don't need to follow my extra instructions using libpng10-0.  The libpng2 library is available directly from the repository, so a quick "sudo apt-get install libpng2" should set you up.

It's only when you make the move to Dapper (6.06) that libpng2 becomes unavailable and more extreme measures are required.

---

### Post by jabeez on 2006-06-09
Well I got my printer to print a test page........WHOOOO HOOOOO!!!! The PIXi550 drivers still don't work, but it did work using the BJC7100 foomatic or whatever mentioned earlier in this thread. I did try using Synaptic to find the libpng10, but it only found libpng12. I've got universe/multiverse, and I think most of the repositories enabled, but unfortunately I'm at work now so it'll have to wait. Oh yeah, and to even be able to print anything I had to run that sudo foomatic-cleanupdrivers I found in the forums earlier, sorry I'm not sure that is the exact command but do a search for printing in the Dapper forums and you'll find it. I'll try installing the older libpng later and report back if it works........Cheers!!

---

### Post by mandragor on 2006-06-11
Months ago I used this HOWTO to get my i850 working under Breezy, currently
under Dapper this is a no-go - Like others I am forced to use the BJC-7000 drivers.

---

### Post by mandragor on 2006-06-13
Actually no, after finding a repository for libtiff3g it finally works under Dapper!
I documented the process in my wiki-page, based mainly on this HOWTO and tips 
from cafn8ed - [https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b](https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b)

---

### Post by jdvoracek on 2006-08-26
> **mandragor said:**
> Actually no, after finding a repository for libtiff3g it finally works under Dapper!
I documented the process in my wiki-page, based mainly on this HOWTO and tips 
from cafn8ed - [https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b](https://wiki.ubuntu.com/VidNor#head-e26f314f13dc34158d81849d0662a0ee58a4fc3b):D thank  you so much for documenting this!  i was going nuts trying to find those libraries in order to get my canon i950 working.  cheers - john

---

### Post by jlmckenzie on 2006-10-30
Where do I find Canon iXXX series printer downloads?
I have a Dell 1150 Inspiron LapTop & Canon i560 printer.
My computer had to be reprogrammed recently and now my 
printer does not work. What do I need to do to setup my 
printer again so I can use it?

---

### Post by kr0n1x on 2006-11-05
> **cmcanulty said:**
> I have a Canon i350, any drivers available for i? I am new to Ubuntu so need easy directions to follow, thanks

*
i need this info please..i've a Canon i350:confused:

---

### Post by crockettoo on 2006-11-05
> **jlmckenzie said:**
> Where do I find Canon iXXX series printer downloads?
I have a Dell 1150 Inspiron LapTop & Canon i560 printer.
My computer had to be reprogrammed recently and now my 
printer does not work. What do I need to do to setup my 
printer again so I can use it?

Follow post#1 of this topic and get the i560 drivers from
[ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus560i-2.4-0.i386 rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus560i-2.4-0.i386 rpm)
and [ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.4-0.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.4-0.i386.rpm)
If you get stuck with the libtiff3 dependency, follow post#66.
HTH

---

### Post by crockettoo on 2006-11-05
> **kr0n1x said:**
> *
i need this info please..i've a Canon i350:confused:

You may be out of luck for this one. The Japanese Canon site does not seem to have drivers, and at [http://www.linuxprinting.org/printer_list.cgi?make=Canon](http://www.linuxprinting.org/printer_list.cgi?make=Canon) it is being called a "paperweight". No-one else here at Ubuntuforums seems to have posted a fix either. All I can suggest is try some other similar-named Canon printer drivers (promises to be frustrating) or buy TurboPrint for Linux [http://www.turboprint.info/](http://www.turboprint.info/) which claims to do the job; however at Euro30 you might as well buy a new Linux-capable printer, and sell the i350 to a Windows devotee for a few dollars.
:-?

---

### Post by kr0n1x on 2006-11-05
i've download Turboprint free edition...i'm installing it on ubuntu but the installer answer me: Printer spooler?!?!?!
option avaible:
-LPR(ng)
-CUPS
what i choice for my canon i350? O_o

---

### Post by kr0n1x on 2006-11-05
[SIZE="4"]**HOW TO install a Canon i350 on ubuntu 6.10**[/SIZE]

go to this link: [http://www.turboprint.info/download.html](http://www.turboprint.info/download.html)
fill all fields, and click Download;
now download the latest version of turboprint (.tgz version!)
and follow the instruction in the webpage:
> .tgz Archive
With the TGZ archive you can adjust some installation parameters, e.g. installation path. You will also get a detailed installation protocol. The TGZ archive is required for DEBIAN / UBUNTU Linux or use with LPRng spooler.

Installation: Extract the archive, change to the new created directory and start "./setup" (root login required):
tar -xzf turboprint-1.94-4.tgz
cd turboprint-1.94-4
./setup
UBUNTU:
sudo ./setup

when the setup ask what Printer Spooler to use...select CUPS.
other option i've selected default :) i've printed a TestPage and my Canon i350 WORK!!!

sorry for my bad english, and really thanks to crockettoo ;)

---

### Post by Devi0s on 2006-11-05
This printer does not show up in Edgy.  Edgy detects the i850 printer, but the alien-installed drivers do not show up in the cannon list, and trying to install it as a BJC7004 seems to work, but then the printer doesnt show up...

---

### Post by slimdog360 on 2006-11-05
> **Devi0s said:**
> This printer does not show up in Edgy.  Edgy detects the i850 printer, but the alien-installed drivers do not show up in the cannon list, and trying to install it as a BJC7004 seems to work, but then the printer doesnt show up...

you can try this [http://ubuntuforums.org/showthread.php?t=282096]("http://ubuntuforums.org/showthread.php?t=282096"). I didnt have any luck in edgy but other people have.

---

### Post by shortsellyhoonow on 2006-11-05
DO you know how to install gtkpod?

Thanks.

[email]shortsellyhoonow@yahoo.com[/email]

---

### Post by TurningJpnz on 2006-11-29
I tried to get the Canon drivers installed using the instructions below. I got numerous error messages when using alien to do the conversion. Is it possible to do this on my AMD 64? Is there something else I can try?

The final message was:
> dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)



Instructions:
----------------
> 1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
(they cover i550, i560, i850,i860,i950, i990)

You need:
bjfilterpixusXXXi-X.X-X.i386.rpm
AND the corresponding cups driver:
bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
$ sudo alien <rpm package>

3. $dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
$dpkg -i bjfiltercups-X.X-X.i386.deb

4. $apt-get install libtiff3g
$apt-get install libpng2

5. Then use the gnome gui for adding a new printer
System > System Settings > Printing
And you will now see your new driver in the list as PIXUS XXXi verX.X

6. And thats it, happy high quality printing from your canon.

-------------------

---

### Post by aljaz on 2007-01-01
Here's how it managed to print a test page in edgy 64 on a Canon i865:

1.) I downloaded files:
[LIST]
[*][libcnbj-2.4_0-1_i386.deb]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/libcnbj-2.4_0-1_i386.deb")
[*][bjfilter-2.4_1-2_i386.deb]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/bjfilter-2.4_1-2_i386.deb")
[*][pstocanonbj_3.3-1_i386.deb]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu/pstocanonbj_3.3-1_i386.deb")
[/LIST]

2.) I installed them using dpkg -i --force-architecure
3.) then I installed the printer using Pixma i860 driver from the list of available drivers
3.) did some testing/troubleshooting with cups ([http://127.0.0.1:631](http://127.0.0.1:631)) because the gnome Printing utility would constantly crash on me. However it was a good source of what was wrong. After creating a job the status said: /usr/lib/cups/filter/pstocanonbj failed. I did then go to that directory and said: ./pstocanonbj. It gave me numerous errors about libraries that are missing but were kind of there... Anyway I figured, since it's a i386 package that I should give him the 386 libraries. So on we go. The program asked for:
[LIST]
[*]libcups.so.2 (package: [libcupsys2_1.2.4-2ubuntu3_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fc%2Fcupsys%2Flibcupsys2_1.2.4-2ubuntu3_i386.deb&md5sum=29492c31d2599e9044276cd105a6c63f&arch=i386&type=main"))
[*]libgnutls.so.13 (package: [libgnutls13_1.4.0-3ubuntu1_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgnutls13%2Flibgnutls13_1.4.0-3ubuntu1_i386.deb&md5sum=893a5820428e7b6c41fbaae50e5e04aa&arch=i386&type=main"))
[*]libtasn1.so.3 (package: [libtasn1-3_0.3.5-1_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibt%2Flibtasn1-3%2Flibtasn1-3_0.3.5-1_i386.deb&md5sum=95de5492caab4ae44aaab9e48ec8dc15&arch=i386&type=main"))
[*]libgcrypt.so.11 (package: [libgcrypt11_1.2.2-2_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibg%2Flibgcrypt11%2Flibgcrypt11_1.2.2-2_i386.deb&md5sum=c17c9ad0fee45a1500e1dd9bbaba6f81&arch=i386&type=main"))
[*]libgpg-error.so.0 (package: [libgpg-error0_1.2-1_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibg%2Flibgpg-error%2Flibgpg-error0_1.2-1_i386.deb&md5sum=d9a4b7b3bc841e6020ac9b5dd0d5ab2b&arch=i386&type=main"))
[/LIST]

4.) ```
sudo gedit /etc/ld.so.conf 
``` #add this path: ***/usr/lib32*** 

5.) in /usr/lib32 you also need softlinks:

[LIST]
libtiff.so.3 (symlink to libtiff.so.4 from the package [libtiff4_3.8.2-6_i386.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Ft%2Ftiff%2Flibtiff4_3.8.2-6_i386.deb&md5sum=56401dcaedc251a6a09761da334dc3e5&arch=i386&type=main"))
libpng.so.3 (symlink to libpng12.so.1.2.8 from the package [libpng3_1.2.8rel-5.1ubuntu0.1_all.deb]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Flibp%2Flibpng%2Flibpng3_1.2.8rel-5.1ubuntu0.1_all.deb&md5sum=ff80da62782949d9ee6e2f45de7368d8&arch=all&type=security"))
[/LIST]

6.) do the ldconfig ```
sudo ldconfig
```
7.) restart cups and off to printing. :)

Hope this helps develop this thread a bit.

Sources: 
[LIST]
[*][Takushi's page]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/")
[*][German HOW-TO on Canon printers]("http://wiki.ubuntuusers.de/Canon-Drucker")
[*][German forum - forum.ubuntuusers.de]("http://forum.ubuntuusers.de/topic/35693/")

[/LIST]

---

### Post by rangi500 on 2007-01-29
Thanks kr0n1x,

Your post on how to get the Canon i350 working on Ubuntu using Turboprint worked fine for me too.

Thanks,
Rangi

---

### Post by kr0n1x on 2007-01-29
> **rangi500 said:**
> Thanks kr0n1x,

Your post on how to get the Canon i350 working on Ubuntu using Turboprint worked fine for me too.

Thanks,
Rangi

good, but the problem is: how to delete turboprint logos in my print???:( (without pay full turboprint versione i mean!)

---

### Post by yabbadabbadont on 2007-01-29
> **kr0n1x said:**
> good, but the problem is: how to delete turboprint logos in my print???:( (without pay full turboprint versione i mean!)

You don't...  :D

---

### Post by dvarsam on 2007-02-06
> **crockettoo said:**
> These are the ones you need for the i550:

[ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus550i-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilterpixus550i-2.2-1.i386.rpm)
[ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfiltercups-2.2-1.i386.rpm)

good luck

I used the above downloaded packages:

1. [color=blue]bjfiltercups-2.2-1.i386.rpm[/color]
2. [color=blue]bjfilterpixus550i-2.2-1.i386.rpm[/color]

I converted them to ".deb" files & installed them!

I also installed:

3. [color=blue]libtiff3g_3.5.5-7woody2_i386.deb[/color]
4. [color=blue]libpng10-0_1.0.18-1_i386.deb[/color]
5. [color=blue]libpng2_1.0.18-1_all.deb[/color]

I then did a "[color=blue]sudo /etc/init.d/cupsys restart[/color]"

Also, according to the First Post of this Thread:

[quote=punkass]5. Then use the gnome gui for adding a new printer
System > System Settings > Printing
And you will now see your new driver in the list as PIXUS XXXi verX.X[/quote]

From the Menu, I select:

1. "System\Administration\Printing"
2. I remove any installed Printers.
3. I right-click on "New Printer" & click on "add"
4. I select "Canon i550" & click on "Next"
5. I can NOT find any "[color=blue]PIXUS 550i verX.X.[/color]" printer available...

What can I do?
Thanks.

P.S.> I have the same problem like user "cement_head":
[quote=cement_head]Followed your directions and do not see the driver listed. Is it under the Canon drivers? Or in the list of manufacturers?[/quote]

In his following post he says:
[quote=cement_head]...after a reboot I can now see them. I just printed a PDF journal article on my Canon i550.[/quote]

I rebooted my [color=red]Ubuntu v6.10[/color] too, but didn't get anywhere...

I then selected the driver "bjc-800" as suggested & tried to print a picture...
Nothing!!!

I then tried typing the command "[color=blue]ls /usr/lib/libpnd.so.2[/color]" user "cafn8ed" suggested:

```
dimitris@dimitris-desktop:~$ ls /usr/lib/libpnd.so.2
ls: /usr/lib/libpnd.so.2: No such file or directory
```

I then performed his suggested:

[color=blue]sudo ln -s /usr/lib/libpng10.so.0 /usr/lib/libpng.so.2[/color]

To get this:

```
dimitris@dimitris-desktop:~$ sudo ln -s /usr/lib/libpng10.so.0 /usr/lib/libpng.so.2
ln: creating symbolic link `/usr/lib/libpng.so.2' to `/usr/lib/libpng10.so.0': File exists
```

I still can NOT get a printed page....

BTW: Whenever I launch the "New Printer" wizard, two "Canon i550" Printers are detected!!!

And got the same result as user "jabeez"... Nada -> Nothing!

---

### Post by tallyson on 2007-02-20
> **drmagoo said:**
> Thanks for the how-to. Which repository/where can I find libtiff3g?
apt-get yields:  E: Couldn't find package libtiff3g

magoo

I have the same problem and also w/ libpng2, and have know idea what a repository is or hoary or warty. Should this install work w/ printer on USB?

Thanks for any help.

---

### Post by Repent on 2007-02-21
If I don't have them how can I get them?

4. $apt-get install libtiff3g
$apt-get install libpng2




joe203@joe203-desktop:~$ sudo apt-get install ibpng2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ibpng2
joe203@joe203-desktop:~$ sudo apt-get install libtiff3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libtiff3g
joe203@joe203-desktop:~$

---

### Post by Repent on 2007-02-21
Bump please help !

---

### Post by Repent on 2007-02-21
So no one looks at this thread anymore?

---

### Post by redsoftretro on 2007-03-04
Hi Repent

You've typed this...

sudo apt-get install ibpng2

but I think you need this...

sudo apt-get install libpng2

Also you may need to add to your sources.list to get the package you're trying to install

sudo echo "deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe" >> /etc/apt/sources.list
sudo apt-get update

---

### Post by flyingfree on 2007-06-14
Okay so I executed by hand every command line in 
[http://www.hildoer.com/linux/scripts/install_canon_i860.sh](http://www.hildoer.com/linux/scripts/install_canon_i860.sh)
but I got an error on the lpadmin line saying I couldn't copy the ppd file?  ?Any suggestions?  I have tried all the various methods listed in this thread to install my i860 on my dapper 32 xubuntu system but to now avail.  not even the suggested bjc driver works.  Any further suggestions or comments.

---

### Post by redsoftretro on 2007-06-14
Try Feisty mate, my Canon works fine with that.

---

### Post by telemetry on 2007-07-18
I successfully installed my canon i865 printer by allowing ubuntu 7.04 32 bit to do it for me.  I simply went to : System and then Administration and chose the printing option.  It detected my i865 perfectly and it is now installed and working like a dream.

So: I hope this might help someone looking for a workaround.

---

### Post by kr0n1x on 2007-07-26
can my Canon i350 work on Ubuntu Feisty?

---

### Post by measekite on 2007-08-30
Canon uses an [COLOR=Red]**ink monito**r[/COLOR] to tell you when you need to change the cart so your head does not burn.  Do these drivers support that?  Gutenprint does not.

Gutenprint also has a bug when choosing cassette or autosheet feeder.  You must use the hardware button on the printer.  Also when choosing custom paper size there is not place to specify the custom size.

---

### Post by measekite on 2007-08-30
> **telemetry said:**
> I successfully installed my canon i865 printer by allowing ubuntu 7.04 32 bit to do it for me.  I simply went to : System and then Administration and chose the printing option.  It detected my i865 perfectly and it is now installed and working like a dream.

So: I hope this might help someone looking for a workaround.

Does the ink monitor work telling you when to change carts?

---

### Post by Golyadkin on 2007-08-30
I am using a Canon PIXMA IP4200 which works flawlessly out of the box with Feisty Fawn, but I somehow cannot change the quality of the print, no draft mode...

---

### Post by Taxi on 2007-09-23
I'm trying to add Canon's drivers for my i560, but they're not showing up in the Driver section of the printer's Properties in Adminstration -> Printing when I select Canon as the manufacturer (and I don't believe it's hiding under some other manufacturer, either).  I'm using Feisty and I followed the directions from post #24:

> **ferrill said:**
> I got it working very well here is what I had to do:

1. Get the correct drivers from here: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
(they cover i550, i560, i850,i860,i950, i990)

You need:
bjfilterpixusXXXi-X.X-X.i386.rpm
AND the corresponding cups driver:
bjfiltercups-X.X-X.i386.rpm

2. use alien to convert the rpms to debs (apt-get install alien if you dont have it)
sudo alien -c <rpm package>

3.
dpkg -i bjfilterpixusXXXi_X.X-X.i386.deb
dpkg -i bjfiltercups-X.X-X.i386.deb

4.
apt-get install libtiff3g
apt-get install libpng2

5. sudo /etc/init.d/cupsys restart

6. Then remove BJC-7000 driver.  System > System Settings > Printing, right click on the printer and select remove.  If you do not delete other driver referencing the printer when print from an application it will never get sent to the printer.

7. Then use the gnome gui for adding a new printer
System > System Settings > Printing
And you will now see your new driver in the list as PIXUS XXXi verX.X

I followed the directions pretty closely, using the files bjfilterpixus560i-2.4-0.i386.rpm and bjfiltercups-2.4-0.i386.rpm from Canon.  The only thing I am aware of having done differently was using libtiff4 and libpng3 from the current repositories, but post #1 was updated by the original poster saying that those should work, too.

I initially tried the instructions from post #1, but apparently there are scripts in one of the packages that need to be translated as well, so after I finished the instructions and that attempt failed I used the "alien -c" in those later instructions in order to avoid that error.  The only thing that I noticed that seemed out of the ordinary was that every time it converted the .rpm's to .deb's it said "hostname: Unknown host" in the terminal twice for each file it converted.  I don't know what it's talking about, but *maybe* it's significant?

I'm aware and glad that the i560 seems to be somewhat supported by the drivers that came with Feisty, but I'd like to get the Canon drivers to work.  (I'm hoping they'll have low/out of ink notifications, printer maintenance, etc. like in Windows.)  Oh, and I do still have a Windows installation with installed drivers for the printer if there's anything worthwhile in there.  I'd appreciate any help anyone can give me.  I'm new to Ubuntu, as well as GNU/Linux in general, so please be somewhat explicit in any instructions you give.  And of course I'd be happy to provide any additional information, as long as you tell me how to find it.

Thank you!

---

### Post by Gwasanaethau on 2007-09-24
Hi all,

I tried this a while back and got everything to work fine, but my printer (i560x) would only print in 600×600 dpi. It's a photo printer so should be able to support up to 2400×2400 dpi. Is everyone having the same problem or have I missed something? :confused:

---

### Post by mudenza on 2007-11-08
Im trying this with Gutsy, but when I arrive to step 3 I get :

dpkg: requested operation requires superuser privilege


Any ideas?

---

### Post by redsoftretro on 2007-11-08
type the 'sudo' command before the command you're having problems with. You'll then be prompted for your password.

Try 'man sudo' to read the help page for a bit of background info.


Nick

---

### Post by stinger30au on 2008-05-31
does the instructions included in this thread work on 8.04 at all

---

### Post by mike27ob on 2009-01-10
Hi, total Linux virgin and struggling greatly. I have an i990 printer, in your HowTo you say

You need:
bjfilterpixusXXXi-X.X-X.i386.rpm
AND the corresponding cups driver:
bjfiltercups-X.X-X.i386.rpm

I can find the pixus i990 file but no corresponding cups file. Is the cups file a more generic file or is it printer specific?

Thanks

Mike

---

### Post by itsjareds on 2009-06-21
I'm having some trouble actually printing the page. I've followed the instructions and everything seems to have run smoothly, I even found my Canon i860 driver in the list. However, when I print a test page, my printer does nothing but the print window goes VERY slowly -- takes about a minute to print. Then I get a notification that says my printing completed.

I think it may have to do with the fact that my computer is connected to this printer through a serial port, not a USB. Is there anything special I need to do for the connection? I don't know much about serial ports, I just know what they look like, and that they're older than USB. Is there any way to list all my serial devices in a similar fashion to lsusb?

Another reason may be because I couldn't find the libtiff3 and libpng2 packages. A search on Synaptic told me that I already have libtiff4 and libpng12-0.

Using Ubuntu 9.04.

---

### Post by itsjareds on 2009-09-21
Help?

It's been about 4 months and I haven't figured this out yet. Reinstalled and now all I get is a successful "Page has been printed" notification about half a second after I print. Nothing happens with the printer. The printer is still labeled "idle" when my printer is truly off. It's in serial port 1.

I found the driver and installed it and it looks good, but no dice. Using Canon i860.

edit: Must be a problem with the driver and serial ports -- printing via USB works fine.

---

