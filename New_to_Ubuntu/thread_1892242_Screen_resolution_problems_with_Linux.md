---
title: "Screen resolution problems with Linux"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by nail33 on 2011-12-07
I recently upgraded my desktop computer with an Asus P8z68-VPro motherboard and an Intel I5-2500K (Sandy Bridge) CPU. I also upgraded to Win7 (64bit). I did this to improve my photo editing speed. I didn't include a graphics card this time because the graphics are built into the CPU. Everything works great using Win7. Eventually I would like to ween myself off of Windozzzzzzz and go 100% Linux. I use Ubuntu (64bit) for everything but photo editing. I know there will be software issues using Linux for photo editing with my windows based software (Canon DPP, PS Elements, etc.), but I have run into a screen resolution problem that needs to be addressed first. When I use Win7, I can choose from 14 different resolutions ranging from 1024x768 to 1920x1080 of which I prefer 1600x900. I'm using a Vizio 22” (1080p) TV/Monitor (16x9 widescreen) for my monitor, which is good enough for my needs. When I'm running Ubuntu (latest version), I only have a choice of three resolutions. They are 800x600, 1024x768, and 1280x720 of which I prefer 1024x768. When I used my old set up, I had a mid-level Nvidia graphics card and was able to use just as many resolutions settings with Linux as with Window$$$$. I've tried different Linux distributions, but it still didn't help. Is the problem with Linux and the Sandy Bridge graphics? Are there proprietary Intel drivers that need to be installed into Ubuntu to get it to work? Have any of you using Linux run into the same problems? Is there a Linux distribution that takes advantage of the I5 graphic capabilities? I'm not a Linux geek (no offense intended, actually I'm humbled), but I'm capable of copying/pasting commands into the terminal. If you could steer me to a site where this problem could be resolved, it would be much appreciated. Basically, I would like to get a resolution of 1600x900 on my monitor while running Ubuntu (or some other distribution). I know I could use my old graphics card, but I would like to take advantage of the built in I5 graphics. Thanks in advance for you help.

---

### Post by gennatolls on 2011-12-07
I don't think the sandy bridge graphics have very good support at the moment. I read phoronix.com almost every day and there's always articles about the sandy bridge graphics for linux, I would suggest searching around that site to see what you can find. Eventually they will come, but for now sandy bridge is still bleeding edge. Have you checked (assuming your in unity on ubuntu 11.10) System Settings --> Additional Drivers? I have a i7-2600k and went with the P67 chipset to avoid this problem and got a Nvidia card. I would use your old graphics card (Nvidia has very good support btw) until you fix this, or the graphics drivers are available. Best of luck.

---

### Post by Mr. Shannon on 2011-12-07
You could try the solution in the link below for adding undetected resolutions.  Also, if by chance you are not using the latest Ubuntu version (11.10) then you could try updating to 11.10 in order to get Mesa 7.11 which works better with the Sandy Bridge GPU (quoting phoronix.com).

[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions")

---

### Post by warfacegod on 2011-12-07
Keep in mind that you are using Intel graphics which suck in Windows or Linux. Also, using the integrated Intel graphics will reduce the efficiency of your cpu.

---

### Post by nail33 on 2011-12-07
@ gennatolls:

You're probably right.........I'll just have to wait for Linux to catch up.

@ Mr. Shannon:

I'm currently running Ubuntu 11.10 and Mesa 7.11 is already installed. I ran xrandr and this is what I get:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192

VGA1 disconnected (normal left inverted right x axis y axis)

HDMI1 disconnected (normal left inverted right x axis y axis)

DP1 disconnected (normal left inverted right x axis y axis)

HDMI2 disconnected (normal left inverted right x axis y axis)

HDMI3 connected 1024x768+0+0 (normal left inverted right x axis y axis) 480mm x 270mm

   1280x720       60.0 +   50.0  

   1024x768       75.1     70.1     60.0* 

   800x600        72.2     75.0     60.3     56.2  

   640x480        72.8     75.0     60.0  

   720x400        70.1  

DP2 disconnected (normal left inverted right x axis y axis)

DP3 disconnected (normal left inverted right x axis y axis)


@ warfacegod:

For photo editing, Intel graphics are more than enough and so far have not stressed my CPU very much. This was supposed to be one of Sandy Bridge's selling points and it works well with Windows for what I'm doing. I'll put my graphics card back in if necessary, but I'd like to avoid that.

@ everyone:

Thank you all for your input.

---

### Post by Mr. Shannon on 2011-12-08
It looks like you are missing the mode needed so try typing the lines below into the terminal.  NOTE: All of this except the way of making the resolution change persistent I just tested on a virtual machine (with a much lower resolution).

```
cvt 1600 900
```
NOTE: if the refresh rate is not 60 Hz then add that value to the end of the line above.

Now copy the line titled *Modeline* in the output from the above command into the xrandr command as follows to make the new display mode.
```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```
NOTE: the modeline in the command above was computed with cvt for the default of 60 Hz at a 1600x900 resolution.  I do not know enough about displays to know whether running cvt on your machine would produce a different result or not, maybe someone else knows.

Run the command below to assing the new display mode to the proper output device.
```
xrandr --addmode HDMI3 1600x900_60.00
```
NOTE: if you used a different refresh rate the mode name (the last element in the command above) may be different, however this will just be the part in quotes from the modline in the output from the cvt command.

Finally, change the scree resolution with the command:
```
xrandr --output HDMI3 --mode 1600x900_60.00
```
NOTE: again the mode name may be different.

If all that works then add the last three commands befor the line ```
/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
```
in the ```
/etc/gdm/Init/Default
``` file to set the resolution persistently.  NOTE: you will need sudo privileges to edit that file.

Hope this helps.

NOTE: All of this was taken from [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by nail33 on 2011-12-08
@ Mr Shannon:

Thank you, Thank you, Thank you. You are a genius!!! It worked great. The only part I haven't done yet is to set the resolution permanently. I'm unsure of how to complete the final task as listed below:

If all that works then add the last three commands before the line 
Code:
/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
in the 
Code:
/etc/gdm/Init
file to set the resolution persistently. NOTE: you will need sudo privileges to edit that file.

How do I find the file /etc/gdm/Init? I pasted it in the terminal and of course that didn't work. I edited a line once long ago, but I forgot how to get into an editing mode. Also, once I get into that file, is it hard to find the line above? I'm assuming when you say “persistently” that means permanently.

PS I know just enough about Linux to get myself into trouble.............I'm a newbie.

Thanks again!!!!

---

### Post by nail33 on 2011-12-09
@ Mr. Shannon

I used this command:

 "$gksudo gedit /etc/gdm/Init/Default"

to edit and got this reply:

** (gedit:2528): WARNING **: Could not load theme icon gtk-home: Icon 'gtk-home' not present in theme

Am I on the right tract? Where do I go from here?

Thanks

---

### Post by Mr. Shannon on 2011-12-09
Sorry for taking so long to get back with you (finals week is next week).

Which desktop environment are you using (gnome, unity, KDE...).  I ask this because that error should not have come up if you where running gnome or unity.  The procedure to set persistent resolution is different depending on your desktop environment as well.

**EDIT:** You should not be getting that message at all really, but it is a known bug.

---

### Post by warfacegod on 2011-12-09
> **nail33 said:**
> 

@ warfacegod:

 For photo editing, Intel graphics are more than enough and so far have not stressed my CPU very much. This was supposed to be one of Sandy Bridge's selling points and it works well with Windows for what I'm doing. I'll put my graphics card back in if necessary, but I'd like to avoid that.

I have a Sandybridge i7 x4 with Hyperthreading in an ASUS g73SW and it totally kicks butt. I've done some benchmarking and it generally kicks the hell out of the new AMD x6 Bulldozer cpu's. I think you may want to, at least, try a separate gpu.

---

### Post by nail33 on 2011-12-09
@ Mr. Shannon:

Thanks for getting back to me. You're really sharp.............I should have told you that I changed from Ubuntu 11.10 (64 bit) to Kubuntu 11.10 (64 bit) while trying to solve this problem. My apologies. I didn't realize that it would make so much difference in regards to resolution settings, as they are both Debian based (I think). I usually try to install the latest versions of Ubuntu hoping that they will be better than the last. I've tried other distributions, but I always come back to Ubuntu because it seems to always work with the least amount of tweaking. I can't seem to get used to Unity, and the Gnome that's available under Ubuntu 11.10 doesn't seem as good as under Ubuntu 10.04 LTS that I have installed on my laptop. I'm not that crazy about KDE either, but it's better than Unity. I'm going to remove Kubuntu 11.10 (64 bit) from the desktop and install Ubuntu 10.04 LTS (32 bit) / Gnome and follow your instructions and see if I can get the resolution that I'm looking for. Sorry for being so wishy-washy. I hope you will continue to follow this thread. I will try to keep it updated. Thanks for your patience. Good luck on your finals!!!

@ warfacegod:

If I can't solve this problem (which is probably me), I'll put a graphics card in. Thanks.

---

### Post by Mr. Shannon on 2011-12-10
**EDIT:** I would not downgrade to 10.04 LTS as you are probably going to have a hard time getting that to work correctly with the Sandy Bridge graphics without Mesa 7.11.  If you wan't gnome then you should try gnome shell (available as an add on to Ubuntu 11.10), though it is more like Unity than the old gnome.  If you wan't something that will act very similar to the classic gnome (gnome 2) then you could try Linux Mint.  Linux Mint is a Ubuntu derivative that uses gnome shell but employs some custom packages to make it behave more like gnome 2.

I can give you the instructions for setting the resolution on KDE (Kubuntu).  Its just a different file and a different editor, but all else is the same.  Below is the instructions for setting the resolution  (persistently when using KDE).

Note: You should always make a backup of a system file before editing it.

Just open the right file (I am assuming it should be called Default) under the directory
```
/etc/kde4/kdm/Xsetup
```
for editing with the command
```
kdesu kate path/to/file
```
This will ask you for a password and then let you edit the file.

Now add
```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr --addmode HDMI3 1600x900_60.00
xrandr --output HDMI3 --mode 1600x900_60.00

```
near the front of the file and then save and exit the text editor.  Sadly I don't know exactly what line it needs to be before as I don't have KDE.
NOTE: If you used different values with your xrandr commands when testing earlier then you should use those values and not the ones that I included in the commands above.

Finally reboot the computer and the resolution should automaticaly be set to 1600x900.

If something went wrong then replace your modified file with the backup you made and reboot to return to the current settings.

About your other question, persistently in this case means that it should stay at that resolution after a reboot unless you change the file again.

If you wan't to go back to gnome, then I can give you those instructions as well.

---

### Post by nail33 on 2011-12-10
@ Mr. Shannon:

I tried using Ubuntu 10.04 LTS 64 bit and 32 bit, but neither would connect to the Internet.......very strange. I could always count on Ubuntu to automatically connect. I'm done with trying to fix that. I reinstalled Ubuntu 11.10 (64 bit) / Unity and again followed your instructions. I could force the 1600 x 900 res using xrandr, but again had problems trying to make it permanent. When I used the $gksudo gedit /etc/gdm/Init/Default command I got this message:

(gksudo:2761): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:2761): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:2761): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:2761): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gedit:2763): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VIQE6V': No such file or directory 

