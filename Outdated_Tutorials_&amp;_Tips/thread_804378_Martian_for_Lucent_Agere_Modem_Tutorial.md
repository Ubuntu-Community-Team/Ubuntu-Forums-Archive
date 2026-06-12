---
title: "Martian for Lucent Agere Modem Tutorial"
date: 2008-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by RJQ on 2008-05-23
Installing the Martian Module for Lucent Agere Modem Tutorial.

 
This is actually quite a simple procedure, just read carefully any text related especially those in the folders of the ScanModem and Martian Module, they also show a less detailed instructions on how to use them, here I am trying to be as accurate as possible mentioning just the essentials and usually missed parts of the process, with some extra details for the novice same that help me in my own situation. I hope this words to be useful for any one in need.

 
If you know already that your modem is the Lucent is fair to skip the following steps in relation, if not you can continue, now if you have a computer with Windows in it still (in a dual boot) you can also look for your modem like this.

 
In Windows click on start > control panel. (then, the easiest way is to switch to classic view, and double-click the System icon.) then, click on the Hardware tab, and then Device Manager. Expand the Modems tab by clicking on the +, and your modem should be listed, in this case the Lucent Agere.

 
If you just have K/Ubuntu you can try [ScanModem]("http://linmodems.technion.ac.il/packages/scanModem.gz"). For more details about ScanModem and how to find if you need the Martian Module please refer to the [Ubuntu documentation]("https://help.ubuntu.com/8.04/internet/C/modem-identify.html") section of the same.

 
Prerequisites for the installation:
[LIST]
[*]Repetitive yet important; knowledge that you need the Martian Module. If you did the ScanModem the 1stRead.txt will tell you if this is the module you need.
[*]The package build-essential (in a fresh installation) which come in the live CD but it is not installed by default.
[*]The last Martian (20080407 for K/Ubuntu 8.04) source package found [here]("http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz").
[/LIST]
 
First you need to install the build-essential package from the live CD, place it in the tray and open in your menu System > Administration > Synaptic then click on Settings > Repositories and add the CD in the bottom of the window where is mention, in this case Ubuntu 8.04. close and then click on reload. Now in the left panel click on Origin and it will show the CD name, click on the name with the Main termination. It shall list build-essential, install it along with its dependencies (those are installed automatically by Synaptic).

 
Download the martian-full-20080407.tar.gz to your desktop (this is the easier folder) and right click on it, select Extract Here, now you have a new folder with the same name than the downloaded one, open the terminal by going Applications > Accessories > Terminal. If you Terminal window does not cover the whole screen you can simply drag the folder in it after a cd command. (example: you@you$ cd /home/Desktop/martian-full-20080407) or you can type the entire command and directory in the terminal. By this time you shall be with a open terminal an in the Martian folder directory looking something like this.

 
> you@you:~/Desktop/martian-full-20080407$   
You can also verify by typing in the terminal ls and the result is the files and folders contained in the Martian folder, open Nautilus by double clicking in the Martian folder on your desktop and shall be the same.

 
Next step is to compile the module by typing the following in the Terminal.

 
> you@you:~/Desktop/martian-full-20080407$ make all   
At this moment you will see some procedure that takes some seconds, if you find that the process is interrupted with and error(s) message it must be that either this is not the last Martian Source file or the Build-Essentials is not installed yet. (It is highly recommended to do this on a recently installed system to prevent any unknown issues).

 
Once the Martian Module is build you proceed to the installation by typing in the Terminal.

 
> you@you:~/Desktop/martian-full-20080407$ sudo make install   
It will ask for you password then after you type it hit the enter key (comment for the new user: the password does not appear in the terminal in any way it stays “blank”). You can find more information about sudo in your system documents.

 
Now the Martian Module is installed and ready to run, in order to start it now you type in the Terminal.

 
> you@you:~/Desktop/martian-full-20080407$ sudo modprobe martian_dev   
Then.

 
> you@you:~/Desktop/martian-full-20080407$ sudo martian_modem   
This last command shall run the module and it will tell you where the modem is located, in this case is 
/dev/ttySM0 (the last is a zero not a capital o). Note that some people prefer to make a symbolic link to make /dev/ttySM0 visible under /dev/modem, but it is not necessary at all since you will have to modify the wvdial.conf file or configure any dialer you must as well enter where the modem is located. Update: For the KPPP in kubuntu the symbolic link shall be implemented, there is a procedure in the following lines in the KPPP section.

 
The Martian Module will not run automatically after boot, you need to modify you /etc/rc.local file for this to happen, note that the martian-full-20080407 folder include a file that automates this process but is not yet well developed since it will write the commands in the wrong position in the rc.local file, but modifying this file is quite simple.

 
Open the Terminal and type.

 
> you@you$ sudo gedit /etc/rc.local   
It will open the text editor with its contents in which instructs you to put any entry ABOVE the exit 0 command in order to work you need to type the following two lines.

