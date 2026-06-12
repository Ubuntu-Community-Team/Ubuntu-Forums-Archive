---
title: "HOWTO: Set up your Brother 2030/70 Laser printer"
date: 2006-01-30
forum: Outdated Tutorials &amp; Tips
---

### Post by ember on 2006-01-30
Hi,

so today I bought a nice new laser printer for my home office, namely a Brother 2030. This neat device is supported well by Linux as Brother provides drivers as well as a tutorial (they even provide .debs). So generally speaking, this is an A+ device for Linux, yet there are some glitches.

So here's a 7 step tutorial to setting up your printer, mainly taken from [URL="http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html#printset"]here/URL]:

1) Download the right .deb for your model (LPR driver) [here]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de").

2) Download the right .deb for your model (CUPS wrapper) [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de").

3) Open a terminal and become root (or use sudo in front of all following commands):
```

su

```


3) Install the LPR driver first with:
```

dpkg -i brhl2030lpr_1.1.2-3_i386.deb

```

(the name may change for your model)

4) STOP! Now we don't install the cups wrapper, but we do the following first:
```

ln -s /etc/init.d/cupsys /etc/init.d/cups

```
Apparently the Brother developers were mistaken about the name of cups, because it differs in Debian from other distributions (i.e. it is named cupsys instead of cups)

5) Now install the cups wrapper:
```

dpkg -i cupswrapperhl2030_1.0.0-1_i386.deb

```
(may again be differently named depending on your printer model)

6) Open a browser and go to [http://localhost:631/]("http://localhost:631/"). You should find your printer there and you can configure it's every option. 

7) Have fun, print fast and enjoy yourself ;)

Best regards,
ember

---

### Post by stalefries on 2006-01-30
Could you rename this to 'How to Install a Brother printer"? It would be the best if you could.

---

### Post by ember on 2006-01-30
I have not tested it with models other than the 2030. Yet it should work.

---

### Post by arnieboy on 2006-03-07
excellent howto this one! worked out of the box for my Brother HL-2040.

---

### Post by fergus on 2006-03-29
arnieboy,

how do you like your 2040?  I am looking into getting one...

fergus

---

### Post by arnieboy on 2006-03-29
[QUOTE=fergus]arnieboy,

how do you like your 2040?  I am looking into getting one...

fergus[/QUOTE]
works great. would have been even better if it had supported duplex printing.

---

### Post by Zelut on 2006-04-01
I am shopping for a laser printer for my home office & stumbled upon this.  I had originally been shopping for an HP but after reading about them being in MS' pocket I think I'll look someplace else.

Locally I can get a Brother 2040 for about $125.  Can anyone offer info about it?  Fairly fast? Good quality? Affordable toner?  Thanks

---

