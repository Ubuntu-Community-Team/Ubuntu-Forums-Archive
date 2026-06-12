---
title: "Window Size/ Hidden Buttons"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by alexiszeigler on 2008-09-23
I have a Dell Inspiron 2500, 700 MHZ 
Recently installed Ubuntu 8.04 Hardy Heron. 
Had some trouble on install with buttons falling beyond the lower edge of the screen. Worked through that, but now I am having the same problem with some programs. In Thunderbird, for instance, to add a new address, the "ok" button is way below the bottom of the screen. It will not let me resize the window to get to the lost button. 
If I go to system>>preferences>>screen resolution 
the only options are 800X600 and 640X480
I found an answer here
[http://ubuntuforums.org/showthread.php?t=634633](http://ubuntuforums.org/showthread.php?t=634633)
that suggests I need to also adjust 
System >> Admin >> Screens & Graphics
Except there is no such menu on my system. 
I have System >> Admin >> but no Screens & Graphics
I do no know how to figure out what kind of graphics card I have....
????
thanks for any help anyone could offer
alexis

---

### Post by Shazaam on 2008-09-23
It is hidden by default. To add it to your menu list go to System>Preferences>Main Menu, then go to Applications>Other and check off "Screens and Graphics"

---

### Post by jemate18 on 2008-09-23
> **alexiszeigler said:**
> I have a Dell Inspiron 2500, 700 MHZ 
Recently installed Ubuntu 8.04 Hardy Heron. 
Had some trouble on install with buttons falling beyond the lower edge of the screen. Worked through that, but now I am having the same problem with some programs. In Thunderbird, for instance, to add a new address, the "ok" button is way below the bottom of the screen. It will not let me resize the window to get to the lost button. 
If I go to system>>preferences>>screen resolution 
the only options are 800X600 and 640X480
I found an answer here
[http://ubuntuforums.org/showthread.php?t=634633](http://ubuntuforums.org/showthread.php?t=634633)
that suggests I need to also adjust 
System >> Admin >> Screens & Graphics
Except there is no such menu on my system. 
I have System >> Admin >> but no Screens & Graphics
I do no know how to figure out what kind of graphics card I have....
????
thanks for any help anyone could offer
alexis


In my computer running with HARDy HERON,

I change my screen resolution by going to

System -> Preferences -> Screen Resolution

That should be included in your menu

As you have said, the only options you have is 800x 600 and....

You might want to edit your xorg.conf located at /etc/X11/xorg.conf

---

### Post by 73ckn797 on 2008-09-23
Go to Accessories/Terminal and type the following:

sudo lshw -C display

You should see what graphics device you have. It will ask for your password. Post the results. Cannot say I will have the fix but that info will help others to get you going if "jemate18's" info does not remedy the issue.

---

### Post by alexiszeigler on 2008-09-23
Well, I went to 
system>>preferences>>main menu>>applications>>other
and checked off "screens and graphics"
then I close the window (there is no "save" button)
and go back to system>>administration
and there is no "screens and graphics" 

rebooted, still not there

sudo lshw -C display
returns the following data

*-display               
       description: VGA compatible controller
       product: 82815 Chipset Graphics Controller (CGC)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 11
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: driver=i810_smbus latency=0 module=i2c_i810

any assistance gratefully appreciated....
alexis

---

### Post by Shazaam on 2008-09-23
You will find it here....
```
Applications>Other>Screens and Graphics
```
Found this....
```
Resolution: To enable the correct display resolution in Ubuntu, you have several options. First of all, there is the fairly useless tool in System > Preferences, the soon to be dead displayconfig-gtk tool, and finally, RandR - the newest method. There will be a graphical frontent (GUI) for RandR soon (keep an eye out for it in System > Administration), but for now you will need to use the command line. Let's say you wanted to change your resolution to 1280x800, you would need to execute the following command:

sudo xrandr -s 1280x800

If that fails, bring up a list of "supported" resolutions with this command:

sudo xrandr -q

Use the first command again and set the highest resolution that RandR claims is supported. Once that is set, try setting the resolution you know is correct, as it may now accept that resolution.

If you're still having issues, press Alt+F2 and type "gksudo displayconfig-gtk" (without "gtk" in Kubuntu), type your password and execute, then select the resolution you want from the list. Some of you may have to select a different screen/monitor in the list before you can successfully change the resolution. Reboot/logout if necessary, then go to Launchpad and report a bug.
```
from here...[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by alexiszeigler on 2008-09-24
Thanks much for the help. 
applications>>other>>screens and graphics 
says 800 X 600 is the highest resolution allowed. 

The scripts reveal the following:

sudo xrandr -q


Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600

default connected 800x600+0+0 0mm x 0mm

   800x600        60.0*    56.0  

   640x480        60.0  


sudo xrandr -s 1024x768


Size 1024x768 not found in available modes


sudo xrandr -s 1200x800


Size 1200x800 not found in available modes


Does this mean I am stuck? Is there any other way to keep the buttons from falling off the end of the page? 

applications>>other>>screens and graphics  says 
Graphics Card (Intel 815) 
Driver (none)

Would installing a (different?) driver help?
thanks,
Alexis

---

