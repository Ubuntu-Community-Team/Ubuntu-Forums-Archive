---
title: "[SOLVED] How do I install Nvidia Drivers?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by kayfes on 2008-06-06
Hi I am new to Ubuntu I have the the Hardy Heron release and I am trying to figure out how to install the Drivers for a 9800gt.

---

### Post by Technoviking on 2008-06-06
I'm not sure if the current NVIDIA drivers in Linux support the 9800gt yet. You can try using the restricted driver manager.

Goto **System --> Administration --> Hardware Drivers** see if will let you install the NVIDIA driver.

---

### Post by PmDematagoda on 2008-06-06
I don't think the 173 drivers have hit the Ubuntu repositories yet, so you may have to install the Nvidia drivers manually.

---

### Post by kayfes on 2008-06-06
How do I go about doing that? I followed some links but I ended up more confused.

---

### Post by kayfes on 2008-06-06
Also in my System>Admin it only shows Hardware drivers and when I open that up there is nothing there.

---

### Post by kayfes on 2008-06-06
Would be much appreciated.  I like how Ubuntu works I just want to get these drivers setup tonight.

---

### Post by PmDematagoda on 2008-06-06
First download the driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run
```

Then install the prerequisites to install the driver:-
```
sudo apt-get install build-essential
```

After that is done, kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```

Run the installer with:-
```
sudo sh NV*.run
```
allow the installer to configure the X-Server.

Start the X-Server with:-
```
sudo /etc/init.d/gdm start
```

And there you go, it's installed.

---

### Post by kayfes on 2008-06-06
The code:

sudo /etc/init.d/gdm stop

Crashed the comp.  Is it supposed to do that or what do I need to do to make that code work?

Thank you for your help.

---

### Post by SteveNorman on 2008-06-06
you need to be in a virtual terminal before you do that, as it stops x server from running. In other words it closes your desktop down and brings you to a command prompt. Do this first:

```
CTRL_ALT_F1
Login
password
```

This will bring up a command prompt (No pictures)

then from the prompt proceed with
```

sudo /etc/init.d/gdm stop

```

---

### Post by kayfes on 2008-06-06
but it still says the same thing when I put then next code in.  

sudo sh NV*.run

sh: Can't open NV*.run


Is there something I need to do after I put

sudo /etc/init.d/gdm stop

in the prompt?

---

### Post by SteveNorman on 2008-06-06
try this

```
sudo chmod a+x ./NVIDIA*.run
```

and then

```
sudo sh NV*.run
```
again

---

### Post by kayfes on 2008-06-06
This is what I get now

chmod: cannot access `./NVIDIA*.run': No such file or directory

---

### Post by Bachstelze on 2008-06-06
Of course, you must first change to the directory where you downloaded the driver. For example, if it's on your desktop :

```
cd ~/Desktop
sudo sh NVIDIA<tab>
```

---

### Post by kayfes on 2008-06-06
I will try that and post again.  Thanks again Steve just so happens thats my name ha.

Just looked and it wasn't steve well whatever you all are very helpful thank you all.

---

### Post by kayfes on 2008-06-06
Just looked and it wasn't steve well whatever you all are very helpful thank you all.

---

### Post by SteveNorman on 2008-06-06
sorry, try 

sudo chmod a+x ./NV*.run

where did you download the file to? is it on your desktop? you will see an icon for it if it is there.

if it is move it to your home directory first and try that.

first get the exact name of the file,,for example if its called nvidiadriver.173.someothercrap

do this

```
cd Desktop
mv nvidiadriver.173.someothercrap.run ~
cd
```
then to make sure its there

```
ls *.run
```

and you should see it,,

now do it all again including the chmod

---

### Post by kayfes on 2008-06-06
this is what I got

Tried running it from the desktop

Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).


Any help would be appreciated.

---

### Post by Bachstelze on 2008-06-06
You can't run it while you have a graphical interface running. You must first stop it using

```
/etc/init.d/gdm stop
```

---

### Post by kayfes on 2008-06-06
mv: missing destination file operand after `NVIDIA-Linux-x86-173.14.05-pkg1.run'
Try `mv --help' for more information.

thank you guys again

---

### Post by SteveNorman on 2008-06-06
after NVIDIA-Linux-x86-173.14.05-pkg1.run there is a space and a tild < ~ >

so in Desktop

mv NVIDIA-Linux-x86-173.14.05-pkg1.run ~

~ is your home directory,,

But try it from Desktop using Hymn's advise

If you get really stuck and have to start over here is a guide from starcannon from this post:

[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia) 

Im off to bed but your in better hands than Mine with Hymntolife

```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
```

---

### Post by kayfes on 2008-06-06
Im off too gotta work in the AM.  I think when I was wandering around blind trying what I found on google I did something I shouldn't have.  Since I just installed Ubuntu today I have no problem spending an hour or so tomorrow getting myself back to a clean slate.  Tomorrow I am just going to reinstall and then use your guys advice from this thread.  If it makes a difference I am trying to dual boot XP and Ubuntu.  Just want to make sure I can play my games lol.

Thank you guys again.

---

### Post by SteveNorman on 2008-06-06
a couple of things,
1 the command ```
sudo /etc/init.d/gdm stop
``` stops the xwindow,,which looks like a system crash. Its supposed to do that. Your screen will go black and give you a prompt.
```
sudo /etc/init.d/gdm
``` start starts it again

2 you have to be in the same directory that the file is in to run it, or do any changes to it. If it is on your desktop (thats usually where it is when you download a driver) You must type ```
cd Desktop first


