---
title: "[SOLVED] Can I run an external projector with ubuntu"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-26
What do I need to do to get my casio external projector to work on my toshiba A100 laptop?

I have it connected but the laptop does not seem to be sending a signal to the projector. 

The Fn+f5 key that I used on windows Vista to toggle the display does nothing. 

Please help cos I have a public presentation to do tomorrow night!

---

### Post by sam_delta on 2008-05-26
what video card/drivers do you have?

you could try ```
gksudo displayconfig-gtk
```

sam

---

### Post by tropdoug on 2008-05-26
Hi sam

its a Nvidia G force series 7, the correct restricted driver is installed

---

### Post by sam_delta on 2008-05-26
try installing nvidia-settings, it might help you configure.

you can install it from the synaptic package manager under system>administration>synaptic or by simply typing the following command in the terminal (aplications>accessories>terminal)
```
sudo aptitude install nvidia-settings
```

sam

---

### Post by iansane on 2008-05-26
right. it should be like using dual monitors.

---

### Post by Bill magee on 2008-05-26
My Hardy installation works on my classroom projectors. You may have to plug in the projector and restart X with ctr-alt-backspace.

---

### Post by tropdoug on 2008-05-26
Phewww that was scarey, I installed the nvidia-settings but in the process it removed nvidia-glx-new which is definately required by my card, cos I lost the resolution settings, and then on reboot it started in low graphics. I had to play with vartious settings to get it to return to what it should be, and that also meant removing the nvidia-settings package. 

So back to square one. I will try the restart suggestion from Bill magee in the meantime and see how I go with that. 

:-)

---

### Post by tropdoug on 2008-05-26
No changes there either. I wonder if its a problem with the laptop and not the system?

---

### Post by sam_delta on 2008-05-26
have you tryed ```
gksudo displayconfig-gtk
```

EDIT, you can also try this command
```
sudo xrandr --output VGA --auto
```
sam

---

### Post by tropdoug on 2008-05-26
Sorry sam, 

yes I have, but if I select the second screen option the dialog will not close, so it obviously cannot find the plug n play that I am telling it is there. I guess that would be because its not actually a monitor, but a projector maybe?

the display on the wall from the projector simply says No RGB signal detected?

EDIT

this is the output from xrandr

```
im@laptop:~$ sudo xrandr --output VGA --auto
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

```

Its not the laptop either, cos if I restart the puter, but leave the projector running I can watch the boot sequence on the wall, up to the point of the Nvidia graphic, so maybe it is something with the card. frustrating stuff.

---

### Post by sam_delta on 2008-05-26
give me a second, im doing some research

sam

---

### Post by sam_delta on 2008-05-26
what happens if you type ```
sudo nvidia-settings
``` in the terminal?

or navigate through system > Administration > Nvidia X Server Settings

after a little research, some people suggest that nvidia-settings is installed within nvidia-glx-new and thats why you cant have both, im not sure if thats true, thats why im asking you to check.

sam

---

### Post by sam_delta on 2008-05-26
also, as i understand, your using restricted drivers, from system>administration>hardware drivers , they show as enabled and in use rite?

sam

---

### Post by tropdoug on 2008-05-26
The return from sudo nvidia-settings is attached ( dialog) and yes I do have the drivers enabled. 

I don't know much about the way a system goes about booting, but logically if I can see the two displays during the initial boot sequence up until the login splash screen shows, and also on shutdown then the laptop graphics are able to display this. so it should be something within the gnome or OS itself that prevents the second screen being displayed, and not the card or drivers. (as I said I am just trying to think logically) 

Sorry to have been so long getting back to you, I lost my network settings for a while, during the resetting of my screen I cannot understand how or why though. anyway I am back now, for about another hour max. 

Thanks for all your help so far.

---