>  
/sbin/modprobe martian_dev
martian_modem

 
exit 0

   

 
Note that there are just two lines added above the exit 0 command, if this does not run the Martian Module then try with sudo like this.

>  
/sbin/modprobe martian_dev
sudo martian_modem

 
exit 0

 
Some times you just need to do it as root therefor the usage of the sudo command. Reboot you computer to verify that the changes work with your system by trying the martian_modem in the Terminal.

 
> you@you$ sudo martian_modem   
It shall give you the following error.

>  
martian: error: open: Device or resource busy 
martian: info: martian is already running.

 
At this moment if you did not found any other error or problem you must have your Lucent Aegere modem working and visible under K/Ubuntu, but now you need to dial to your Internet Provider for this you usually have the phone number to dial, your ID and password and that is all you need for a simple setting. For advance configurations refer to its respective guides in your system documents or in the Ubuntu documentation.
 
WVDIAL
This program is installed by default and you can configure it in different ways, the most simple is to open the terminal and type.

 
> you@you$ sudo gedit /etc/wvdial.conf   
Then hit the enter key and a text editor will display the contents of this file, it will show three to four options without any value, you will need to have a least this ones to make it run the dial process. Note that Phone, Username and Password need to have your own information. Modem, PPPD and Carrier Check are the same as shown here.

>  
[Dialer Defaults]
Modem = /dev/ttySM0
Phone = 12345678910
Username = YourID
Password = YourPassword
New PPPD = yes
Carrier Check = no

 
For any extra option refer to the wvdial manual pages in your system documents. There is also a wvdial.conf example in the Script folder of the Martian folder.

 
Save you document and in the terminal type.

 
> you@you$ sudo wvdial   
After you hit the enter key you will hear the modem dialing. Later you can create a launcher icon in your panels or menu for this command.

 
GNOME-PPP
This is a little program for Ubuntu that will work with your wvdial and configure it in the GUI itself instead of the text editor, just type your information in the required spaces and dial. The only problem is that you will not be able to do it without the root mode, (it happens since Ubuntu 7.10) the solution is to edit the command in the configuration window of the launcher. 

 
In the menu or in the panel (any where you have it) right click on the icon launcher and select Properties, a window will open and in the command space type gksu gnome-ppp (or browse the path, it will look like this gksu /usr/bin/gnome-ppp) close the window and now it will ask for you password any time you launch the program.

 
Note that if you launch the gnome-ppp the first time you are going to configure it as root, it shall detect the modem device by itself, or you can type it (/dev/ttySM0) in case you did not open the program as root since it will not display it in the drop down menu.

 
Also gnome-ppp is not on the default installation, you can download and isntall it in Synaptic.

 
KPPP
For Kubuntu this is the program to use, just type your information in the respective spaces that apply and it will dial right away.
Update: Since I use gnome-ppp even in Kubuntu I did not realize that KPPP will not let you enter the correct device in this case ttySM0, there are several work a rounds for this problem, the simplest one is to open the terminal and create the symbolic link.

 
> you@you$ sudo ln -s /dev/ttySM0 /dev/modem   
And open KPPP whit the /dev/modem as device.

 
If you want to adventure in to the automated script you can create one and make it executable at startup and save time at the moment you want to use KPPP.

 
First create a blank document in your desktop by right clicking in any empty space in your screen then Create New > Text File, you can give it any name, for this example we use modemlink, open your file and place the following in it.

 
> #!/bin/sh -e
#
#Symbolic link for kppp
#

 
sudo ln -s /dev/ttySM0 /dev/modem

 
and then save it. Now open the Terminal and execute the following commands:

 
> you@you$ sudo cp ~/Desktop/modemlink /etc/init.d
Then hit the enter key, now.

 
> you@you$ cd /etc/init.d   
And here just to verify try the list command.

 
> you@you$ ls   
It shall give you a list of the files in this directory in green font color and your new file modemlink will be white. This is because the file is not executable yet. In the Terminal then we do.

 
> you@you$ sudo chmod 755 /etc/init.d/modemlink   
Hit the enter key, now try again the ls command and your file should look also in green color. Restart you computer and try it.

 
Notes: Your system documents can be accessed in the Help icon or by pressing the F1 key in a empty desktop.

 
This method was used with K/Ubuntu 8.04 and also in 7.04 and 7.10, they all work just with this module, the only variable is the martian-full-diferent_date file to be downloaded, they work better with the one made in the same range of time.

