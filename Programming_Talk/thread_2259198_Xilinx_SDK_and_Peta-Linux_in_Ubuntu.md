---
title: "Xilinx SDK and Peta-Linux in Ubuntu"
date: 2015-01-02
forum: Programming Talk
---

### Post by Polorboy on 2015-01-02
Lets try this again....


I will keep it extremely simple this time, don't want to confuse anyone:

anyone ever use Xilinx Vivado, Xilinx SDK, and Xilinx Peta-Linux to write code for Xilinx FPGA's in Ubuntu before?

I get this error, even running with "sudo":

chmod: cannot access &#8216;/tmp/tmp.d5BKKHLOQn/petalinux-v2014.4-final/tools/common/petalinux/utils/petalinux-env-check&#8217;: No such file or directory
INFO: Checking installation environment requirements...
/tmp/tmp.vSiKqoCQ59/petalinux-v2014.4-final/tools/common/petalinux/utils/petalinux-install: line 274: /tmp/tmp.d5BKKHLOQn/petalinux-v2014.4-final/tools/common/petalinux/utils/petalinux-env-check: No such file or directory

---

### Post by ian-weisser on 2015-01-02
'No such file or directory' means just that. Not a permission error or I/O error or memory error or other error. 

If it's the result of a typed command, your target file is wrong. (Bad instructions? Typo?)

If it's the result of a script, then the script has a bug. It's looking for an application (petalinux-env-check) that's not at the expected location. 
Perhaps a version change moved it somewhere else?
Maybe something is installed in the wrong order?
Please report the bug to the script author.

---

