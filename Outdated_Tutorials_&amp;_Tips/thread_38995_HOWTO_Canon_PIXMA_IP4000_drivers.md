---
title: "HOWTO: Canon PIXMA IP4000 drivers"
date: 2005-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by paris_m_ on 2005-06-02
This is a HOWTO install the canon pixma ip4000 drivers, released by canon japan and downloaded from: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)
There are also drivers for ip3000 and ip8500, which i assume would also install in the same manner described here (not tested). The source code for the pixma range is also in that url so it might be possible to compile drivers for the other pixmas (for ip1000 and ip1500).

Limitations of the driver are:
 1. No duplex printing
 2. No CD-R printing
I 've tested the driver printing text and pictures in plain paper only(I don't have special paper but should work fine). Picture quality seems to be the same as in winxp. The colour tone looks to be just a bit reddish in some pictures (with default settings) but this can be fixed playing around with colour settings.

I'm still a newbie and i don't know much about cups so i expect recommendations for better functionality. I found hints on installing in these threads:
[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general)
[http://forum.kanotix.net/viewtopic.php?t=7784](http://forum.kanotix.net/viewtopic.php?t=7784)  (in german, translated through [http://www.systranbox.com/systran/box](http://www.systranbox.com/systran/box))

In japan pixma printers are released under different names:
pixus ip3100  ->  pixma ip3000 
pixus ip4100  ->  pixma ip4000 
pixus ip8600  ->  pixma ip8500 

[COLOR=DarkRed]The HOWTO:[/COLOR]
**1. Install required packages**
Install alien with synaptic
Install libxml1 with synaptic (required later on to run canon's bjcups application)

**2. Download Driver**
open terminal
cd to your preferred download directory
For ip4000:
$ wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-lprng-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-lprng-2.50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip4100-2.50-2.i386.rpm)
For ip3000:
$ wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip3100-lprng-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip3100-lprng-2.50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip3100-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip3100-2.50-2.i386.rpm)
for ip8500:
$ wget [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-common-2.50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip8600-lprng-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip8600-lprng-2.50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip8600-2.50-2.i386.rpm](ftp://download.canon.jp/pub/driver/bj/linux/bjfilter-pixusip8600-2.50-2.i386.rpm)

**3. Convert .rpm to .deb**
$ sudo alien bjfilter-common-2.50-2.i386.rpm
$ sudo alien bjfilter-pixusip4100-lprng-2.50-2.i386.rpm
$ sudo alien bjfilter-pixusip4100-2.50-2.i386.rpm
(note: change filenames appropriate to much your printer's)

**4. Install**
$ sudo dpkg -i <names of the 3 generated deb files>

**5.Edit .ppd file**
To allow printing quality options to be accessed through cups' printer properties you must edit as root the printer's ppd file.(This applies only to the ip4000. I don't know the settings for ip3000 or ip8600.Backup and try it)
$ sudo gedit /usr/share/cups/model/canonpixusip4100.ppd
Add these lines:
*OpenUI *CNQuality/Quality: PickOne  
*DefaultCNQuality: 3  
*CNQuality 2/High: "2"  
*CNQuality 3/Normal: "3"  
*CNQuality 4/Standard: "4"  
*CNQuality 5/Economy: "5"  
*CloseUI: *CNQuality 

You can also replace these lines:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution
with:
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600
*Resolution 600/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"  
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"  
*CloseUI: *Resolution

Save the file

**6. Fix libs**

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1

(i don't know why i do this but otherwise the printer does not work)

**7. Restart Cups**
$ sudo killall cupsd
$ sudo cupsd

**8. Setup Printer**
-System>Administration>Printing>New Printer
-Choose Local or network printer and specify port or url, respectively
-Forward
Manufacturer>canon
Model> PIXUS iP4100 Ver.2.50 (depends on your printer)
Driver>Standard
-Apply
(if you can't find your printer choose:install driver>choose the ppd file you edited, reboot and try again to setup printer)

**9. Test**
Right Click on printer> properties>print test page

**10. Setup on GIMP**
-open an image to print
-file>print>Choose your printer name>setup printer:
Printer Model>PostScript level 2
command>lpr -P <your printer name>     (mine is PIXUS-iP4100-Ver.2.50)
PPD File>browse at /usr/share/cups/model/ (mine is /usr/share/cups/model/canonpixusip4100.ppd)
-OK
-Save Settings
-Print

I don't know if changing to a higher resolution works. The test pages showed same quality with any resolution.I think that resolution is actually controlled with the quality settings only, at the cups' printer properties menu>advanced>quality(High, Normal, standard, economy). I also suppose that the .ppd file can be further tweaked to allow more options to be set up in the cups properties menu, and more features might be unlocked (if somebody is experienced with cups help would be appreciated).

[B]
11.Run bjcups application[/B]
Bjcups is canon's application that allows you to set printer's settings and perform maintenance tasks such as head alighnment.
$ bjcups -P <printer name>  (mine is PIXUS-iP4100-Ver.2.50)
To print a file you may also use:
$ bjcups -P <printer name>  <filename>

Finally, at [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/) you can find some other applications that might be useful, the source code for the drivers, and a user's guide for the driver in Japanese. I somehow translated it in English using [http://www.systranbox.com/systran/box](http://www.systranbox.com/systran/box) .

Hope it works ;-)
Please post for any problems or fixes

---

### Post by momist on 2005-06-05
Thank you Paris M   :) 

I am about to buy one of these printers, and my research had indicated that the Japanese had such drivers, but I would not have known what to do with them!

Every day is a school day.

---

### Post by coaxx on 2005-06-07
Thank U for Your Howto. 

I use the Canon IP5000 Printer, is there a way to install the drivers without compiling? (Does it work with the 4000 drivers?)

edit:

Again thank U very much, my IP5000 works with the ip4000 drivers!

---

### Post by pmazer on 2005-06-08
[QUOTE=coaxx]Thank U for Your Howto. 

I use the Canon IP5000 Printer, is there a way to install the drivers without compiling? (Does it work with the 4000 drivers?)

edit:

Again thank U very much, my IP5000 works with the ip4000 drivers![/QUOTE]
 I just wanted to confirm that the 4100 drivers do indeed work with the iP5000... yay!

---

### Post by paris_m_ on 2005-06-08
[QUOTE=pmazer]I just wanted to confirm that the 4100 drivers do indeed work with the iP5000... yay![/QUOTE]
 I am glad that the 4100 drivers work for the ip5000. I have downloaded the drivers source file from Canon Japan and it only supports these printers: 
pixma ip1000 
pixma ip1500
pixus ip3100
pixus ip4100
pixus ip8600

Some other folks at linuxprinting.org forums compiled the ip1000and ip1500 drivers at their machines and have them available for download.
For the ip1000 look at this thread:
[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2344](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2344)
For the ip1500 look at this threads:
[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2332](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2332)
[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2342](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general;article=2342)

---

### Post by coaxx on 2005-06-08
OK I've done some testing prints with my IP5000 (using the IP41000 drivers) to compare image quality.

Well, I have to tell You that printing quality is much worse than printed with Win XP. But printing with a Windows Client throught Cups will result in exactly the same quality as direct connected to Windows (raw mode)! :-)

OK now the question is, is this the case only because the 4100-driver is used or do all linux drivers have worse image quality.

Text quality is excelent here and the resolution seems very high, images are sharp but colors are bad!

---

### Post by paris_m_ on 2005-06-09
[QUOTE=coaxx]OK I've done some testing prints with my IP5000 (using the IP41000 drivers) to compare image quality.

Well, I have to tell You that printing quality is much worse than printed with Win XP. But printing with a Windows Client throught Cups will result in exactly the same quality as direct connected to Windows (raw mode)! :-)

OK now the question is, is this the case only because the 4100-driver is used or do all linux drivers have worse image quality.

Text quality is excelent here and the resolution seems very high, images are sharp but colors are bad![/QUOTE]
 I know. The colour output of my ip4000 is not so good with this driver. Try to print using commandline and the bjcups program:
$ bjcups -P <printer name> <filename>
With this application you can manually setup colour balance, an option not implemented in the .ppd file canon provided, even if it is supported by the driver. However with this application you can't setup the page correctly. The default colour settings are not good so a better colour output might be obtained using manual colour settings. Anyway I hope that in future releases of the driver by Canon Japan (if any) or with the help of somebody who knows a bit more about printing in linux (I'm a newbie) the problem is solved.