### Post by phux on 2006-04-25
It just wont work well with gnome :( (default printing works, but no settings possible)

I installed my HL-2030 on a Kubuntu 5.10 and Ubuntu 6.06... both worked perfectly, but my Ubuntu 5.10 wont print the way i want. Default printing works, but it simply ignores 2-on-1-page-settings.

After the installation, exactly as written above, the HL2030 appears on Printers, as normal. It can be swtiched to 300 or 600 dpi, driver-list says "HL-2030 for Cups" and everything seems to be correct.
BUT as written before... it wont react to any settings, but print default style on and on...

*HELP*

---

### Post by ramtuff21 on 2006-05-01
[QUOTE=kuyaedz]I am shopping for a laser printer for my home office & stumbled upon this.  I had originally been shopping for an HP but after reading about them being in MS' pocket I think I'll look someplace else.

Locally I can get a Brother 2040 for about $125.  Can anyone offer info about it?  Fairly fast? Good quality? Affordable toner?  Thanks[/QUOTE]

I love it but I don't do any intensive printing.  It's pretty fast for an inexpensive laser printer.  I got mine used (refurbished) throuhg TigerDirect for about $70.  They also sell toner through Tiger pretty cheap.  If anybody knows of anything cheaper I'd love to hear about it.

---

### Post by BobSongs on 2006-05-15
Well, it's very similar to [my tutorial]("http://www.ubuntuforums.org/showthread.php?t=105703") for the MFC210C. The pattern looks familiar. Excellent.

Well, figured I should put a link in this tutorial to mine for those who haven't found what they're looking for.

Cheers!

---

### Post by helmet on 2006-06-04
hey

this worked great on Breezy but to get it to work in Dapper (fresh install) here's what I did:

the device URI initially shows up as 'usb:/dev/usb/lp0' or something like that, and CUPS or whatever doesn't know what to do with it. configure the printer again, selecting Brother and the HL2040 for Cups driver, and then select the usb brother thing. the device URI shows up now as usb://Brother/HL-2040%20series (for my HL2040 anyway)

and everything works fine :D

---

### Post by troypiggo on 2006-06-15
[QUOTE=helmet]hey

this worked great on Breezy but to get it to work in Dapper (fresh install) here's what I did:

the device URI initially shows up as 'usb:/dev/usb/lp0' or something like that, and CUPS or whatever doesn't know what to do with it. configure the printer again, selecting Brother and the HL2040 for Cups driver, and then select the usb brother thing. the device URI shows up now as usb://Brother/HL-2040%20series (for my HL2040 anyway)

and everything works fine :D[/QUOTE]

I've got the same printer, and a "clean" install of Dapper Server, but can't get it to install.

When I get to the sudo dpkg -i cupswrapperhl2040_1.0.0-1_i386.deb stage I get this error:

[FONT="Courier New"](Reading database ... 27236 files and directories currently installed.)
Preparing to replace cupswrapperhl2040 1.0.0-1 (using cupswrapperhl2040_1.0.0-1_i386.deb) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2040-1.0.0: line 22: lpadmin: command not found
 * Restarting Common Unix Printing System: cupsd
   ...done.
Unpacking replacement cupswrapperhl2040 ...
Setting up cupswrapperhl2040 (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperHL2040
 * Stopping LPRNG printer spooler lpd
   ...fail!
 * Restarting Common Unix Printing System: cupsd
   ...done.
/usr/local/Brother/cupswrapper/cupswrapperHL2040-1.0.0: line 488: lpadmin: command not found[/FONT]

How do I get that command to work?  I don't understand your post quoted above.

[FONT="Courier New"]$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04f9:0028 Brother Industries, Ltd
Bus 002 Device 001: ID 0000:0000[/FONT]

---

### Post by troypiggo on 2006-06-15
[QUOTE=troypiggo]I've got the same printer, and a "clean" install of Dapper Server, but can't get it to install.

When I get to the sudo dpkg -i cupswrapperhl2040_1.0.0-1_i386.deb stage I get this error:

[FONT="Courier New"](Reading database ... 27236 files and directories currently installed.)
Preparing to replace cupswrapperhl2040 1.0.0-1 (using cupswrapperhl2040_1.0.0-1_i386.deb) ...
/usr/local/Brother/cupswrapper/cupswrapperHL2040-1.0.0: line 22: lpadmin: command not found
 * Restarting Common Unix Printing System: cupsd
   ...done.
Unpacking replacement cupswrapperhl2040 ...
Setting up cupswrapperhl2040 (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperHL2040
 * Stopping LPRNG printer spooler lpd
   ...fail!
 * Restarting Common Unix Printing System: cupsd
   ...done.
/usr/local/Brother/cupswrapper/cupswrapperHL2040-1.0.0: line 488: lpadmin: command not found[/FONT]

How do I get that command to work?  I don't understand your post quoted above.

[FONT="Courier New"]$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04f9:0028 Brother Industries, Ltd
Bus 002 Device 001: ID 0000:0000[/FONT][/QUOTE]


*Never mind.  I had installed cupsys but not cupsys-client.  All good now.*

---

### Post by metapundit on 2006-08-10
Ember said
> I have not tested it with models other than the 2030. Yet it should work.

I just wanted to note that this worked for my 2070N as well. After the lpr and cups .debs were installed, I had to modify the printer in my System panel to be a network printer (by default it is installed as USB printer). Select Properties->Interface, hit the change button and type in the IP of your printer). With the addition of that configuration detail, it's working great! 

This is on a fresh install of Kubuntu 6.06...

---

### Post by A_608 on 2006-08-22
Just a note. I had to go into the printer-properties-connection and choose the local printer option for my printer to work.

---

### Post by Sin_fe on 2006-09-16
Where do you choose "more than one page in one paper" for this model?
I just can't find it.

Thanx in advanced.

---

### Post by KillerKiwi on 2006-09-20
Beutiful, install brother fax 2850 printing over samba share via a winxp machine... got to love the ubuntu community.

Lazyweb - Has any body added this to the wiki?

---

### Post by haiku99 on 2006-10-02
**edit 01/07::     did a clean install of Edgy, no problems installing the hl-2040 this time(below trouble was w/ Dapper) and the this howto worked fine again....**


thanks, this got for my hl-2040 printing, however I ran into a couple of frustrating problems with setup that others may also experience....paper size was defaulting to A4 causing alignment to be off, resetting it to letter at system>administration>printing did not take (although it appeared to on the menu), this is evidently a common problem...when I went to [http://localhost:631/](http://localhost:631/) to make changes CUPS asked for a user id and password, mine did not work, also a common problem from what I've read.  Anyway, there is a good workaround by bennyj as follows
"I was having the same problem with the user and password not being accepted in the cups web interface.This is what fixed it for me.

open a terminal
type in "adduser cupsys shadow" (without quotes)press enter.dont forget sudo!
then type in /etc/init.d/cupsys restart

You should see it restarting in the terminal.
now browse to the cups web interface and add your printer.

Hope this helps
Benny
Reply With Quote"

once I did that and corrected my paper size all was well....geez linux/ubuntu is a royal PITA sometimes...but I'm sticking with it...](*,) :)

---

### Post by Dutch on 2006-10-14
Hi I would like to ad:

[http://www.marzocca.net/linux/ubuntux31.html](http://www.marzocca.net/linux/ubuntux31.html)

```

    *  Root and CUPS

Soon after installation has finished, and changed the wallpaper, I let the user root come through:
sudo password root

and assigned it a password. This is because often I will need to be a real root, as in CUPS server manager. By the way, if you need to get access to the CUPS manager from its web interface (http://localhost:631) you need your root password, but you also need to add the cupsys user to this group:
sudo adduser cupsys shadow

and restart cups server:
sudo /etc/init.d/cupsys restart

 
```

That did it to me !

---

### Post by jeecol on 2006-10-18
Thank you all!

   I followed the methods to install my Brother HL-2070N (net printer), and now I can use it via internet. However, it's shame on me, as a Linuxer, I got the IP of my printer, when I installed the driver on another computer in my home (it's MS win with brother driver CD). Can anyone tell me how to know the IP of the printer by Ubunut? Thanks. [I have several computers at home, a D-link router and a cable modem]

-----------
jeecol is one dollar

---

### Post by hellbringer on 2006-10-19
> **phux said:**
> It just wont work well with gnome :( (default printing works, but no settings possible)

I installed my HL-2030 on a Kubuntu 5.10 and Ubuntu 6.06... both worked perfectly, but my Ubuntu 5.10 wont print the way i want. Default printing works, but it simply ignores 2-on-1-page-settings.

After the installation, exactly as written above, the HL2030 appears on Printers, as normal. It can be swtiched to 300 or 600 dpi, driver-list says "HL-2030 for Cups" and everything seems to be correct.
BUT as written before... it wont react to any settings, but print default style on and on...

*HELP*

I'm having the same problem, my DCP-315CN ignores my changes to the settings, any clues?

---

### Post by hellbringer on 2006-12-06
*bump*

---

### Post by ajm2005 on 2006-12-09
:)

---

### Post by Nano on 2006-12-17
Let's see if you can help me, guys, on this.
I have the same printer but shared from a Windows machine in a small network.
How can I add it to my Ubuntu box?

---

### Post by rusyear04 on 2007-01-04
hi alltogether!

i did recently buy an HL-2030 myself and now want to install it/plug in into my ubuntu-machine (edgy eft)  as well...
when i go to "add printer" i do get a recognized printer *Brother HL-2030 series*. i choose that one.
next step is to choose the driver. here i do run into "problems" since i can only find an **HL-2060** driver. i'm a bit afraid of simply trying it out since i do have quite a problem with my old printer & second pc under ubuntu...

anybody has a clue what/how to do this is *edgy*?

thanx!

---

### Post by prosonik on 2007-01-06
Hi

You need to tell cups where the .ppd file is.

After following the directions,
i did a 
```
#sudo updatedb then
locate 2030 | grep 'ppd'

```
That resulted with:
```
/usr/share/cups/model/HL2030.ppd
```

Cut and paste the location of your .ppd file into cups and your good to go.

Now, I have to figure out how to print index cards

Prosonik

---

### Post by [bigmac] on 2007-01-08
> **rusyear04 said:**
> hi alltogether!

i did recently buy an HL-2030 myself and now want to install it/plug in into my ubuntu-machine (edgy eft)  as well...
when i go to "add printer" i do get a recognized printer *Brother HL-2030 series*. i choose that one.
next step is to choose the driver. here i do run into "problems" since i can only find an **HL-2060** driver. i'm a bit afraid of simply trying it out since i do have quite a problem with my old printer & second pc under ubuntu...

anybody has a clue what/how to do this is *edgy*?

thanx!

It works perfectly for me with the hl-1250 driver, try choosing that one.

---

### Post by aef110 on 2007-01-27
I just purchased the HL-2030 to replace my dying HL-1450. I installed the native Brother drivers following all instructions on this thread, and while the print quality is beautiful, all pages are printed off-center.

I've been searching for solutions and have been unable to solve this problem. I did install Netpbm in order to make use of the pbmpage command, but running it from a terminal only produces on-screen garbage and sends nothing to the printer. I should note I'm using A4 paper, and I've checked and double-checked all settings for paper size and document page size to ensure everything's set to A4. I've tried printing from various programs including OpenOffice, Kpdf and Adobe Reader 7, all with the same error.

I deleted and reinstalled the printer using the instructions on this thread.  A test page sent from CUPS prints perfectly. Still, other programs print pages too far to the right -- which is not the case with my Canon iP4000 from the same machine. This leads me to believe that there's something else in the print chain interfering with the printing.

I'm quite new to Linux and would be very grateful for any assistance.

---

### Post by ym4546 on 2007-02-19
> **aef110 said:**
> I just purchased the HL-2030 to replace my dying HL-1450. I installed the native Brother drivers following all instructions on this thread, and while the print quality is beautiful, all pages are printed off-center.

I've been searching for solutions and have been unable to solve this problem. I did install Netpbm in order to make use of the pbmpage command, but running it from a terminal only produces on-screen garbage and sends nothing to the printer. I should note I'm using A4 paper, and I've checked and double-checked all settings for paper size and document page size to ensure everything's set to A4. I've tried printing from various programs including OpenOffice, Kpdf and Adobe Reader 7, all with the same error.

I deleted and reinstalled the printer using the instructions on this thread.  A test page sent from CUPS prints perfectly. Still, other programs print pages too far to the right -- which is not the case with my Canon iP4000 from the same machine. This leads me to believe that there's something else in the print chain interfering with the printing.

I'm quite new to Linux and would be very grateful for any assistance.

I use an HL-2070N over the network and have this same problem. It worked flawlessly in Kubuntu 6.06. I've only had this problem since upgrading to 6.10. I think Brother did update their driver by the time I downloaded it for 6.10... anyone have ideas on a cause or a fix for this?

Thanks.

---

### Post by conxorxa on 2007-03-10
> **A_608 said:**
> Just a note. I had to go into the printer-properties-connection and choose the local printer option for my printer to work.


I'll flesh this out a little because it tool me a while to figure it out until I found the steps in the howto for another printer: 

[http://ubuntuforums.org/showthread.php?t=302960](http://ubuntuforums.org/showthread.php?t=302960)

[INDENT]
In the menu go to System Settings, Printers
If the printer is connected to the same PC then the driver has already been installed and selected
Select the printer and make it default if required.
While having the printer selected, click on the Properties tab and select the Interface icon on the right hand side. If the URI: usb:/dev/usb/lp0 shows, this is incorrect. click the Change button, enter your password for administrator mode. Now select Local printer, Next, then Brother MFC-215C and Finish.
You should now see URI: //Brother/MFC-215C
Right-click the MFC210C and click “Test Printer”. See if test page is received.
[/INDENT]

[Just substitute HL-2030 for MFC-215C]

---

### Post by conxorxa on 2007-03-10
Does anyone know how to set up manual duplex printing?  According to the Brother website:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html"), 
it should be an option but it doesn't appear in the printer options in the CUPS web interface.

---

### Post by printmefine on 2007-03-10
> **ember said:**
> Hi,

so today I bought a nice new laser printer for my home office, namely a Brother 2030. This neat device is supported well by Linux as Brother provides drivers as well as a tutorial (they even provide .debs). So generally speaking, this is an A+ device for Linux, yet there are some glitches.

So here's a 7 step tutorial to setting up your printer, mainly taken from [URL="http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html#printset"]here/URL]:

1) Download the right .deb for your model (LPR driver) [here]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de").

2) Download the right .deb for your model (CUPS wrapper) [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de").

3) Open a terminal and become root (or use sudo in front of all following commands):
```

su

```


3) Install the LPR driver first with:
```

dpkg -i brhl2030lpr_1.1.2-3_i386.deb

```

(the name may change for your model)

4) STOP! Now we don't install the cups wrapper, but we do the following first:
```

ln -s /etc/init.d/cupsys /etc/init.d/cups

```
Apparently the Brother developers were mistaken about the name of cups, because it differs in Debian from other distributions (i.e. it is named cupsys instead of cups)