```

to get in to that directory OR move the file into whatever directory you want it in.  moving a file is done with this format:

```
mv file_name newlocation
```

so to move it into home,,which is represented by a tilde ( ~ )

do
```

mv file_name ~
```

Since you tried to run the file,,you should follow that article I posted,,which removes anything left from previous attempts before re-installing. If you follow that procedure you will have to move the nvidia.run file into your home directory (the ~ ). As you run through the removal steps you will get some error messages for those steps that where unnecessary,,this is ok. When you get to the configuration procedure you will answer yes to all including the creation of a configuration file. 

Just follow the procedure step by step in order and you will be ok. It will look like your system crashed,,but its supposed to do that so it can work on the visual stuff while its not running

---

### Post by kayfes on 2008-06-07
now when i go to Apps>System tools>nvidia x server settings, as this is the nvidia anything I can find anywhere it say to run nvidia-config as root.  Will this enable the the drivers and if so how do I do that?

I should also mention that now I am running in low graphics mode after I followed everyones directions.  And when I chose to configure everything the drivers for the Nvidia didn't show anything relevant to a 9 series for the card and I couldn't choose my monitor from the list.  I have an LG L226wtq.

---

### Post by kayfes on 2008-06-07
Any help anyone can give would be great.  Im at the point where I want to put my old card in which is 7 series geforce but that would mean I wasted the money on the 9 series.  I just want to get this card working right other than that I love Ubuntu thus far.

---

### Post by kayfes on 2008-06-07
Damn I am so lost with what to do to get these drivers running.  Is there anyone out there who is running a 9 series nvidia card that can help me out?  Ill be honest I refuse to go back to XP and I am going to figure this one way or another.  The thing that made mind up when choosing to switch to Linux and eventually Ubuntu was the fact that it had some appealing options visually when running it and I want to do that.  I have yet been able to use the extra settings in visual effects.  Everything else works fine for me except those and I think that once I get my card working I can use those.

---

### Post by kayfes on 2008-06-07
How do I do this:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Any help would be greatly appreciated.

---

### Post by ardvark71 on 2008-06-07
> **kayfes said:**
> How do I do this:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Any help would be greatly appreciated.

Hi...

What version of Ubuntu and video card?

Also, can you make a copy of your xorg.conf file and post it?

Best Regards...

---

### Post by alienexplorers on 2008-06-07
enter in terminal
> sudo nvidia-config
restart

---

### Post by kayfes on 2008-06-07
steven@steven-desktop:~$ sudo nvidia-config 
sudo: nvidia-config: command not found


I have the Hardy Heron version.

I went through installation for nvidia based on a post I made before this.

I put in on a Cd 2 days ago from my school and installed yesterday with dual boot.  Want to figure out linux before I make the full switch.

---

### Post by Bachstelze on 2008-06-07
> **kayfes said:**
> now when i go to Apps>System tools>nvidia x server settings, as this is the nvidia anything I can find anywhere it say to run nvidia-config as root.  Will this enable the the drivers and if so how do I do that?

```
sudo nvidia-xconfig
```

will indeed enable the drivers, given they have been properly installed. Be careful though, if the drivers are in fact not installed properly, it will just break your graphical interface.

*EDIT : Threads merged. Please do not create more than one thread for the same issue.*

---

### Post by kayfes on 2008-06-07
And I still get his message

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

When I try to use Apps>system tools> Nvidia x server settings

---

### Post by Bachstelze on 2008-06-07
You must restart X for the changes to take effect. Close all your applications, save your work, and press Ctrl+Alt+Backspace.

If you end up with no graphical interface, do this to restore the old settings :

```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by kayfes on 2008-06-07
my resolution settings are fixed but I still can't enable the extra settings for appearance settings> visual effects.  That was my main goal with installing the drivers.  What gives here?