Once you update your kernel the module will not work, in this case just go to the martian folder and re do the following commands for re-installation.

> you@you$ sudo make install
you@you$ sudo modprobe martian_dev
you@you$ sudo martian_modem

In case you delete this folder allready just add the first steps in this tutorial to recompile the module.
 
The Ubuntu forums is the place to find most of the answers, try severeal key words like Lucent, Agere. Martian, Modem, etc. there are many links also that will point to important information, also when you Google for answer if using Ubuntu as part of the criteria does not give you useful results try Linux instead and you ranges will be wider.

 
Comments and Questions in expectation, please share your experience.

---

### Post by sdowney717 on 2008-06-08
yes, it looks like it is working
```

scott@scott-desktop:~/martian-full-20080407$ make all
make -C kmodule/ modules
make[1]: Entering directory `/home/scott/martian-full-20080407/kmodule'
make -C /lib/modules/2.6.24-18-generic/build M="/home/scott/martian-full-20080407/kmodule"  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  CC [M]  /home/scott/martian-full-20080407/kmodule/martian.o
/home/scott/martian-full-20080407/kmodule/martian.c: In function ‘martian_isr’:
/home/scott/martian-full-20080407/kmodule/martian.c:160: warning: value computed is not used
/home/scott/martian-full-20080407/kmodule/martian.c: In function ‘martian_add’:
/home/scott/martian-full-20080407/kmodule/martian.c:664: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  CC [M]  /home/scott/martian-full-20080407/kmodule/marsio.o
  CC [M]  /home/scott/martian-full-20080407/kmodule/mfifo.o
  LD [M]  /home/scott/martian-full-20080407/kmodule/martian_dev.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/scott/martian-full-20080407/kmodule/martian_dev.mod.o
  LD [M]  /home/scott/martian-full-20080407/kmodule/martian_dev.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make[1]: Leaving directory `/home/scott/martian-full-20080407/kmodule'
make -C modem/ all
make[1]: Entering directory `/home/scott/martian-full-20080407/modem'
-e     CC	main.o
-e     CC	dumpers.o
-e     CC	log.o
-e     CC	session.o
-e     CC	mport.o
-e     CC	pty.o
-e     CC	sysdep.o
-e     CC	isr.o
-e     CC	smp.o
-e     CC	core_if.o
-e     CC	coresubst.o
-e     CC	link.o
-e     CC	tweakrelocsdynamic.o
-e     CC	coreadd.o
-e     CC	elf386tweakrelocs
-e     LD	marscore.o
-e     TWEAK	marscore.o
-e     LD	martian_modem
make[1]: Leaving directory `/home/scott/martian-full-20080407/modem'
scott@scott-desktop:~/martian-full-20080407$ sudo make install 
[sudo] password for scott: 
make -C kmodule/ install
make[1]: Entering directory `/home/scott/martian-full-20080407/kmodule'
make -C /lib/modules/2.6.24-18-generic/build M="/home/scott/martian-full-20080407/kmodule" modules_install
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-18-generic'
  INSTALL /home/scott/martian-full-20080407/kmodule/martian_dev.ko
  DEPMOD  2.6.24-18-generic
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
if ! /sbin/modprobe -nq martian_dev ; then /sbin/depmod -a; fi
make[1]: Leaving directory `/home/scott/martian-full-20080407/kmodule'
make -C modem/ install
make[1]: Entering directory `/home/scott/martian-full-20080407/modem'
-e     LD	martian_modem.debug
-e     STRIP	martian_modem.debug
-e     STRIP	martian_modem.stripped
-e     INSTALL	/usr/sbin/martian_modem
-e     INSTALL	/usr/lib/debug/usr/sbin/martian_modem.debug
make[1]: Leaving directory `/home/scott/martian-full-20080407/modem'
scott@scott-desktop:~/martian-full-20080407$ sudo modprobe martian_dev 
scott@scott-desktop:~/martian-full-20080407$ sudo martian_modem 
martian: info: Your port is /dev/ttySM0

```