5) Now install the cups wrapper:
```

dpkg -i cupswrapperhl2030_1.0.0-1_i386.deb

```
(may again be differently named depending on your printer model)

6) Open a browser and go to [http://localhost:631/]("http://localhost:631/"). You should find your printer there and you can configure it's every option. 

7) Have fun, print fast and enjoy yourself ;)

Best regards,
ember



Reposting here, since I did not get a reply in another forum. 


I installed my Brother Printer following these instructions.

After I restarted my computer and went to System->Administration->Printing , I get the error "The CUPS server could not be contacted".

If I do a " sudo /etc/init.d/cupsys restart" , it says "sudo: /etc/init.d/cupsys: command not found"

I would appreciate help on this - linux noob here :)

Thanks all.

---

### Post by mp035 on 2007-03-12
Hi printmefine,

It looks as though step 4 didn't work for some reason:

```
ln -s /etc/init.d/cupsys /etc/init.d/cups
```

try this:
```
 sudo ln -s /etc/init.d/cupsys /etc/init.d/cups 
```

if it works great, if it doesn't try these two commands and post the resonse you get on the terminal:
```
 
you@yourlinuxbox:~$ ls -l  /etc/init.d/cupsys

// your shell will print some info about the file here //

you@yourlinuxbox:~$ ls -l  /etc/init.d/cups

// it will print something about this file here//

you@yourlinuxbox:~$

```

