---
title: "Howto: Printer Brother MFC-215C on Kubuntu Dapper"
date: 2006-09-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-09-22
Hi,
  Thanks to Bobsongs and the very helpfull Brother support people I have managed to get my Brother MFC-215C printing, scanning, faxing and sharing with Windows and Kubuntu. I have decided to publish this seperately from the MFC-210C thread.

_**Howto:Printer Brother MFC215C Install on Kubuntu Dapper.**_

Thanks to Brother for their excellent linux support and the members on the Ubuntu forums who provided some much needed information, special thanks to BobSongs for his contribution. Anyone else who recognises a line or so, thank you, everyone appreciates your input. This howto only covers the Kubuntu Dapper versions, but I am sure that it can be made to run on Ubuntu as well without many changes.

By the way, please note that there are new firmware updates on the Brother website. The firmware updater is only in Windows, so you will need to update while logged in via Windows. I suggest you read this on the website as there is a change to the ink level warnings etc. included.

Download the following files from the Brother Website,   CUPSwrapper , LPRdriver  , Fax CUPSwrapper , Fax LPRdriver and the Sane Scanner backend

Note that some printer driver files for the MFC-215c are not yet ready and Brother suggests that the files for the MFC-210C are used used in the meantime. The direct links are for the latest at time of writing, so check the website for any updates and use those if available.

There are some preparations required, such as installing C Shell, Sane, (and Xsane if you use Ubuntu, Kubuntu uses Kooka) Some folder corrections needed to be done as the .deb files from the Brother site are for debian and was not compiled specifically for Kubuntu Dapper.
You can install the .deb files in many ways, dpkg -i, local repository or CD via Synaptic. I have used the Kubuntu shortcut from the gui to keep the instructions short and clear. You can also use krusader or konqueror for creating and moving files in root mode etc.

Preparations
Create a folder on the desktop, called “brother”, and put all downloaded files in that folder.
Use Synaptic to install csh (C Shell) and sane from the repositories
Create a new directory in /var/spool/lpd                 (Dapper needs lpd directory which is not present)
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups            (Dapper uses CUPS and file wants CUPSYS - link)

Install the printer drivers:

NB: Ensure printer is switched off

Right click on the mfc210clpr-1.0.2-1.i386.deb file and select Kubuntu Package Menu, Install Package
Right click on the cupswrappermfc210c_1.0.0-1_i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer back on

In the menu go to System Settings, Printers
If the printer is connected to the same PC then the driver has already been installed and selected
Right-click the MFC210C and click “Test Printer”. See if test page is received

Printer sharing in Kubuntu Dapper

To share a dedicated printer on a specific PC with other PC's on the same network you need Samba  installed for sharing with Windows and NFS for sharing with other Linux PC's. Install these with Synaptic from the repositories.
Now go to Menu, System Settings, Sharing, File Sharing and you should see a list under Shared Folders that includes a line /var/lib/samba/printers/ with a tick or a cross under the Samba and NFS column. To enable sharing of the printers under Samba and NFS, go into Adminstrator mode, select Simple Sharing and select both Samba and NFS. Once you have two green ticks it means that you can share with both linux and/or Windows PC's. You might as well do the same for any folders you want to share. Create them and enable sharing and allow it via NFS and/or Samba.
Now to check that you can see the shares, reboot the PC's and then click on the PC icon called System Menu in the kicker bar. Select Remote Places, Samba Shares and then open the Workplaces. You should see your own PC and the remote PC's. Check that this is possible on all the PC's. Now you can be sure what can be seen on what PC. Note, you will not see the printers in here, but only shared drives and folders.
If you are using all linux PC's you will not need to install drivers on the client PC, but only on the server PC that has the printer connected to it (we are not refering to a network printer here, that has its own IP address, but a dedicated printer on a PC that is shared via that PC).
If your sharing and network is properly setup with the server PC, the printers installed on the server PC will show up in your printer list as if they were installed on your PC (nice CUPS and linux feature) and you just use them.
If the server PC is a Windows PC you will have to install printer drivers for the printer on the Kubuntu PC by going to Menu, System Settings, Printers, Add, Add Printer Class.
Now the Add Printer Wizard opens and click next, select SMD Shared Printer Windows, next,
Use anonymous, next, SMB Printer Settings – use Scan, find the correct printer, click on it and it will be entered in the fields, next etc. until installation complete and test page works. Thats it, now you have a shared printer!!