---

### Post by RJQ on 2008-06-09
> **sdowney717 said:**
> yes, it looks like it is working...

I glad it works, thanks for sharing your terminal outpost it make it even easier for the readers to see what is going to happens during compilation.

I just upgrade the kernel in my machine and the re-installation of the module worked painlessly.

cheers!

---

### Post by donaldnic on 2008-07-10
> **RJQ said:**
> Installing the Martian Module for Lucent Agere Modem Tutorial.

 
This is actually quite a simple procedure, just read carefully any text related especially those in the folders of the ScanModem and Martian Module, they also show a less detailed instructions on how to use them, here I am trying to be as accurate as possible mentioning just the essentials and usually missed parts of the process, with some extra details for the novice same that help me in my own situation. I hope this words to be useful for any one in need.

 
If you know already that your modem is the Lucent is fair to skip the following steps in relation, if not you can continue, now if you have a computer with Windows in it still (in a dual boot) you can also look for your modem like this.

 
In Windows click on start > control panel. (then, the easiest way is to switch to classic view, and double-click the System icon.) then, click on the Hardware tab, and then Device Manager. Expand the Modems tab by clicking on the +, and your modem should be listed, in this case the Lucent Agere.

 
If you just have K/Ubuntu you can try [ScanModem]("http://linmodems.technion.ac.il/packages/scanModem.gz"). For more details about ScanModem and how to find if you need the Martian Module please refer to the [Ubuntu documentation]("https://help.ubuntu.com/8.04/internet/C/modem-identify.html") section of the same.

 
Prerequisites for the installation:
[LIST]
[*]Repetitive yet important; knowledge that you need the Martian Module. If you did the ScanModem the 1stRead.txt will tell you if this is the module you need.
[*]The package build-essential (in a fresh installation) which come in the live CD but it is not installed by default.
[*]The last Martian (20080407 for K/Ubuntu 8.04) source package found [here]("http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/martian-full-20080407.tar.gz").
[/LIST]
 