### Post by sam_delta on 2008-05-26
alright, about what you were saying, as far as i know, when your booting, your system uses generic vesa drivers for your card, (like if you are in safe graphics), so thats why you can see the double screen while booting (you can also do dual screen without any problems using safe graphics mode, but your resolution will be poor) , as soon as x server starts (log in windown), your computer uses the nvidia drivers you have installed.

well, before we go into a terminal and try what it says, we make a backup of the xorg file by typing
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

if something goes wrong, and you boot into safe graphics, just type
```
 sudo mv etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
and restart your pc, settings should return to normal.

for some reason, your computer seems not to be using nvidia driver.
well, do what it says go into a terminal and type ```
sudo nvidia-xconfig
```
restart x server by typing control+alt+backspace (copy the command of above, just in case it does not work)
if this dosnt work, we can try installing the drivers using the program envy-ng 

sam

---

### Post by tropdoug on 2008-05-27
Ok sam 

your really doing a great job here, thanks.

Ok I ran the nvidia-xconfig command and then had to run another one, something to do with dpkg-xconfig .... I will be more precise in my next post I have to practise for tonight, (I borrowed a arrrrgh windblows laptop) 

anyway after doing what it said, I was able to run the nvidia-settings tools and you were right I wasn't actually running the nvidia driver. It found the projector and I was able to get two displays, everything looked good. I saved the new xconf file and then closed it all down. I then restarted to check it all, and when I came to open a terminal it is a blank white square, so something is not right. 

As it stands right now, I can only get full use of the desktop and apps if I log in as a failsafe gnome session. I have tried the process a number of times and still getting something wrong. 

I have to fly right now, but if you have any thoughts please post them for me. If I can crack this one, I think there a few people that need to know the answer to it.

---

### Post by sam_delta on 2008-05-28
trop, im sorry for the trouble, i didnt knew you where going to get into that much trouble.

can you explain a little bit more to detail on whats happening? example, why you cant use your desktop as a normal session? what happens when you log as a normal session?

im sure there is a solution to this
sam

---

### Post by tropdoug on 2008-05-28
LOL, don't worry about me Sam, I look on it as learning new things, its just nice to have people willing to help. 

When I log in normally the graphics are patchy, like bits of the desktop disappear or exist as a black box, and when I try to use a terminal it pops up as a blank white square, which wont do anything. 

I am still trying to work out how it is happening. One other thing that seems to be occurring as well, is that the xsession asks me to choose between the Gnome selected keyboard which is set somewhere as a 105 key no options keyboard, as opposed to the one it was expecting being a 101 key us no options keyboard. If I select the Gnome choice I get the same thing next start. I have edited the xorg.conf file to read 101 key, and am about to try it again. I am not sure where else that setting might be stored (in Gnome maybe) 

Anyway, I did get two displays, so there is a solution it will happen. I will feed you back more details soon.

Doug

---

### Post by sam_delta on 2008-05-28
so its a video driver problem?, or probably xorg.config file problem

remember that we made a backup of the old xorg? you can restore it at any time by typing 
```
sudo cp etc/X11/xorg.conf.bak etc/X11/xorg.conf.bak2
sudo mv etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
then restart

sam

---

### Post by tropdoug on 2008-05-28
ummm I blew it! I allowed one of the config commands to overwrite the original backup, and lost it. Dumb Dumb Dumb! 

so I decided to try to go back by uninstalling the nvidia drivers, rebooting and then reinstalling them via synaptic. In the process I lost my wireless network and am currently thinking I may have to do a complete reinstall. 

I will get to the bottom of this though, no OS is going to beat me. lol more later.

---

### Post by sam_delta on 2008-05-28
does your video is now working as it should??? we can fix wireless, what network card do you have??? also, i heard that completely removing the xorg file would attempt to create a new one, which will be equivalent to a new install. you can try that before doing a fresh install

man, im so sorry i got you into all this trouble :/ 

a recomendation if you do a fresh install. if you can make a separate /home partition, that would be awesome, as if in the future, you want to do a fresh install you just re-install the /filesystem and you wont loose your settings/data on your home folder. 