Now for some bug clearing:
The above will not work properly as it seems as if the CUPS configurations in Dapper are not set by default to allow sharing of printers on a linux network. Do not ask me why, I am only a messenger! Here is an easy and quick solution to correct this:
Go to the  /etc/cups/cups.d/ports.conf there should be the following lines
Listen 631
Listen /var/run/cups/cups.sock

It is likely that the line Listen localhost : 631 is present so change it to Listen 631 and save

Go to /etc/cups/cups.d/browse.conf there should be the following line
Browsing on

It is likely that Browsing off is present, so change it to Browsing on and save

Now you can reboot and see if you can see the printer under printer settings


Camera media card reading;
You can just insert the media card and it will appear as a usb flash disk on Kubuntu and just copy, read or whatever from and to it. Just do not change the special file structure that your camera created as it may make the card unusable in your camera.

Fax Printing :

With appreciation to Brother Solutions Centre with their help and prompt response to queries on configuring BRFAX.
Brother has provided a very usefull function that allows faxes to be sent directly from a PC, via your Brother MFC. It works on linux and even from other linux PC's connected to the same lan. The only thing missing at the moment is good documentation. The test was done on the Kubuntu version of Ubuntu, but should work on Ubuntu as well. The actual printer configuration can be done via the CUPS web interface ([http://localhost:631/printers)](http://localhost:631/printers)), but I used the Kubuntu (KDE) printer configuration from the menu, as some CUPS configurations, such as printer sharing and administrator mode are not enabled by default in Kubuntu Dapper. Details can be found in the forums on this and how to correct.

Ensure that Sun-Java5-jre is installed from the repositories using your package manager (i.e. Synaptic, adept, apt-get etc,as this runs the applet /usr/local/Brother/fax/brmfcfax.jar, which is the dialup gui for your PC-Fax.
Now you have to set this version as default:
sudo update-alternatives –config java
You will now get a selection that shows a list and which is in use.
Select the version: /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
Now while the PC is SWITCHED OFF, install the two special drivers from the Brother website. The order of the driver installation is important, first lpd, then cups.
Install both in this sequence:

Right click on the brmfcfaxlpd-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package
Right click on the brmfcfaxcups-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer BACK ON:

In the menu go to System Settings, Printer and you should see another printer installed called BRFAX. The device URI is incorrectly created as /dev/usb/lp0. To correct this go to Menu, System Settings, Printers. Select BRFAX and select the Properties tab and then the Interface icon. Now click on Change and a window called Modify Printer should open. Select Local printer, Next, then select Brother MFC-215C USB#1 and click Finish.

This printer is not used to print faxes directly. It is used by the “brpcfax” utility script file. To send a fax, you must use the “brpcfax” utility to process your print jobs and you can only use a postscript file.

a) Use “Print to file” from your application to generate a postscript file called i.e “testfax.ps”
b) Right click the testfax.ps file and select “Open with”  and now click “Send As Fax”, the dialup screen gui should come up, enter fax number and click Send.

Before you can do this Konquerer must first be configured

1)Open Konquerer
2)Go to Settings, Configure konquerer
3)Click file associations
4)Type “ps” in the search box and select “Application”-- “Postscript” from the list
5)Click “Add” and type “brpcfax” and click OK
6)Select the new “brpcfax option and click 'Edit”
7)Select the Application tab
8)In Command line enter: brpcfax -P BRFAX -o PAPER=A4
9)For the Name enter Send As Fax
10)Click on the blank Icon, System Icons, select printmgr (looks like a fax)
11)Click OK and save

Scanner Installation:

Ensure you have already installed sane as per the beginning of this howto.
You must additionally install a special driver which is the Brother backend for sane scanner which is used by Kooka (Kubuntu).

Ensure that printer is switched off

Right click on the brscan2-0.2.1-0.i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer on

Run Kooka in root  (kdesu kooka) to check if the installation works (or Xsane if using Ubuntu)
The reason for this is that the scanner MFC-215C is quite new and not yet present in the Kubuntu Dapper config files and you can just add these two lines. To fix this go to /etc/udev/rules.d/45-libsane.rules and find the 2 lines starting with #Brother MFC-210C , copy these lines below and change the model number to 215 and the product id to 0193 and reboot. Kooka should now run as ordinary user from the menu. This probably is more Dapper related. To lsusb in the terminal can give you the scanner details as well

# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
# Brother|MFC 215C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"



Network Installation (printer own IP) (Not tested yet)

