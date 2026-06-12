---
title: "Nvidia graphics card"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by quarkhirad on 2012-02-27
I have installed ubuntu 11.10 on my DELL XPS l502x latop. It is a core i7 2.2GHz, 8Gb ram, 2GB nvidia 540M graphics card. Now after installation i open system settings and then open system info and click on graphics. It shows the following:

Driver Intel Sandybridge mobile x86/MMX/SSE2 
Experience standard 

Looking at this it is obvious that my nvdia graphics card is not being detected. 

I then realized that i have to install the restricted nvdia graphics driver ( this is what i did on my HP dv6767TX wich had a nvidia graphics). Thus i opened additional drivers in system settings .It says no propriety drives are being used.

How do i install the restricted drivers?

My compiz is sluggish and slow obviously because the drivers are not installed.

---

### Post by kc1di on 2012-02-27
have you done a system update? if so make sure you reboot before trying to install the drivers.

---

### Post by haqking on 2012-02-27
depends on your preference but i always use the proprietary drivers, the installer is a piece of cake and works real well

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by SeijiSensei on 2012-02-27
As I suspected, the machine is using "Optimus" to manage its two video cards.  Do a search here for "optimus" and one for "bumblebee" to take a look at your options.

On my daughter's HP laptop, I had to change a BIOS setting so that Linux would see her ATI card as well as her Intel one.

---

### Post by quarkhirad on 2012-02-27
kc1di 

> i tried restarting but the problem still exists. 

haqking

> I went to the link and using option one i selected the following 

Product type      Geforce
Product series    Geforce 500 series
operating system  linux 32 bit
language          English (us)

In the search results i checked the supported products tab and found the driver in the search result supports 540m graphics card. I then downloaded the file 

NVIDIA-Linux-X86-295.20.run 

Now how do i use the file to install my drivers.

---

### Post by quarkhirad on 2012-02-27
> **SeijiSensei said:**
> As I suspected, the machine is using "Optimus" to manage its two video cards.  Do a search here for "optimus" and one for "bumblebee" to take a look at your options.

On my daughter's HP laptop, I had to change a BIOS setting so that Linux would see her ATI card as well as her Intel one.

Sorry my friend i dint understand what you said can you please ellaborate.

---