First you need to install the build-essential package from the live CD, place it in the tray and open in your menu System > Administration > Synaptic then click on Settings > Repositories and add the CD in the bottom of the window where is mention, in this case Ubuntu 8.04. close and then click on reload. Now in the left panel click on Origin and it will show the CD name, click on the name with the Main termination. It shall list build-essential, install it along with its dependencies (those are installed automatically by Synaptic).

 
Download the martian-full-20080407.tar.gz to your desktop (this is the easier folder) and right click on it, select Extract Here, now you have a new folder with the same name than the downloaded one, open the terminal by going Applications > Accessories > Terminal. If you Terminal window does not cover the whole screen you can simply drag the folder in it after a cd command. (example: you@you$ cd /home/Desktop/martian-full-20080407) or you can type the entire command and directory in the terminal. By this time you shall be with a open terminal an in the Martian folder directory looking something like this.

 
   
You can also verify by typing in the terminal ls and the result is the files and folders contained in the Martian folder, open Nautilus by double clicking in the Martian folder on your desktop and shall be the same.

 
Next step is to compile the module by typing the following in the Terminal.

 
   
At this moment you will see some procedure that takes some seconds, if you find that the process is interrupted with and error(s) message it must be that either this is not the last Martian Source file or the Build-Essentials is not installed yet. (It is highly recommended to do this on a recently installed system to prevent any unknown issues).

 
Once the Martian Module is build you proceed to the installation by typing in the Terminal.

 
   
It will ask for you password then after you type it hit the enter key (comment for the new user: the password does not appear in the terminal in any way it stays “blank”). You can find more information about sudo in your system documents.

 
Now the Martian Module is installed and ready to run, in order to start it now you type in the Terminal.

 
   
Then.

 
   
This last command shall run the module and it will tell you where the modem is located, in this case is 
/dev/ttySM0 (the last is a zero not a capital o). Note that some people prefer to make a symbolic link to make /dev/ttySM0 visible under /dev/modem, but it is not necessary at all since you will have to modify the wvdial.conf file or configure any dialer you must as well enter where the modem is located. Update: For the KPPP in kubuntu the symbolic link shall be implemented, there is a procedure in the following lines in the KPPP section.

 
The Martian Module will not run automatically after boot, you need to modify you /etc/rc.local file for this to happen, note that the martian-full-20080407 folder include a file that automates this process but is not yet well developed since it will write the commands in the wrong position in the rc.local file, but modifying this file is quite simple.

 
Open the Terminal and type.

 
   
It will open the text editor with its contents in which instructs you to put any entry ABOVE the exit 0 command in order to work you need to type the following two lines.


   

 
Note that there are just two lines added above the exit 0 command, if this does not run the Martian Module then try with sudo like this.


 
Some times you just need to do it as root therefor the usage of the sudo command. Reboot you computer to verify that the changes work with your system by trying the martian_modem in the Terminal.

 
   
It shall give you the following error.


 
At this moment if you did not found any other error or problem you must have your Lucent Aegere modem working and visible under K/Ubuntu, but now you need to dial to your Internet Provider for this you usually have the phone number to dial, your ID and password and that is all you need for a simple setting. For advance configurations refer to its respective guides in your system documents or in the Ubuntu documentation.
 
WVDIAL
This program is installed by default and you can configure it in different ways, the most simple is to open the terminal and type.

 
   
Then hit the enter key and a text editor will display the contents of this file, it will show three to four options without any value, you will need to have a least this ones to make it run the dial process. Note that Phone, Username and Password need to have your own information. Modem, PPPD and Carrier Check are the same as shown here.


 
For any extra option refer to the wvdial manual pages in your system documents. There is also a wvdial.conf example in the Script folder of the Martian folder.

 
Save you document and in the terminal type.

 
   