sam

---

### Post by tropdoug on 2008-05-28
seriously sam, you haven't got me in this trouble, it's all a learning curve, I once spent 15hrs doing and redoing a formula in MS acces cos I knew there was a way to get something done, and I wasn't about to let a computer beat me. so truly no more sorry's ok :-)

so lets see where am i now. Well after stuffing the nvidia part, I decided to give it a last go to install the correct ones, and used Envy. that program worked like a charm, (apparently) but yet when I do nvidia-settings again it still tells me the drivers are not installed. The funny thing is, the rotating cube in compiz works fine and that needs the accelerated graphics supplied by the nvidia driver. so its really weird. I wonder if there is another tool to really tell me whether it is running right. 

For the projector I really need that GUI for the driver settings cos it was only then that I was able to briefly get two cloned displays. 

when we solve this, it will make a great explanation lol

---

### Post by sam_delta on 2008-05-29
alright tropdoug, i like how you think, great philosophy

as for the settings, i found 2 usefull links

this link contains mostly things that we already know, but reading it carefully and reading the comments from the people might lead to goos information
[http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup](http://my.opera.com/sjosul/blog/ubuntu-8-04-dual-monitor-setup)

this second link contains 2 methods of doing dual screens, the "new one" which is the one using nvidia-settings and the "old one" which is the one that you manually edit the xorg file.
[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

if you have any questions regarding any method or command, please, feel free to ask

ill keep reading those procedures and comments and see what i can get
sam



EDIT, [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)
this is another link i found on howto manually edit the xorg with a good explanation on what each line represent (note that it is for an older ubuntu version, but might work in hardy)

sam

---

### Post by tropdoug on 2008-05-29
ok sam

I have been reading those posts. The new method, the gksudo nvidia-settings one just brings me up with[COLOR=Blue] "driver not installed run sudo nvidia-xconfig[/COLOR] which results in my white terminal box that does nothing on resetting the xserver. 

but when I studied the manual method, one thing I noticed was this 

[COLOR=Red][I][B][FONT=Verdana]2. Next navigate to your "Device" Section, which should appear similar to the example shown below, the identifier and BusID WILL be different:

[/FONT][/B][/I][COLOR=black]```
[FONT=Verdana]Section "Device"
           Identifier          "nvidia 7900"
           Driver               "nvidia"
           [COLOR=Blue]BusID                "PCI; 1;5;0"[/COLOR]
EndSection[/FONT]
```[/COLOR][/COLOR]when I checked my xorg.conf this is what I have already 

```
 Section "Device"
    Identifier    "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver        "nvidia"
EndSection 
```notice that there is no BusID there. 

I checked the hardware manager and attached are two screen shots of the driver where it appears the string for the BusID is simply "PCI" would you agree?

if you do then I might add that, as the BusID, into the xorg.conf and see how that goes. Does that sound logical?

Ok I will leave it there for tonight I have to go out on business. I will check back tomorrow. 

thanks once again sam.
Thanks Doug

---

### Post by sam_delta on 2008-05-29
the bus id is usually used to target a specific device into a hardware, it is mostly used when you have more than one video card, i duno if not having that line would cause problems but adding that line would not hurt

to find out your video card busid 

go into a terminal and type ```
lspci
``` youll get all your hardware, search for the line that lists your video card and copy the sequence of numbers at the beggining of the line, they should look something like 01:00.0 then
> To translate the numeric sequence given by lspci into the BusID entry you will need to change the period to a colon and you can leave out any leading zeros.
(quote from the link below )

example, if lspci returns 02:0a.1 the busid will be BusID "PCI:2:a:1"

take a look at the second post in the following link 
[http://ubuntuforums.org/showthread.php?t=607001](http://ubuntuforums.org/showthread.php?t=607001)

it also list another way of finding your card busid but it requires you to shut x server down, which i think its harder

note: id you recommend to make a backup of the xorg.conf file each time you attempt to edit it
sam

---

### Post by tropdoug on 2008-05-30
Well what a day, a million reboots, and a lot of frustration, but finally it works!
well almost.

Ok, turns out that using 
```
 sudo aptitude install nvidia-settings[FONT=monospace]
```

had the effect of uninstalling the nvidia glx new package that this version of the nvidia driver needs. Sooooo I went the other way, and found out that using the restricted driver manager gui, resulted in the correct glx package being reinstalled, and then suddenly nvidia-settings actually worked. That is not a lot of help to others having this problem, and it certainly seems that the nvidia driver causes the most issues when trying to get dual monitors working, but persistence seems to have paid off.

Now finally I was able to run the settings utility, found the crt projector and set it up, and bingo I have two displays. BUT ..... always a but, once I saved the configuration and got out of the utility, all seemed ok. I was able to do work on a oo presentation. Then I shutdown and rebooted and that was the start of another problem, see the screen shots attahced. My desktop is too small. I tried various different resolution sizes, and could not fix it. 

So I thought I might see if a setting in Compiz had perhaps been altered. Odd thing, the menu item for "advanced appearances" has disappeared. Compiz is definitely still installed, because I have the rotating cube, transparency and gears etc working normally, but no way to check the settings. 

So there is still something weird going on. the screen resolution is still set to 1280x800 but notice that the first screen appears to be the crt projector? which is not even on right now. 

the desktop screenshot shows that the right side and bottom of the screen are not correct. and another one shows that even thought the settings utility does come up, the terminal command returns a host of errors. :confused::confused::confused:

I am somewhat confused.

any ideas sam? or anyone else. 
[/FONT]

---

### Post by sam_delta on 2008-05-30
for the compiz menu, go into synaptic and make sure the package called "compizconfig-settings-manager" is installed, you can also right click on the "system" menu on the top left part of your panel and click on "edit menus" and check if for some reason, the advnced effects is unchecked under system>preferences

for the settings manager, i guess its a config file being wrong, located at /home/kim/.nvidia-settings-rc  , try to reinstall nvidia-settings but make sure you delete the settings file before reinstalling, to delete the file ```
rm /home/kim/.nvidia-settings-rc
``` you dont need sudo in this command since you are in your home directory.

if nvidia-settings start working again, i guess youll get your desktop fixed.
you can also restart x server by typing Control+alt+backspace

also, try restarting the panels, and see if they take the screen's shape. to restart the panels just type ```
killall gnome-panel
``` panels will disapear and then theyll come back in few seconds

ill keep researching though, ill get back if i get something
sam

---

### Post by tropdoug on 2008-05-30
well sam I have reached a workable solution. Deleting the .nvidia-settings-rc file was the answer, when I restarted nvidia-settings after that it went much better. 

I have had to set the resolution of the laptop to 1280x768 the laptop screen sits correctly and the beamer works as well. I cant figure out why this is occuring however I will live with it. see the config below. 

Sam thank you very much for bearing with me during these last four days. It has been a journey,but I would have given up long before this without your support. Thanks mate it's appreciated, you are a fine example of why Linux will be the OS of choice very soon. 

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

(**I deleted the bits we are not interested in)**

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CAS XJ-S30/S35"
    HorizSync       30.0 - 65.0
    VertRefresh     55.0 - 86.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7300"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1280x800"
# Removed Option "metamodes" "CRT: 1280x800 +0+0, DFP: 1280x800 +0+0"
# Removed Option "metamodes" "CRT: 1024x768 +0+0, DFP: 1280x800_60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768 +0+0, DFP: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by sam_delta on 2008-05-30
thanks Doug, i also learned alot myself douring this last days, and after failing several times theres always light at the end of the tunnel isnt it??? :p
never give up, theres always a way around.

enjoy ubuntu :)
sam

---