(gedit:2763): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 


When I left off the /Default part and just used the $gksudo gedit /etc/gdm/Init command, I got this reply:

(gksudo:2882): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:2882): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:2882): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 

(gksudo:2882): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 



Again, this was using the Unity platform. Should I install Gnome and try again?

I tried Mint 11.10 (64bit) awhile back but had to make too many tweaks so I removed it.

Thanks again for your patience.

You might find this link, of interest concerning changing resolutions (especially the replies of it not working):

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

### Post by Mr. Shannon on 2011-12-11
Use this command to fix the errors:
```
sudo apt-get install gtk2-engines-pixbuf
```

Apparently Canonical changed the session manager for 11.10 so you should use the command:
```
gksudo gedit /usr/sbin/lightdm-session
```
to edit the file.  As it is a deferent file now.

And then add the xrandr lines to that file right before the line ```
# Load resources
``` and then save and close the file.  Now reboot and everything should work now.
This is from [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")

If this still does not work I know of a way to workaround the issue as long as you don't mind that the resolution will not change until several seconds after you have logged in.

Sorry I keep telling you the wrong steps.

---

### Post by nail33 on 2011-12-11
@ Mr. Shannon:

You the man!!! It works perfectly. I thought maybe when I rebooted it would always go to 1600 x 900 with no way to change to another resolution without editing a file again......which would have been fine. But, to my surprise, it was listed right in with the other display modes which I can still choose if I wish..........that's even better. You ought to consider making your solution a “sticky”, as I'm sure others have come across this problem. I can't thank you enough for solving the problem and taking the time out to help me. People like you are the reason why these forums are so helpful to those of us that want to join the open source community. I will use this as a link, for others that may have the same problem. Thanks again!!!

PS Will this work if I choose to boot into a Gnome session with Ubuntu 11.10?

---

### Post by Mr. Shannon on 2011-12-12
> 
PS Will this work if I choose to boot into a Gnome session with Ubuntu 11.10?

As long as the session manager does not change (session managers and desktop environments are not the same) then the resolution change should continue to work.  So choosing the gnome shell desktop should not effect the resolution settings set in /usr/sbin/lightdm-session as long as installing gnome shell does not change the session manager.  If you change session managers then you just need to find that managers startup script and add those 3 xrandr lines to the file.

---