This is how to get the printer to just be on the network (not attached to a print server). This will only work with models that have a built-in ethernet port. (MFC-425CN). The model MFC-215C will have to have an external network driver module (jetdirect or similar) attached. Otherwise it will have to use another PC as a print server.
You need to know the IP address of the printer. The printer can tell you this (check out the instruction booklet as the command combinations may be different for different models.) 
Open your browser to CUPS by entering [http://localhost:631/](http://localhost:631/). Click "Manage Printers." 
If everything went well, you should see your printer in the list. 
Select "Modify Printer." The important step is to select the device for the printer. Choose "LPD/LPR Host or Printer." 
Enter lpd://xxx.xxx.xxx.xxx in the window (where the xxx's are the printer's IP address). 
Send it a test page. You can configure paper size from CUPS (it seems to default to A4). 
From here you can also set your print manager to use CUPS if you so desire and it will also print on the network. 


Printer sharing on PC in home network:

Windows to Kubuntu  Printer connected directly to a Windows XP PC and shared with a Kubuntu PC over the network. This means drivers for the MFC-215C must be installed on both PC's, XP and Kubuntu.
Enable the Printer sharing in Windows and give the printer an unique share name i.e Brotherxp

After installing the drivers as above on the Kubuntu PC, go to Menu System Settings, Printers, Add printer, Add printer wizard opens and you need to complete this. Next, enter nothing here(security), next and click Scan.
If your Kubuntu PC can see the Windows PC it will show the workgroup name and the PC name. Enter these in Workgroup, Server and put the Printer share name you gave in XP (i.e. Printerxp) in Printer, Next.
KDE will now build a database of drivers and you can select Brother, scroll down to MFC-210C (which you have installed in the first part) , Next, Test page and you are working.

Kubuntu to Kubuntu Printer drivers are installed on the Kubuntu PC that has the printer connected to it. No drivers need to be installed on any of the other Kubuntu PC's that are on the same lan. If printer sharing in CUPS and on Kubuntu is properly configured, the printer will automatically appear in the printer list, as if installed, when the Kubuntu PC sees the installed printer on the server(sharing) Kubuntu PC.


Scanner over network (printer has own IP) (Not tested yet, but see next post)

It is assumed that the scanner drivers and sane have been installed as shown at the beginning of this howto.
To use your machine as a network scanner, you need to set a friendly name, model name and IP address or node name for the driver:  
using IP address:
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx
or using node name
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx
Example
brsaneconfig2 -a name=BROTHER-SCANNER model=MFC-215C nodename=BRN_XXXXX
You can check the result by running the command:
brsaneconfig2 -q
If the setting is done correctly, you will see the result as below:
	0 BROTHER-SCANNER "MFC-215C" N:BRN_XXXXX
Now run Kooka ( Xsane if using Kubuntu)
	And scan something, click Acquire Preview and there you go...

---

### Post by rogowar on 2006-09-29
I'd like to thank you very much for the tutorial.  I have an MFC-8840D with the network interface, and I'm printing and scanning over the network to an IPP defined CUPS printer.  Lovely.  I wanted to add some notes from my install.

> **Matchless said:**
> Hi,
Now you have to set this version as default:
sudo update-alternatives –config java
You will now get a selection that shows a list and which is in use.
Select the version: /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


I was unable to find this in apt until I modified /etc/apt/sources.list and added multiverse to deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe.  Then a simple 

sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts 

did the trick.  

> **Matchless said:**
> Hi,
Network Installation (printer own IP) (Not tested yet)
Open your browser to CUPS by entering [http://localhost:631/](http://localhost:631/). Click "Manage Printers." 


There are 2 notes to make here.  The first is that, for reasons mystifying to me, Dapper has a disabled version of the CUPS web interface.  If you pay attention, you see that there is a not on the first page telling you how to re-enable it.  I followed those instructions (cupsys added to shadow group, me added to lpadmin group), but was too stupid to figure out that I needed to restart the cups daemon.  So:

sudo /etc/init.d/cupsys restart ENTER

and it took the new group permissions and allowed me to manage a printer with my user/pw.  

> **Matchless said:**
> Hi,
Scanner over network (printer has own IP) (Not tested yet)
...
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx
or using node name
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx
Example
brsaneconfig2 -a name=BROTHER-SCANNER model=MFC-215C nodename=BRN_XXXXX
You can check the result by running the command:
brsaneconfig2 -q


Quick note, I did have to brsaneconfig my scanner.  Because the 8840D is older, it uses the older brsaneconfig (no 2).  I opted for IP.  When first running kdesu kooka, it asked me if I wanted to use the network scanner, I said yes, and clicked the box to always use the scanner.

Again, thanks for the tips, particularly the right-click on the .deb then Kubuntu Package Manager tip.  I prefer the interface to the pure command line dpkg.

---

### Post by Matchless on 2006-09-29
Thanks for your contribution!

---

### Post by bodhi.zazen on 2006-10-30
Nice How-to Matchless !

This thread has been added to the UDSF wiki.

[Howto:Printer Brother MFC215C Install on Kubuntu Dapper](http://doc.gwos.org/index.php/HowToInternetAccessBluetoothGSMPhone)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Matchless on 2006-11-10
Thanks,
            How does one access it there?

---

### Post by jackdaw28 on 2007-03-01
Has anyone managed to get the fax working in Xubuntu edgy? It shows up in CUPS but the brpcfax script doesn't open the dialler. If I open the jar file the script refers to the dialler opens but it has nothing to print because it wasn't opened via the script.:confused:

---

### Post by Matchless on 2007-03-03
Hi,
       Theoretically speaking the same procedure should work in Xubuntu, but I have never used Xubuntu myself. Just a few thoughts, sometimes even on Kubuntu i found it not to work first time and after completely redoing the steps it worked. The Bobsongs has slightly changed the process in his excellent howto for the MFC-210. Have a look there as well and hopefully you will get lucky.

> **jackdaw28 said:**
> Has anyone managed to get the fax working in Xubuntu edgy? It shows up in CUPS but the brpcfax script doesn't open the dialler. If I open the jar file the script refers to the dialler opens but it has nothing to print because it wasn't opened via the script.:confused:

---

### Post by jackdaw28 on 2007-03-04
A liitle more detail (Xubuntu edgy):
I followed both Bobsongs' and Matchless' instructions. The printer works fine. The fax is installed correctly via CUPS and has the same URI as the printer. 
I've used the custom command /usr/bin/brpcfax in Thunar to open the .ps file but this will not open /usr/local/Brother/fax/brmfcfax.jar for some reason. brmfcfax.jar is in this directory and so corresponds with the location in the brpcfax script. I have java installed and if I click on brmfcfax.jar the dialler opens but has nothing to fax becuase it wasn't opened by the script..
Strangely the .ps file shows up in the queue in CUPS.

---

### Post by labinnsw on 2007-03-09
I am using Ubuntu 6.10 Edgy Eft. Just picked up a DVD and decided to install it. Point is I don't have a clue. Never used command prompts and seeing linux for the first time. Please be very detailed and step by step in any assistance rendered.

My problem is I have a Brother MFC-215C that I cannot get to work with Ubuntu. I have followed all the instructions of Matchless and been through the FAQs on the Brother Web site. (took me about 2 months) The printer indicates "Receiving Data" but does not print. I would like to uninstall and start over from scratch.

How do I uninstall the drivers? ([dpkg -r cupswrappermfc210c_1.0.0-1_i386] returns a response, [warning, ignoring request to uninstall cupswrappermfc210c_1.0.0-1_i386 which is not installed]) That is the jist of it anyway. However, when I go to install it Gedit says the same thing is already installed and gives me the option to re-install it.)

What am I doing wrong?

labinnsw

---

### Post by Matchless on 2007-03-09
> **labinnsw said:**
> 

How do I uninstall the drivers? ([dpkg -r cupswrappermfc210c_1.0.0-1_i386] returns a response, [warning, ignoring request to uninstall cupswrappermfc210c_1.0.0-1_i386 which is not installed]) That is the jist of it anyway. However, when I go to install it Gedit says the same thing is already installed and gives me the option to re-install it.)

labinnsw

An easy way is to use Synaptic package manager. Use the search function for the file and it will show it, then just delete if. This is full graphic interface use and no commands needed.
Enjoy

---

### Post by jackdaw28 on 2007-03-11
Xubuntu edgy problem solved.:) 

The problem was not with Xubuntu edgy at all but with java 1.6.
I ran "java -jar /usr/local/Brother/fax/brmfcfax.jar" in a terminal and got the error "java command not found". This was odd because I could open brmfcfax.jar just by double clicking on it in Thunar.
A little searching revealed that this error is common with installations of linux java 1.6 and is not an ubuntu specific issue.
I had installed java through Synaptic and so marked it for complete removal. I then installed it via Automatix which correctly made the path for the java command. It now works perfectly.

---