---

### Post by Bachstelze on 2008-06-07
Please paste the output of those commands :

```
glxinfo| grep -i direct
grep -i driver /etc/X11/xorg.conf
sudo grep -i driver /var/log/Xorg.0.log
```

---

### Post by kayfes on 2008-06-07
I have a PNY 9800 GT graphic card.  Why can't I use the extra settings for visual effects in Ubuntu?

Might seem stupid but those are what made me try this OS.

---

### Post by Bachstelze on 2008-06-07
> **kayfes said:**
> I have a PNY 9800 GT graphic card.  Why can't I use the extra settings for visual effects in Ubuntu?

We're working on it ;) Please paste the output of the commands I told you.

---

### Post by kayfes on 2008-06-07
steven@steven-desktop:~$ glxinfo| grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
steven@steven-desktop:~$ 


steven@steven-desktop:~$ grep -i driver /etc/X11/xorg.conf
	Driver		"kbd"
	Driver		"mouse"
	Driver		"nv"
steven@steven-desktop:~$ 


steven@steven-desktop:~$ sudo grep -i driver /var/log/Xorg.0.log
[sudo] password for steven: 
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
	ABI class: X.Org Video Driver, version 2.0
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	ABI class: X.Org Video Driver, version 2.0
(**) NV(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(**) NV(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(**) NV(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
(**) NV(0):  Driver mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz
(**) NV(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(**) NV(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
(**) NV(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(**) NV(0):  Driver mode "1152x864": 104.0 MHz (scaled from 0.0 MHz), 67.7 kHz, 74.8 Hz
(**) NV(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(**) NV(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(**) NV(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(**) NV(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(**) NV(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(**) NV(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(**) NV(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(**) NV(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
	ABI class: X.Org Video Driver, version 2.0
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
steven@steven-desktop:~$

---

### Post by Bachstelze on 2008-06-07
All right, you're still using the old nv driver. As I said, if the new driver is installed,

```
sudo nvidia-xconfig
```

will enable it. If it does not, then that means the driver is not installed. So, did you manage to complete the driver installation or not?

---

### Post by kayfes on 2008-06-07
Well at least it said I did.  

Code

NVIDIA-linux-x86-173.14.05-pkg1.run

which was run from the home file location where it is at.

---

### Post by Bachstelze on 2008-06-07
Good, and the installation completed successfully? Then *sudo nvidia-xconfig* is all you need. Run it, and then paste the contents of /etc/X11/xorg.conf.

---

### Post by kayfes on 2008-06-07
steven@steven-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

steven@steven-desktop:~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied
steven@steven-desktop:~$

---

### Post by Bachstelze on 2008-06-07
To view the contents of a file, you can for example use the *cat* command, like this :

```
cat /etc/X11/xorg.conf
```

However, there seems to be something wrong with your current xorg.conf, try generating a fresh one, and then apply nvidia-xconfig again :

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig
```

---

### Post by kayfes on 2008-06-07
steven@steven-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

steven@steven-desktop:~$

---

### Post by Bachstelze on 2008-06-07
It seems that debconf is failing to detect your graphics card, maybe because it's too new. Please paste the contents of the file, as I told you earlier :

```
cat /etc/X11/xorg.conf
```

---

### Post by kayfes on 2008-06-07
I actually run my own business and am going to be tied up until probably Monday.  This is my home PC so it won't interfere with my business.  Thank you again and I will check this thread tomorrow before I open up shop probably around 7 am pst. 

Thank you for your help, your help and others help is the mainrason I am going to make the switch from MSWXP to Linux.

---

### Post by SteveNorman on 2008-06-07
The post I put in from star commander is the technique for loading the latest drivers,(page 2 of this thread)

-It deletes old drivers,
-deletes failed install attempt residuals from different install possibilities 
-deletes and creates a new xorg file.

I recommend doing those steps as it gives you a fresh start before loading the new driver. I just did it for my 8800 series,,which uses the same driver. My new card was not recognized until I did star commanders instructions,,note for note.

---

### Post by Xerp on 2008-06-07
Envy does a great job at driver installation for me!

---

### Post by SteveNorman on 2008-06-07
the problem is the newness of the card he's using,,you have to load it manually,,or use an older driver which defeats the purpose. Envy etc wont load the brand new drivers yet.

when you get it installed right you should start having game induced seizures in no time!

---

### Post by kayfes on 2008-06-07
had some free time tonight

this is what I got

steven@steven-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon May 19 00:33:37 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
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

steven@steven-desktop:~$ 



Also I went ahead and reinstalled Ubuntu and now that is the only OS on my comp.

I then went ahead and did what steve said and followed stars directions.  However in stars guide in direction 6 this is what i get

steven@steven-desktop:~$ sudo cp /etc/x11/xorg.conf ./xorg.conf.backup
cp: cannot stat `/etc/x11/xorg.conf': No such file or directory

---

### Post by Bachstelze on 2008-06-07
With that xorg.conf file, you should be using the nvidia driver after you restart X.

> **kayfes said:**
> 
steven@steven-desktop:~$ sudo cp /etc/x11/xorg.conf ./xorg.conf.backup
cp: cannot stat `/etc/x11/xorg.conf': No such file or directory

It's X11, not x11.

---

### Post by kayfes on 2008-06-07
ok so i go to apps>system tools> x server and this is what it says when I open it

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I run sudo nvidia-xconfig

steven@steven-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

steven@steven-desktop:~$ 


Then when I open up the nvidia x server i still get same message from above.

---

### Post by Neo0351 on 2008-06-07
Here's how i got my 9600gt just use the 173.14.05.  Make sure you download the drivers for you architecture.
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by Bachstelze on 2008-06-07
> **HymnToLife said:**
> With that xorg.conf file, you should be using the nvidia driver **after you restart X**.

:-\"

---

### Post by SteveNorman on 2008-06-07
do 
```
ctrl-alt-backspace
```

log back in

then in terminal

```
nvidia-settings


```

then X Server Settings,what does it say?

---

### Post by myland on 2008-06-07
I'm really total lost In this Resoulation. The 8.04 is just giving me what I want to do. The screen is 3/4 bigger that it is suppose to. I tried everything. 
What about resinalling the 7.04 would that be better than what I have now. It work fine for awhile then it 3/4 of the screen if you go to the resulation area it is 640X320@50 or something like that with options to change it but downwared like 320X???.
Thanks, 
Tom

---

### Post by kayfes on 2008-06-07
Have no idea why this wont work.  Is anyone else using a 9 series nvidia card and having similar issues?

---

### Post by kayfes on 2008-06-07
Got it working finally just did what steve said thank you guys everyone who helped.  Nows it time to get some games running!  Anyone have any suggestions on to play games on Ubuntu?

Also I am not sure how to mark the thread as solved so any help there would be cool.

---

### Post by SteveNorman on 2008-06-07
Glad it worked! Thread tools >>mark as solved,,the little medal on the bottom right is for thanking the poster,,and the report is for telling on them

---

### Post by kayfes on 2008-06-07
Got Compiz fusion running now with the 3d cube desktop and its great.  I am going to be asking myself forever why I didn't get rid of XP a long time ago!  Thank you guys again for your help.

---

### Post by kayfes on 2008-06-08
If you update Ubuntu you will have to go through stars run through provided by Steve after you install.  At least thats what I had to do.  It only takes a couple of minutes no biggy, I kind of freaked when I restarted after install and was back to low quality screen settings.  I actually just ran through steps 8-12.  I don't know if that was the right way to do it but it worked for me.

---

### Post by Glugglug on 2008-06-08
Thanks I've got it running I think the ctrl+alt+f1 was a vital part in all that .

---

### Post by Sonic Reducer on 2008-06-08
1) ```
sudo apt-get install envy-ng
```

2) then go to **Applications** > **System Tools** > **EnvyNG**

3) choose either nVidia or ATI on the left column and then either manual selection or automatic detection of hardware.

4) hit ok.

5) wipe hands on pants

---

### Post by Old Technology on 2008-10-19
okay, I installed envyNG and ran it. With the driver enabled, my laptop's integrated screen doesn't work.

help, please?:confused:

---

### Post by regtheo on 2008-12-11
I was trying for two days to understand some things and install my Nvidia 8600 GT. I made it thanks to these posts.

I thank you so much!

---