---

### Post by coaxx on 2005-06-14
[QUOTE=paris_m_]

**10. Setup on GIMP**
-open an image to print
-file>print>Choose your printer name>setup printer:
Printer Model>PostScript level 2
command>lpr -P <your printer name>     (mine is PIXUS-iP4100-Ver.2.50)
PPD File>browse at /usr/share/cups/model/ (mine is /usr/share/cups/model/canonpixusip4100.ppd)
-OK
-Save Settings
-Print

[/QUOTE]

This does not work for me. I use Gimp at a network client. Printing from KDE Apps works but not from gimb. I can chose the printer then I set "PostScript level 2"..but... What do I have to set for the ppd file and print command in gimp when printing to a network printer? Default is here  "lp -s -d<printername> -oraw" and an empty line for the ppd. When I print with this settings cups will get the print-job, but it wont print. It will be listed under "completed jobs" with the name "(stdin)" thx!!

---

### Post by paris_m_ on 2005-06-17
[QUOTE=coaxx]This does not work for me. I use Gimp at a network client. Printing from KDE Apps works but not from gimb. I can chose the printer then I set "PostScript level 2"..but... What do I have to set for the ppd file and print command in gimp when printing to a network printer? Default is here  "lp -s -d<printername> -oraw" and an empty line for the ppd. When I print with this settings cups will get the print-job, but it wont print. It will be listed under "completed jobs" with the name "(stdin)" thx!![/QUOTE]
 Print Command:  lpr -P <your printer name>  (mine is PIXUS-iP4100-Ver.2.50)
PPD File>usr/share/cups/model/canonpixusipXXXX.ppd (XXXX is your printer model)

---

### Post by coaxx on 2005-06-18
[QUOTE=paris_m_]Print Command:  lpr -P <your printer name>  (mine is PIXUS-iP4100-Ver.2.50)
PPD File>usr/share/cups/model/canonpixusipXXXX.ppd (XXXX is your printer model)[/QUOTE]

