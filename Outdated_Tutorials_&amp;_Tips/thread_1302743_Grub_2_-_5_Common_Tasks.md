---
title: "Grub 2 - 5 Common Tasks"
date: 2009-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by drs305 on 2009-10-27
[COLOR=MAROON][B][SIZE=4][CENTER]*GRUB 2 - 5 Common Tasks*[/CENTER]
[/SIZE][/B][/COLOR]

This is a simple guide for handling some of the most common tasks a user might wish to perform. For detailed information on Grub 2, refer to the Ubuntu community documentation at [https://help.ubuntu.com/community/Grub2]("http://%22https://help.ubuntu.com/community/Grub2%22") or post comments/questions on the sister page on this forum at [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

[COLOR="DarkRed"]**Grub Customizer:**[/COLOR]
For those who would prefer a GUI app, I highly recommend Grub Customizer. It can accomplish all the tasks detailed in this guide. Here is the link to a post with installation instructions and how to use it.
[_HOWTO: Grub Customizer_]("http://ubuntuforums.org/showthread.php?t=1664134") 

[B][COLOR=Navy]
[LIST=1]
[*]Unhide/Hide the Menu
[*]Menu Default Entry
[*]Menu Resolution
[*]Timeout
[*]Add a Splash Image
[/LIST]
[/COLOR][/B]
Note: *Line to edit ([COLOR=DarkRed]XX[/COLOR])* - [COLOR=DarkRed]XX[/COLOR] is the approximate line number.


[LIST=1]
[*]**[COLOR=Navy][SIZE=3]Unhide/Hide the Menu[/SIZE][/COLOR] **
File: */etc/default/grub*
Line to edit (5):
>   *GRUB_HIDDEN_TIMEOUT=0*
Example to unhide the menu: *# GRUB_HIDDEN_TIMEOUT=0* and *DEFAULT_TIMEOUT=[COLOR=DarkRed]X[/COLOR]*   

By default, if no other operating system is found on the system, GRUB 2 will *not* display the menu. The system will boot directly into the default entry.

**To display the menu:**
[LIST]
[*]Place a comment symbol (#) at the start of the "GRUB_HIDDEN_TIMEOUT=[COLOR=DarkRed]X[/COLOR]" line.
[*]Make sure the "DEFAULT_TIMEOUT=[COLOR=DarkRed]X[/COLOR]" entry is a positive integer. [COLOR=DarkRed]X[/COLOR] is the number of seconds the menu will be displayed.
> 
**[COLOR="DarkRed"]#[/COLOR]** GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="**[COLOR="DarkRed"]10[/COLOR]**"

[/LIST]

```

gksu gedit /etc/default/grub

```Save the file, then update the menu:
```
sudo update-grub
```

**To hide the menu on boot**:
There should be no # symbol at the start of the line: *GRUB_HIDDEN_TIMEOUT=[COLOR=DarkRed]0[/COLOR]* line. "[COLOR=DarkRed]0[/COLOR]" in both entries (GRUB_TIMEOUT & GRUB_HIDDEN_TIMEOUT) above should boot the system without a timeout. A positive integer will leave a blank screen for that number of seconds, allowing the user time to press "ESC" or "SHIFT" to display the menu. The splash screen will still display during the timeout.


[*]**[COLOR=Navy][SIZE=3]Menu Default Entry[/SIZE][/COLOR] **
File: */etc/default/grub*
Line to edit (4): 
> *GRUB_DEFAULT=0*
Example: *GRUB_DEFAULT=1*   # (The second "menuentry" item).

Natty / Grub 1.99 Note:
If you want to use an entry in a submenu, the way to designate the number in the DEFAULT_GRUB line is different. Please refer to this thread about Grub 1.99 submenu's for instructions:
[http://ubuntuforums.org/showthread.php?p=10720316#post10720316]("http://ubuntuforums.org/showthread.php?p=10720316#post10720316")


There are several ways to update the default selection in GRUB 2. Below are choices for using a simple GUI app to make the change for you, a manual way via editing the GRUB 2 files. Another method, using the command "grub-set-default" does not appear to work in GRUB 2 with Ubuntu at this time.

[LIST=1]


[*] Boot Repair: Boot Repair is an excellent utility designed to fix booting problems. It can also run the boot info script, which is invaluable in providing helpers with information needed to provide targeted assistance. For purposes of the this section though, Boot Repair can easily set the default boot option under the "Advanced" > "Grub Location" options. Boot Repair is my recommendation for setting the default OS. Visit the Boot Repair site at: 
[[Boot-Repair] Graphical tool to repair the PC boot in 1 click!]("http://ubuntuforums.org/showthread.php?t=1769482")


[*] Grub Customizer: Grub Customizer is a GUI app designed for Grub 2. It is a great tool for accomplishing most of the tasks found on this page. Here is a link on how to install and use Grub Customizer:
[Grub Customizer]("http://ubuntuforums.org/showthread.php?t=1664134")


[*] StartUp-Manager: For those who prefer a GUI app to change the default selection.
If you want a simple, GUI-based app that can change the default entry, you can install and run StartUp-Manager. This app was written for Grub legacy but still works for this option in Grub 2. Click on the "SUM" link in my signature line for instructions on how to install and an explanation of the various settings you can change with StartUp-Manager.


[*]"sudo grub-set-default"
**If the /etc/default/grub "GRUB_DEFAULT=" setting is set to "saved"**, you can change the default setting at any time by running:
```

sudo grub-set-default [COLOR=Red]X[/COLOR]

```
with [COLOR=Red]X[/COLOR] being either the menuentry position (the first menuentry is 0), or with the exact menu string from the menuentry. For more details, refer to [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1302743").
Examples:  *sudo grub-set-default 3* or *sudo grub-set-default "Ubuntu, Linux 2.6.31-14-generic"*


[*] Edit the Files: Get to Know GRUB 2

If you prefer to change the GRUB 2 files manually:

You can see the current "menuentry" items listed in the */boot/grub/grub.cfg* by running this command:
```
grep "menuentry" /boot/grub/grub.cfg
```Counting starts with zero (0). The first "menuentry" item is "0", the second is "1", etc. The third visible "menuentry" would be 2. 

Determine the number you wish to make the default, and enter it in */etc/default/grub*. Make the change and save the file.
```
gksu gedit /etc/default/grub
```The user can also select "saved" as an option, which will use the last successfully booted kernel/OS as the default selection.
Examples: 
[LIST]
GRUB_DEFAULT=0
GRUB_DEFAULT="Microsoft Windows XP Home Edition"
GRUB_DEFAULT="saved"
[/LIST]
If using the exact title, use the title exactly as it appears in the menuentry for that item in /boot/grub/grub.cfg
> GRUB_DEFAULT=1

Save the file, then update the menu:
```
sudo update-grub
```
[/LIST]

 
[*]**[COLOR=Navy][SIZE=3]Menu Resolution[/SIZE][/COLOR] **
File:  */etc/default/grub*
Line to edit [noparse](18)[/noparse]:
> *# GRUB_GFXMODE=640x480*
Example: *GRUB_GFXMODE=1280x1024*

Change the value to the resolution you wish to use *for the Grub 2 menu display*. This setting effects only the Grub menu resolution. Run "update-grub" after saving the file to update the menu.

***Make sure the resolution is supported before the operating system is loaded, especially if you intend to use a non-standard resolution.***
If you are not sure of the resolutions available from your monitor *during the initial boot*: From the Grub menu, type "c" to enter the Command Line mode, then type "*vbeinfo*". This will list the resolutions available to Grub 2 during boot. Not *all* resolutions available after your system boots may be available to GRUB 2.

Add the new line.
Leave this line alone for reference: #GRUB_GFXMODE=640x480
```
gksu gedit /etc/default/grub
```Save the file, then update the menu:
```
sudo update-grub
```


[*]**[COLOR=Navy][SIZE=3]Timeout[/SIZE][/COLOR] **
File: */etc/default/grub*
Line to edit (7):
> *GRUB_TIMEOUT=10*
Example: *GRUB_TIMEOUT=3*

Change the value to the number of seconds you wish the menu to be displayed. 
```
gksu gedit /etc/default/grub
```Save the file, then update the menu:
```
sudo update-grub
```
[LIST]
[*]If you want to see the menu, make sure the "GRUB_HIDDEN_TIMEOUT" line begins with a comment (#) symbol. (# GRUB_HIDDEN_TIMEOUT=)
[/LIST]

**Command Line Bonus:**
If you want to change it very quickly and are a trusting sort, just run the following command to replace the timeout value and run update-grub. ***Change the value in [COLOR="DarkRed"]dark red[/COLOR] to the timeout value you desire.*** The command below changes the timeout to 5 seconds.
```
sudo sed "s/GRUB_TIMEOUT=[0-9]*/GRUB_TIMEOUT=**[COLOR="DarkRed"]5[/COLOR]**/g" -i /etc/default/grub && sudo update-grub
```

 
[*]**[COLOR=Navy][SIZE=3]Add a Splash Image[/SIZE][/COLOR] **
File:  */etc/grub.d/05_debian_theme*
Grub 1.97~beta (Karmic) and Grub 1.98 (Lucid and later) use different instructions to set the background image. 

Image Information:
[LIST]
[*]May be a tga, png or 8-bit jpeg image.
[*]Must be RGB. Indexed color foramtting is not allowed.
[*]It helps if the image is the same size as the resolution you are setting. 
[*]The "console" mode must be disabled in */etc/default/grub* (default setting).
[*]You can see the resolutions available to Grub 2 from the Grub menu during boot. Press "c" and at the grub prompt type *vbeinfo*
[/LIST]


**Grub 1.98 (Lucid)**
Line to edit (10):  
> *  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"*
Example: [I]  WALLPAPER="/home/drs305/my-images/really-great-background.png"
[/I]


**Grub 1.97~beta (Karmic)**
Line to edit (16):  
> *for i in {/boot/grub,/usr/share/images/desktop-base}/moreblue-orbit-grub.{png,tga} ; do*
Example: [I]for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}Moraine_Lake_17092005[SIZE=3].[/SIZE]{png,tga} ; do
[/I]
Note that the filename ends with a *period*, before the brackets for the extension.


Ubuntu's repositories provide a standard selection of Grub backgrounds. To add a standard Grub 2 splash image:
[LIST=1]
[*]Download the GRUB 2 splash image package:
```
sudo apt-get install grub2-splashimages
```
[*]Determine the image you wish to use. The *grub2-splashimages* are downloaded to */usr/share/images/grub*
[*]Open the */etc/grub.d/05_debian_theme* file for editing:
```
gksu gedit /etc/grub.d/05_debian_theme
```
[*]Edit the file as described previously, using the instructions for the version of Grub 2 you are using.
[/LIST]


Save the file, then update the menu *:
```
sudo update-grub
```
* While the file is running, if the splash image was successfully imported you will see "Found Debian image <image-name>" among the terminal outputs.

Other splash images or locations can be used. Refer to the community documentation for more information.
[/LIST]

**LINKS:**
Here is a collection of scripts which automate many Grub 2 tasks, courtesty of Herman:
[_Herman's Grub 2 Scripts_]("http://members.iinet.net/~herman546/p20.html") Useful scripts for many Grub 2 tasks.

---

### Post by sh4d0w808 on 2009-10-29
> **drs305 said:**
> 1. Download the GRUB 2 splash image package:
Code:

sudo apt-get install grub2-splashimages

2. Open this file for editing:
3. Determine the image you wish to use.


Possibly something is missing at the end of 2nd step...


Anyway: thank U again for GRUB 2 informations, now it is the time to learn GRUB 2! Congratulation!

---

### Post by drs305 on 2009-10-29
> **sh4d0w808 said:**
> Possibly something is missing at the end of 2nd step...

Yes indeed. Lost in the ether of the Internet at some point. Rather than wait to see if it ever returns, I have retyped the missing filename. Thanks.  ;-)

---

### Post by ranch hand on 2009-10-29
I have updated my link to Grub2 Basics and added this thread to my links on my Introduction that I posted in the ABT forum.

---

### Post by 600WPMPO on 2009-11-05
Very well written...!! thanks a lot..

One more point that can be added:

In the file "05_debian_themeand as 06_custom_theme", we must look at the line which reads "use_bg=false"

> **use_bg=false**
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/picture.{jpg,png,tga}

You have to set the variable "use_bg=false" to true. i.e. **use_bg=true**

Then set the path and name of your desired GRUB background image.


I hope it helps..

----------------------------

One doubt I have:

Some people say that to change screen resolution of grub2, edit /etc/grub.d/00_header, search for &#8220;set gfxmode=640x480&#8221; and change it as you like.

But, you like to edit /etc/default/grub # GRUB_GFXMODE=640x480

which one to prefer?

---

### Post by ranch hand on 2009-11-05
For me, that change seems to stop the whole process.  Just goes to the default black background.

---

### Post by desht on 2009-11-05
> **600WPMPO said:**
> 
You have to set the variable "use_bg=false" to true. i.e. **use_bg=true**
Then set the path and name of your desired GRUB background image.


Don't do that; if you look at the script, you'll see that it sets "use_bg" to true itself, if the image is OK and there is a valid Grub module to read the file.

> 
One doubt I have:

Some people say that to change screen resolution of grub2, edit /etc/grub.d/00_header, search for “set gfxmode=640x480” and change it as you like.

But, you like to edit /etc/default/grub # GRUB_GFXMODE=640x480

which one to prefer?

Definitely change the setting in /etc/default/grub, not in /etc/grub.d/00_header.  Again, if you look at 00_header, it just uses the value that you define in /etc/grub/default:

```
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  ...

```

---

### Post by 600WPMPO on 2009-11-05
> **600WPMPO said:**
> 
One more point that can be added:

In the file "05_debian_themeand as 06_custom_theme", we must look at the line which reads "use_bg=false"


You have to set the variable "use_bg=false" to true. i.e. **use_bg=true**

Ok, please do not use this option as it is not working. I was wrong in suggesting it. This even gave me an error when doing "sudo update grub".
More info is from drs305:

> Looking at the script, it appears that the "bg" value in line 14 (false) is reset to the background image value several lines later if the image exists and you are using GFXTERM. Since most users would be using gfxterm making this value "true" would bypass the subsequent section which designates where the bg image resides.

I apologise for any errors caused by this post.

-----------------------------------------------------

[CENTER]**2 difficulties I'm facing:**[/CENTER]

However, I have not yet succeeded in making my Grub2 display a background image.

When I follow all the steps as mentioned under "5. Add a Splash Image", it does not give the "Found Debian image xxxxxxx" among the terminal outputs.The resulting Grub background is black.

Secondly, when I change the Grub resolution, it works fine, but after the boot selection menu, an error message blinks for a second which says something like "vga=792 is deprecated use set gfxpayload=1024x768x24;1024x768 before the linux command"


How do I correct this?
Please help gentlemen...

---

### Post by drs305 on 2009-11-05
> **600WPMPO said:**
> However, I have not yet succeeded in making my Grub2 display a background image.

When I follow all the steps as mentioned under "5. Add a Splash Image", it does not give the "Found Debian image xxxxxxx" among the terminal outputs.The resulting Grub background is black.

Secondly, when I change the Grub resolution, it works fine, but after the boot selection menu, an error message blinks for a second which says something like "vga=792 is deprecated use set gfxpayload=1024x768x24;1024x768 before the linux command"


The common problems I foresee if you are trying to use the grub2-splashimages is that they are not downloaded to the same folder looked at by G2 by default. If you aren't using the default G2 splash images, make sure the line in 05_debian_theme points to the correct location. Also make sure you have the "." following the graphic filename in the "for i ..." line.

If you cannot figure it out, post the 05_debian_theme line "for i" concerning splashimages (approximately line 15.


2. The vga message is because you probably have a "vga=XXX" in your /etc/default/grub settings. For setting the G2 menu resolution (only), use the GFXMODE lines. For setting the system resolution, apparently the vga= method isn't the preferred method any longer as these settings are made by the system as it boots.

---

### Post by 600WPMPO on 2009-11-05
> **drs305 said:**
> The common problems I foresee if you are trying to use the grub2-splashimages is that they are not downloaded to the same folder looked at by G2 by default. If you aren't using the default G2 splash images, make sure the line in 05_debian_theme points to the correct location. Also make sure you have the "." following the graphic filename in the "for i ..." line.

If you cannot figure it out, post the 05_debian_theme line "for i" concerning splashimages (approximately line 15.

Yes, I had checked it and made sure the files are in that folder only

I downloaded the splashimages from the Ubuntu repositories by

sudo apt-get install grub2-splashimages

This installed the splash image package at:

/usr/share/images/grub/

Since the code was:
```
for i in {/boot/grub,/usr/share/images/desktop-base,/usr/share/images/grub}/xxxxxxxx.{png,tga}
```

i copied the images to /usr/share/images/desktop-base

but this didn't help...


> **drs305 said:**
> The vga message is because you probably have a "vga=XXX" in your /etc/default/grub settings. For setting the G2 menu resolution (only), use the GFXMODE lines. For setting the system resolution, apparently the vga= method isn't the preferred method any longer as these settings are made by the system as it boots.

Ok, so now how do I correct this? Should I put a # before the "vga=XXX" in your /etc/default/grub file ? Will that work ?

---

### Post by drs305 on 2009-11-05
> **600WPMPO said:**
> so now how do I correct this? Should I put a # before the "vga=XXX" in your /etc/default/grub file ? Will that work ?

You simply remove the entry in whatever line it appears. It is probably at the end of one of GRUB_CMDLINE... lines. You will then have to set up the resolution within your OS. For Ubuntu, you can probably do so via System, Preferences, Display.

I don't see a problem with your splash-image location. Most of the images are for 640x480 and if you have your gfxmode set to something other than that I believe G2 has a problem displaying the image.

---

### Post by 600WPMPO on 2009-11-05
> **drs305 said:**
> You simply remove the entry in whatever line it appears. It is probably at the end of one of GRUB_CMDLINE... lines. You will then have to set up the resolution within your OS. For Ubuntu, you can probably do so via System, Preferences, Display.

Yes.. that did it.. Now I dont get that vga=792 is deprecated error..!! Thanks a lot.. :D

My desktop resolution is 1280x1024, but that doesnt make any difference to the grub resolution, does it?

So, this means that we can only change the grub menu resolution and not the grub (background) resolution which will stay at 640x480... ?



> **drs305 said:**
> I don't see a problem with your splash-image location. Most of the images are for 640x480 and if you have your gfxmode set to something other than that I believe G2 has a problem displaying the image.

Ok.this problem is also solved..!! 

Instead of putting the splash images in /usr/share/images/desktop-base, I kept them where they were downloaded i.e. usr/share/images/grub , and copied the file as you mentioned :

```
for i in {/boot/grub,/usr/share/images/desktop-base,**/usr/share/images/grub**}/xxxxxxxx. {png,tga} ;do
```

---

### Post by drs305 on 2009-11-05
> **600WPMPO said:**
> My desktop resolution is 1280x1024, but that doesnt make any difference to the grub resolution, does it?

So, this means that we can only change the grub menu resolution and not the grub (background) resolution which will stay at 640x480... ?

The screen displaying the grub menu and grub images will display a default resolution of 640x480 unless you change it with the GRUB_GFXMODE setting in /etc/default/grub.  The image size should match the resolution - if not it will be distorted or not cover the entire screen. Normally if it's too small (640x480 on a 1280x1024 resolution) the image will anchor to the upper left corner of the screen. You would have to create or alter an image of the proper size to fill the screen. GIMP is a default program that can resize these images.

For troubleshooting the failure to get a splash image to display, take a look at the terminal while "update-grub" runs. Does it  find a Debian theme or is nothing at all mentioned. It is normally about the first message after "Generating grub.cfg" the command starts.

If it finds the image:  
Generating grub.cfg ...
Found Debian background: sample.tga

If it doesn't find sample.tga:
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic

---

### Post by ranch hand on 2009-11-05
I do this in a crude way but it does work.

I take the image and put in the fileit needs to be in, in my case desk-top base, and see what it looks like and adjust from there.  It helps if the the resolution is 72,000x72,000 as that is what the images are if you get the official package (including the grub folder).  My screen is a Dell at 1440x900 and I find a lot of images "almost" fit so I tweek a lot.

---

### Post by 600WPMPO on 2009-11-05
> **drs305 said:**
> The screen displaying the grub menu and grub images will display a default resolution of 640x480 unless you change it with the GRUB_GFXMODE setting in /etc/default/grub.  The image size should match the resolution - if not it will be distorted or not cover the entire screen. Normally if it's too small (640x480 on a 1280x1024 resolution) the image will anchor to the upper left corner of the screen. You would have to create or alter an image of the proper size to fill the screen. GIMP is a default program that can resize these images.

That's very correct..

I've done it now... here's how I changed the Grub background resolution:

I downloaded a desktop wallpaper of resolution 1024x768 (see attached image).

I then converted it to .tga format via GIMP.

Copied this file to /usr/share/images/grub/ where all my splash images reside.

Changed grub menu resolution to 1024x768

Updated Grub

Success..!!


p.s. One doubt though: 

I have throughout been unsuccessful in changing Grub menu resolution via editing  etc/default/grub # GRUB_GFXMODE=640x480. The Grub menu resoultion always stayed at the default 640x480.

What works for me is editing  /etc/grub.d/00_header, and changing &#8220;set
gfxmode=640x480&#8221; to my liking.. be it 800x600 or 1024x768.

If this doesnt cause any harm, it is okay to edit the header?

---

### Post by drs305 on 2009-11-06
> **600WPMPO said:**
> 
p.s. One doubt though: 

I have throughout been unsuccessful in changing Grub menu resolution via editing  etc/default/grub # GRUB_GFXMODE=640x480. The Grub menu resoultion always stayed at the default 640x480.

What works for me is editing  /etc/grub.d/00_header, and changing “set
gfxmode=640x480” to my liking.. be it 800x600 or 1024x768.

If this doesnt cause any harm, it is okay to edit the header?

Nice guide on how you made your graphics work.

You must remove the comment symbol (#) from the start of the GRUB_GFXMODE line. The # symbol tells the script to disregard the line. Remove it, and the line will work.

You should probably leave the 00_header file the way it was originally. The resolution in there is a "fallback" setting in case nothing else is found. It will certainly work, as you discovered, but GRUB 2 is written for the user to make changes in the /etc/defualt/grub file. 

Try changing 00_header back to it's original state, remove the # symbol from the GFX line in /etc/default/grub, and finally run "sudo update-grub" to incorporate the changes.

---

### Post by 600WPMPO on 2009-11-06
> **drs305 said:**
> You must remove the comment symbol (#) from the start of the GRUB_GFXMODE line. The # symbol tells the script to disregard the line. Remove it, and the line will work.

Try changing 00_header back to it's original state, remove the # symbol from the GFX line in /etc/default/grub, and finally run "sudo update-grub" to incorporate the changes.

I have always removed the #, but it won't work. Here's my /etc/default/grub file:


```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=2
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=" splash vga=773"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

As you can see, I wanted to change the resolution to 800x600, so I made this change, but the grub menu would still stay at 640x480.

So. I edited the header to a resolution of 1024x768. It worked. I've kept the /etc/default/grub file still at 800x600,as it is not making any difference to me.

So, any ideas what's going wrong ?

---

### Post by drs305 on 2009-11-07
> **600WPMPO said:**
> 
So, any ideas what's going wrong ?

Sorry to take a while to get back to you on this. I discovered that I had the same situation on my laptop dual-boot system. When I run update-grub on this system the gfxmode in grub.cfg (line 23) does not change. When I run it on my single OS desktop the change is made.

Initially, these are things I checked:
1. /etc/default/grub, and etc/grub.d files are all executable
2. the graphic mode selected is compatible with grub 2 (from the boot menu, press "c", then type "vbeinfo" get see the allowable resolutions).
3. Using the default settings in /etc/grub.d/00_header
3. run "sudo update-grub"
4. Check the contents of /boot/grub/grub.cfg to see if the gfxmode changed.

I could not find a problem. So I then planned to replace /etc/default/grub, /etc/grub.d/00_header and /usr/sbin/grub-mkconfig with known valid copies. On my laptop, it turned out there was a problem with /etc/default/grub (somewhere). 

You can find a "clean" copy of /etc/default/grub in /usr/share/grub/default  Try replacing your current one with a copy of the original and see if it works.  That fixed the problem for me and now when I change the GRUB_GFXMODE= value and run update-grub the change is made to /boot/grub/grub.cfg.

I haven't tweaked any of my settings yet to see if there might be a bug connected with a particular setting, but for now the defaults work correctly.

---

### Post by 600WPMPO on 2009-11-07
> **drs305 said:**
> You can find a "clean" copy of /etc/default/grub in /usr/share/grub/default  Try replacing your current one with a copy of the original and see if it works.  That fixed the problem for me and now when I change the GRUB_GFXMODE= value and run update-grub the change is made to /boot/grub/grub.cfg.

Thanks for replying...

I think we are almost there..

Can you please tell where can I find a fresh copy of /etc/grub.d/00_header ?

---

### Post by musarraf172 on 2009-11-07
Can anybody write a step by step guide on how to install grub2 in linux superblock not on mbr? 

I am using a IBM 51 laptop which is having a custom IBM specific MBR. I don't want to destroy it.

Secondly, can anyone tell me how to reinstall grub2 if it is corrupted?
Something similar to stage1 or stage2 in legacy grub....

---

### Post by 600WPMPO on 2009-11-08
> **musarraf172 said:**
> Can anybody write a step by step guide on how to install grub2 in linux superblock not on mbr? 

I am using a IBM 51 laptop which is having a custom IBM specific MBR. I don't want to destroy it.

Secondly, can anyone tell me how to reinstall grub2 if it is corrupted?
Something similar to stage1 or stage2 in legacy grub....

Why don't you read this excellent thread here by drs305:

[Grub2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

This is a legendary thread.. to be read again & again..!!!!! :lolflag:

---

### Post by drs305 on 2009-11-08
> **600WPMPO said:**
> Thanks for replying...

I think we are almost there..

Can you please tell where can I find a fresh copy of /etc/grub.d/00_header ?

I've copied a fresh /etc/grub.d/00_header file here:
[http://pastebin.com/f56f21db4]("http://pastebin.com/f56f21db4")

Don't forget to make it executable:
```

sudo chmod +x /etc/grub.d/00_header

```

---

### Post by 600WPMPO on 2009-11-09
> **drs305 said:**
> I've copied a fresh /etc/grub.d/00_header file here:
[http://pastebin.com/f56f21db4]("http://pastebin.com/f56f21db4")

Don't forget to make it executable:
```

sudo chmod +x /etc/grub.d/00_header

```

Ok.. all grub customization problems are now solved..!! thanks a lot drs305.. you have been most helpful..!!

Here's how it happened:

Yesterday evening, I switched on my system, expecting a cute & cuddly Koala on my desktop, but you know what I find ? 

Just after the grub menu & the ubuntu logo, instead of my Xsplash, all there was a blinking cursor...

ctrl+alt+del immediately restarted before I could write init3,
rebooting into recovery mode failed..

I then did a fresh install.. and tweaked the grub as per the instructions on the first page, and everything worked fine.

Last time, I had used startup manager (SUM) to change the resolution initially, which changed a line in my /etc/default/grub file (post#17, page2):
from
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX=" splash vga=773"
```

Now, when I edit /etc/default/grub without any previous SUM interventions, I am successfully able to change grub menu resolution without the need to edit the header..!!


p.s. Any idea about that blinking cursor issue? Was that a failure to load X ? Did it involve my editing the header?

---

### Post by tbessie on 2009-11-09
I just posted this:

[http://ubuntuforums.org/showthread.php?t=1320203](http://ubuntuforums.org/showthread.php?t=1320203)

Shouldn't the installer ASK me where I want to install Grub, as it always has (or recently, anyway)?  I mean, to just assume that of course EVERYONE who's installing 9.10 (server edition, at least) will want to overwrite their MBR... that's kind of wrong-headed.

Is there no way, in the 9.10 server edition installer itself, to tell it "install Grub to partition X"?

- Tim

---

### Post by musarraf172 on 2009-11-09
> **600WPMPO said:**
> Why don't you read this excellent thread here by drs305:

[Grub2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

This is a legendary thread.. to be read again & again..!!!!! :lolflag:

Thanks dear... 

got this   [http://ubuntuforums.org/showthread.php?t=1195275&page=9](http://ubuntuforums.org/showthread.php?t=1195275&page=9)

---

### Post by drs305 on 2009-11-09
> **musarraf172 said:**
> Thanks dear... 

got this   [http://ubuntuforums.org/showthread.php?t=1195275&page=9](http://ubuntuforums.org/showthread.php?t=1195275&page=9)

Looks like it sent you to page 9. This is the start page:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Or for the more 'formal' version:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by musarraf172 on 2009-11-09
> **drs305 said:**
> Looks like it sent you to page 9. This is the start page:
[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

Or for the more 'formal' version:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Once again thank you very much.Great tutorial.:lolflag:

---

### Post by tbessie on 2009-11-10
> **musarraf172 said:**
> Once again thank you very much.Great tutorial.:lolflag:

That tutorial still doesn't say anything about having the 9.10 server installer itself let you choose your Grub installation location, though, does it?  I couldn't find any mention of that.

- Tim

---

### Post by musarraf172 on 2009-11-11
> **tbessie said:**
> That tutorial still doesn't say anything about having the 9.10 server installer itself let you choose your Grub installation location, though, does it?  I couldn't find any mention of that.

- Tim

I am not sure about the server installer. I will check and get back....

---

### Post by cimh on 2009-11-13
Hi 

I'm puzzled about installing new splash images. Any help would be fantastic.

1. I have download the new images
2. I have edited 05_Debian_Theme to point at the image.
eg.  for i in {/boot/grub,/usr/share/images/grub}/Sparkler.{png,tga} ; do
3. I have run sudo update-grub
4. It says Found debian background Sparkler.tga

but on boot I get the monochrome small ubuntu logo splash rather than the new image - I have tried a few images - also altered the permissions of the image to make it executable or not - but none of these things made a difference - 

Its probably something obvious but an hour of fiddling hasnt solved it - any ideas?

cimh
asus eee 901: Karmic + LXDE

---

### Post by ranch hand on 2009-11-13
What you are seeing is the usplash image.  The Grub2 splash image is the background behind your menu on the screen.

I take it you only have one OS on your box.

You need to go to /etc/default/grub and edit the file.  You need to hash the line;
```

GRUB_HIDDEN_TIMEOUT=0

```
so it reads
```

## GRUB_HIDDEN_TIMEOUT=0

```

---

### Post by cimh on 2009-11-13
> **ranch hand said:**
> I take it you only have one OS on your box.
## GRUB_HIDDEN_TIMEOUT=0


Thnxs for quick reply. yes only one os. I #'d out that line - updated but no difference - then I tried #ing out the line below to but also no difference.

grub looks like this now:
```

GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
# GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

you can see I'd earlier un#ed the grub_gfxmode line as well. It wouldnt be anything to do with the screen res on the eee (1024 x 600) would it?

cimh

---

### Post by ranch hand on 2009-11-13
It appears that you a the grub timeout we at 0.  I would increase that.

You have to remember to run;
```

sudo update-grub

```
for any change to take place.

---

### Post by cimh on 2009-11-13
Excellent thanks.  So
# GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT="1"

brings up the splash image for a couple of secs overlaid by the text but it soon disappears to be replaced by the monochrome ubuntu splash again. Is that supposed to happen? I thought the new splash screen would stay on until I got to gdm?

cimh

---

### Post by ranch hand on 2009-11-13
Nope.  The goal is to replace usplash with upstart but that has not worked yet.  So, you get the grub menu, upsplash, xsplash, GDM and then xsplash again on booting.

Hopefully this is resolved in 10.04.

---

### Post by yaztromo on 2009-11-19
I have more than one OS installed but still want to hide the menu unless I press shift. Following your OP does not work for me. Is it possible to hide the menu with more than one OS installed at all?

EDIT: Nevermind I fixed it. To hide the menu you also have to set GRUB_TIMEOUT=0.

---

### Post by drs305 on 2009-11-19
> **yaztromo said:**
> I have more than one OS installed but still want to hide the menu unless I press shift. Following your OP does not work for me. Is it possible to hide the menu with more than one OS installed at all?

In /etc/default/grub, set the GRUB_HIDDEN_TIMEOUT to 0 or a positive integer.

Hiding the menu is a problem for some users (including me on some systems). Here are some of the ways that might work for you. Each one is separate from the others and should start from an unchanged system (i.e. restore the original settings before trying the next).


1. Add this line to /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
run sudo update-grub
Leaving it set up like this will not allow G2 to find updates on other partitions/OSs. The next post may work without giving up this feature.

2. Refer to post #17 in this thread:
[http://ubuntuforums.org/showthread.php?p=8290027#17]("http://ubuntuforums.org/showthread.php?p=8290027#17")

3. Refer to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495")

---

### Post by burgerearl on 2009-11-22
Maybe this is obvious for those more experienced with editing Linux config files than I am (newb), but it might be helpful to add a note that when adding a background image, the image name is case sensitive. That caught me up at first.

Thanks for the writeup!

---

### Post by drs305 on 2009-11-22
> **burgerearl said:**
> Maybe this is obvious for those more experienced with editing Linux config files than I am (newb), but it might be helpful to add a note that when adding a background image, the image name is case sensitive. That caught me up at first.

This is true of Linux in general. But if it happened to you it is 100% certain it's happened to others.

---

### Post by LucianoP on 2010-03-07
I have installed grub2-splashimages and edited /etc/grub.d/05_debian_theme to point to the chosen image, but I got the following error when updating grub:

```
Generating grub.cfg ...
/etc/grub.d/05_debian_theme: 3: source: not found
/etc/grub.d/05_debian_theme: 31: is_path_readable_by_grub: not found
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```Ant guess on how to fix this?
Thx

---

### Post by ranch hand on 2010-03-07
LucianoP
What is the path to the image that you want to use?  What type of image is it (.png, jpg, etc)?  What is the resolution of the image?

---

### Post by LucianoP on 2010-03-08
> **ranch hand said:**
> LucianoP
What is the path to the image that you want to use?  What type of image is it (.png, jpg, etc)?  What is the resolution of the image?
hey Ranch
this is the image I want to use /usr/share/images/grub/Plasma-lamp.tga
a standard 640x480 pic
I have reviewed the /etc/grub.d/05_debian_theme but everything looks ok

---

### Post by ranch hand on 2010-03-08
Try putting it is /usr/share/images/desktop-base and change the path to that folder.  I would change the type to .png too.  If you do that after putting it in the folder you will have both there and as long as debian-theme is calling for either you should pick it up.

Run both "update-grub" and "grub-mkconfig" after doing those things.

I have had a couple installs that didn't seem to like the "grub" images folder.  The other is the default.

---

### Post by LucianoP on 2010-03-09
> **ranch hand said:**
> Try putting it is /usr/share/images/desktop-base and change the path to that folder.  I would change the type to .png too.  If you do that after putting it in the folder you will have both there and as long as debian-theme is calling for either you should pick it up.

[FONT=Verdana]None worked :(
 I also tried to reinstall both grub-pc and grub2-splashimages[/FONT][FONT=Verdana] via Synaptic.[/FONT]

is_path_readable_by_grub: not found  is really strange

---

### Post by ranch hand on 2010-03-09
> **LucianoP said:**
> [FONT=Verdana]None worked :(
 I also tried to reinstall both grub-pc and grub2-splashimages[/FONT][FONT=Verdana] via Synaptic.[/FONT]

is_path_readable_by_grub: not found  is really strange
I have only gone that route once as I do not like their images.  When you have Gimp you can size and edit just about any image you want to put in there.

Just for fun copy the file below and paste it to gedit.  Save the sucker in your /etc/grub.d directory as 05_debian-theme.new.  That is what it is in my box from some upgrade lately.
> 
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/menu.png"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi

Make sure that it is executable and disable all other 005_debian-theme files no matter how they are labeled.

You will have to edit the image name.

Update your grub.

Try that.

---

### Post by LucianoP on 2010-03-27
Hi Ranch,
Thanks for the tip!
Now it worked fine
:)

I noticed these lines were missing in my original 05_debian_theme
> if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/menu.png"
  COLOR_NORMAL="white/black"
  COLOR_HIGHLIGHT="red/black"

---

### Post by ranch hand on 2010-03-27
Every once in a while grub-common does things like that.  Probably because it is supporting both grub and grub-pc (grub-legacy and grub1.9x - I have grub1.96, 1.97beta4, 1.98 and 0.97 on this box).

The images that you can download are fine but they install another folder in /etc/share/images (grub) and as you can see the default folder is already there.

With gimp it is easy to resize any image to fit the menu so I just do it that way.  The default colors are actually;
Normal="black/black"
Highlight="magenta/black"
but that does not work well for my background on whichever of my installs I swiped that from.  I think it is nice to be able to read the menu.

It is really neat that the image is that easy to change and can be a good image too.  Grub0.97 is kind of a pain to put a back ground into and is also limited to 8(!) colors so the image must be pretty simple to render at all.

---

### Post by uid313 on 2010-03-28
But I want the menu to normally not appear.

So I have;
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"

But I want the menu to appear if I hold down Esc or Shift or something.

How?

---

### Post by drs305 on 2010-03-28
> **uid313 said:**
> But I want the menu to normally not appear.

So I have;
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"

But I want the menu to appear if I hold down Esc or Shift or something.

How?

Holding down the SHIFT key should bring up the menu for you.

---

### Post by Macamba on 2011-05-06
I edited my grub.cfg and changed my grub_default to
```
GRUB_DEFAULT="Microsoft Windows XP Home Edition"
```
(Note that this was the same entry I got from the grep "menuentry" /boot/grub/grub.cfg) Next I  executed a sudo update-grub and restarted my machine. When the menu appeared my first entry with 'Ubuntu, with Linux 2.6.38-8-generic' was highlighted. So nothing changed. 

Next I tried to change my default OS by executing a 
```
sudo grub-set-default 4
``` followed again with a sudo update-grub and a restart. Again with the same result. What am I doing wrong?

Edit: I performed another reboot, and now XP was highlighted. So I was a tad to early with my question. 

However, might it be possible to change the order in which the different choices are displayed? Like XP first?

---

### Post by drs305 on 2011-05-06
> **Macamba said:**
> 
However, might it be possible to change the order in which the different choices are displayed? Like XP first?

Although I wrote a scripting guide for manually changing the order (see 'Tweaks' link), a much easier way is to use the GUI app Grub Customizer. Click the 'Customizer' link in my signature line to go my guide on how to install and use it.

Another way would be to rename /etc/grub.d/30_os-prober to /etc/grub.d/06_prober, which would put other OS's at the top of the menu. You wouldn't have as much control over the order though, so I'd stick to Grub Customizer.

---

### Post by Macamba on 2011-05-06
Thanks.

---

### Post by bull-head on 2011-07-11
i followed all your comments...and finally it is working now ...great....thanks:)

---