### Post by kc1di on 2012-02-27
here is a page that will outline how to install that driver file. 
[http://www.moonlitdog.com/nvidia_ubuntu]("http://www.moonlitdog.com/nvidia_ubuntu")
Still don't quite understand why the additional driver tool did not find it.

---

### Post by idoitprone on 2012-02-28
i have a nvidia optimus laptop with the same card i will help you
give me time to make a small guide

---

### Post by idoitprone on 2012-02-28
This is to install bumblebee
to use descrete card
open terminal
```
optirun program
```these are steps to install
I have not tested the ppa since i do not use ubuntu but i use debian
```


sudo add-apt-repository ppa:bumblebee/stable 
sudo apt-get update
 sudo apt-get install bumblebee bumblebee-nvidia
sudo apt-get install virtualgl-libs:i386

sudo usermod -a -G bumblebee $USER
```this is a kernel module to switch off the card when not in use automatically

```
sudo apt-get install git-core build-essential checkinstall
git clone https://github.com/Bumblebee-Project/bbswitch.git
cd bbswitch
make
sudo make load
```

Note: i hope i got all the correct dependencies or else look at the README or MAKEFILE
**[https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu](https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu)**

---

### Post by bogan on 2012-02-28
Hi!, **quarkhirad,**

If you had installed the 'Other Hardware' driver it would have been nvidia-current which is v280.13, but which I do not believe supports your card.

No-one seems to have answered your query:>  In the search results I checked the supported products tab and found the driver in the search result supports 540m graphics card. I then downloaded the file: NVIDIA-Linux-X86-295.20.run

Now how do i use the file to install my drivers. Personall, I use the 290.10 driver with my GT520 card and have not tried the 295 version.
Provided that your system recognizes the Nvidia card. -  does:```
 lspci | grep VGA 
``` Show both cards? -  the following should help: [ substitute the correct file name.]

To Install the nvidia driver all that is necessary is to CD to the folder where you have downloaded the .run file, make it executable and run it.
First, you should add some Blacklists to the /etc/modprobe.d folder, and then, as the nvidia driver must only be installed when the GUI xorg server and screen is inactive, reboot to a Text Terminal, or shut down the Xsession from a GUI screen,

To do this check the /etc/modprobe.d folder for a file named blacklist.conf,
If it does not exist you will need to create one.

In the terminal enter:```
 gksu gedit /etc/modprobe.d/blacklist.conf
```then add:


```
 # Added for nvidia driver.
blacklist vga16fb
blacklist rivafb
blacklist rivatv
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidiafb
blacklist nvidia-173
blacklist nvidia-96
```And Save As: /etc/modprobe.d/blacklist.conf.

Reboot, preferable to Restart, and either:
From a GUI screen Terminal:```
sudo service lightdm stop    # 'gdm' in place of 'lightdm' if < 11.10
```OR:  From the Grub Menu, put cursor on the Ubuntu entry you intend as your primary usage and press 'e' to edit,
Go to the Linux boot line where it should have ' ro quiet splash' or to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ",and add ' text' instead of 'quiet splash'
press Ctrl+x to boot. [ Edit: alternative wording added, if editing /etc/default/grub.]
At the prompt log in and enter password.

In either case:
CD to where the nvidia file is and enter: dir
This will check you are in the right place and enable you to copy the exact name of the file - or use 'Tab' to complete it.```
sudo chmod a+x NVIDIA-Linux-x86-290.10.run  # Check the exact spelling; 'x86' is for 32bit
sudo sh NVIDIA-Linux-x86-290.10.run               # ditto
```Follow screen instructions.
You may get a warning that nouveau is running and must be purged first, but carry on, that's what the blacklists are for.
When complete, reboot.
nvidia-installer, nvidia-settings and nvidia-XServer-config will be installed and you can adjust things to suit your hardware and wishes.

I do not know to what extent having 'Optimus' with two cards affects this, or what change you might need to make to the Bios settings.

Good luck.
Chao!, **bogan**.

---

### Post by idoitprone on 2012-02-28
> **bogan said:**
> Hi!, **quarkhirad,**

If you had installed the 'Other Hardware' driver it would have been nvidia-current which is v280.13, but which I do not believe supports your card.

No-one seems to have answered your query:Personall, I use the 290.10 driver with my GT520 card and have not tried the 295 version.
Provided that your system recognizes the Nvidia card. -  does:```
 lspci | grep VGA 
``` Show both cards? -  the following should help: [ substitute the correct file name.]

To Install the nvidia driver all that is necessary is to CD to the folder where you have downloaded the .run file, make it executable and run it.
First, you should add some Blacklists to the /etc/modprobe.d folder, and then, as the nvidia driver must only be installed when the GUI xorg server and screen is inactive, reboot to a Text Terminal, or shut down the Xsession from a GUI screen,

To do this check the /etc/modprobe.d folder for a file named blacklist.conf,
If it does not exist you will need to create one.

In the terminal enter:```
 gksu gedit /etc/modprobe.d/blacklist.conf
```then add:


```
 # Added for nvidia driver.
blacklist vga16fb
blacklist rivafb
blacklist rivatv
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidiafb
blacklist nvidia-173
blacklist nvidia-96
```And Save As: /etc/modprobe.d/blacklist.conf.

Reboot, preferable to Restart, and either:
From a GUI screen Terminal:```
sudo service lightdm stop    # 'gdm' in place of 'lightdm' if < 11.10
```OR:  From the Grub Menu, put cursor on the Ubuntu entry you intend as your primary usage and press 'e' to edit,
Go to the Linux boot line where it should have ' ro quiet splash' or to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ",and add ' text' instead of 'quiet splash'
press Ctrl+x to boot. [ Edit: alternative wording added.]
At the prompt log in and enter password.

In either case:
CD to where the nvidia file is and enter: dir
This will check you are in the right place and enable you to copy the exact name of the file - or use 'Tab' to complete it.```
sudo chmod a+x NVIDIA-Linux-x86-290.10.run  # Check the exact spelling; 'x86' is for 32bit
sudo sh NVIDIA-Linux-x86-290.10.run               # ditto
```Follow screen instructions.
You may get a warning that nouveau is running and must be purged first, but carry on, that's what the blacklists are for.
When complete, reboot.
nvidia-installer, nvidia-settings and nvidia-XServer-config will be installed and you can adjust things to suit your hardware and wishes.

I do not know to what extent having 'Optimus' with two cards affects this, or what change you might need to make to the Bios settings.

Good luck.
Chao!, **bogan**.

The problem is tht he has nvidia **optius latop**. The descrete grahic card can turn on and off. It works by using the intel chip to offload the work to the nvidia card. The problem is that the nvidia graphic card is not connected by the display porrts. It uses the intel display port. The op has to intall bumblebee and bbswitch to gain a similar functionality

---

### Post by quarkhirad on 2012-02-28
```
 lspci | grep VGA 
``` 

The follwing is the output.From the output my graphics card is a GT 555M. 

```

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)
```


 ```
gksu gedit /etc/modprobe.d/blacklist.conf 

then add:


# Added for nvidia driver.
blacklist vga16fb
blacklist rivafb
blacklist rivatv
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidiafb
blacklist nvidia-173
blacklist nvidia-96 And Save As: /etc/modprobe.d/blacklist.conf.
```


Done 

```
sudo service lightdm stop    # 'gdm' in place of 'lightdm' if < 11.10
```

Done

```
sudo chmod a+x NVIDIA-Linux-x86-290.10.run  # Check the exact spelling; 'x86' is for 32bit
sudo sh NVIDIA-Linux-x86-290.10.run               # ditto
```


When i executed the sh command it popped a screen which asked me to read the license agreement. I said i accept. It the gave an error. I then said do not continue. Can i ignore this error. If not please tell me what to do. 

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Feb 29 07:57:39 2012
installer version: 295.20

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 295.20.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: No)
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by bogan on 2012-02-29
Hi!, **quarkhirad,**