After you hit the enter key you will hear the modem dialing. Later you can create a launcher icon in your panels or menu for this command.

 
GNOME-PPP
This is a little program for Ubuntu that will work with your wvdial and configure it in the GUI itself instead of the text editor, just type your information in the required spaces and dial. The only problem is that you will not be able to do it without the root mode, (it happens since Ubuntu 7.10) the solution is to edit the command in the configuration window of the launcher. 

 
In the menu or in the panel (any where you have it) right click on the icon launcher and select Properties, a window will open and in the command space type gksu gnome-ppp (or browse the path, it will look like this gksu /usr/bin/gnome-ppp) close the window and now it will ask for you password any time you launch the program.

 
Note that if you launch the gnome-ppp the first time you are going to configure it as root, it shall detect the modem device by itself, or you can type it (/dev/ttySM0) in case you did not open the program as root since it will not display it in the drop down menu.

 
Also gnome-ppp is not on the default installation, you can download and isntall it in Synaptic.

 
KPPP
For Kubuntu this is the program to use, just type your information in the respective spaces that apply and it will dial right away.
Update: Since I use gnome-ppp even in Kubuntu I did not realize that KPPP will not let you enter the correct device in this case ttySM0, there are several work a rounds for this problem, the simplest one is to open the terminal and create the symbolic link.

 
   
And open KPPP whit the /dev/modem as device.

 
If you want to adventure in to the automated script you can create one and make it executable at startup and save time at the moment you want to use KPPP.

 
First create a blank document in your desktop by right clicking in any empty space in your screen then Create New > Text File, you can give it any name, for this example we use modemlink, open your file and place the following in it.

 

 
and then save it. Now open the Terminal and execute the following commands:

 
Then hit the enter key, now.

 
   
And here just to verify try the list command.

 
   
It shall give you a list of the files in this directory in green font color and your new file modemlink will be white. This is because the file is not executable yet. In the Terminal then we do.

 
   
Hit the enter key, now try again the ls command and your file should look also in green color. Restart you computer and try it.

 
Notes: Your system documents can be accessed in the Help icon or by pressing the F1 key in a empty desktop.

 
This method was used with K/Ubuntu 8.04 and also in 7.04 and 7.10, they all work just with this module, the only variable is the martian-full-diferent_date file to be downloaded, they work better with the one made in the same range of time.

Once you update your kernel the module will not work, in this case just go to the martian folder and re do the following commands for re-installation.



In case you delete this folder allready just add the first steps in this tutorial to recompile the module.
 
The Ubuntu forums is the place to find most of the answers, try severeal key words like Lucent, Agere. Martian, Modem, etc. there are many links also that will point to important information, also when you Google for answer if using Ubuntu as part of the criteria does not give you useful results try Linux instead and you ranges will be wider.

 
Comments and Questions in expectation, please share your experience.
Sorry but my english is not good. I will write in spanish forward.

Intenté instalar mi Lucent modem con el archivo pero mi sistema es de 64 bits (8.04 LTS Hardy) y al terminar de compilar me da un error que dice que no se pueden convertir drivers de la plataforma xf_386 a xf_amd64.

Parece que el archivo non-free incluido en el paquete es para sistemas de 32 bits y no funciona con archivos de 64 bits.

Es una lástima que no pueda enviarte la salida textual, porque estoy escribiendo desde un cybercafe con Windows y de casualidad encontre este mensaje buscando con Google.

Si pudiera alguien de ustedes ayudarme, agradeceria mucho su apoyo.

donaldnic

---

### Post by Wix on 2008-07-14
donaldnic:

Thanks for your write-up.  I came across a problem.

All check out fine with the scanmodem and then proceeded to do a compile.

There seems to be a problem with the latest
martian-full-20080625.tar.gz   file.   I tried to compile this version with
kernel -2.6.24-19-generic for Ubuntu.  I believe there is something wrong
with the make file and ......   I have tried to contact the creator's but, have had no success...........                      

Following are results from my attempts>>>>>