This works, thank You!

---

### Post by omiazad on 2005-06-27
After all the hooking and cooking, my IP1000 is working fine. But I want to desable color printing. Can anyone tell me how can I turn color printing off?

---

### Post by dieffel on 2005-07-15
Hi!

I just noted that u need "sudo" in front of the "ln -s" command in point 6 

dieffel

---

### Post by paris_m_ on 2005-07-18
Thanks for the note. I have corrected the error.

---

### Post by omiazad on 2005-07-19
[QUOTE=omiazad]After all the hooking and cooking, my IP1000 is working fine. But I want to desable color printing. Can anyone tell me how can I turn color printing off?[/QUOTE]
 I asked you how to disable Color printing and I could not understand your solution. Can anyone help me with a specific solution?

---

### Post by flytopia on 2005-07-19
Another solution is to use the [Turboprint drivers](http://www.turboprint.de/english.html). I've got them working well with my IP4000.

They're not free or Open Source, but they do support high-quality colour, duplex printing and CD printing.

If you're happy with low quality output, you can use the free version. It's limited to 300dpi, but duplex printing still works.

If you want the higher quality, it costs €30/US$40.

flytopia

---

### Post by omiazad on 2005-07-20
Well, I installed TurboPrint drivers as well. These days they have stopped low quality output. Now they are printing their logo on the doc. So this is not a good solution.

---

### Post by paris_m_ on 2005-07-21
For now I think no option for grayscale only printing is available in the cups printer properties. So you can't turn off color printing permanently. Though you can try turning it off  each time you print something through the application you are using, if this option is available in the specific application (e.g. firefox, openoffice, gimp).

---

### Post by derhelge on 2005-08-24
Hi,

thanks for this really easy understandable howto.
i ve mad all this steps and i got no error messages at any time.
but when i want to print nothings happens...
the Job gets the status "job-printing" and themes to be sucessfull...
but at my printer isnt any test-print ;-)

the cups log-files tell me "Broken pipe" and thats very often...
has anyone an idea?

thanks und bye,
der.helge

PS: sorry for my bad english...

---

### Post by nbcthreat on 2005-10-06
I've just done a fresh Ubuntu install and update and found these great instructions for getting my iP 4000 up and running. They have worked flawlessly, but I'm wondering if anyone has been able to get the printer to pull paper from the cassette underneath rather than the paper feeder on top of the unit.

When I run

bjcups -P PIXUS-iP4100-Ver.2.50 

I get

lpr: error - unable to access "PIXUS-iP4100-Ver.2.50" - No such file or directory

And yes, the name of the printer is correct. When I run 

/usr/bin/lpstat -v

I get

device for PIXUS-iP4100-Ver.2.50: usb://Canon/iP4000

Has anyone else gotten the bjcup application working?

---

### Post by 43moon on 2005-10-14
Great tutorial paris_m_, thanks a lot~

---

### Post by ichigo on 2005-10-24
[QUOTE=nbcthreat]
When I run

bjcups -P PIXUS-iP4100-Ver.2.50 

I get

lpr: error - unable to access "PIXUS-iP4100-Ver.2.50" - No such file or directory

And yes, the name of the printer is correct. [/QUOTE]

I've got the same problem with my iP3000 or at least a similar one.
When I enter that command with the correct printer name bjcups seems to work, but after clicking "ok" I get that error message.
Besides this printing sometimes works, sometimes not. I apsolutely don't understand when and why it works/doesn't work....
Do you have an idea what's wrong?

---

### Post by twoseids on 2005-10-25
[QUOTE=ichigo]I've got the same problem with my iP3000 or at least a similar one.
When I enter that command with the correct printer name bjcups seems to work, but after clicking "ok" I get that error message.
Besides this printing sometimes works, sometimes not. I apsolutely don't understand when and why it works/doesn't work....
Do you have an idea what's wrong?[/QUOTE]
Same problem for me too with my 4100.  Otherwise everything works great!

---

### Post by coaxx on 2005-11-12
I have similar problems here. Sometimes I have to delete the printing jobs / Stop the printer or unplug and plug in the printer's USB cable. I use the cups web Adminstration frontend to do this http://<your_ip_where_cups_is_running>:631/printers/

Then printing on paper from cassete works.

---

### Post by vinnyjones on 2005-11-24
Hi i also want to change it to cassette and when i tried going into the CUPS web administration it asks me for a username and password... Which username and password would i enter here?

---