I would try again, making sure I have highlighted the 'Accept' button with the arrow key and see what happens.

From the log file entry I doubt it will install successfully, if not, try:```
 sudo nvidia-installer --f
``` You will probably get an 'unknown command', but if not, it will force a download and install over anything already installed.

If it does not, I would then delete the .run file,  re-download a fresh copy and try again.

**Edit:**
According to the NVIDIA download site the 295.20 driver also supports the GT 555M card.

Good Luck,

Chao!, **bogan.**

---

### Post by quarkhirad on 2012-03-01
Ok i did it i installed it and i restarted my computer. However when i open NVIDIA X-server settings it gives an error

```
You do not appear to be using the NVIDIA X driver.  
Please edit your X configuration file (just run `nvidia-xconfig` as root),
 and restart the X server.
```

However when i run the command this is what i get 


```
khirad@Jeena:~$ sudo nvidia-xconfig 
[sudo] password for khirad: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

Can someone help.

Oh and just for your information now i have no effects. The desktop switcher is like ubuntu 6.06. That is no visual effects. I guess it is because of this Xorg.config thing.

---

### Post by quarkhirad on 2012-03-01
Oh i would also like to add that after i restart the computer i dint get my login screen instead i got a black screen with several process and [pass] or [fail] on the right side of the screen. 

So i logged into a text terminal ( ctrl+alt+F1) and then typed the following. 

```
sudo mv /etc/X11/xorg.conf /home/khirad/Desktop
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo service lightdm stop
sudo service lightdm start 
```

Only then did i get my login screen.

---

### Post by quarkhirad on 2012-03-01
This is the xorg file that nvidia created. 


```
khirad@Jeena:~$ cat /home/khirad/Desktop/xorg.conf 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 280.13  (buildmeister@swio-display-x86-rhel47-05.nvidia.com)  Wed Jul 27 17:18:55 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by bogan on 2012-03-02
Hi!, **quarkhirad**,