mine looks like this:
```

mark@linuxbox:~$ ls -l  /etc/init.d/cupsys
-rwxr-xr-x 1 root root 2130 2006-10-10 02:54 /etc/init.d/cupsys
mark@linuxbox:~$ ls -l  /etc/init.d/cups
lrwxrwxrwx 1 root root 18 2007-03-12 15:01 /etc/init.d/cups -> /etc/init.d/cupsys
mark@linuxbox:~$ 

``` 

regards

---

### Post by mp035 on 2007-03-12
Hi all, 
I have the same problem as aef10 and ym4546 mentioned in post #29, although I am using an HL-2040 (Australian version).  For clarity I will repeat the problem:

The printer constantly prints out to the upper right of the page, even though the print previews show the printing to be in the centre.  It appears as though the "A4" setting is somehow invalid.

It seems to be printing in "letter" size, even when the paper setting is set to A4.

If I change the size to "legal", the printer prints off the page as expected, but if I change it back to A4, it then stays in "legal" size, rather than the original "letter".

It almost seems that what ever parameter is passed to the driver to specify A4,  is invalid, so the driver stays with the previously selected paper size.

I have checked that the printer is set to A4 in cups (got it to let me log in :)), in KDE system settings, and in open office.

It prints in the centre when I print from my windows machine (2 pc's connected to 1 printer, windows is connected to paralell and ubuntu is connected to the usb) 

All applications on my ubuntu have the same problem. (Acrobat, Open office, etc...)

It worked fine under kubuntu 6.06 Dapper.

PLEASE HELP!!! ](*,) 

