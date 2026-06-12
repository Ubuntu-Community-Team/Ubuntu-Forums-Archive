---
title: "Edgy Howto: Brother Printer MFC-215c complete"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-11-19
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Hi,[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]   I have updated this howto for Feisty Fawn Kubuntu 7.04 working. It should work on ubuntu and also on the older versions. Thanks to those who responded and confirmed the network printing and scanning. It seems as if the same process can be used for may other Brother Printers as well. Also have a look at BobSongs great howto for the MFC-210c at  [http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c](http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c)  for more detail.

Guitara has written a script to do all the dirty work given below and you can get it here : [http://ubuntuforums.org/showpost.php?p=2277190&postcount=283](http://ubuntuforums.org/showpost.php?p=2277190&postcount=283) 
[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][U][B]Howto:Printer Brother MFC215C Install on Kubuntu Feisty Fawn.
[/B][/U][/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This is a detailed step by step howto for installing the Brother MFC-215C printer drivers on Kubuntu Feisty Fawn v7.04. The installation should be very similar for other Brother printers and should work on older versions of both Ubuntu and Kubuntu. Thanks to everyone who contributed to the compilation of the howto. You know who you are.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]By the way, please note that there are new printer firmware updates on the Brother website. You can check your version on your printer. The firmware updater is only for use in Windows, so you will need to update while logged in via Windows. I suggest you read this on the website as there is a change to the ink level warnings etc. included that may make your printer more efficient.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]N[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]ote that some printer driver files for the MFC-215c are not yet ready and Brother suggests that the files for the MFC-210C are used used in the meantime. The direct links are for the latest at time of writing, so check the website for any updates and rather use those if available.[/SIZE][/FONT][/COLOR]
 

 [FONT=Arial, sans-serif][SIZE=2]Download the following files from the Brother [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Website[/SIZE][/FONT]]("http://solutions.brother.com/linux/en_us/")_[/COLOR][FONT=Arial, sans-serif][SIZE=2],   [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]CUPSwrapper[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb&lang=English_cups")_[/COLOR][FONT=Arial, sans-serif][SIZE=2] , [/SIZE][/FONT][COLOR=#000080]_[FONT=Arial, sans-serif][SIZE=2][LPRdriver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr")[/SIZE][/FONT]_[/COLOR][FONT=Arial, sans-serif][SIZE=2] , [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Fax CUPSwrapper[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb&lang=English_gpl")_[/COLOR][FONT=Arial, sans-serif][SIZE=2] , [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Fax LPRdriver[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr")_[/COLOR][FONT=Arial, sans-serif][SIZE=2] and the [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Sane Scanner backend[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb&lang=English_sane")_[/COLOR][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now also install csh (C Shell) and Sane (and Xsane if you are using Ubuntu, Kubuntu uses Kooka which is installed by default) from the repositories, using your program manager i.e Synaptic.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Some folder corrections will need to be done as the .deb files from the Brother site are for debian and were converted from rpm and were not compiled specifically for Kubuntu.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You can install the downloaded .deb files in many ways, dpkg -i, local repository or CD via Synaptic. I have used the Kubuntu shortcut method from the GUI to keep the instructions short and clear. You can also use Krusader or Konqueror for creating and moving files in root mode etc.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Just for information, Kubuntu has an excellent System Settings, Printer dialogue GUI for configuring and setting up your printer. Thus using the terminal or the following CUPS tool is not needed, but can be used.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]CUPS has it own configuration tool for printers and can be accessed by entering [/SIZE][/FONT][/COLOR][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]http://localhost:631/printers[/SIZE][/FONT]]("http://localhost:631/printers")_[/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] on your browser. This is actually quite good and easy to use.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Preparations**_[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]These steps are required before the installation of the drivers otherwise they will produce errors. [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The last two steps (creating links) may not be necessary for some earlier versions of ubuntu from Dapper and back and may be because of Feisty using the latest kernel.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Create a folder on the desktop, called &#8220;brother&#8221;, and put all downloaded files in that folder.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Use Synaptic to install [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**csh**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] (C Shell) and [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**sane**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] from the repositories, if not already done.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Create a new directory in /var/spool/lpd                 (Feisty needs lpd directory which is not present)[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo ln -s /etc/init.d/cupsys /etc/init.d/cups            (Feisty uses CUPS and file wants CUPSYS &#8211; link)[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo ln -s /usr/share/cups/model/brmfc210c_cups.ppd /usr/share/ppd  [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]                         (Feisty puts brmfc210c_cups.ppd in   /usr/share/cups/model/                           and file looks for it in /usr/share/ppd/  - link)[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo ln -s /usr/share/cups/model/brfax_cups.ppd  /usr/share/ppd[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]                          (Feisty puts brfax_cups.ppd in  usr/share/cups/model/  and                            file looks for it in /usr/share/ppd/  - link)[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Install the printer drivers:**_[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]NB: [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer is switched off (**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]unplug mains)[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Right click on the mfc210clpr-1.0.2-1.i386.deb file and select Kubuntu Package Menu, Install Package
Right click on the cupswrappermfc210c_1.0.0-1_i386.deb file and select Kubuntu Package Menu, Install Package[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Switch the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer back on**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] (replug mains)

In the Kubuntu menu go to System Settings, Printers
If the printer is connected to the same PC then the driver has already been installed and selected[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Select the printer MFC-210C and make it default if required. (right click)[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]While having the printer selected, click on the Properties tab and select the Interface icon on the right hand side. If the URI: usb:/dev/usb/lp0 shows, this is incorrect. Click the Change button, enter your password for administrator mode. Now select Local printer, Next, then Brother MFC-215C and Finish.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You should now see URI: //Brother/MFC-215C
Right-click the MFC210C and click &#8220;Test Printer&#8221;. See if test page is received
[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Printer sharing on home network**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Sharing a printer means that the printer is connected to one dedicated PC on your network and other PC's can share this printer through that dedicated PC. Before you can get a shared printer to work you need to make perfectly sure that each PC on the network can communicate perfectly with each other and that the printers are shown as shared with Samba and with NFS. If this does not work you will have problems.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]To share a dedicated printer connected to a specific PC with the other PC's on the same network you need Samba  installed for sharing with Windows and NFS for sharing with Linux PC's. Install these with Synaptic from the repositories.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now go to Menu, System Settings, Sharing, File Sharing and you should see a list under Shared Folders that includes a line /var/lib/samba/printers/ with a tick or a cross under the Samba and NFS column. To enable sharing of the printers under Samba and NFS, go into Administrator mode, select Simple Sharing and select both Samba and NFS. Uncheck Public and Writable. Once you have two green ticks it means that you can share with both linux and/or Windows PC's. You might as well do the same for any folders you want to share. Create them and enable sharing and allow it via NFS and/or Samba, in the case of folders you should check Public and Writable.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now to check that you can see the shares, reboot the PC's and then click on the PC icon called System Menu in the kicker bar. Select Remote Places, Samba Shares and then open the Workplaces. You should see your own PC AND the remote PC's. Check that this is possible on all the PC's. Now you can be sure that your PC's are seeing each other and ready to have printer sharing set up. Note, you will not see the printers in here, but only actual shared drives and folders on which sharing has been allowed.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_Printer on linux PC, sharing with other linux PC's_[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If you are using all linux PC's you will not need to install drivers on the client (other) PC, but only on the server PC that has the printer connected to it (we are not refering to a network printer here, that has its own IP address, but a dedicated printer on a PC that is shared via that PC).[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If your sharing and the network is properly setup with the server PC, the printers installed on the server PC will show up in your printer list on each PC as if they were installed on that PC (nice CUPS and linux feature) and you just use them.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_Printer on Windows PC, sharing with other linux PC's_[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If the server PC is a Windows PC you will have to install the Windows drivers on the Windows PC and activate printer and file sharing. and give the printer an unique share name i.e. Brotherxp. Then install the above linux printer drivers for the printer on the Kubuntu PC and then go to Menu, System Settings, Printers, Add, Add Printer Class. [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now the Add Printer Wizard opens and click next, select SMD Shared Printer Windows, next, Use anonymous, next, SMB Printer Settings &#8211; use Scan. [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If your Kubuntu PC can see the Windows PC it will show the workgroup name and the PC name. Enter these in Workgroup, Server and put the Printer share name you gave in XP (i.e. Printerxp) in Printer, Next.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]KDE will now build a database of drivers and you can select Brother, scroll down to MFC-210C (which you have installed in the first part), [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]find the correct printer, click on it and it will be entered in the fields, Next etc. until installation is complete and test page works. [/SIZE][/FONT][/COLOR] 
 

  

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_Now for some configurations settings:_[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The above will not work properly as the CUPS configurations in Kubuntu are not set by default to allow sharing of printers on a network and you have to enable this before it will work.  Its is easy in Kubuntu:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Got to System Settings, Printer[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Open the Printer Server tab and just select both &#8220;Access printers on local network&#8221; this is on the PC that needs to see a shared printer from another PC and &#8220;Share printers on local network&#8221; this is on the PC that needs to share its printer with other PC's.  A cross next to these will show if enabled.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Select the Restart Server in System Settings - Printer or you can reboot the PC's and see if you can see the printer under printer settings on the other PC's.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Thats it, now you have a shared printer!![/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Camera media card reading;**_[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You can just insert the media card and it will appear as a usb flash disk on Kubuntu and just copy, read or whatever from and to it. Just do not change the special file structure that your camera created as it may make the card unusable in your camera.
[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Fax Printing :**_[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

[/SIZE][/FONT][/COLOR][FONT=Arial, sans-serif][SIZE=2]Brother has provided a very useful function that allows faxes to be sent directly from a PC, via your Brother MFC. It works on linux and even from other linux PC's connected to the same lan. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]The actual printer configuration can be done via the CUPS web interface ([/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]http://localhost:631/printers[/SIZE][/FONT]]("http://localhost:631/printers")_[/COLOR][FONT=Arial, sans-serif][SIZE=2]), but I used the Kubuntu (KDE) printer configuration from the menu, as some CUPS configurations, such as printer sharing and administrator mode are not enabled by default in Kubuntu Dapper. Details can be found above on how to correct.[/SIZE][/FONT]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure that Sun-Java5-jre is installed from the repositories using your package manager (i.e. Synaptic, adept, apt-get etc,as this runs the applet /usr/local/Brother/fax/brmfcfax.jar, which is the dialup gui for your PC-Fax.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now you have to set this version as default (may not be required to do in Feisty):[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo update-alternatives  - -config java[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You will now get a selection that shows a list and which is in use.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Select the version: /usr/lib/jvm/java-1.5.0-sun/jre/bin/java[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now while the printer is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**SWITCHED OFF**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2], install the two special drivers from the Brother website. The order of the driver installation is important, first lpd, then cups:[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Right click on the brmfcfaxlpd-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Right click on the brmfcfaxcups-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Switch the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer BACK ON:**[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]In the menu go to System Settings, Printer and you should see another printer installed called BRFAX. The device URI is incorrectly created as /dev/usb/lp0. To correct this go to Menu, System Settings, Printers. Select BRFAX and select the Properties tab and then the Interface icon. Now click on Change and a window called Modify Printer should open. Select Local printer, Next, then select Brother MFC-215C and click Finish.[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This BRFAX printer is not used to print faxes directly, BRFAX is used by the &#8220;brpcfax&#8221; utility script file. To send a fax, you must use the &#8220;brpcfax&#8221; utility to process your print jobs and you can only use this with a postscript file which then sends it to the BRFAX printer.[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]a) Use &#8220;Print to file&#8221; from your application (i.e. OOo) to generate a postscript file called i.e &#8220;testfax.ps&#8221;[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]b) Right click the testfax.ps file and select &#8220;Open with&#8221;  and now click &#8220;Send As Fax&#8221;, the dialup screen gui should come up, enter fax number and click Send.[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Before you can do this Konquerer must first be configured[/SIZE][/FONT][/COLOR]

[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]1)   Open Konquerer[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]2)   Go to Settings, Configure konquerer[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]3)   Click file associations[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]4)   Type &#8220;ps&#8221; in the search box and select &#8220;Application&#8221;-- &#8220;Postscript&#8221; from the list[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]5)   Click right hand &#8220;Add&#8221; (under Application Preferance Order) and type &#8220;brpcfax&#8221; and click OK[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]6)   Select the new &#8220;brpcfax option and click 'Edit&#8221;[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]7)   Select the Application tab[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]8)   In Command line enter: brpcfax -P BRFAX -o PAPER=A4[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]9)   In the Name field enter [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**Send As Fax**[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]10) Go to General tab[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]11) Click on the blank Icon, System Icons, select Devices form drop down and select the &#8220;print_class&#8221; icon (looks like a fax)[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]12) Click OK and save[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If you Send As Fax a .ps document, you will dial the number on the pop up screen on your PC and then you will hear the printer fax being seized, dialtone, then dialling and the fax sent.
[/SIZE][/FONT][/COLOR]

 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Scanner Installation:**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure you have already installed Sane (and Xsane for Ubuntu) as per the beginning of this howto.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You must also additionally install a special driver which is the Brother backend for sane scanner which is used by Kooka (Kubuntu).[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure that [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer is switched off**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Right click on the brscan2-0.2.1-0.i386.deb file and select Kubuntu Package Menu, Install Package[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

Switch the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer on**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

Run Kooka in root  (kdesu kooka) to check if the installation works (or Xsane if using Ubuntu)[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The reason for this is that the scanner MFC-215C is quite new and not yet listed in the Kubuntu Feisty config files and you have to add some lines. To fix this go to /etc/udev/rules.d/45-libsane.rules and find the 2 lines starting with #Brother MFC 9600 and you will see that other versions are missing, insert the lines below and reboot. Kooka should now run as ordinary user from the menu. Use lsusb in the terminal, it can give you your scanner details as well[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]# Brother|MFC 115C[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner"[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]# Brother|MFC 210C[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]# Brother|MFC 215C[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"

Reboot PC and test.

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Network Installation (printer own IP)**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This is how to get the printer to just be on the network (not attached to a print server). This will only work with models that have a built-in ethernet port. (MFC-425CN). The model MFC-215C will have to have an external network driver module (jetdirect or similar) attached. Otherwise it will have to use another PC as a print server.
You need to know the IP address of the printer. The printer can tell you this (check out the instruction booklet as the command combinations may be different for different models.) 
Open your browser to CUPS by entering [http://localhost:631/](http://localhost:631/). Click "Manage Printers." 
If everything went well, you should see your printer in the list. 
Select "Modify Printer." The important step is to select the device for the printer. [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Choose "LPD/LPR Host or Printer." 
Enter lpd://xxx.xxx.xxx.xxx in the window (where the xxx's are the printer's IP address). 
Send it a test page. You can configure paper size from CUPS (it seems to default to A4). 
From here you can also set your print manager to use CUPS if you so desire and it will also print on the network. 
[/SIZE][/FONT][/COLOR]

  

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Scanner over network (printer has own IP)**_[/SIZE][/FONT][/COLOR]
  

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]It is a[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]ssumed that the scanner drivers and Sane (and Xsane for Ubuntu) have been installed as shown at the beginning of this howto.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]To use your machine as a network scanner, you need to set a friendly name, model name and IP address or node name for the driver:  
using IP address:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xxx.xxx.xxx.xxx[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]or alternatively using node name[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Example[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]brsaneconfig2 -a name=BROTHER-SCANNER model=MFC-215C ip=xxx.xxx.xxx.xxx[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You can check the result by running the command:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]brsaneconfig2 -q[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If the setting is done correctly, you will see the result as below:
    0 BROTHER-SCANNER "MFC-215C" I:xxx.xxx.xxx.xxx
Now run Kooka ( Xsane if using Ubuntu)
    And scan something, click Acquire Preview and there you go...[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
[/SIZE][/FONT][/COLOR]

---

### Post by rejser on 2006-11-20
Excellent howto, was about to install my HL 2030 after Edgy install, used this howto for the printer part (hd it installed by the other howto that is very similar for dapper). 
Problem is, it starts to move alot of papers (about 15 papers for every testpage), but nothing on them. Tested the printer from different usb ports and which changes nothing, it works flawless on my girlfriends win xp notebook. Any tips on what I could have missed or something to try?

---

### Post by Matchless on 2006-11-24
> **rejser said:**
> Excellent howto, was about to install my HL 2030 after Edgy install, used this howto for the printer part (hd it installed by the other howto that is very similar for dapper). 
Problem is, it starts to move alot of papers (about 15 papers for every testpage), but nothing on them. Tested the printer from different usb ports and which changes nothing, it works flawless on my girlfriends win xp notebook. Any tips on what I could have missed or something to try?

Hi,
   I am not familiar with your model, but can just suggest that you ensure that you have the latest drivers from the Brother site, clean out your installation completely. Uninstall with package manager and search for files related to the installation (I use Krusader) and do a new installation and make sure the steps are followed correctly. I have just retested my own howto on a new clean install, but only Kubuntu and it works.
Good luck.

---

### Post by stefros on 2006-12-16
Hi,

I am having trouble using my printer. I am working with DCP-115 C and used MFC-210C driver as described in your HOWTO. The scanner is running fine,but the printer is not working.

When I am selecting one document for printing, my printer is showing "Receive DATA", but this was everything.

I can scan without any problems.

Can you help me?

I am using Edgy EFT (Ubuntu 6.10) with a DCP-115C

Thanks

---

### Post by Matchless on 2006-12-16
All I can suggest is that you go into the System  Settings again and open up the printer that was created when you installed the drivers, check the properties and that it is pointing to the correct device, or just delete the printer in System settings and add a new one from scratch.
Hopefully that should help you

---

### Post by stefros on 2006-12-16
I just deleted the packages and made a new installation and - what a surprise - it worked well for me. Thx a million

---

### Post by ChronoStriker1 on 2006-12-17
I have a MFC-5440CN and using your instructions and the correct drivers for my printer everything went very smoothly.  Thank you for putting an easy to read howto up, it made everything a lot easyer for me. :D

---

### Post by Matchless on 2006-12-17
> **ChronoStriker1 said:**
> I have a MFC-5440CN and using your instructions and the correct drivers for my printer everything went very smoothly.  Thank you for putting an easy to read howto up, it made everything a lot easyer for me. :D
I am glad that some of you are finding this usefull

---

### Post by balloons on 2006-12-20
I have written a shell script to automate the installation of these drivers, based on bobsongs script for dapper. Please test and let me know of any bugs you find. Works for me. I modified his script to work for dapper or edgy, so if it works properly, bobsongs can host the revised script which adds edgy support. Thanks to matchless for this great howto, made my scripting job easier.

EDIT: Go here for the current versions

[http://ubuntuforums.org/showpost.php?p=2277190&postcount=283](http://ubuntuforums.org/showpost.php?p=2277190&postcount=283)

---

### Post by CroEragon on 2006-12-22
I used this on my MFC 215c and I had no problems whatsoever.
I just have one questions.
When i run Kooka with command "kdesu kooka" it shows output below and then loads Kooka prefectly and everithing works.
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-4897' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
KComboBox::setTrapReturnKey not supported with a non-KLineEdit.
```
What does that mean?

And when i just run Kooka from Kmenu (without sudo permission) it just showes message that there is no scanner even if i select brother scanner at the beaginning.
Why is that so?
I just wanna know why this happens, remember,  if i use root permission everything works, just shows upper output.

---

### Post by Matchless on 2006-12-23
Did you follow the howto in the scanner part where it gives some lines that need to be inserted to make it run normally without root?

---

### Post by CroEragon on 2006-12-23
> Scanner Installation:


Ensure you have already installed sane as per the beginning of this howto.
You must additionally install a special driver which is the Brother backend for sane scanner which is used by Kooka (Kubuntu).


Ensure that printer is switched off

Right click on the brscan2-0.2.1-0.i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer on

Run Kooka in root (kdesu kooka) to check if the installation works (or Xsane if using Ubuntu)
The reason for this is that the scanner MFC-215C is quite new and not yet present in the Kubuntu Dapper config files and you can just add these two lines. To fix this go to /etc/udev/rules.d/45-libsane.rules and find the 2 lines starting with #Brother MFC-210C , copy these lines below and change the model number to 215 and the product id to 0193 and reboot. Kooka should now run as ordinary user from the menu. This probably is more Dapper related. To lsusb in the terminal can give you the scanner details as well


# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
# Brother|MFC 215C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"
Actually i didn't because there is no MFC 210 line whatsoever. I didn't do it because i was not sure what to put in, and i don't have 210 line to copy and modify.
What should i do?

---

### Post by Matchless on 2006-12-24
OK,
       This must be your problem then. Open the file in your editor and do a search for Brother, this will take you to a line or two wher another model of brother is located, then insert the lines beneath these exactly as given in the howto, save and reboot and you should be scanning. Ignore the lines for the MFC210 or add them it does not matter I gave both as an example as older versions of Kubuntu had the MFC210 lines already in and Edgy had very little Brother info in the file.

---

### Post by ipa on 2007-01-10
I sent this to Brother Support, hopefully it will help those with X86-64 Edgy cannot print test page problems. I have a MFC-425CN installed to the network using the MFC-210C drivers.
I used the script as found on this thread (thanks very much) and added --force-install to the dpkg -i lines. I had to run it a second time as I did not have the extra repos enabled and csh was not installed.

 I found by enabling the save error logs in localhost:631/admin page I could view a detailed description of what was happening.
 /usr/local/Brother/lpd/rastertobrij2 was reported as not being found, but really it was just not executing, which caused postscript to exit without creating a page. This zero sized page then was happily sent to the printer which then of course did nothing. Heh, who would have guessed.
Working now, yahoo! Next to see about fax and scan... 

Ivan


you may wish to add to your x86-64 faq:
install ia32-libs

sudo apt-get update
sudo apt-get install ia32-libs

these libraries enabled the /usr/local/Brother/lpd/rastertobrij2
executable to work so that a test page could be compiled and sent to the printer.

Took me all day, and a lucky discovery of the ldd command output, to put me on the right track.

Thank you for your continued linux support... it will benefit your bottom line  in the end as the user base is growing exponentially.

Kind regards,
Ivan

---

### Post by ipa on 2007-01-11
For those trying to install a network scanner on an Edgy AMD64 machine follow this thread:
[http://ubuntuforums.org/showthread.php?t=278923](http://ubuntuforums.org/showthread.php?t=278923)

---

### Post by BobSongs on 2007-01-17
Matchless:

Ohh, I finally get it. I re-read your tutorial and I've made modifications to mine. It works! I got the fax printing going. Thanks, buddy! You've been very helpful to completing my tutorial on the [MFC-210C]("http://www.ubuntuforums.org/showthread.php?t=105703").

I've borrowed from your tutorial and shaped it into how I write my tutorial. But you've helped a great deal.

Thanks again.

---

### Post by Matchless on 2007-01-17
Bobsongs,
             And my turn to thank you as your mfc210 howto gave 95% of the details for the mfc215c! All I now need is a linux version of the Inksaver program. I am still amazed at the excellent help I got from Brother support to put me on the way in getting the fax going!
Keep up the good work, your howto is an absolute winner and lifesave to a lot of people out there.

---

### Post by emmet on 2007-01-23
Just to let you know that these instructions helped to get my MFC-5840CN running. Both printing and scanning is running correctly.

I was using Ubuntu 6.10 AMD64. The instruction on the Brother web site also helped a lot, since you need to copy a file across to the Lib64 folder in order to get it to work with the AMD64.

Many thanks

---

### Post by Tabe_ on 2007-01-26
I tested the installation with my MFC-315CN printing directly over network. It works. So you can quote as TESTED the network installation.

The Scanner didn't work. I hope i can solve this soon.

---

### Post by Matchless on 2007-01-26
Rabe_,
         Thanks have updated howto


> **Tabe_ said:**
> I tested the installation with my MFC-315CN printing directly over network. It works. So you can quote as TESTED the network installation.

The Scanner didn't work. I hope i can solve this soon.

---

### Post by GothicX on 2007-01-28
Great Howto.. I've sucessfully working my Brother DCP-115C.

Thanks!

---

### Post by GothicX on 2007-01-28
I need some help...

My printer is working, the scanner not..

kmos@bash:~$ lsusb
Bus 001 Device 003: ID 04f9:018c Brother Industries, Ltd 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Check the screenshot for the error. I've put these lines and rebooted.

# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
# Brother|MFC 215C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"

---

### Post by GothicX on 2007-01-28
I've solved the problem.. I think you must add this to your tutorial..

kmos@bash:~$ lsusb
Bus 001 Device 003: ID 04f9:**018c** Brother Industries, Ltd

Now modify the idProduct to 018c and reboot. Start xsane at Graphics menu at it must work..

# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="**018c**", MODE="664", GROUP="scanner"

Thanks!

---

### Post by Matchless on 2007-01-30
Hi,
    What you did is correct as 0193 is for the MFC-215c. Your scanner must be a different one as it is product id 018c. What is the model number of your printer? It looks like a DCP-115c which has its own product id.

---

### Post by GothicX on 2007-01-30
> **Matchless said:**
> Hi,
    What you did is correct as 0193 is for the MFC-215c your scanner must be a different one as it is code 018c. What is the model number of your printer?

I've a Brother DCP-115C :-) Printer and Scanner working.. I've also installed FAX, but It doesn't say anything after I put the number to send the PostScript file.

---

### Post by Matchless on 2007-01-30
Just make sure you have followed the fax setup in the howto carefully and that your context menu shows [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]“Open with”  and  “Send As Fax” when you right click on a file.ps. If not then this part is not correctly created.
Bobsongs has also solved this in a slightly different way in his MFC-210c howto :
[http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c](http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c). I hope this helps you with yours.
[/SIZE][/FONT][/COLOR]

---

### Post by GothicX on 2007-01-30
I'm using Gnome, so your Open With doesn't work here.. but I used that with your command to send fax. I need to put country code in the phone number? after click Send what appears?

---

### Post by Matchless on 2007-01-30
Ok, I have to work from memory as I am online now and cannot dialout as well. Once the dial box appears and you punch in the number, the printer should be seized from the PC and if the speaker is on loud you will hear dialtone and then the dialling on the fax/printer speaker. If your printer has a lcd panel you will also see an indication there. You can try any number, it does not have to be successfull dialout to test this part.
Sometimes the first installation can be tricky and it is easy to make a mistake and can be solved by completely removing the first one and reinstalling by going through the whole process carefully.

---

### Post by GothicX on 2007-01-30
Yeah, My printer has LCD.. I will check there and try again when I've time.. Thanks!

---

### Post by jackdaw28 on 2007-03-01
Has anyone managed to get the fax working in Xubuntu edgy? It shows up in CUPS but the brpcfax script doesn't open the dialler. If I open the jar file the script refers to the dialler opens but it has nothing to print because it wasn't opened via the script.:confused:

---

### Post by Jose Catre-Vandis on 2007-03-10
Great howto.

**_Brother DCP-540CN_**

Following the instructions helped me easily setup my new Brother DCP-540CN Network Printer/Scanner for Ubuntu Edgy (Gnome). The device sits on the network and serves a mix of Linux and Windows PCs. The installation for linux was completed without the need to connect via usb. Detailed below is the routine for the DCP-540CN for _[COLOR="SeaGreen"]NETWORK[/COLOR]_ cobbled together from the brother website FAQ, this post, and what I had to change.

NOTE: This howto now tested and working for GUTSY 7.10  :) and drivers updated to latest versions

**_Prep_**
Download all the necessary drivers from the Brother site
```
http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_others/dcp540cnlpr-1.0.0-9.i386.deb
```
```
http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/dcp540cncupswrapper-1.0.0-10.i386.deb
```
```
http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.4-0.i386.deb
```
Use Synaptic to install csh (C Shell) and sane/xsane from the repositories (not needed for Gutsy as Xsane installed by default)
```
sudo aptitude install csh sane xsane # not needed for Gutsy
```
Create a new directory in /var/spool/lpd (Edgy needs lpd directory which is not present)
```
sudo mkdir /var/spool/lpd
```
(Edgy/Gutsy uses CUPS and file wants CUPSYS &#8211; link)
```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
```

**[COLOR="Red"]SWITCH OFF THE PRINTER[/COLOR]** (This seems to be the most important point that caused failure on installation previously, I will tell Brother about this!)[COLOR="Red"]**SWITCH OFF THE PRINTER**[/COLOR]

**_Installation_**

[COLOR="Red"]Is your printer switched off?[/COLOR]

Using Gdebi Installer or command line, install the lpr and wrapper packages in this order (important!)

```
sudo dpkg -i --force-all dcp540cnlpr-1.0.0-9.i386.deb
```
```
sudo dpkg -i --force-all dcp540cncupswrapper-1.0.0-10.i386.deb
```

OK, you can now switch on the printer.
If you want, have a quick look in System>Administration>Printing to see if the printer is there, set it as default. Don't try any printing yet

Open your web browser and go to the CUPS printer interface 
```
http://localhost:631
```
You need to know the IP address of the printer. The printer can tell you this (check out the instruction booklet as the command combinations may be different for different models.)
Click "Manage Printers."
If everything went well, you should see your printer in the list.
Select "Modify Printer." The important step is to select the device for the printer. Choose ```
LPD/LPR Host or Printer
```
Enter ```
lpd://xxx.xxx.xxx.xxx/binary_p1
``` in the window (where the xxx's are the printer's IP address).
For ppd enter ```
/usr/share/cups/model/brdcp540cn.ppd
```
You should get a "printer configured successfully" page, then be return to the main printer page
Send it a test page. You can configure "Printer Options" from CUPS.
With any luck, your printer will spark into life and print!
Now open up a document in gedit/whatever and test print again.
Go back into System>Administration>Printing and check/change any printer options you might want.

*Note: when I printed a test page from CUPS, even though it printed fine, the print job still lingered on the page, I had to delete this job from the printer queue when I went to test print from gedit.*
[I]
Note: do not appear to be getting any print settings coming through, e.g. fast/fast normal apart from page size[/I]
[EDIT] Fast and Fast Normal print settings started working after a reboot!

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**_Scanner_**

Advice is to have printer switched off again, although i didn't switch off and the installation went flawlessly. To be on safe side, suggest switch off while installing drivers.

Again for a **[COLOR="SeaGreen"]Network[/COLOR]** setup only:

You have already installed sane and xsane
Run xsane in a terminal just to check it is up and working (it won't show the scanner we want yet)
install the Brother scanner driver either using Gdebi or command line:
```
sudo aptitude install brscan2-0.2.4-0.i386.deb
```
(you need the brsan2 version)

To use your machine as a network scanner, you need to set a friendly name, model name and IP address or node name for the driver:
using IP address:
```
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx
```
or using node name
```
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx
```
Example
```
brsaneconfig2 -a name=BROTHER-SCANNER model=DCP-540CN ip=xxx.xxx.xxx.xxx
```
You can check the result by running the command:
```
brsaneconfig2 -q
```
which should give you an output like this: (after printing a long list of device names)
```
Devices on network
  0 BROTHER-SCANNER     "DCP-540CN"         I:xxx.xxx.xxx.xxx
```

Now run Xsane
And scan something, click Acquire Preview and there you go...

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Note: Uninstalling printer and scanner drivers to start again:

This is a pain, "dpkg -r" gets quite upset about trying to uninstall these drivers.

To uninstall the printer drivers go to:
```
cd /var/lib/dpkg/info/
```
and scroll through the files to find a set of files that start with "dcp540cn*"
Using root nautilus, delete all these files, then in terminal
```
sudo dpkg -r --force-remove-reinstreq dcp540cncupswrapper
sudo dpkg -r --force-remove-reinstreq dcp540cnlpr
```

To uninstall the scanner driver:
```
cd /var/lib/dpkg/info/
```
and scroll through the files to find a set of files that start with "brscan2*"
Using root nautilus, delete all these files, then in terminal
```
sudo dpkg -r --force-remove-reinstreq brscan2
```

All this worked for me, and I hope it will work for you, but you attempt all this at your own risk

Thanks to Brother, and all the contributors on the forum for their work and heartache in sorting these printers out

---

### Post by labinnsw on 2007-03-10
Matchless, Thanks for your reply to my post under the Kubuntu How to. Happy to say, in the end I did not need to uninstall anyway.

Guitara, you're a genious. Even though I did not know what I was doing, I was able to use your shell script to get the printer working. Did some reading and 1. entered in the Terminal "sudo -i /XXXXXXXXXX/Edgy_Brother_MFC-210C_Installer.txt" (Where /XXXXXXXXXX is the path to the script) 2. entered my password. 3. Selected the printer from the pop-up window 4. followed the instructions. Worked like magic. I am very impressed with you guys, yourself and Matchless.

Just in case another novice like myself is reading this and wants to find the path. Locate the downloaded script and right click on it. Select properties. From here you can highlight and copy the path.

Thanks a lot guys, now I am totally satisfied with my Ubuntu.

Regards
labinnsw

---

### Post by GothicX on 2007-03-24
My printer Brother DCP-115C is still working after upgrade from Edgy to Feisty Herd5, now Beta :-)

---

### Post by axcairns on 2007-04-30
Excellent howto! I just set up a MFC-215C on Feisty with no problems. The only quirk was that there was no line for the MFC-210 in 45-libsane.rules but I just copied and pasted your example for the 215C and was off and running!

Cheers,


Allan

---

### Post by Matchless on 2007-05-01
Hi,
    Guitara has set up a script for doing all the dirty work. You can get it here [http://ubuntuforums.org/showpost.php?p=2277190&postcount=283](http://ubuntuforums.org/showpost.php?p=2277190&postcount=283)  There is even one for feisty.
Guitara, thanks, I am sure this will help many and I will put a link on my howto as well.

---

### Post by Quark Green on 2007-05-04
Hello all,
Thank you for this howto. I followed the instructions to set up printing on MFC-215C connected via USB and it worked first time.
Regards, QG.

---

### Post by Matchless on 2007-05-04
Thanks for the feedback, this helps letting me know that there are no typos and other mistakes.
Appreciated.

---

### Post by cowkiller on 2007-05-08
Thanks man, you're a lifesaver... I couldn't print anything in my brother MFC-215C so far and you dunno how was this printing problem driving me mad :lolflag: 
It worked at the first try in Ubuntu.

---

### Post by Matchless on 2007-05-08
Glad it helped!

---

### Post by johninbanagher on 2007-05-08
Great How To, I installed my DCP-340CW on a clean install of fiesty with no probs

---

### Post by Matchless on 2007-05-09
Thanks for the feedback!

---

### Post by Christian Matschke on 2007-05-29
Wow, Matchless, what a great tutorial! Thank you very much for this!

I encounter a strange problem with my MFC-215C under Ubuntu, and I wonder whether someone else has made a similar experience: When I print an Open Office document, it works fine. But when I print a pdf using Evince, the upper circa 17mm of the document are cut, because the content somehow has moved up. Is there any way to correct this? I am a Linux/Ubuntu newbie, sort of.

---

### Post by Matchless on 2007-06-01
Now another problem has been picked up and this is when sharing the printer from a XP PC with a (ahem....) Vista home basic laptop! The laptop detects the shared printer and then attemps to load the XP driver from the XP PC and then fails and there is then no way to point the printer to the Vista driver  - even MS sometimes forgets about their own OS's!
This can be overcome by enabling Print services for Unix on the XP PC, enabling LPR Port Monitor on Vista and then adding a Local printer, create a new LPR Port and add IP and shared printer name and the Vista driver is used. This is only a problem if the printer drivers on XP and Vista differ.
Quite ironic!

---

### Post by swent on 2007-06-02
> **Christian Matschke said:**
> 
I encounter a strange problem with my MFC-215C under Ubuntu, and I wonder whether someone else has made a similar experience: When I print an Open Office document, it works fine. But when I print a pdf using Evince, the upper circa 17mm of the document are cut, because the content somehow has moved up. Is there any way to correct this? I am a Linux/Ubuntu newbie, sort of.

I am not sure wether it will help you, but I just solved a problem with my DCP-540CN. I had configured it via System -> Administration -> Printer, but when I printed a test page, the content was moved up (don't know how much, but 17mm seems about right). Today I configured the printer via the web interface. Strangely enough, the paper size was still set to 'letter', in spite of having been configured to 'A4' via the gnome application. So I changed the size to A4Borderless, printed a test page from the web panel, and it worked. The I printed a test page from the gnome application, and voila, it worked, too. I think, the gnome printer configuration somehow does not like the PPD file from brother, but I am not sure. At least it works now.

Hope this helps.

--Swen

---

### Post by Rezn on 2007-07-09
Just wanted to say thanks for the great tutorial! 

I got my DCP-340CW up and running in a couple of minutes.

Thanks.

---

### Post by Matchless on 2007-07-09
You are welcome!

---

### Post by Nessa on 2007-07-17
Wheeeeee! The printer works! I've yet to test the scanner but I'm happy with the results. Thank you for sharing this! :)

---

### Post by Matchless on 2007-07-17
Another happy linux user!

---

### Post by weboholic on 2007-08-01
Hello, Matchless, this is a great howto and I know that for sure, because it did worked for me once, 2 months ago. I had back then Ubuntu. However meanwhile I've once removed Ubuntu (actually Vista wiped it out), but after a month or two of using Vista it just turned out, that it sucks :). So I am back to Ubuntu Feisty now and I am getting error on installing the cupswrapper. 
Check the screenshot please. I've tried to include as most information as possible. There are two aptitude searches visible. The first one is before, the second one is after. The newer package 1.0.2.3 throws a similar error. I've double checked each step from the beginning -> csh, (x)sane,mkdir, the 3 ln's and successfully installed the lpr package.

Any hint will be much appreciated.

Thank you in advance.

---

### Post by Matchless on 2007-08-02
weboholic,
               I cannot see what is actually going wrong on your side, but so far I have only installed on a version of Feisty directly after installing from the CD and not after updating Feisty to kernel 2.6.20.16. This is only a thought. Also have a look at Bobsongs howto for MFC-210c [http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c](http://ubuntuforums.org/showthread.php?t=105703&highlight=mfc-210c), he has had a lot of input from many members and maybe following his process will help you in finding the problem. Most of these procedures for the Brother printers are very similar, except for the files to be downloaded on some. Hope this helps in some way.
Maybe you can try the script by guitara at [http://ubuntuforums.org/showpost.php?p=2277190&postcount=283](http://ubuntuforums.org/showpost.php?p=2277190&postcount=283)

---

### Post by ee2592 on 2007-09-09
[QUOTE=Jose Catre-Vandis;2275292]
Download all the necessary drivers from the Brother site
```
http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_others/dcp540cnlpr-1.0.0-9.i386.rpm
```

Hi, thanks for this great help for installing my new dcp-540cn  - with only some little problems described now:
1.  I think, you didn't mean dcp540cnlpr-1.0.0-9.i386.rpm  but dcp540cnlpr-1.0.0-9.i386.deb - file, downloadable here:
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp540cnlpr-1.0.0-9.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/dcp540cnlpr-1.0.0-9.i386.deb&lang=English_lpr)

2.  Another little problem, I had: My printer show me his ip in his display in this form: 192.168.178.023 , but for the installation I must take 192.168.178.23 (without zero!)

3. Your downloadadress for brscan2-0.2.1-1.i386.deb failed, successful download here:
wget [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-1.i386.deb)

Greetz,
ee

---

### Post by _zeppelin_ on 2007-09-11
For those people that are getting this error:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=24079&d=1170029730[/IMG]
AS user
BUT can use the scanner as root.

You can resolve this problem adding 'OPTIONS+="last_rule"' to your udev rules. Edit /etc/udev/rules.d/45-libsane.rules . Your lines should be:
```
# Brother MFC 9600
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0101", MODE="664", GROUP="scanner", OPTIONS+="last_rule"
# Brother MFC 7300c
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0106", MODE="664", GROUP="scanner", OPTIONS+="last_rule"
# Brother DCP 115C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner", OPTIONS+="last_rule"

```

---

### Post by steven zeferelli on 2007-09-17
many thanks for useful post.
Finally got my acer t180 working completely without Hasta la Vista baby.

---

### Post by bsmonks on 2007-09-19
Thanks, matchless! Installed my MFC-420cn on the first try. It's connected straight into my network and I can now print and scan from it. Yay!

I would, however, request that you make your instructions a little more n00b friendly. I was trying to figure out how to > Create a new directory in /var/spool/lpd for several minutes. I tried from Konqueror (several times, because the the first couple times I might not have held my tongue just the right way when I clicked the mouse.) and I even tried "md" (from my MSDOS days years ago) in the Konsole. And nothing worked. I finally started reading through the thread to see if any other newbies had the same problem. I got to page 4 and saw Jose Catre-Vandis's post. He included the "mkdir" command in his set of instructions. After that, everything in your instruction set worked to perfection!

Thanks again!

---

### Post by Jose Catre-Vandis on 2007-10-20
Brother DCP-540CN howto updated and working in clean install of Gutsy 7.10

[http://ubuntuforums.org/showpost.php?p=2275292&postcount=31](http://ubuntuforums.org/showpost.php?p=2275292&postcount=31)

---

### Post by frank-hoeg on 2007-11-12
Used this guide to install a networked  Brother DCP-315cn on gutsy gibon, it worked first time.
Haven`t checked the fax, but print/scan works just fine.
Thanks for making this howto.
Frank

---

### Post by buntgrau on 2008-01-09
Now, after two days and one night without sleeping, my system is running nearly completly - just one thing is not working and it seemed to be that i need to install windows again, because it is impossible for me to print.

here you all explain very good how to do - but in fact, even i try to follow these steps, i only get erroe messages because for example dcp540cncupswrapper-1.0.0-10.i386.deb is not working even i download exacly like you all wrote.

i do not know what else i can do - i have the Brother CVP-540CN and i need to print out a lot of things - i am new with UBUNTU, but anything else was nearly no problem. Would be nice if it would be possible for someone to make a package or so i can run completly ...

---

### Post by GothicX on 2008-01-09
I've added the Brother DCP-115C to OpenPrinting website, so if someone has something to add or change.

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-115C](http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-115C)

Thanks

---

### Post by fernandesfer on 2008-01-11
Great! This solved the problem of scanning! Just had to make some arrangements to modify this file, as permissions there are only for superusers!

HAVE YOU A SOLUTION SIMILAR TO PUT IT WORKING AS PRINTER?

Thanks in ADVANCE!
FF

---

### Post by Jose Catre-Vandis on 2008-01-12
> **buntgrau said:**
> Now, after two days and one night without sleeping, my system is running nearly completly - just one thing is not working and it seemed to be that i need to install windows again, because it is impossible for me to print.

here you all explain very good how to do - but in fact, even i try to follow these steps, i only get erroe messages because for example dcp540cncupswrapper-1.0.0-10.i386.deb is not working even i download exacly like you all wrote.

i do not know what else i can do - i have the Brother CVP-540CN and i need to print out a lot of things - i am new with UBUNTU, but anything else was nearly no problem. Would be nice if it would be possible for someone to make a package or so i can run completly ...

Is the CVP-540cn an alternate name to DCP-540cn? (seems logical!)

Which part of the world are you in and which version of Ubuntu are you running? Gutsy implements things slightly differently than Feisty and before.

---