The xorg.conf file you posted shows nvidia-xconfig version 280.13, which is nvidia-current and, AFAIK, does not support your card; not v 290.10 or 295.2 which do.

Did you use the 'Additional Drivers' app to install the driver??

I will try and get someone who knows more about NVIDIA and 'Optimus', than I do, to have a look.

Chao!,** bogan**.

---

### Post by quarkhirad on 2012-03-02
Bogan 
Yes i used additional drivers to install my graphics card.

---

### Post by quarkhirad on 2012-03-02
> **idoitprone said:**
> This is to install bumblebee
to use descrete card
open terminal
```
optirun program
```these are steps to install
I have not tested the ppa since i do not use ubuntu but i use debian
```


sudo add-apt-repository ppa:bumblebee/stable 
sudo apt-get update
 sudo apt-get install bumblebee bumblebee-nvidia
sudo apt-get install virtualgl-libs:i386

sudo usermod -a -G bumblebee $USER
```this is a kernel module to switch off the card when not in use automatically

```
sudo apt-get install git-core build-essential checkinstall
git clone https://github.com/Bumblebee-Project/bbswitch.git
cd bbswitch
make
sudo make load
```

Note: i hope i got all the correct dependencies or else look at the README or MAKEFILE
**[https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu](https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu)**

I did it all and then restarted lightdm. I have got my compiz effects of desktop cube etc :) :). However it is slow and sluggish :( :(. When i check the graphics tab in system info in System settings it says its using intel sandybridge. Thus it is not utilizing my graphics card.

---

### Post by MAFoElffen on 2012-03-02
LOL.... I caught up with this thread.

The Op has two challenges: 

1. The NVidia 550x requires nVidia 295.20 or newer. It is a "new" chipset. The 290.10 driver that is in the "main" repo's only supports up to the 530.x chipset. That leaves him with 2 options-

 a) DL and install 295.20 binary from NVidia
 [COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")**[/SIZE][/COLOR][/SIZE][/COLOR]

 b) Add the Edgers PPA <-- nvidia 295.20 is in the Edger's PPA.  
[Xorg-Edgers PPA]("http://www.ubuntuupdates.org/ppa/xorg-edgers")

Note that 290.20 is not in the "main" repository yet... 

2. That laptop is Optimus (Hybrid Graphics).  Good instructions on installing Bumblebee there in that previous post... But you still need to install the NVidia driver first.  The Bumblebee install script then installs it's scripts, copies the NVidia Xorg.conf file to where it will copy from when in use.

Other options are 
 a) Install "Ironhide," which branched from Bumblebee, but is a graphical interface over the same scripts as Bumblebee...
 b) Turn on/off the discrete GPU (nVidia) via the BIOS Setup. A "few" manufacturers have this option.
 c) Turn off the discrete GPU (nVidia) via ACPI by means of the vga_switcheroo flag... Which is what Bumblebee and Ironhide does and relies on.

** Basically what happens is that the discrete card (in this case Nvidia) is switched on or off. When on, the Xorg.conf files that is set up for Nvidia is copied into the /etc/X11/ directory. When the discrete card is turned off then, then you copy in an Xorg.conf for the Intel driver. The Intel GPU stays on all the time/no way to turn that one off. 

So the basis for all this is to try to save battery power when doing regular things in a low resolution, then turning on and using the higher resolution card when visual aesthetics are prefered. You could leave the discrete GPU on all the time, it would just drain the battery faster...

Note that Microsoft has been trying to dissuade laptop manufacturers away from this kind of technology for about 2 years or so...

Enough info, or do you need detailed instructions or link to such.

---

### Post by bogan on 2012-03-03
Hi**!, MAFoElffen,**

Thanks for your response and info. There are several more threads referring to the same issue; much appreciated.

@**quarkhirad**,

Hope Mike's info clarifies things for you.

Dont bother with the failure of SystemInfo to correctly identify the Graphics in use.

On my Desktop it said the graphics was Vesa when it was Nvidia 280, and when I updated to v290.2 it said it was 'Unknown'.

Chao!, **bogan.**

---