Thanks.

---

### Post by smylie on 2007-03-18
> **conxorxa said:**
> Does anyone know how to set up manual duplex printing?  According to the Brother website:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html"), it should be an option but it doesn't appear in the printer options in the CUPS web interface.


I have a  HL-2040 that i've been able to get duplex running on okay.

I found some apps (like kdevelop or gedit) just work with their printer options.

Failing that, you can get duplex by using lpr directly:

```
  $ lpr -P YOUR_PRINTER_NAME_GOES_HERE -o number-up=2 your_file.txt
```

Then it just depends on the application you're trying to print from. 

For firefox (what i particularly wanted this for), there will be  a default printer in the printer list called "default", that you can enter a customized command for (ie, the above).


this is really stupid . . . it should be much easier to use = /

---

### Post by dapicester on 2007-03-29
Hi, my HL2030 is actually working, but i cannot share it with samba. I would like to know what should i do in order to share my printer with samba, since modifying the [printers] and [print$] section of smb.conf doesn't work.
Thanks

---

### Post by haiku99 on 2007-04-04
thanks again, this also worked for a Brother MFC-7220....FWIW since I had previously installed a HL-2040 attempting to install the new packages gave error messages until I completely removed the old ones, this was easy to do via Synaptic, found them by searching for the model number and cupswrapper

