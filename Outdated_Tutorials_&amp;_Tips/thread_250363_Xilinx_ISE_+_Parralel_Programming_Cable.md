---
title: "Xilinx ISE + Parralel Programming Cable"
date: 2006-09-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Fluffy_v on 2006-09-04
After some time I have managed to get the Xpilinx ISE 8.2i installed and working with the parallel programming cable that was included with my development board. Once I had the right files, it was pretty easy.

I am still pretty new to linux in general, but i will try and help if anyone has problems with this guide.

I have no idea if this will work with the USB programming cable, as I do not have one to test.

The driver source files are not the most current, I could not get the most current ones to work.


there are a few tutorials on installing and compiling the programming cable drivers, but none really worked for me.  These are the two I used to finally get things working.
[http://www.c3a.de/wiki/index.php/ISE_Webpack_Ubuntu](http://www.c3a.de/wiki/index.php/ISE_Webpack_Ubuntu)
[http://www.freelabs.com/~whitis/electronics/fpga/xilinx_install_deb3.1.html](http://www.freelabs.com/~whitis/electronics/fpga/xilinx_install_deb3.1.html)


My test system:
 Fresh Ubuntu 6.061 install(no idea if it will work on any other version)
 800Mhz PIII laptop
 512MB Ram
 20Gig HD.

Programming was tested and verified on a Digilent Spartan-3 Board with the included parallel programming cable.

Here are the steps I took to finally get things working, most are console commands.

# a few things are needed to build the programming cable drivers:
sudo apt-get install gcc make linux-headers-386


# need a place to store the ISE and driver source files.
mkdir xilinxISEinstall
cd xilinxISEinstall

# need to get the ISE and the driver source files (the webpack is 107MB)
wget [http://direct.xilinx.com/direct/webpack/82/WebPACK_82i_SFD.sh](http://direct.xilinx.com/direct/webpack/82/WebPACK_82i_SFD.sh)
wget [http://www.jungo.com/download/WD800LN.tgz](http://www.jungo.com/download/WD800LN.tgz)
wget [ftp://ftp.xilinx.com/pub/utilities/M1_workstation/linuxdrivers.2.6.tar.gz](ftp://ftp.xilinx.com/pub/utilities/M1_workstation/linuxdrivers.2.6.tar.gz)



# install the ISE (this install is SLOW) 
# need to agree to the licenses
# ignore the windriver errors at the end of the install
# will build the drivers later
sh WebPACK_82i_SFD.sh


# extract the windrvr driver source
tar xzf WD800LN.tgz

# build & install the windrvr driver 
cd WinDriver/redist
./configure
make
sudo make install

#enable user acces to windrvr driver
sudo chmod 666 /dev/windrvr6 

#go back to base directory
cd ..
cd ..


# extract xilinx driver 
tar zxvf linuxdrivers.2.6.tar.gz

# build & install xilinx driver 
cd linuxdrivers.2.6/xpc4drvr
./configure
make
sudo insmod ./xpc4drvr.ko


# need to run the xilinx settings script now that the drivers are installed
cd {to where you installed the ise, default is /home/"user_name"/Xilinx}
chmod 744 settings.sh
./settings.sh


Have fun! The ISE is installed and the parallel cable driver should be functioning.

Fluffy_v

---

### Post by skroll on 2006-09-04
Thanks for this guide!   I dabble in some FPGA work, and this will be helpful.  I have a laptop without a parallel port, so I have to use USB, which was alot of hoop jumping in Windows, so I can imagine it's going to involve WINE to get it to program via USB.

(I had a Digilient USB cable which is specific for a brand of prototyping board, and wouldn't work through IMPACT, it had its own custom software)

---

### Post by hecato on 2006-10-16
Should I ask if this will work on 64-bits??

Even I dont need to install drivers, only test the tool at home and do some simulation (but programming will be good).

---

### Post by hecato on 2006-10-17
Reporting that it run OK, I donwloaded the whole Gb :roll:, and installed it, the only problem was precisesly the drivers... I will see if I can do something, tought I really dont need it for the moment ;).


> 
insmod: error inserting '/lib/modules/misc/windrvr6.o': -1 Invalid module format
insmod: error inserting '/lib/modules/misc/windrvr6.o': -1 Invalid module format
error:  zipfile probably corrupt (segmentation violation)


************ setup done! ***************
That is the error, and with message box some like (I dont remember correctly)
> 
Can not execute xilinx_install/.xinstall/install_driverscript
Let see how this 32-bits app work :) on my 64-bit CPU ;).






----------------
By the way, I only installed

> 
**libstdc++6**
**motif3**
[B]portmap
[/B]Before I do first setup (tought I dont know if the setup work without them).

Tought now watching I see that I have no 6-pic installed, but I have
> 
libstdc++6-4.0- dbg, dev, pic 


---

### Post by Fluffy_v on 2006-10-23
Sorry, life has kept me rather busy as of late, I should really update this guide a bit.  Hopefully I will have some time this weekend.

The ISE software runs just fine without the drivers, but you won't be able to program anything.  The steps here were how I got the parallel programming cable to work.  If you just want to run the ISE without programming, then just download the webpack from Xilinx and install it.  Don't do the web install one, I have never had that one work.

I remember coming across many people who had trouble with the ISE on a 64-bit CPU.  Up until a few days ago I did not have access to a 64-bit CPU.  I need to install Ubuntu on it and see about the ISE and the programming cable.

---

### Post by Jbloudg20 on 2006-12-13
I was able to install the program just fine, but I cannot open it. I googled, and it seems the command is 'startise'. I get a command not found error when I type that.

So I began searching the files, and I founf one in the bin/lin directory called ise. This will let me startt the environment, but I think I need root privledges to be able to program my board. I tried typing 'sudo ise' into the terminal, and i get command not found. I changed my directory to '.../bin/lin' and tried again with the same problem.

Any help?

---

### Post by rahul_gota on 2006-12-26
I am pretty new to linux but that's how i made my ise to work.

I am not sure whether u hav  problem starting the ise. if so, easiest way is to create a launcher on your desktop and put the path as where the ise executable is .. default is /home/*username*/Xilinx/bin/lin/ise.

Or u can run the settings.sh script using
 . settings.sh 
command in the Xilinx folder and then can type ise on the command line. Unless u  close the terminal window, the command will work.

---

### Post by Jbloudg20 on 2006-12-27
I can synthesize and map, but when it comes time to place and route:
```
Process "Map" completed successfully
ERROR:ProjectMgmt - TOE: ITclInterp::ExecuteCmd gave Tcl result 'error copying "lab1.ncd" to "lab1_last_par.ncd": not owner'.
Tcl_ErrnoId: EPERM
Tcl_ErrnoMsg: not owner
_cmd: ::xilinx::Dpm::dpm_chTransformExecuteForPar dpm_parRun $piThisInterface
errorInfo: error copying "lab1.ncd" to "lab1_last_par.ncd": not owner
    while executing
"file copy -force $_NcdFile ${iv_ModuleName}_last_par.ncd"
    (procedure "::xilinx::Dpm::dpm_chTransformExecuteForPar" line 56)
    invoked from within
"::xilinx::Dpm::dpm_chTransformExecuteForPar dpm_parRun $piThisInterface"
WARNING:ProjectMgmt - "/media/hdb5/My Documents/Fall 2006/ece280/lab1/lab1_map.ngm" line 0 duplicate design unit: 'Module|lab1'

```

---

### Post by jaymode on 2007-01-28
This doesn't seem to be working in Edgy due to some problems with dash instead of bash and there is also some stuff different in the Kernel source.

---

### Post by jaymode on 2007-01-29
Actually according to this page it does work in edgy. 

[http://gentoo-wiki.com/Talk:HOWTO_Xilinx](http://gentoo-wiki.com/Talk:HOWTO_Xilinx)

Gonna give it a shot.

---

### Post by johnnybgood115 on 2007-10-22
I'm trying to run this on Gutsy Gibbon and whenever I run ./configure for the windrvr6 driver, I get an error message saying there's an unexpected "(" on line 531.  

Any help? Is there an updated download for these drivers?

---

### Post by UL_SHM on 2008-02-12
> **johnnybgood115 said:**
> I'm trying to run this on Gutsy Gibbon and whenever I run ./configure for the windrvr6 driver, I get an error message saying w.  

Any help? Is there an updated download for these drivers?

I using the driver package that was downloaded from Xilinx, and encountered the same error and many syntax errors at to run the ``install_drivers'' script on Gusty Gibbon on Intel 32bit machine.

If the line 531 of configure script is below, it may be syntax error.
function add_gcc_flag()

I modified this line as below, and after no error about line 531 of configure.
add_gcc_flag()

But other errors are left.

---

### Post by Jonas85 on 2008-05-23
try running
```
bash install_drivers
```
instead of
```
./install_drivers
```
I installed Xilinx ISE and I found there were some scripts that couldn't work without bash.
I wrote how to install Xilinx ISE on Ubuntu Hardy in [http://ubuntuforums.org/showthread.php?t=805159]("http://ubuntuforums.org/showthread.php?t=805159")

---

