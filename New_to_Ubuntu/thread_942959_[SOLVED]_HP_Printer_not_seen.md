---
title: "[SOLVED] HP Printer not seen"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by ranch hand on 2008-10-09
OK, things are moving right along.  The modem works, I'm online with the right OS.

Now if I can get the printer to work every thing will be great.

This is a Dell XPS 420.  We bought a couple months ago, complete with Vista Home Premium.
Vista I am happy to say is the reason that I now use Ubuntu.  The switch took time because of the modem problem.

The recommendation by most on the forums here was to go to a serial modem.  I went with an internal, mainly because this box had no serial ports.

Our old Deskjet 712c runs on a parallel port.  HP says that it will run under Vista with no problem.  Would not run on an adapter for USB to Parallel.  So, when I ordered the modem I also got a RS232 card.

This card came with a mini CD with drivers, which made the card work fine under Vista and the printer worked.

I can't print with Ubuntu though.  I am sure that this is fixable.  I believe that the printer is supposed to be supported, I could be wrong.

Below is my sys: lspci results.

tom@hogwash:~$ cd /sys

tom@hogwash:/sys$ lspci

00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller

00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge

00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)

01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]

04:04.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)

04:05.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)

04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

tom@hogwash:/sys$ 


I believe the card is seen (note the NetMos I/O controller).

So, what the heck do I do to get the printer to be seen so I can use it?

HELP!  please

---

### Post by phidia on 2008-10-09
The Ubuntu wiki has a guide for printers [here]("https://help.ubuntu.com/community/Printers"). Are you saying that you have an adapter card that changes the parallel port to usb? That could be tricky if that's the case.

Do you have a parallel port on the computer?

---

### Post by ranch hand on 2008-10-09
phidia
hello
The card is a pci card that gives me 2 serial and 1 parallel ports.

There were none on the box when we got it.

I do have a usb cable that has a parallel connector on the other end.  As far as I can see that is about whaat it is good for.  It looks interesting.

This card, with the supplied drivers worked under Vista and the printer worked there with the drivers that come with Vista.

The problem now is to get this combination of new card and printer to work under Ubuntu.

---

### Post by SunnyRabbiera on 2008-10-09
> **ranch hand said:**
> phidia
hello
The card is a pci card that gives me 2 serial and 1 parallel ports.

There were none on the box when we got it.

I do have a usb cable that has a parallel connector on the other end.  As far as I can see that is about whaat it is good for.  It looks interesting.

This card, with the supplied drivers worked under Vista and the printer worked there with the drivers that come with Vista.

The problem now is to get this combination of new card and printer to work under Ubuntu.

Well keep in mind linux isnt windows.
But its strange you are having issues because most HP printers are known to work with linux.

---

### Post by ranch hand on 2008-10-09
> **SunnyRabbiera said:**
> Well keep in mind linux isnt windows.
But its strange you are having issues because most HP printers are known to work with linux.

Oh, I know it is not win, that is why I am using it.

The HP site and my son both thought it should be no problem.  I don't think it is much of one.  If I could get to it, Ubuntu actually has a better generic tool kit for HP than does windows.

The point about it working under Vista was that it shows that the computer components, included the card I installed are capable of working together.  I was not sure about that when I installed it.

I am sure that the main problem here is me.  I have been looking at the tutorial recommended by phidia.  I did not find that on my search for such a thing because I specified Hardy.  This is for Dapper.

It says; "If you have a Parallel (LPT) printer you should first remove the "lp" entry from the file /etc/modules (see bug #29050).
Therefore open a terminal/console and enter the following command: sudo nano /etc/modules

Remove the "lp" entry, press Ctrl-X to exit and save the changes."

This all goes well up to the last and I can't get it to exit at all.  There are a lot of options non of which I am getting to work.  I looked up the file in file system first to see what the tutorial was talking about.  It looks pretty simple.  But then again, I may be too.

---

### Post by phidia on 2008-10-09
If this is the pci card: > 04:04.0 Communication controller: NetMos Technology PCI 9835 Multi-I/O Controller (rev 01)

And it's fully supported in linux (no sure thing). 
Then with the printer plugged in and powered on what does "lpstat -p" entered in a terminal output?

---

### Post by ranch hand on 2008-10-10
printer class disabled since Thu 09 Oct 2008 06:56:25 PM MDT -
	reason unknown
printer DESKJET_710C is idle.  enabled since Thu 09 Oct 2008 06:51:57 PM MDT
printer PDF is idle.  enabled since Mon 30 Jun 2008 10:34:31 PM MDT

When I tried to set up the printer I was told it wasn't right, no reason given and thatI should run hp-setup.  This I have not figured out because you have to do that as root.

It is about 1:30am and past my bedtime.  At least I got some of the way.  I got the qt python stuff needed for hp-toolbox, I think I got all of it.  About 4.75 hours at modem speed.  Did not loose connection once though.

I better hit the hay.  Groggy

---

### Post by angelsguitar on 2008-10-10
Seems that your printer is not supported by HPLIP (HP Linux Imaging and Printing).  Take a look at this:

[http://hplipopensource.com/hplip-web/models/deskjet/hp_deskjet_712c.html]("http://hplipopensource.com/hplip-web/models/deskjet/hp_deskjet_712c.html")

I don't know if there's any other way to make it work (maybe gutenprint, turboprint or something else?) but at least HPLIP won't work here.  So I believe the printer is the problem, not the card.

---

### Post by ranch hand on 2008-10-10
Well, I think I'll give up on this, at least for a while.  It is not as though it is a new printer.

I figured the card was fine when I got the printer to tbe seen.  Just unplugged and plugged in the printer a couple of times and it showed up.

I have to thank you folks for your time and help though.

---

### Post by phidia on 2008-10-10
I think angelsguitar is on the right track with trying a different driver.
I wouldn't recommend turboprint personally but maybe just seeing if another driver will work.

And for all printer questions in linux [openprinting]("http://www.linuxfoundation.org/en/OpenPrinting") is a great resource.

The openprinting site says that printer works "perfectly" in linux. It requires the pnm2ppa driver. 
See their info on that printer [here]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_712C").

---

### Post by ranch hand on 2008-10-10
I will check that out.

I also looked up what SUPPORTED HP printers use these ink cartridges.  I like them they are a lot bigger than most.  This is a good thing when you are 80 real rough scorio roads from the nearest sorce.  Scorio is volcanic shale.  Pretty earthy red.  Eats tires.  The tires we use should be good for about 60k miles highway.  We get about 20 if lucky.  Internet buying is our friend and we get USPS delivery 3 times a week.

---

### Post by ranch hand on 2008-10-10
I looked at the pnm2ppa driver driver info and it looks interesting.  Downloaded same as tar.gz.  Now what?  I can't open the readme files.  All I get is a box asking me for an application with which to open it.  I haven't a clue.

---

### Post by phidia on 2008-10-10
Try using "less" in a terminal to view the README(s).

Example > less README while in the correct directory.

You could also select an app like gedit from the box you mentioned.

---

### Post by ranch hand on 2008-10-10
I can't seem to get anything to work here.

The files are on the desktop.  I can open them in with Archive but then I can't do a thing with them and can't find the path to Archive.

---

### Post by phidia on 2008-10-10
> **ranch hand said:**
> I can't seem to get anything to work here.

The files are on the desktop.  I can open them in with Archive but then I can't do a thing with them and can't find the path to Archive.

Are the files still compressed? You can preview compressed files with the achieve manager but you do need to unpack them. But maybe I'm not understanding.

If they are compressed just right click on the package and select "Extract here" from the menu that appears.

---

### Post by ranch hand on 2008-10-10
I did that and saved the files to my download file.  I have to do something with the buggers though and am totally at sea which is tough here in Montana.

I have found that I can get to the file.  I just need to learn to type accurately.

I think I just need to study this more.  I don't know if it will sork or not but I am going to have to learn this sometime.  If nothing else, I found a printer cheap and better than this one.  I have a day or so to see if I can do this so I better get to it.

We are having a winter storm now.  Wet snow at 32F.  Trees are going to be down by morning.  I better go check stock and get the truck under cover or I'll be heating the door to get in.

I will report in the morning.

---

### Post by ranch hand on 2008-10-11
Well, this is interesting.

Have been trying to install the pnm2ppa stuff.  Got the install file open, have no  idea why I had trouble with that.

Got the install started alright then hung up on: 
install: cannot create regular file `/usr/local/bin/pnm2ppa': Permission denied

Got into the Nautilus File browser and changed the permission so that I had permission and that went in.

Then hit this:
install: cannot change permissions of `/usr/local/bin': Operation not permitted

Tried previous stuff to no avail.  Got looking in through the file and pnm2ppa appears to be there as an executable file 443.4kb.

I do appear to have hit a wall here.  Called my son in the state of Misery and we played for a while to no avail, although I did learn a few things and it was fun.

So that is where it stands now.  I am part way through an install and am stuck and hope that I can get it started again or at least back out some way that does not break anything.

Total of about 6 inches snow.  4 on the ground.  Very muddy under that.  Tough getting around.  Pretty.

---

### Post by phidia on 2008-10-11
Try using > sudo in front of the command(s) you previously tried that failed. You probably shouldn't change permissions on system files either.
If you need administrative privledge then "sudo", for Ubuntu, is how you do that. Good luck.

---

### Post by ranch hand on 2008-10-11
Most of this was done in sudo.

When that didn't work I will admit to getting a bigger hammer.  If you checked my profile you would have seen a mention of being a Blacksmith.

I had fun, about the last, on Win98 when I first got it.  Had it for about 3 weeks before having to reformat the HDD and reinstall.

The last part was not done in sudo.  I just tried that.  I hate it when people have a simple fix for stuff I have been fighting with.

Now if I can just get to /etc.  I'll give it a whack.

---

### Post by ranch hand on 2008-10-11
Maybe I won't have a whack at it.
From terminal;
Now, edit /etc/pnm2ppa.conf to choose your printer

Terminal;
tom@hogwash:/etc$ sudo  edit /etc/pnm2ppa.conf
Warning: unknown mime-type for "/etc/pnm2ppa.conf" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
tom@hogwash:/etc$ 

I tried looking to see if there is any new options in Admin/printing.  There is but I can't get it to work.  It it does reccomend the pnm2ppa driver from Foomatic.  I like the foomatic part.  But no way to get there.

At least I can drop one Terminal I had open.  Left it open out of concern that half installed stuff may be a little tough on the old girl.  Of coarse in MS this is not a problem, you just reload windows.  This something I do not miss.

I look forward to speaking to my upstart son about this again.  Sudo indeed.

---

### Post by ranch hand on 2008-12-06
This was fixed by getting a supported HP printer.  Deskjet 832c uses the same huge cartridges.  Works great.  Prints photos better than the old one and better than this one did under Vista.

---