---

### Post by printmefine on 2007-05-14
> **mp035 said:**
> Hi printmefine,

It looks as though step 4 didn't work for some reason:

```
ln -s /etc/init.d/cupsys /etc/init.d/cups
```

try this:
```
 sudo ln -s /etc/init.d/cupsys /etc/init.d/cups 
```

if it works great, if it doesn't try these two commands and post the resonse you get on the terminal:
```
 
you@yourlinuxbox:~$ ls -l  /etc/init.d/cupsys

// your shell will print some info about the file here //

you@yourlinuxbox:~$ ls -l  /etc/init.d/cups

// it will print something about this file here//

you@yourlinuxbox:~$

```

mine looks like this:
```

mark@linuxbox:~$ ls -l  /etc/init.d/cupsys
-rwxr-xr-x 1 root root 2130 2006-10-10 02:54 /etc/init.d/cupsys
mark@linuxbox:~$ ls -l  /etc/init.d/cups
lrwxrwxrwx 1 root root 18 2007-03-12 15:01 /etc/init.d/cups -> /etc/init.d/cupsys
mark@linuxbox:~$ 

``` 

regards


Hi mp035, 

Sorry, I was following the other thread I had posted on this topic (no replies there though :) ) . 

sudo ln -s /etc/init.d/cupsys /etc/init.d/cups  did not  work.  I get the following :

ln: creating symbolic link `/etc/init.d/cups' to `/etc/init.d/cupsys': File exists

