---
title: "Xerox Phaser 8500 Driver Install Help"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by uptwobucks on 2008-09-13
I am using uBuntu. 

I have downloaded this file from Xerox "Linuxi386XPXX_4.10.62.tgz" have managed to extract the file and make a folder. I can see the directory by typing "ls" in the terminal window. I can open the folder and see the files are included in the directory..

I think my next step is to run "sudo ./configure". But I get no command found. Can someone please help me with this install.

Please post a step by step if possible.

Thanks,
UpTwoBucks

---

### Post by phidia on 2008-09-13
If you are following the README file and you do need to compile you will need the build-essential package. > sudo apt-get install build-essential
That will ask you to insert the install cd. After that completes you should be able to just refer back to your README file.

---

### Post by uptwobucks on 2008-09-13
Ok, I have completed your instructions. Seems everything went well. But it did not ask me to insert the CD.

The Readme appears to be for a more advanced user, not me.

                                         readme
*******************************************************************
*******************************************************************
*                       *** IMPORTANT NOTE                ***               *
*                                                                           *
* CentreWare Services for UNIX Systems is a two part installation process   *
* 1. a code package i.e SolarisXPXX_4.00.60.tar                             *
* 2. a printer support package i.e. PrinterPkgXPXX_2006_06_15.tar           *
*                                                                           *
* The code package must be installed first followed by the printer          *
* support package.                                                          *
*                                                                           *
* Installation requires the user have root or superuser privileges.         *
*                                                                           *
*******************************************************************
*******************************************************************
To install the package expand the tar file and execute setup.
NOTE: setup for the code package will expand and install the compressed tar
   file in the install directory; generate script files and other files
   that are needed at run time. You do not need to uninstall the package
   if you are upgrading or reinstalling.
The following syntaxes are supported:
1. setup
2. setup tmp_path
3. setup install install_path
4. setup install install_path tmp_path
install_path is the installation directory which will contain
              all of the Xerox software.
tmp_path      is a temporary work area. /tmp is the default work area.
To uninstall a previous installation:
1. Use xpadmin to remove all Xerox print queues.
2. For Solaris installation, use pkgrm to remove the CTRWxpxx package.
   For all other installations, remove the "Xerox" installation directory.
3. Remove /var/spool/Xerox directory.

________________________________________

I am now lost. Can you help me with the next step please.

Thanks,
UpTwoBucks

---

### Post by halitech on 2008-10-05
I wish they would redo the information on their website. Compiling anything is not needed. Go here: [http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8500_8550&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8500_8550&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=) and download the LinuxCupsPrinterPkg.tar.gz file. Extract the file to a folder.

then, go to System - Administration - Printing

Add a new printer - Select AppSocket/HP Jet Direct and enter the IP address, leave the port number on 9100

Select Provide PPD and browse to where the files were extracted to earlier

Go next, select your model and options and you should be good to go.

I would also recommend setting a static IP on the front of the machine to avoid having interuptions when you have a power outage

---