### Post by henkeboy on 2005-11-26
I can't download any files at all from: 
wget [ftp://download.canon.jp/pub/driver/b....50-2.i386.rpm](ftp://download.canon.jp/pub/driver/b....50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/b....50-2.i386.rpm](ftp://download.canon.jp/pub/driver/b....50-2.i386.rpm) [ftp://download.canon.jp/pub/driver/b....50-2.i386.rpm](ftp://download.canon.jp/pub/driver/b....50-2.i386.rpm)

... I only got this answer that the files doesn't exist. Im running Breezy, and my printer is a ip4000. whats wrong? plz help !

---

### Post by henkeboy on 2005-12-04
I fixed to download the drivers! But I can rub Bjcups. I can open the app but when I have done some changed and klick "OK" I get the message: lpr: error - unable to access "PIXUS-iP4100-Ver.2.50" - Filen eller katalogen finns inte (last words are swedish). The problem for me is that i cant print from cassete. Is there anyone who can do that or run bjcups?

---

### Post by nchase on 2005-12-13
I can get printing to work...but my printing starts roughly halfway down the page instead of at the top. Does anyone know why this might be happening? (trying to print a document from openoffice writer)

---

### Post by inSaNo on 2006-01-05
I've just installed this driver to use it for my **Canon PIXMA iP4200**, and the printer will actually print something..

But i think this driver is not good for my type, because the colors do not lign up.
the prints are somewhat readable, but all different colors are shifted..

Too bad, i would have really liked to use my printer..

---

### Post by JoeMcC00L on 2006-01-09
Thanks, it worked exactly as it's supposed to. I'm running gentoo, so I skipped the "alien" and "dpkg" steps and used "sudo rpm -ivh <package_name.rpm> --nodeps" instead. Worked like a charm.

Thanks,
Joe

---

### Post by pandion_auk on 2006-01-17
I've just installed Breezy on my parent's computer, and am trying to get thier printer working correctly (with the S800 gimp-print driver it works somewhat, but with a few quirks). They have an ip4000 with a sony viao pcv-rx550.

When using wget, it tells me the files can't be found. Are they moved somewhere else? Can somebody who's successfully downloaded and used them from this thread upload them?

Help me convert my parents to linux. Don't let thier chance slip away! :)

/me didn't have hardware troubles with his HP comp, printer, fan, or speakers.

---

### Post by Thomas,Bakker on 2006-02-01
does this tutorial also work on the 64bits system of ubuntu?
for now im going to install turboprint, (hope i succeed its my 2nd day as linux user)

---

### Post by RagingOcelot on 2006-02-04
Has anyone been able to tweak the driver settings for this printer so one could make borderless prints?  There is no true 4x6 borderless setting in the default print sizes.  The closest you come to is the Hagaki 100x148 size.  

Also, I don't believe bjcups is working properly for me.  I'll enter

bjcups -P CanonIP4000 

and the command won't print anything in the Terminal.

---

### Post by madadam on 2006-02-09
I know this is a (an?) ubuntu forum, but has anyone got this working under debian?  I'm not able to get a test page printed.  

The installation looks fine, but then in the /var/logs/cups/error_log, I see that bjfilterpixusip4100 has died, with a bunch of junk starting with:
D [09/Feb/2006:17:58:11 -0500] [Job 1] Error: invalid printer model name
D [09/Feb/2006:17:58:11 -0500] [Job 1]
D [09/Feb/2006:17:58:11 -0500] [Job 1] Canon Bubble Jet Print Filter for Linux Ver.2.50
D [09/Feb/2006:17:58:11 -0500] [Job 1] Copyright CANON INC. 2001-2005
D [09/Feb/2006:17:58:11 -0500] [Job 1] All Rights Reserved.
D [09/Feb/2006:17:58:11 -0500] [Job 1]
D [09/Feb/2006:17:58:11 -0500] [Job 1] bjfilterpixusip4100 --gui (gui mode)
D [09/Feb/2006:17:58:11 -0500] [Job 1] bjfilterpixusip4100 [switches] [file]
...

this is the same output that I get if I try to run bjfilterpixusip4100 from the command line.  

Anyone have any idea what's going on?
thanks,
a

---

### Post by smaloney on 2006-02-09
Hi I followed your instructions carefully and got to the installation of the printer and even find PIXUS iP4100 ver 2.50 but when I highlight it it does not allow me to apply the settings?  Went back and tried to load the file that was edited and still did not work?

What did I miss?

---

### Post by anitsirK on 2006-02-26
[QUOTE=smaloney]Hi I followed your instructions carefully and got to the installation of the printer and even find PIXUS iP4100 ver 2.50 but when I highlight it it does not allow me to apply the settings?  Went back and tried to load the file that was edited and still did not work?

What did I miss?[/QUOTE]

Choose "Standard" on the "Driver" drop-down.  I had to go back and re-read the instructions for this, myself.

I have my own question.  I've installed it, and it printed the test page, but it's not clearing the job queue.  This is for an iP5000.  Does anyone else with an iP5000 have the same problem?  I can just delete the jobs manually after they're done, but this seems strange.

---

### Post by axelb on 2006-03-21
Has anyone tested the debian drivers?
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/canon-pixus25.html)

I will test them as soon as I can, but I do not have the printer here.

Also this tread on kanotix gives som usefull information:
[http://forum.kanotix.net/PNphpBB2-viewtopic-t-7784-postdays-0-postorder-asc-start-30.html](http://forum.kanotix.net/PNphpBB2-viewtopic-t-7784-postdays-0-postorder-asc-start-30.html)

Best regards
Axel Bojer

---

### Post by axelb on 2006-03-31
Well, the mentioned debiandriver works, but by me this gives two problems:
(Kubuntu 5.10, updated)
1) I can not use the autofeeder, not matter if I choose that under the kde printer settings. I saw someone else also complaining about this, I confirm to have the same problem :-(
2) Perhaps worse: The print get a reddisch color where the background is supposed to be gray, but I shall try the mentioned advise and play around with the settings.