ls -l  /etc/init.d/cupsys  gives :

ls: /etc/init.d/cupsys: No such file or directory
 

ls -l /etc/init.d/cups gives:

lrwxrwxrwx 1 root root 18 2007-03-10 10:52 /etc/init.d/cups -> /etc/init.d/cupsys


Thanks for your help!

---

### Post by gerkin on 2007-07-06
this worked for me:

See: my post here: [http://ubuntuforums.org/showthread.php?t=440415&highlight=brother+hl2040+printer](http://ubuntuforums.org/showthread.php?t=440415&highlight=brother+hl2040+printer) for a possible solution

---

### Post by sumithar on 2007-09-22
Thanks bro.  I bought an HL-2040 recently on clearance w/o even thinking if it would work with Linux.
I followed your tutorial blindly and presto, it works.
Regards

---

### Post by gnarly_buttons on 2007-11-10
The tutorial/how-to is great.  It works perfectly when I use 32-bit Kubuntu.  Are there drivers somewhere for 64-bit Kubuntu?

Thanks,
Scott

---

### Post by Max Roswell on 2007-11-13
Not for nothing, but I just wanted to post that I set up my 2070N printer and got it working first try by doing nothing but going to System > Administration > Printing and using default everything.

I'm on Feisty.  Just FYI.

---

### Post by Yleeyas on 2007-12-15
Thanx ember,

Just installed my HL2040 using this HowTo and worked like a charm :)

The only hiccup is the "http://localhost:631/printers/" part; when I try to manage printers I get  " error: bad request"

I do have access to the setup via system>admin>printing so all is well \\:D/

thanx again,

yleeyas

edit: Scratch the hiccup part, the link started working all of a sudden

---

### Post by AgentZ86 on 2008-01-20
> **ember said:**
> Hi,

so today I bought a nice new laser printer for my home office, namely a Brother 2030. This neat device is supported well by Linux as Brother provides drivers as well as a tutorial (they even provide .debs). So generally speaking, this is an A+ device for Linux, yet there are some glitches.

So here's a 7 step tutorial to setting up your printer, mainly taken from [URL="http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html#printset"]here/URL]:

1) Download the right .deb for your model (LPR driver) [here]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de").

2) Download the right .deb for your model (CUPS wrapper) [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de").

3) Open a terminal and become root (or use sudo in front of all following commands):
```

su

```


3) Install the LPR driver first with:
```

dpkg -i brhl2030lpr_1.1.2-3_i386.deb

```

(the name may change for your model)

4) STOP! Now we don't install the cups wrapper, but we do the following first:
```

ln -s /etc/init.d/cupsys /etc/init.d/cups

```
Apparently the Brother developers were mistaken about the name of cups, because it differs in Debian from other distributions (i.e. it is named cupsys instead of cups)

5) Now install the cups wrapper:
```

dpkg -i cupswrapperhl2030_1.0.0-1_i386.deb

```
(may again be differently named depending on your printer model)

6) Open a browser and go to [http://localhost:631/]("http://localhost:631/"). You should find your printer there and you can configure it's every option. 

7) Have fun, print fast and enjoy yourself ;)

Best regards,
ember

I'm installing on gutsy, but for some reason I type ln -s /etc/init.d/cupsys /etc/init.d/cups as su and I get this:

ln -s /etc/init.d/cupsys /etc/init.d/cups
ln: creating symbolic link `/etc/init.d/cups' to `/etc/init.d/cupsys': Permission denied

strange why would I get permission denied for the super user ??

I also get this when trying this:

dpkg -i mfc240clpr-1.0.0-9.i386.deb
dpkg: requested operation requires superuser privilege

Please advise
I'm using Gutsy with all the latest updates

I actually installed the LDR and the Cups wrapper initially by just clicking on the download and installing with gecko or something, so maybe my install didn't go to the correct place but still I don't understand these super user errors cause I can login with su username and then pass, but if I just type su at the terminal then then pass it does not login to anything.