### Post by Polorboy on 2015-01-02
I am following instructions here: [http://blog.idv-tech.com/2014/02/10/petalinux-sdk-on-ubuntu-13-10-64bit/](http://blog.idv-tech.com/2014/02/10/petalinux-sdk-on-ubuntu-13-10-64bit/)

Those commands are not typed in by anyone, they are coming from a .run file provided by Xilinx.

---

### Post by sandyd on 2015-01-02
> **Polorboy said:**
> I am following instructions here: [http://blog.idv-tech.com/2014/02/10/petalinux-sdk-on-ubuntu-13-10-64bit/](http://blog.idv-tech.com/2014/02/10/petalinux-sdk-on-ubuntu-13-10-64bit/)

Those commands are not typed in by anyone, they are coming from a .run file provided by Xilinx.

At which step are you getting the error?

---

### Post by Polorboy on 2015-01-02
About half way down the page at this location:

Change permissions for PetaLinux installer and run it:

[INDENT]d9@ubuntu:~/Downloads$ sudo chmod 755 petalinux-v2013.10-final-installer.run
d9@ubuntu:~/Downloads$ sudo ./petalinux-v2013.10-final-installer.run --log petalinux_inst.log /opt
[/INDENT]
 
The only difference being that I am not installing drivers for the Zedboard, I have the Xilinx ZC706 development board.  Which I have the drivers for from Xilinx.
 
[INDENT]
[/INDENT]
[INDENT]
[/INDENT]

---

### Post by ian-weisser on 2015-01-02
Are you willing to post that .run file here?
I don't use any of that software myself.

---

### Post by Polorboy on 2015-01-02
It is all free to download for anyone at [http://www.xilinx.com/support/download.html](http://www.xilinx.com/support/download.html), the files are over a GB and I have no where to host them for download.  You will need to make an account at Xilinx to get access.  The Vivado suite is over 5GB, the PetaLinux installer is 1.1GB.

I tried using their web installer in Linux but it crashes due to permissions and unable to create a directory, even when running with sudo.

I am fairly certain that all of this has to do with permissions problems since the programs are supposed to be creating these directories themselves and can't, even when running with "elevated" privileges.

---

### Post by sandyd on 2015-01-02
> **Polorboy said:**
> It is all free to download for anyone at [http://www.xilinx.com/support/download.html](http://www.xilinx.com/support/download.html), the files are over a GB and I have no where to host them for download.  You will need to make an account at Xilinx to get access.  The Vivado suite is over 5GB, the PetaLinux installer is 1.1GB.

I tried using their web installer in Linux but it crashes due to permissions and unable to create a directory, even when running with sudo.

I am fairly certain that all of this has to do with permissions problems since the programs are supposed to be creating these directories themselves and can't, even when running with "elevated" privileges.

The web installer works fine for me
```

bash Xilinx_Vivado_SDK_2014.4_1114_1_Lin64.bin
```

Installer shows up, asks me for username/pass etc

Just install it to /home/*yourusernamehere*/*foldername*
and you should be fine.

---

### Post by Polorboy on 2015-01-02
I need to install it to the same location that Vivado was installed to, which defaulted to the opt directory.

---

### Post by sandyd on 2015-01-02
I dont remember if gksudo is installed, so...
```

sudo apt-get install gksu
gksudo bash Xilinx_Vivado_SDK_2014.4_1114_1_Lin64.bin
```

Installer should now be able to install into /opt

---

### Post by steeldriver on 2015-01-02
> **Polorboy said:**
> I need to install it to the same location that  Vivado was installed to, which defaulted to the opt directory.

According to [this xilinx wiki]("http://www.wiki.xilinx.com/Zynq+Base+TRD+2013.3#x-5%20Installation%20of%20Petalinux%20SDK")
> 
PetaLinux will be installed in the petalinux-v2013.10-final directory,  directly underneath the working directory of this command.
So, if you install the installer into your home directory /home/user,  PetaLinux will be installed in /home/user/petalinux-v2013.10-final.
**You may move the resulting petalinux-v2013.10-final directory to a preferred location before continuing**.


---

### Post by Polorboy on 2015-01-04
I tried to install gksudo, and got this:

sudo apt-get install gksudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksudo

---

### Post by Polorboy on 2015-01-04
I was somehow able to get it installed, still not quite sure how that happened.  Getting it to run is the next hurdle.

  However, now I am getting a warning that I am not root and an error that it can't find g++ in the path.  G++ was the first thing I installed.  I read somewhere that it was suggested to make a "make" file.  Now, the entirety of my experience has been developing in Windows, which as far as I am concerned is significantly simpler and easier to do.  Regardless, I don't ever see myself ever having to type the command "make" since I am going to be doing everything from the Xilinx SDK and that itself should be doing all of that stuff.  My question is, how do I add g++ to the Linux path variable permanently.  I know it can get done any number of ways that are varying degree of temporary, but I want to do it once and never have to do it again.  Again, this is a simple task in Windows.  I literally just go to system settings and edit the Path variable, takes about 2 seconds.  From what I have read and understand this is no simple task in Linux.  Anyone care to let me know how it is done?

---

### Post by ian-weisser on 2015-01-04
See [http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-pathfor](http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-pathfor) a rundown of many of ways to add a path to your $PATH, and the discussion of which may be appropriate for you.

It's very easy on Linux, too.

---

### Post by Polorboy on 2015-01-06
I am still unable to install gksudo, since that is the "recommended" way to run an gui application from the console.  I am still getting the following when trying to install gksudo:

sudo apt-get install gksudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksudo

I also tried to create a launcher, but quickly realized that this also was removed from Ubuntu.  So, I found the following article about adding the functionality back to Ubuntu and that is also not working: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles).  I created a launcher for the Xilinx SDK as in the "Using gnome-panel/alacarte" section but the SDK does not launch.  

I finally get this installed and the only way to launch it is to go directly to the folder where it installed and run the application via "sudo" from a console?  Why does Linux have a GUI again?  I don't think I have ever launched a usable program from an icon or any desktop element?  I am not being facetious, I don't get what having a GUI does when everything has to be launched from a console anyway?  It is getting annoying though.

I was also getting the ibus warning that I wasn't root, so I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=2140352](http://ubuntuforums.org/showthread.php?t=2140352) and [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944).  What I got from that was that it was going to be ignored, so I deleted the folder.  I don't know what it does or why it is even needed.  A few people seemed to have success with removing the error by deleting the folder.

---

### Post by Irihapeti on 2015-01-06
The package you need goes by the name of gksu.

```
sudo apt-get install gksu
```
will install it. You can then run gksudo from a terminal.

---

### Post by sandyd on 2015-01-06
> **Polorboy said:**
> I am still unable to install gksudo, since that is the "recommended" way to run an gui application from the console.  I am still getting the following when trying to install gksudo:

sudo apt-get install gksudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksudo

I also tried to create a launcher, but quickly realized that this also was removed from Ubuntu.  So, I found the following article about adding the functionality back to Ubuntu and that is also not working: [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles).  I created a launcher for the Xilinx SDK as in the "Using gnome-panel/alacarte" section but the SDK does not launch.  

I finally get this installed and the only way to launch it is to go directly to the folder where it installed and run the application via "sudo" from a console?  Why does Linux have a GUI again?  I don't think I have ever launched a usable program from an icon or any desktop element?  I am not being facetious, I don't get what having a GUI does when everything has to be launched from a console anyway?  It is getting annoying though.

I was also getting the ibus warning that I wasn't root, so I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=2140352](http://ubuntuforums.org/showthread.php?t=2140352) and [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944).  What I got from that was that it was going to be ignored, so I deleted the folder.  I don't know what it does or why it is even needed.  A few people seemed to have success with removing the error by deleting the folder.

Sorry, made a typo - and fixed it

---

### Post by Bucky Ball on 2015-01-07
> **Irihapeti said:**
> The package you need goes by the name of gksu.

```
sudo apt-get install gksu
```
will install it. You can then run gksudo from a terminal.

^^^
This. ;)

---