wix@passport-laptop:~/Lucent$ ls
martian-full-20080625  Scanmodem
wix@passport-laptop:~/Lucent$ cd martian-full-20080625
wix@passport-laptop:~/Lucent/martian-full-20080625$ make all
make: *** No rule to make target `all'.  Stop.
wix@passport-laptop:~/Lucent/martian-full-20080625$ make clean
make -C kmodule/ clean
make[1]: Entering directory `/home/wix/Lucent/martian-full-20080625/kmodule'
make -C /lib/modules/2.6.24-19-generic/build
M="/home/wix/Lucent/martian-full-20080625/kmodule" clean
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: Leaving directory `/home/wix/Lucent/martian-full-20080625/kmodule'
make -C modem/ clean
make[1]: Entering directory `/home/wix/Lucent/martian-full-20080625/modem'
   RM    OBJS
   RM    BINS
   RM    TOOLS
make[1]: Leaving directory `/home/wix/Lucent/martian-full-20080625/modem'
wix@passport-laptop:~/Lucent/martian-full-20080625$ make all
make: *** No rule to make target `all'.  Stop.
wix@passport-laptop:~/Lucent/martian-full-20080625$ ls
ChangeLog     INSTALL   Makefile~                     modem
Cleaning.txt  kmodule   martian-full-20080625.tar.gz  README
Concept       Makefile  martian.h                     scripts
wix@passport-laptop:~/Lucent/martian-full-20080625$ make
The martian_dev.ko driver and the complementary helper martian_helper are
for use with kernels after 2.6.20. Use the martian-20080407.tar.gz for
earlier kernels.
wix@passport-laptop:~/Lucent/martian-full-20080625$


Would appreciate any help or direction...    Thanks    Wix

---

### Post by C. Wizard on 2008-08-09
RJQ,
Thank you for taking the time to write this Tutorial. Greatly
appreciated.
However, I wasn't able to get it to compile on Kubuntu 8.04 amd_64. 
Any recommendations on what has to be done to get it to work
on a 64 bit system?
Again, Thank you.

---

### Post by C. Wizard on 2008-08-10
OK. I found a binary driver for the Agere Soft modem, but it won't install in amd_64.
Is there a way to force it to install in a 
64 bit system?
Many Thanks.

---

### Post by RJQ on 2008-08-13
I am sorry guys, I was not around... any way, I can see that there is a problem with the 64 bits machines, have not read any thing about it, but I will try to find some info, the person(s) in care of the module are posting new upgrades on their site, may be there we can find some info. also let us try linmodems info to see if there is something interesting., hope we can find some solution.

Donalnic: Tan pronto como encuentre algo de informacion te la paso, disculpa la tardanza no andaba por estos rumbos ultimamente.

---

### Post by RJQ on 2008-12-04
It also works for 8.10 too. the martian developers got all the steps needed for the installation in a text file. it is much easier this time. I had tested in both Ubuntu and Kubuntu and it works as before. To bad the systems by their own are buggier than ever. so good luck to the adventurers.

there is also a few lines for the 64 bit users in the same text file called "install"

---

### Post by mackra on 2009-06-04
x86_64 platform. 
----------------

martian_modem is a 32-bit application. It can be built on x86_64 the way prescribed, but you need 32-bit development environment for that. Second option is to use binary built on i386.

The above text is from the INSTALL text file

Assuming that I am a complete idiot, explain what I need to install for the 32-bit development requirement.  Or how do I build it on a i386 on machine A (32bit) and what do I do with it on machine B (64bit).

Rich

---

### Post by kingtiger01 on 2009-10-25
that means you need the amd64-dev headers and the i386-dev headers...

on a side note... anyone got this to work with hylafax right... ive hit a brickwall trying to fix ltmodem to make it work on >2.6.10-kernel

since i couldnt get martian to work with faxing...

Most of the probems i had with that were relative to the kernel-headers missing version info.

but am getting no where with the c-code...

---

### Post by aliirani on 2011-01-08
I use a lucent modem.
I can't install this modem in ubuntu 10.04!
Is there any idea to solve this problem?!
[http://ubuntuforums.org/showthread.p...1#post10330831](http://ubuntuforums.org/showthread.p...1#post10330831)

---