plr -P </usr/bin/lpstat -v> works :-)
But sudo bjcups -P </usr/bin/lpstat -v> starts the GUI, but then wont save.
The message is:
lpr: error - unable to access "CANONPIXUSIP4100-deb" - Ingen slik fil eller filkatalog (the last part is norwegian and means: Can't find that file or folder).
Maybe I destroyed something by installing both drivers (see next part).

I tried the rpm to debian-packages as mentioned at the start of this thread too, but it seemde to be exactly the same driver, I will try more later.

Best regards
Axel Bojer

---

### Post by paris_m_ on 2006-04-11
> Originally Posted by **axelb**  	
Has anyone tested the debian drivers?
[http://mambo.kuhp.kyoto-u.ac.jp/~tak...n-pixus25.html](http://mambo.kuhp.kyoto-u.ac.jp/~tak...n-pixus25.html)

I will test them as soon as I can, but I do not have the printer here.

Also this tread on kanotix gives som usefull information:
[http://forum.kanotix.net/PNphpBB2-vi...-start-30.html](http://forum.kanotix.net/PNphpBB2-vi...-start-30.html)

Best regards
Axel Bojer
After reading somewhere that the correct canon-japan driver for the pixma ip4000 is the pixus860i I have noticed in the canon-japan website that:
Canon Pixus ip4100 although it has the same case as the pixma ip4000, it uses the BCI-7e* series of inks while both pixma ip4000 and pixus860i use the BCI-6* series. So I opened up:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/")
and followed the page's instructions to install the debian drivers for 860i. (note: I'm on breezy)
After some testing and tweeking the ppd file, as described in this how-to, to enable high quality printing, it seems that **this is** the driver for the ip4000. :) The printed colours now look exactly as in winXP and do not look reddish as with the pixus4100 driver. However i don't have any time to do more testing with other than plain paper and with different applications.
Problems-Limitatios-bugs:
[LIST]
[*]Printing only possible with sheet feeder. No cassette.
[*]No cd, no duplex printing
[*]With some apps the printing job shows to begin, then ends but no printing happens, while cpu usage goes to 100% and remains there. I don't know what causes this but after removing cupsys (with all conf settings through synaptic) and re-installing it, the problem is solved.
[*]ink and printer monitoring not possible
[/LIST]

I have also tried to install the new gutenprint pre-5.0.0rc2 (ex gimp-print) drivers which include an open source driver for ip4000. This release  I suppose will be included in dapper. I have installed it in breezy using this how-to:[http://ubuntuforums.org/showthread.php?t=119595]("http://ubuntuforums.org/showthread.php?t=119595")
However, the driver seems that it is still buggy, at least in breezy. Read this thread: [http://sourceforge.net/forum/forum.php?thread_id=1434931&forum_id=4359,]("http://sourceforge.net/forum/forum.php?thread_id=1434931&forum_id=4359,")
I 've managed to print only after setting up the printer through the web interface as indicated in the thread, only at 600x600 resolution. The quality is inferior to the canon-japan pixus860i driver but the news is that **duplex printing and cd printing is said to be supported** (I haven't tested). Note that there is some kind of bug in the gnome cups manager with this version: After finishing printing, the job shows to be still active and you have to manually cancel it. Therefore I would recommend not to install and wait for Dapper to see if this is resolved.
I hope that this info is useful. Unfortunately I'm still a newbie in linux and don't have the time (I'm a university student) to reply to something i do not have the knowledge. So sorry if not replying to some posts.

---

### Post by ondrass on 2006-04-19
[QUOTE=paris_m_]This is a HOWTO install the canon pixma ip4000 drivers, released by canon japan and downloaded from: [ftp://download.canon.jp/pub/driver/bj/linux/](ftp://download.canon.jp/pub/driver/bj/linux/)[/QUOTE]

Please note, that Canon has released 2.60 version of their binary drivers.
[QUOTE=paris_m_]
**6. Fix libs**

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1
[/QUOTE]

**[SIZE="5"]Don't!!![/SIZE]** That number means **compatibility** on binary interface. libpng2 and libtiff3 can be easily compiled from older debian sources. Just go to:

1. [http://ftp.debian.org/debian/pool/main/t/tiff/](http://ftp.debian.org/debian/pool/main/t/tiff/) download tiff-3.5.5 (orig.tar.gz, diff.gz and dsc), issue dpkg-source -x tiff*dsc, go to created dir, install build-essential, devscripts, libz-dev and libjpeg62-dev, and run debuild
2. [http://ftp.debian.org/debian/pool/main/libp/libpng/](http://ftp.debian.org/debian/pool/main/libp/libpng/) download libpng_1.0.18*, compile

Install libtiff3g_3.5.5*deb, libpng2*deb and libpng10-0*deb and you are done.

libxml1 is available even in dapper, no need to break your system by doing stuff you don't understand.

---

### Post by mschievano on 2006-04-30
something for ip4200 and amd 64?

---

### Post by dolfdiop on 2006-06-03
I Have the same problem as you. When I try to make the instazll, here is the message I get:
20:26:38 (93.22 KB/s) - « bjfilter-pixmaip1500-lprng_2.50-3_i386.deb » sauvegardé [90702/90702]

dpkg : erreur de traitement de bjfilter-common_2.50-3_i386.deb (--install) :
 l'architecture du paquet (i386) ne correspond pas à celle du système (amd64)
dpkg : erreur de traitement de bjfilter-pixmaip1500_2.50-3_i386.deb (--install) :
 l'architecture du paquet (i386) ne correspond pas à celle du système (amd64)
dpkg : erreur de traitement de bjfilter-pixmaip1500-lprng_2.50-3_i386.deb (--install) :
 l'architecture du paquet (i386) ne correspond pas à celle du système (amd64)
Des erreurs ont été rencontrées pendant l'exécution :
 bjfilter-common_2.50-3_i386.deb
 bjfilter-pixmaip1500_2.50-3_i386.deb
 bjfilter-pixmaip1500-lprng_2.50-3_i386.deb
resolving dependencies...

does somebody knows where to find the bjfilter packages for amd64?


[QUOTE=mschievano]something for ip4200 and amd 64?[/QUOTE]

---

### Post by chorca on 2006-06-08
Same error i'm getting about AMD64. seems we're gonna be left out in the rain here if canon doesn't compile their binaries for that arch, which may take awhile.

---

### Post by bohboh on 2006-06-11
I have been battling with installing ip4000 for 4 days:

1. Tried the drivers already installed, didnt work.
2. Downloaded latest turboprint drivers. They worked but only printed to one third of the page and on other occasions stopped printing half way through.
3. Tried it with other printer drivers, bjcxxx

When i was starting to think that this wasnt going to work, i managed it!

In the end i had to install the latest version of CUPS, but when i did and apt-get it told me that i already had the latest version. But when i did a google search i found that there was a newer version, so i downloaded it, installed it and alas.. all is well.

[Cups 1.2.1]("http://linux.softpedia.com/get/Printing/Common-UNIX-Printing-System-10427.shtml")

Admittedly i had to purchase the turboprint drivers, but for £20, that isnt too bad.

Hope this helps others.

---

### Post by Johan! on 2006-08-05
My Pixma IP4000 printer now works decently, and without installing extra packages :) 

This is what I did:

[LIST=1]
[*]Go to System>Administration>Users and Groups
[*]Go to Groups
[*]Make sure that all users and groups are visible
[*]Look for the group lpadmin, select it, and press Properties
[*]Check if your username is listed in the group, if not add it.
[*]Look for the group shadow, select it, and press Properties
[*]Add the user cupsys to the group

[*]In the terminal, type
```
sudo /etc/init.d/cupsys restart
```

[*]Open Firefox, and go to [http://localhost:631/printers]("http://localhost:631/printers")
[*]Find the printer, and click Set Printer Options
[*]Edit the options so it looks like the attachment
[*]Click Set Printer Options
[*]Click Print Test Page
[/LIST]

And you're done!:-P

Also added a scan of the test print to my message.

I found the info here: [http://sourceforge.net/forum/message.php?msg_id=3560353]("http://sourceforge.net/forum/message.php?msg_id=3560353")
And here: /usr/share/doc/cupsys/README.Debian.gz

EDIT:

Grayscale printing works perfectly, color printing not.
I'm trying to find out which settings i need to change to fix that...

EDIT 2:
IT WORKS!:) 
The problem: The printer that was added by system>administration>printing doesn't work

The solution: Install your printer in the web interface, that one works.

---

### Post by William the Conquerer on 2006-08-17
w00t!  Thanks Johan!  It works for me =)

---

### Post by SirYes on 2006-11-03
I was able to resolve the problem with printing using the cassette, instead of automatic feeder. I just changed the section:

```
*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: asf
*InputSlot asf/Auto Feeder: ""
*InputSlot cassette/Cassette: ""
*CloseUI: *InputSlot
```
to:
```
*OpenUI *InputSlot/Paper Feed: PickOne
[COLOR="Green"]*DefaultInputSlot: cassette[/COLOR]
[COLOR="Navy"]*InputSlot cassette/Cassette: ""
*InputSlot asf/Auto Feeder: ""[/COLOR]
*CloseUI: *InputSlot
```

Additionally, I swapped the order of input slot lines (marked blue) from "asf ; cassette" to "cassette ; asf". I'm not sure if this was really needed, but now printer gets the paper from the cassette as expected. :D

**@paris_m_:**
One more thing. Even if the symbolic links to required libraries are evil, making the symlinks is the easiest way to solve this problem. However, [ondrass was right]("http://ubuntuforums.org/showpost.php?p=937908&postcount=39") when he pointed out that this may lead to compatibility problems. So I think that since **libxml1** is already mentioned in *"1. Install required packages"*, you should remove one specific line of this HOWTO:

$sudo ln -s /usr/lib/libpng12.so.0 /usr/lib/libpng.so.2
$sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
[COLOR="Red"]$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1[/COLOR]

---

### Post by goatflyer on 2006-12-11
My printer is the Canon PIXMA iP8500, and your instructions are great!!!

Only three minor differences to report:

#1

When converting the .rpm packages to .deb using alien, I got a warning about scripts not being converted, so I did:

```

sudo alien --scripts bjfilter-pixusip8600-2.50-2.i386.rpm
sudo alien --scripts bjfilter-pixusip8600-lprng-2.50-2.i386.rpm

```


#2
In my /usr/lib directory there was already a symlink:
    libxml.so.1 -> libxml.so.1.8.17

so I did NOT do this part of your 'fix libs' step:
$sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml.so.1


#3
Printing the test page worked perfectly.

When setting up the printer in Gimp-print, I did not find my printer model in the list of Canon models, so I left it blank.
When I tried to print in Gimp, I got some kind of error window complaining about a class not found (sorry, I don't have the text available).  So I re-setup the printer, just using the standard command, and Gimp printed fine after that.

Open office printed perfectly first shot.


Again, thanks for the amazing instructions!

---

### Post by Dr_Snapid on 2006-12-14
> **SirYes said:**
> I was able to resolve the problem with printing using the cassette, instead of automatic feeder. I just changed the section:

```
*OpenUI *InputSlot/Paper Feed: PickOne
*DefaultInputSlot: asf
*InputSlot asf/Auto Feeder: ""
*InputSlot cassette/Cassette: ""
*CloseUI: *InputSlot
```
to:
```
*OpenUI *InputSlot/Paper Feed: PickOne
[COLOR="Green"]*DefaultInputSlot: cassette[/COLOR]
[COLOR="Navy"]*InputSlot cassette/Cassette: ""
*InputSlot asf/Auto Feeder: ""[/COLOR]
*CloseUI: *InputSlot
```


If you do this and still your printer prints from the ASF, make sure you use the cups web interface to change the default tray at [http://localhost:631](http://localhost:631) because the normal interface does not work.](*,) 

Go into the interface, click printers > set printer options > change paper feed to 'cassette' then click 'set printer options'. When prompted for a password, use your own login and password that you use when you log into the system at startup.:-D

---

### Post by tom76 on 2007-01-03
For Debian, I've found a very simple solution, which actually works on first try :)  (I don't know about Ubuntu etc., though).  
It's here:
[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon) 
Please note that I had some problems uninstalling the previous version of the driver package. I don't know about this one.
Thanks so much for providing this Mr Takushi Miyoshi!

---

### Post by maddentim on 2007-02-08
Hi - Hope someone still monitors this thread...  I have Ubuntu 6.10 and have a ip3000.  I follow (or at least tried to!) the nice instructions here.  I have been able to get some stuff to print, but generally it hangs.  The printer icon shows up by the clock and when I click on it i get the job list.  On it I see my job but its status is "Stopped: job stopped".  Any thoughts on what I have done wrong.

Tim

---

### Post by dmizer on 2007-03-15
> **maddentim said:**
> Hi - Hope someone still monitors this thread...  I have Ubuntu 6.10 and have a ip3000.  I follow (or at least tried to!) the nice instructions here.  I have been able to get some stuff to print, but generally it hangs.  The printer icon shows up by the clock and when I click on it i get the job list.  On it I see my job but its status is "Stopped: job stopped".  Any thoughts on what I have done wrong.

Tim

see the link in the post above yours.  there is also an ubuntu repository.  much easier than trying to do this all from alien.  i've been using these drivers for some months now.

but they don't work for dapper.

---

### Post by ernstblaauw on 2007-03-18
I just used the webinterface and it works! My IP4000 prints. However, one feature of the printer is not working: duplex printing. I like to use it, so my question: Has anybody managed to enable duplex printing? I enabled it using the CUPS webinterface, but the setting doesn't make a difference.

**Update:**
I upgraded to CUPS 1.2.9, but that doesn't change anything: still no duplex printing...

---

### Post by dmizer on 2007-03-19
duplex printing is unfortunately not supported with this driver build.  sorry.

by the way, these drivers came from canon direct, so it's at least some progress on the manufacture front.

---

### Post by ernstblaauw on 2007-03-19
> **dmizer said:**
> duplex printing is unfortunately not supported with this driver build.  sorry.

by the way, these drivers came from canon direct, so it's at least some progress on the manufacture front.

Ah, that's good :-). Do they cooperate, or supply updates once in a while? Or did they release one driver and that's all? Hopefully, they will supply more updates (with duplex printing :)), because I don't to start Windows for printing. 
If so, will I find a note in the changelog of CUPS? Or do I have to look somewhere else?

---

### Post by dmizer on 2007-03-19
your best bet is to install the driver as per the repository from takushi san's page mentioned back in post 49.  i have already received updates from his repository.  so if you've installed from source as suggested by the howto in this thread, you should uninstall and reinstall the correct driver as indicated in takushi san's page.

then, if there is an update that includes duplex printing, you will receive it via automatic updates in ubuntu.

that said, i wouldn't suggest holding your breath in anticicpation.  the most recent update from canon on this driver set was may of 2006.

---

### Post by ernstblaauw on 2007-03-19
> **dmizer said:**
> your best bet is to install the driver as per the repository from takushi san's page mentioned back in post 49.  i have already received updates from his repository.  so if you've installed from source as suggested by the howto in this thread, you should uninstall and reinstall the correct driver as indicated in takushi san's page.

then, if there is an update that includes duplex printing, you will receive it via automatic updates in ubuntu.

that said, i wouldn't suggest holding your breath in anticicpation.  the most recent update from canon on this driver set was may of 2006.
Ok. I see. However, there is no driver for the IP4000 on the link he posted. Which one do I need?

---

### Post by dmizer on 2007-03-19
as per the first post in this thread:

> **paris_m_ said:**
> pixus ip3100  ->  pixma ip3000 
pixus ip4100  ->  pixma ip4000 
pixus ip8600  ->  pixma ip8500
so you would need to install the libcnbj-2.5 bjfilter-2.5 pstocanonbj packages, and use the driver for the ip4100

---

### Post by ernstblaauw on 2007-03-19
> **dmizer said:**
> as per the first post in this thread:


so you would need to install the libcnbj-2.5 bjfilter-2.5 pstocanonbj packages, and use the driver for the ip4100
I installed the drivers using the repository. However, when installing a new printer with CUPS, no new printers appear. I just have the same list as before installing the packages described at the site. I already restarted CUPS, but that doesn't make a difference. Do you know how I can use the new printer drivers?

---

### Post by dmizer on 2007-03-19
i assume the printer is connected to your computer via usb cable.  if this is the case, try removing the cable and reconnecting it.  then try to install your printer again.

---

### Post by ChrisUK on 2007-04-17
I have been trying to install my Canon Pixma IP8500 and I have been following this guide.
I get to 8. Setup Printer.
I cannot find my printer in the driver list at all. I have manually pointed it to the ppd file in the USR folder and it still isn't on the list..
Any idea's?

---

### Post by ernstblaauw on 2007-05-01
Ubuntu 7.04 - AMD64

I just installed the printer inside CUPS - no rpms, deb or anything else installed. And it works! Even duplex printing!

However, i do not have the Canon job program - I can't see the inkt levels (or can I somewhere?).

---

### Post by seodavid on 2007-06-22
> **paris_m_ said:**
> http://www.linuxprinting.org/forums.cgi?group=linuxprinting.canon.general[/url]

I clicked that link and now i have some kind of virus that avg cannot fix...
[img]http://xs216.xs.to/xs216/07255/virusdang.png[/img]

---

### Post by benjoseph on 2007-07-24
Sorry friends, I do not know exactly how to post a question to the forum, therefore if this my question is not pertinent to this page forgive me.  My problem is that I have a Canon PIXMA iP3000, and when I print files with INKSCAPE, it will only print TEN copy of the same file, then I have to reboot the system to print another Ten pages of the same file. Is anyone having a solution to this problem? 
Thank you so much folks. 

Giacomo

---

### Post by maddentim on 2007-07-25
your question seems fine.  My first suggestion would be for you to check the printer's system wide properties by clicking the menu system -> adiminstration -> printing.  a box will come up with the installed printers.  right click on the canon and click on properties.  you can then see all the default settings that you have.  Second, i would try printing with another program and seeing if it prints 10 copies.  that would narrow it down to inkscape or not.  

One solution might be to install CUPS-PDF driver and print to pdf and then from the pdf to the printer.

Good luck!

---

### Post by hexd1972 on 2007-08-22
Hi,
I have a pixma ip4000 on ubuntu 7.04, everything went fine during the install you showed.  The printer is installed but it wont print anything, I know when i was in windows the color on some of the ink was running out.  Maybe linux wont let me print because of that?
Wont let me do the test page or anything, just holds the jobs in the queue.  Any Ideas?

thanks

---

### Post by dubnde on 2008-03-29
Was about to start following this thread and I am glad I connected my printer first. Like maddentim, I just connected the the usb printer and it was detected and set up following the dialogue. Printing ok with two-sided printing fine.

Good luck

---

### Post by Breepee on 2008-09-09
I can get an IP8500 from someone, but I'm using Ubuntu 64bit. I suppose these drivers will not work, will they? And does anyone know if there are any driverss in cups for the 8500 yet?

---

### Post by baoling on 2008-10-04
you can download driver Canon Pixma Ip4100 here:
[http://support-vn.canon-asia.com/EN/search?canonsearch=1&lang=EN&category=Inkjet+Printers&series=PIXMA&model=PIXMA+iP4200&menu=Download](http://support-vn.canon-asia.com/EN/search?canonsearch=1&lang=EN&category=Inkjet+Printers&series=PIXMA&model=PIXMA+iP4200&menu=Download)

---

### Post by logone on 2009-04-23
now i use in school ubuntu 8.10 and have a pixma ip4000r with network connection.

i have succesful print a page using the port socket://ipaddress:9100

bye!

---

### Post by CheesyD on 2009-04-28
> **logone said:**
> now i use in school ubuntu 8.10 and have a pixma ip4000r with network connection.

i have succesful print a page using the port socket://ipaddress:9100

bye!


I tried everything and then I tried the port socket://ipadress:9100 idea posted above. Worked like a charm for my ip4000. Thanks logone!!

---

### Post by cg0191 on 2010-05-22
Now day's under Lucid (10.04) just plug in the printer to the computer, cups activates the driver needed for your IP4000 and you're printing.. just like my Mac.

Interestingly when I first connected my Canon IP4000 printer it was switched OFF but Lucid still saw the USB identity of the printer! Amazing...

By the time I switched it on I was able to print a test page. Wow what an anticlimax to the old days of fighting to get every device working.

Kudos to all the hard working people who make this happen.

---

