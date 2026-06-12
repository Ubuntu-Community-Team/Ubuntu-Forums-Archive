---
title: "Gutsy Howto Brother MFC215C printer"
date: 2007-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2007-11-24
I have updated my old MFC215C complete printer install howto for Gutsy. I have again decided to rather post this separately from the older versions so as to not land up with a thread that consists of hundreds of posts. the older posts are labeled for the older versions and can be found with search. 

                                 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2][U][B]Howto:Printer Brother MFC215C Install on Kubuntu Gutsy Gibbon 7.10
[/B][/U][/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This is a detailed step by step howto for installing the Brother MFC-215C printer drivers on Kubuntu Gutsy Gibbon v7.10. [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]It is quite amazing that suppliers who support linux and provides linux drivers, do not get their drivers distributed as part and parcel with Ubuntu! If these are &#8220;Restricted&#8221; I am sure that they could be provided for download as such, but this is another debate. [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The installation should be very similar for other Brother printers and should work on older versions of both Ubuntu and Kubuntu. Thanks to everyone who contributed to the compilation of the howto. You know who you are.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]By the way, please note that there may be new printer firmware updates on the Brother website. You can check your version on your printer. The firmware updater is only for use in Windows, so you will need to update while logged in via Windows. I suggest you read this on the website as there is a change to the ink level warnings etc. included that may make your printer more efficient.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]N[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]ote that some printer driver files for the MFC-215c are not yet ready and Brother suggest that the files for the MFC-210C are used used in the meantime. The direct links are for the latest at time of writing, so check the website for any updates and rather use those if available.[/SIZE][/FONT][/COLOR]
 

 [FONT=Arial, sans-serif][SIZE=2]Download the following files from the Brother [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Website[/SIZE][/FONT]]("http://solutions.brother.com/linux/en_us/index.html")_[/COLOR][FONT=Arial, sans-serif][SIZE=2],   [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]CUPSwrapper[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC210C-1.0.0-1.i386.rpm&lang=English_gpl")_[/COLOR][FONT=Arial, sans-serif][SIZE=2] , [/SIZE][/FONT][COLOR=#000080]_[FONT=Arial, sans-serif][SIZE=2][LPRdriver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr")[/SIZE][/FONT]_[/COLOR][FONT=Arial, sans-serif][SIZE=2] , [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Fax CUPSwrapper[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb&lang=English_gpl")_[/COLOR][FONT=Arial, sans-serif][SIZE=2] , [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Fax LPRdriver[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr")_[/COLOR][FONT=Arial, sans-serif][SIZE=2] and the [/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]Sane Scanner backend[/SIZE][/FONT]]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.4-0.i386.deb&lang=English_sane")_[/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now also install csh (C Shell) and Sane (and Xsane if you are using Ubuntu, Kubuntu uses Kooka which is installed by default) from the repositories, using your program manager i.e Synaptic or Adept.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Some folder corrections will need to be done as the .deb files from the Brother site are for Debian and were originally converted from rpm and were not compiled specifically for Kubuntu.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You can install the downloaded .deb files in many ways, dpkg -i, local repository or CD via Synaptic or Adept. I have used the Kubuntu shortcut method from the GUI to keep the instructions short and clear. You can also use Krusader or Dolphin/Konqueror for creating and moving files in root mode etc.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Just for information, Kubuntu has an excellent System Settings, Printer dialogue GUI, for configuring and setting up your printer. [/SIZE][/FONT][/COLOR] 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Thus using the terminal or the following CUPS tool is not really needed, but can be used and is given for information. [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]CUPS has it own configuration tool for printers and can be accessed by entering [/SIZE][/FONT][/COLOR][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]http://localhost:631/printers[/SIZE][/FONT]]("http://localhost:631/printers")_[/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] on your browser. This is actually quite good and easy to use.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Preparations**_[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]These steps are required before the installation of the drivers otherwise the installation may produce errors. [/SIZE][/FONT][/COLOR] 
  

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Put all these downloaded files on the Desktop.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Use Synaptic to install [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**csh**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] (C Shell) and [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**sane**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] from the repositories, if not already done.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Brother drivers need lpd directory which is not present in Gutsy[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Create a new directory in /var/spool/lpd [/SIZE][/FONT][/COLOR] 
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Create a link as Brother drivers use cupsys and Gutsy uses cups[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo ln -s /etc/init.d/cupsys /etc/init.d/cups [/SIZE][/FONT][/COLOR] 
  
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Install the printer drivers:**_[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]NB: [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer is switched off (**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]unplug mains)[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Right click on the mfc210clpr-1.0.2-1.i386.deb file and select Open With, Gdebi Package Installer, Install Package.
Right click on the cupswrappermfc210c_1.0.2-3_i386.deb file and select Open With, Gdebi Package Installer, Install Package.[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Switch the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer back on**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] (replug mains)

In the Kubuntu menu go to System Settings, Printers
If the printer is connected to the same PC then the driver has already been installed and selected[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Select the printer MFC-210C and make it default if required. (right click)[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]While having the printer selected, click on the Properties tab and select the Interface icon on the right hand side. If the URI: usb:/dev/usb/lp0 shows, this is incorrect. Click the Change button, enter your password for administrator mode. Now select Local printer, Next, then Brother MFC-215C and Finish.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You should now see URI: //Brother/MFC-215C
Right-click the MFC210C and click &#8220;Test Printer&#8221;. See if test page is received. (Sometimes this takes a few seconds)
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
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Thats it, now you have a shared printer!![/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Camera media card reading;**_[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You can just insert the media card and it will appear as a usb flash disk on Kubuntu and just copy, read or whatever from and to it. Just do not change the special file structure that your camera created as it may make the card unusable in your camera.
[/SIZE][/FONT][/COLOR]

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Fax Printing :**_[/SIZE][/FONT][/COLOR][FONT=Arial, sans-serif][SIZE=2]Brother has provided a very useful function that allows faxes to be sent directly from a PC, via your Brother MFC. It works on linux and even from other linux PC's connected to the same lan. [/SIZE][/FONT] 
 [FONT=Arial, sans-serif][SIZE=2]The actual printer configuration can be done via the CUPS web interface ([/SIZE][/FONT][COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]http://localhost:631/printers[/SIZE][/FONT]]("http://localhost:631/printers")_[/COLOR][FONT=Arial, sans-serif][SIZE=2]), but I used the Kubuntu (KDE) printer configuration from the menu, as some CUPS configurations, such as printer sharing and administrator mode are not enabled by default in Kubuntu Dapper. Details can be found above on how to correct.[/SIZE][/FONT]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure that Sun-Java6-jre is installed from the repositories using your package manager (i.e. Synaptic, Adept, apt-get etc,as this runs the applet /usr/local/Brother/fax/brmfcfax.jar, which is the dialup gui for your PC-Fax.[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Now you have to set this version as default (may not be required to do in Gutsy):[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]sudo update-alternatives  - -config java[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
You will now get a selection that shows a list and which is in use.[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
Select the version: /usr/lib/jvm/java-6-sun/jre/bin/java[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

Now  [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**SWITCHED OFF **[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]the printer by disconnecting the power and[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2] install the two special drivers from the Brother website. 

The order of the driver installation is important, first lpd, then cups:[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
Right click on the brmfcfaxlpd-1.0.0-1.i386.deb file and select [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Open With, Gdebi Package Installer, Install Package.[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
Right click on the brmfcfaxcups-1.0.0-1.i386.deb file and select [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Open With, Gdebi Package Installer, Install Package.[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

Switch the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer BACK ON:**[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]In the menu go to System Settings, Printer and you should see another printer installed called BRFAX. 
The device URI is incorrectly created as /dev/usb/lp0. 
To correct this go to Menu, System Settings, Printers. 
Select BRFAX and select the Properties tab and then the Interface icon. 
Now click on Change and a window called Modify Printer should open. Select Local printer, Next, then select Brother MFC-215C and click Finish.[/SIZE][/FONT][/COLOR]  
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This BRFAX printer is not used to print faxes directly, BRFAX is used by the &#8220;brpcfax&#8221; utility script file. To send a fax, you must use the &#8220;brpcfax&#8221; utility to process your print jobs and you can only use this with a postscript  (xxx.ps) files which then sends it to the BRFAX printer.
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]a) Use &#8220;Print to file&#8221; from your application (i.e. OOo) to generate a postscript file called i.e &#8220;testfax.ps&#8221;[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
b) Right click the testfax.ps file and select &#8220;Open with&#8221;  and now click &#8220;Send As Fax&#8221;, the dialup screen gui should come up, enter fax number and click Send.

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Before you can use this in either Dolphin or Konquerer, you need to do the configurations in Konquerer which is also applicable for Dolphin:[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
1)   Open Konquerer[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
2)   Go to Settings, Configure konquerer[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
3)   Click file associations[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
4)   Type &#8220;ps&#8221; in the search box and select &#8220;Application&#8221;-- &#8220;Postscript&#8221; from the list[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]5)   Click right hand &#8220;Add&#8221; (under Application Preferance Order) and type &#8220;brpcfax&#8221; and click OK[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
6)   Select the new &#8220;brpcfax option and click 'Edit&#8221;[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]7)   Select the Application tab[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]8)   In Command line enter: brpcfax -P BRFAX -o PAPER=A4[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
9)   In the Name field enter [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**Send As Fax**[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
10) Go to General tab[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
11) Click on the blank Icon, System Icons, select Devices form drop down and select the &#8220;print_class&#8221; icon (looks like a fax)[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
12) Click OK and save[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If you Send As Fax a .ps document, you will dial the number on the pop up screen on your PC and then you will hear the printer fax being seized, dialtone, then dialling and the fax sent.
[/SIZE][/FONT][/COLOR]

 
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]_**Scanner Installation:**_[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure you have already installed Sane (and Xsane for Ubuntu) and csh, as per the beginning of this howto.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]You must also additionally install a special driver which is the Brother backend for sane scanner which is used by Kooka (Kubuntu).[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Ensure that [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer is switched off**[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Right click on the brscan2-0.4.1-0.i386.deb file and select Open With, Gdebi Package Installer, Install Package.[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

Switch the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**printer on**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]

Run Kooka in  to check if the installation worked (or Xsane if using Ubuntu). The scanner device will be detected, but Kooka will have a problem with Sane.[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]The reason for this is that this has not been listed in the Gutsy config files by the developers and you have to add some lines. 
To fix this go to /etc/udev/rules.d/45-libsane.rules and find the 2 lines starting with #Brother MFC 9600 and you will see that many other versions are missing, insert the lines below or the id value of your model and reboot.  
You can use lsusb in the terminal to give you your scanner details if you do not have it.[/SIZE][/FONT][/COLOR]
 

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
    And scan something, click Acquire Preview and there you go...[/SIZE][/FONT][/COLOR]

---

### Post by evets on 2008-02-06
MFC-665CW Kubuntu 3.5x Feisty. Wireless Network. Printer on dedicated static ip.

Already had the printer and scanner installed, but the fax was killing me. Followed the steps, everything seemed to go ok, and the MFC shows receiving data, but that's it.

Time for bed, I'll go over it again tomorrow.

Thank you. For the work you put into this post. :)

---

### Post by ulrith on 2008-06-19
Could you please advice, is it possible to see printer toner status in Ubuntu Linux?

---

### Post by Badcam on 2010-05-12
Could someone please advise, how I can do this part with Gnome?:
> 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]This BRFAX printer is not used to print faxes directly, BRFAX is used by the &#8220;brpcfax&#8221; utility script file. To send a fax, you must use the &#8220;brpcfax&#8221; utility to process your print jobs and you can only use this with a postscript  (xxx.ps) files which then sends it to the BRFAX printer.
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]a) Use &#8220;Print to file&#8221; from your application (i.e. OOo) to generate a postscript file called i.e &#8220;testfax.ps&#8221;[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
b) Right click the testfax.ps file and select &#8220;Open with&#8221;  and now click &#8220;Send As Fax&#8221;, the dialup screen gui should come up, enter fax number and click Send.

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]Before you can use this in either Dolphin or Konquerer, you need to do the configurations in Konquerer which is also applicable for Dolphin:[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
1)   Open Konquerer[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
2)   Go to Settings, Configure konquerer[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
3)   Click file associations[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
4)   Type &#8220;ps&#8221; in the search box and select &#8220;Application&#8221;-- &#8220;Postscript&#8221; from the list[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]5)   Click right hand &#8220;Add&#8221; (under Application Preferance Order) and type &#8220;brpcfax&#8221; and click OK[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
6)   Select the new &#8220;brpcfax option and click 'Edit&#8221;[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]7)   Select the Application tab[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]8)   In Command line enter: brpcfax -P BRFAX -o PAPER=A4[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
9)   In the Name field enter [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]**Send As Fax**[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
10) Go to General tab[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
11) Click on the blank Icon, System Icons, select Devices form drop down and select the &#8220;print_class&#8221; icon (looks like a fax)[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]
12) Click OK and save[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Arial, sans-serif][SIZE=2]If you Send As Fax a .ps document, you will dial the number on the pop up screen on your PC and then you will hear the printer fax being seized, dialtone, then dialling and the fax sent.
[/SIZE][/FONT][/COLOR]

---

