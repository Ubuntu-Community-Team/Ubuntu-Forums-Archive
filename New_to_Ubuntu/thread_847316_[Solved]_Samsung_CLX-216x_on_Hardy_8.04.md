---
title: "[Solved] Samsung CLX-216x on Hardy 8.04"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by spandon on 2008-07-02
Purchased a Samsung CLX-2160 printer recently,but could not get the scanner to work.
having checked with Samsung and Ubuntu forums, plenty of help, but much of it to "experto" to grasp everything required to do to get this printer to work correctly.
Eventually got the printer working as a Multi-functional Printer both in mono and colour, during the process I made notes for installations on OS upgrades.
I have now refined these notes in PLAIN English in the hope that it may help someone in the future to set up this printer easier than I found it.
my notes:-
**_Samsung CLX-2160 Printer_**

**_Setup for Ubuntu (Hardy) 8.04_**

This priner works perfectly well with the default driver, but to use the scanner it requires the download and installation of the Samsung driver and the tweak with the `howto´ from **tayroni at [http://ubuntuforums.org/showpost.php?p=4776310&postcount=114](http://ubuntuforums.org/showpost.php?p=4776310&postcount=114)** .

To Test the printer utilising Ubuntu 8.04 installed driver:-
Start Ubuntu
Setup the printer as per the instructions supplied by Samsung
Switch printer on
Select System, Administration, Printing
The printer should now be recognised as Samsung CLX-216x Series.
Select Printer Options and change settings if required then select Apply.
Select  Settings
Print Test Page
You should now have a Test Page printed.

[B](note) This also works when in a &#8220;Live Session&#8221; when testing the OS from a cd (without installing the OS)
[/B]
**_To use the Printer as a Scanner:-_**
Create a folder on the desktop and name it driver.
Go to the Samsung website and download the Linux Printer driver for CLX-2160 (the one I d/l  was driver 20070720164102890  dtd 24/3/08
Once downloaded to your desktop, move the tar.gz file to the driver folder you created earlier.
You now have to extract the files from this tar.gz file
Open the driver folder and r/click on file and select Extract here.
Once completed, you will find the tar.gz file and a folder named cdroot (if you open this folder you will find you have a file named autorun and a folder named Linux).
R/click on the autorun file, select Properties and note the location of this file, as you will require this info later.
Open the terminal (Applications, Accessories, Terminal)
Now type cd the location of the file you noted earlier (mine was: cd /home/your username/Desktop/driver/cdroot).
You should now see this as your location, now type:
sudo ./autorun
During the installation you will be given a chance to change the printers name, I added MFP at the end of the printer name, this was so that I stood out from the printer already installed by Ubuntu.
Once the Installation process has finish, you will have an icon on you Desktop, named Samsung Unified Driver Configurator.

Now it is time to do the tweak by tayroni (all it entailed was to open the file, delete the asterisk from the start of four lines and then save the file) and reboot the machine.

Select System, Administration, Printing.
Click on the MFP printer (or whatever name you gave it) from the list of  Local Printers   click on Printer options and make whatever changes you require for this printer, then click on Apply (if any changes have been made).
Switch on Printer.

To test the Configurator :

Double click the icon, it will open and show you the two printers, the Ubuntu installed one and the one you have just installed.

Click on the MFP printer (or whatever name you gave it)

**_Printer Test_**
Select Test... from the menu, then Start from the drop down menu, a Test Print will now be printed, in mono or colour (whichever you chose when making changes earlier).

**_Scanner Test_**
Open scanner lid and place something face down on the table, lower the lid.
Press &#8220;Scan to&#8221; on the printer panel (panel will now read &#8220;Ready to Scan&#8221; .
Click on the Scanner icon in the Configurator window, another window opens &#8220;Scanner Configuration&#8221;, in this window there is an icon of a scanner named &#8220;CLX-216X Series on USB:0.
Click on Properties and the &#8220;Scanner Properties&#8221; window opens which is split into 2 panes, the left hand one containing methods of adjusting the scan and the right hand one contains a blank page.
Now click on the Scan icon in the left hand pane and you will hear the scanner working, when completed another window opens named &#8220;Image Manager&#8221; with the image of the item placed on the table earlier and numererous methods for adjusting the image further and also a save icon where the image can be named and saved to many different locations you wish to choose.

I found it best to configure the 2 installed printers (the Ubuntu automatically installed printer and the manually installed Samsung Unified Driver Configurator printer (MFP)) in this way:

The Ubuntu CLX-216x Series printer as the default and in mono as I would be using this printer the most and in mono for word processing etc.

The CLX-2160 MFP printer configured for colour that could be made the default temporarily when I needed the scanner and print out colour images etc.

---

### Post by jeronimo5 on 2008-08-10
Is this working too for Kubunto 8.04?

---

### Post by jeronimo5 on 2008-08-10
It's working in kubuntu too :)
for printing I advise foo2zjs drivers from theri site also for colour

---