Anyhow this is strange

Additionally I can go to the [http://localhost:631](http://localhost:631)
and the new printer is there etc. shows as online and I can select test print, but the printer just does not print anything and and it's shows in the printer progress tool in Ubuntu that it's processing, but I guess i'ts not going to the correct place.

Seems like it should be working, and I don't know how to diagnose further, I think i'ts something to do with the sym link command, but since I'm having a permission issue I can't complete this portion 

Anyhow I'll keep working on it.


Please advise
Thanks

---

### Post by AgentZ86 on 2008-01-20
I turned off the printer then back on again, just to see if something would change. No effect.

I attempted reinstall and now I get error regarding permission for the installation.
I did  not do any uninstall prior to the attempt but I get errors and now also I noticed that my printer is not in the printer list or at: [http://localhost:631](http://localhost:631)

When clicking on the file and allowing the package installer to install the cups wrapper, i get an error cannot open, either corrupt or not permissions.

So I don't know if this has to do with the fact that I've already installed it, but because of this I now have a problem with synaptic. I was going to attempt to uninstall the driver with synaptic but I get errors there too now ?

Now Synaptic give me this error on startup and won't run:

E: The package mfc240ccupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Now what ? I'm starting to break stuff. ??

:confused:

---

### Post by tora201 on 2008-03-31
Did ya get it going? Tutorial worked fine with my 2040 in Mint Daryna with latest updates. No problems whatsoever. Strange that you had problems.....

---

### Post by autocrosser on 2008-04-01
Just a note: Brother printer .debs are available in Hardy--We worked to get them in the repositories.

---

### Post by AgentZ86 on 2008-04-01
> **tora201 said:**
> Did ya get it going? Tutorial worked fine with my 2040 in Mint Daryna with latest updates. No problems whatsoever. Strange that you had problems.....

Not sure if you were asking me, but yes I've got it working.

And wrote myown tutorial also in another post for my specific printer, thanks all

---

### Post by Elderlygent on 2008-07-22
Sorry, I can't get the screenshot to come up in the text. I'll try again

---

### Post by wirespot on 2008-08-08
If the cupswrapper .deb fails to install, try doing this:

```
sudo mkdir -p /usr/share/cups/model/
```

Apparently it wants to put its PPD file there but the directory doesn't exist and the deb doesn't create it itself.

I just finished installing a 2030 and it works great. The above was the only kink. I like the 2030 driver from the Brother debs better cause it's got toner saving, otherwise it's pretty much the same as the Gutenprint 2060 driver.

---

### Post by mattsl on 2008-09-07
FYI: This HOWTO works for the hl-2035 model too (I'm on Hardy).

---

### Post by Jense on 2009-01-28
Old post, but to make it work in Ibex you have to create the directory ```
/usr/share/cups/model/
```.
Else I got this error message on configuring the wrapper
```
/usr/local/Brother/cupswrapper/cupswrapperHL2030-2.0.1: 64: cannot create /usr/share/cups/model/HL2030.ppd: Directory nonexistent                                                                           
 * Restarting Common Unix Printing System: cupsd                                               [ OK ] 
cp: cannot stat `/usr/share/cups/model/HL2030.ppd': No such file or directory                         
dpkg: Fehler beim Bearbeiten von cupswrapperhl2030 (--install):                                       
 Unterprozess post-installation script gab den Fehlerwert 1 zurück                                    
Fehler traten auf beim Bearbeiten von:                                                                
 cupswrapperhl2030                                                           
```

Thanks a lot for writing this howto, helped me a great deal.

---

### Post by artartart on 2010-05-31
> **Jense said:**
> Old post, but to make it work in Ibex you have to create the directory ```
/usr/share/cups/model/
```.
Else I got this error message on configuring the wrapper


Thanks. Works fine for HL-2030 on Ubuntu 10.04.

---

### Post by lemik on 2010-06-26
I have HL-2035. Ubuntu 10.04 I did everything as in the first post, and printer does not print. Where to look for error?

---

