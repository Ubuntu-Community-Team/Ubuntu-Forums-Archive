---
title: "Howto: Beryl (for Intel embedded graphics cards)"
date: 2006-09-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Uncle Spellbinder on 2006-09-28
*** ***_[color=#CC0000]UPDATED with most current info, 29-October-2006[/color]_*** ***

As Beryl is now incredibly easy to install, the "official" repos should be followed. Please see below. Enjoy Beryl!

****************************************************************************************************
Edgy, see the official "Howto": [** _[b]How-to install Beryl with AIGLX on Edgy Eft**_[/b]](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft)

Dapper, See the official "Howto": [***_ How-to install Beryl with AIGLX on Dapper_***](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

****************************************************************************************************

---

### Post by foxy123 on 2006-09-29
I take it this howto is for Edgy only?

---

### Post by Hotaru on 2006-09-29
It dind't work for me :(.
I have first completly removed all compiz-related packages with Synaptic and then followed your how-to. Everything seems to be installed, I have Emerald and Beryl apllications in System>Preferences, but nothing happens when I try to run them.

---

### Post by foxy123 on 2006-09-29
Just to say that it works for Dapper as well. You just need a different repository. I am not sure which but this is what I have in my sources.list. Please remove compiz manually as beryl does not remove everything.

```
##AIGLX-Compiz
deb http://xgl.compiz.info/ dapper main aiglx
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

deb-src http://xgl.compiz.info/ dapper main aiglx
deb-src http://www.beerorkid.com/compiz dapper main aiglx
deb-src http://ubuntu.compiz.net/ dapper main aiglx
deb-src http://media.blutkind.org/xgl/ dapper main aiglx

```

---

### Post by iam_foo on 2006-09-29
hi..i get this error msg when starting beryl or the manager..

XGL Absent, checking for NVIDIA
libGL warning: 3D driver claims to not support visual 0x5b
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x5b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
beryl: Couldn't load plugin 'manager'


i have just installed edgy. fresh. i updated with repositories.
i installed beryl as described above.


there is absolutely no compiz present.
[ find / -name 'compiz' ]

tanks

**dell inspiron 6000 w intel i810. //edgy/gnome.

any help is greatly appreciated.

---

### Post by Sirin on 2006-10-01
*deleted*

---

### Post by Toufik on 2006-10-02
> **iam_foo said:**
> there is absolutely no compiz present.
[ find / -name 'compiz' ]

That's **BERYL** and not compiz!!

Bye the way, this how-to is for edgy.  It is so easy because AIGLX is already in edgy.  For **Dapper**, the repos is 
```
deb http://ubuntu.beryl-project.org/ dapper main aiglx
```
But remember that you need to install first AIGLX.  Use this How-to:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)


Another point is to completely remove compiz before:
```
sudo aptitude purge compiz compiz-core compiz-plugin compiz-manager csm cgwd cgwd-themes
```

Finally, it works also with **Kubuntu**, follow the same instructions except to start automatically beryl-manager at each startup, make a link:
```
ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager
```

**Uncle Spellbinder** -> Maybe it's worth to add these in your first post

---

### Post by GPH on 2006-10-02
It works well on my computer, but as soon as I close a window, Beryl crashes and goes back to metacity.

Any ideas on this ?

**SOLVED**
I had to enable Multiverse and Universe and do an update.

---

### Post by Fire on 2006-10-02
Okay I can't figure this out.  I have beryl running on my system.  When I start running it all my windows lose there title bar.  I can't move any of the windows.  And when I select a theme from emerald nothing happends.

Any help would be great from someone that has this running.. thanks

---

### Post by Fire on 2006-10-02
OKay I have found something but unsure what to do with it.

Warning**: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
The program 'emerald' recieved and X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
   (Details: serial 657 error_code 8 request_code 153 minor_code 8)
   (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will recieve the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful backtrace   
   from your debugger if you break on the gdk_x_error() function.)
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX-EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display : 0.0

Any help would be great.. thank you

---

### Post by LamB on 2006-10-02
I can't figure it out... I get
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

any sugestions?? ](*,) 
thanks

---

### Post by k84 on 2006-10-02
Hi, i installed beryl successfully by just adding the repos and installing it. I remember in Dapper we had to add some lines to the xorg.conf for the Intel embedded cards, something like in this [post]("http://ubuntuforums.org/showpost.php?p=1552759&postcount=207"). Is this still needed in Edgy? right now im running it without those configurations and it's ok but i just wanna know if it's recommended to add those lines to the xorg configuraion file.

---

### Post by iam_foo on 2006-10-03
i thought i would post that i got my beryl working.
first, the gentleman who tried to correct me.
i  ran the compiz command because i had read a couple
posts saying it was important to remove all compiz files.
so to make sure i wasnt updated with some compiz pkgs
i ran the command.
i was aware i was using beryl.
second, my problem was fixed by running the 
$ beryl-xgl 
command..which i hadnt thought of because i assumed
it would use the already present aiglx.
i still get the same error msg, but it works.
beryl-manager works as well.

the error msgs are a result of intel embeded graphics sUcking.

and i havent really come across any major problems that wont be fixed by future updates.

i love my computer again.:twisted:

t@nks 2 @ll

---

### Post by Uncle Spellbinder on 2006-10-03
*** ***[color=#CC0000]UPDATED with most current info, 03-October-2006[/color]*** ***

**SEE** [**_FIRST POST_**](http://www.ubuntuforums.org/showpost.php?p=1555244&postcount=1)

---

### Post by Buffalo Soldier on 2006-10-03
Do I need to edit xorg.conf file? Guides such as this one [http://ubuntuforums.org/showpost.php?p=1552759&postcount=207](http://ubuntuforums.org/showpost.php?p=1552759&postcount=207)

talks about adding lines under Section "Device" ```
Option "XAANoOffscreenPixmaps" "true"
```
and at the end of the file
```
Section "Extensions"
Option "Composite" "true"
EndSection
```

---

### Post by Uncle Spellbinder on 2006-10-03
@ Buffalo Soldier

In Edgy, I didn't and have had no problems. Not sure about Dapper (there's a link in post #1 for Dapper/Edgy).

---

### Post by auroraborealis on 2006-10-03
Hey, I got Beryl working in Edgy, but when I double click on the title bar, it shades rather than maximizes. How do I change this behavior?

---

### Post by bollocks00 on 2006-10-03
I followed the instructions to a tee, but beryl isn't working.  I can get the emerald in the system tray, but I can't switch to Beryl from Metacity.  Attempting to do so with the terminal open gives:

```

** (beryl-manager:5989): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
XGL Absent, checking for NVIDIA
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
Nvidia Absent, assuming AIGLX
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

** (beryl-manager:5989): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
```

Any thoughts on how to get Beryl working from here?

Also I'm running Edgy Eft with Intel 915 graphics.

---

### Post by bollocks00 on 2006-10-03
Anyone?

---

### Post by Uncle Spellbinder on 2006-10-04
> **bollocks00 said:**
> Anyone?

I'm stumped. We seem to have the same graphics. Did you uninstall Compiz (if you had it)? The XGL and Nvidia entries in your output don't make sense to me if they aren't necessary. Hopefully someone with more knowledge on your output will post. Sorry I can't help on this.
:(

---

### Post by Buffalo Soldier on 2006-10-04
> **bollocks00 said:**
> I followed the instructions to a tee, but beryl isn't working.  I can get the emerald in the system tray, but I can't switch to Beryl from Metacity.  Attempting to do so with the terminal open gives:

```

** (beryl-manager:5989): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
XGL Absent, checking for NVIDIA
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
Nvidia Absent, assuming AIGLX
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

** (beryl-manager:5989): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
```

Any thoughts on how to get Beryl working from here?

Also I'm running Edgy Eft with Intel 915 graphics.

Just checking, do you have the **Load	"glx"** line in your **xorg.conf** file?
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	**[color=red]Load	"glx"[/color]**
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

---

### Post by bollocks00 on 2006-10-04
yeah, my xorg.conf looks just like that one, except it doesn't have the Load "dbe"

Edit: Tried it with Load "dbe" just in case.  No luck.

---

### Post by 20valv3 on 2006-10-04
Followed every step in installing Beryl on Intel embedded on dapper... Beryl will not run.  No compiz was present before.  

I get the following:

```

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

---

### Post by zupermanz on 2006-10-04
> **20valv3 said:**
> Followed every step in installing Beryl on Intel embedded on dapper... Beryl will not run.  No compiz was present before.  

I get the following:

```

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

I have the same problem....
and have followed every step.
I use kubntu dapper

---

### Post by sunny_nwho on 2006-10-04
> **zupermanz said:**
> I have the same problem....
and have followed every step.
I use kubntu dapper


neither did ui get it working I have a i855GM and Ubuntu Dapper. Anyone plz help

---

### Post by cogsprocket on 2006-10-04
Try installing you desktop environment package.  I'd been playing around with several different desktop environments and caused my Beryl install to crash with the same series of errors.  It may sound a bit far fetched but I installed the gnome-desktop-environment package and it came right back for me.

On the other hand I think I should point out that I DID have Compiz running prior to switching to Beryl.

---

### Post by zupermanz on 2006-10-05
I finally fixed it!

sudo gedit /etc/kde3/kdm/kdmrc

in line 464 i think i've changed 
ServerCmd=/usr/bin/X -br --------->ServerCmd=/usr/bin/Xorg-air :0

Then i've copied the libraries missing to xorg-air directory


sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

sudo reboot

beryl-manager

thats it! (at least for me)

---

### Post by LamB on 2006-10-05
> **zupermanz said:**
> 
Then i've copied the libraries missing to xorg-air directory

sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

sudo reboot

beryl-manager

thats it! (at least for me)

thanks.. the modules and drivers were missing in my xor-air folder too.
it works perfectly now

---

### Post by 20valv3 on 2006-10-05
> **zupermanz said:**
> I finally fixed it!



Then i've copied the libraries missing to xorg-air directory


sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

sudo reboot

beryl-manager

thats it! (at least for me)

Used the same solution.  I found this fix from old compiz-aiglx guides.  Either copy or link the drivers from xorg to xorg-air

---

### Post by bollocks00 on 2006-10-05
> **zupermanz said:**
> I finally fixed it!

sudo gedit /etc/kde3/kdm/kdmrc

in line 464 i think i've changed 
ServerCmd=/usr/bin/X -br --------->ServerCmd=/usr/bin/Xorg-air :0

Then i've copied the libraries missing to xorg-air directory


sudo cp /usr/lib/xorg/modules/drivers/* /usr/lib/xorg-air/modules/drivers
sudo cp /usr/lib/xorg/modules/input/* /usr/lib/xorg-air/modules/input

sudo reboot

beryl-manager

thats it! (at least for me)

Does anyone know what the equivalent of this would be in ubuntu, edgy eft?  I don't even have a /kde3 folder.

Thanks.

---

### Post by iam_foo on 2006-10-05
@ bullocks

did you try:

$ beryl-xgl

?

---

### Post by bollocks00 on 2006-10-05
```

lenny@IBM:~$ beryl-xgl
XGL Absent, checking for NVIDIA
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
Nvidia Absent, assuming AIGLX
Xlib:  extension "GLX" missing on display ":0.0".
beryl-xgl: Root visual is not a GL visual
beryl-xgl: Failed to manage screen: 0
beryl-xgl: No manageable screens found on display :0.0

```

Any ideas?

---

### Post by Namroc on 2006-10-06
well almost everything is working here.  Have a Dell Inspiron 6000 with an Intel Mobile 915GM/GMS/910GML Express Graphics Controller.  Everything seems to be working fine (no errors) but my windows are stuck.  I had this problem before with aiglx in dapper and fixed it before but that was ages ago.  Anyone have any sugestions that might help refresh my memory? any help is greatly appriciated ^_^

---

### Post by iam_foo on 2006-10-06
first:

```
sudo apt-get install alien
```

```
wget -c http://downloadmirror.intel.com/df-support/8211/eng/dri-I915-v1.1-20041217.i386.rpm
sudo alien dri-I915-v1.1-20041217.i386.rpm
sudo dpkg -i dri-i915_v1.1-20041218_i386.deb
```

you may want to try 915resolution as well.

if that doesnt work..try this:

reboot
"hit escape to load grub menu"
select the first option that includes the word (recovery mode) at the end of the line.this will boot you into a text prompt.  
try this:
just in case..
```
sudo apt-get remove --purge nvidia-glx
```

```
sudo apt-get install --reinstall xserver-xorg-driver-i810
```

```
sudo reboot
```

boot normally into your WM. open a terminal.
type:

```
glxgears
```

if that doesnt work:

```
glxinfo
```

if you get this error mssg:

**Error: couldn't find RGB GLX visual**

try this:

reboot the same as described above.[recovery]

```
sudo apt-get remove --purge xserver-xorg-driver-i810
```

```
sudo apt-get install xserver-xorg-driver-i810
```

reboot.

---

### Post by bollocks00 on 2006-10-06
Thanks, foo!

I'm not sure which part of that worked, but I suspect it was either

sudo apt-get remove --purge nvidia-glx

or

sudo apt-get remove --purge xserver-xorg-video-i810
sudo apt-get install xserver-xorg-video-i810

For others who were having this problem, note that I purge/installed xorg-**video**-i810, not xorg-driver-i810.  This is what worked for me!

---

### Post by zupermanz on 2006-10-07
I've noticed another problem...: When i playback video and the window of the player becomes trasparent i instead of video i see only a blue window (i hear  the sound of the film). I noticed that this happens when i chage the opacity of the players window to something below 100%,
My question: Is there a way to fix that or to disable the trasparencies in inactive windows?

Thanks in advance

---

### Post by Hotaru on 2006-10-07
Yeah, I experience this transparency thingy as well :(. I guess disabling trail focus plugin would solve it, but that's not really a solution... :(

---

### Post by iGama on 2006-10-07
i have a Ati 9200 , using the open source drivers and it worked ;)

( the ati open source drivers in edgy finally have direct rendering :D )

---

### Post by vkkim on 2006-10-07
EDIT: IT WORKS!  I'm not sure exactly why, but it started working I messed around in my xorg.conf.

I am also using the i810 driver, but none of the solutions in the thread has worked (I followed the Dapper instructions in the link on a clean 6.06 install).  Any help would be greatly appreciated

```
victor@thinkpad:~$ beryl-manager
victor@thinkpad:~$ XGL Absent, checking for NVIDIA
The program 'emerald' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 656 error_code 8 request_code 153 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

** (beryl-manager:6467): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

---

### Post by Pablasso on 2006-10-07
I tried all that was stated here (dapper), linked modules, reinstalled drivers, ran beryl-xgl, etc. but beryl just doesnt starts

im on inspiron 6000 with intel embedded graphics

---

### Post by cogsprocket on 2006-10-07
*I'm having an odd problem.  On a recent Ubuntu install with an i915 I've installed AIGLX and Beryl.  Beryl runs fine, but when trying to access the logout, restart, switch user screen the whole system locks up.  I can return to metacity and it works just fine, but while Beryl is running no can do.   This is really odd.  Anybody have any idea what might cause this?*

I did several things that may or may not have fixed this problem.  First I've  added build essentials and second I originally used the beryl-project repository as in the Dapper tutorial that Uncle Spellbinder links to in the original post.

```
deb http://ubuntu.beryl-project.org/ dapper main aiglx
```

If this is in fact the culprit then the answer is as has been suggested before; to change the target on the repos Uncle Spellbinder provides:

```

deb http://www.beerorkid.com/compiz dapper main
deb http://media.blutkind.org/xgl/ dapper main
deb http://compiz-mirror.lupine.me.uk/ dapper main
deb http://ubuntu.compiz.net/ dapper main

```

Incidently I used the beerorkid repo as I have in the past with Compiz and CGWD.  If you wind up having the same problem I did make the changes I did and it may fix your problem.

---

### Post by pau on 2006-10-11
Hi,

I am having an odd problem... I followed the guide but my windows don't have borders. This is very annoying. Is there a way to recover the windows' borders?

Have an Intel 855GME and besides that everything works very well... acceleration, very fast etc etc

Thanks

---

### Post by sunny_nwho on 2006-10-11
did u try changing the themes with emerald...even i had the saem problem first abut alter when i changed these it was alright...even I have the same chipset...an i810 on an Acer laptop...Ubuntu on my system rocks with beryl.

---

### Post by ariel on 2006-10-26
My two cents:

I also have an embedded intel graphic card in my laptop. Instead of this howto, I just followed the _very_ simple official beryl howto:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Just three commands, no file editing or anything, not even a reboot. Works really much better than compiz.

---

### Post by hikaricore on 2006-10-28
wow that's ignorant, someone actually erased: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") citing that it should just work out of the box now... *sighs*  good thing i finished reading this yesterday

---

### Post by Pablasso on 2006-10-28
> **hikaricore said:**
> wow that's ignorant, someone actually erased: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") citing that it should just work out of the box now... *sighs*  good thing i finished reading this yesterday

wow.. i was using that guide this morning to set up 2 computers (both intel integrated eww), that was CLOSE, i hope they restore the guide if i have to do it again

---

### Post by Uncle Spellbinder on 2006-10-29
*** ***_[color=#CC0000]UPDATED with most current info, 29-October-2006[/color]_*** ***

As Beryl is now incredibly easy to install, the "official" repos should be followed. Please see below. Enjoy Beryl!

****************************************************************************************************
Edgy, see the official "Howto": [** _[b]How-to install Beryl with AIGLX on Edgy Eft**_[/b]](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft)

Dapper, See the official "Howto": [***_ How-to install Beryl with AIGLX on Dapper_***](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

****************************************************************************************************

---

### Post by learning on 2006-10-29
This worked great for me on my laptop (toshiba A105-S4254).  I have what I am sure is a dumb question, but can't seem to find the answer using google...

How do I make beryl default on start up, instead of logging in and starting it using the terminal?

---

### Post by Pablasso on 2006-10-29
just add it to startup programs on System->Preferences->Sessions

---

### Post by herringbone on 2006-11-02
I'm having some trouble myself, trying to get all of this running on a Dell Optiplex GX270.  Should be an Intel i865G.  Here's my error message from Konsole:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Anyone got ideas?  I am using Kubuntu, and have followed every howto to the letter thus far.

---

### Post by b_umlaut_n on 2006-11-07
I'm using Ubuntu Dapper, and when I try to start using beryl, through beryl-manager, beryl-xgl, or just beryl, my window manager crashes.

First, the windows disappear, then the icons on the desktop. Then, I get a Beryl splashscreen surrounded by gray, then another Beryl splashscreen surrounded by gray, then the second half fades out. Then, my window manager restarts: I see a terminal, then it goes to the login screen.
I know that sounds really weird, but that's what happens.

I've used two different howtos, including the official one, and this always happens. I've tried just about all of the fixes in this thread, other than the ones for Kubuntu. I haven't seen anything with the same problem as me.

When I redirect the output of the beryl to a file (beryl > beryl.log), I get this:

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Initiating splash

And that's all.


Can anyone help me?

---

### Post by hikaricore on 2006-11-07
> **ariel said:**
> My two cents:

I also have an embedded intel graphic card in my laptop. Instead of this howto, I just followed the _very_ simple official beryl howto:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

Just three commands, no file editing or anything, not even a reboot. Works really much better than compiz.

Wow, I did the same thing, and it works.

I was never able to get beryl (or compiz) to work before following that wiki, which is insane since i've tried 6 times (4 since switching to edgy) lol.

Glad i read your post.  :)

---

### Post by acascianelli on 2006-11-10
This Howto worked flawlessly.  Thanks, Linux never looked so good. :)

---

### Post by acascianelli on 2006-11-10
...Amazing, it even works on my IBM T40 laptop with a old Radeon Mobility.

Linux + Beryl > Vista

---

### Post by jude999 on 2006-11-12
Excellent!!!

Just works perfect out of the box, it looks awsome! I love it!

---

### Post by benndamann33 on 2006-11-18
bdg4@BensSweetComputer:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x5b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

The previous errors are encountered when I run beryl(After initializing beryl -manager). It works quite well for the most part(window borders occasionally disappear)...but I am interested as to what the windwos mean. the beryl:water error does indeed prevent me from using the water effects(i.e. rain)

---

### Post by mad_jack on 2006-11-27
> **Uncle Spellbinder said:**
> *** ***_[color=#CC0000]UPDATED with most current info, 29-October-2006[/color]_*** ***

As Beryl is now incredibly easy to install, the "official" repos should be followed. Please see below. Enjoy Beryl!

****************************************************************************************************
Edgy, see the official "Howto": [** _[b]How-to install Beryl with AIGLX on Edgy Eft**_[/b]](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft)

Dapper, See the official "Howto": [***_ How-to install Beryl with AIGLX on Dapper_***](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

****************************************************************************************************

What's happened to the beryl-project.org domain? DNS no longer returns an address!

---

### Post by mad_jack on 2006-11-27
> **mad_jack said:**
> What's happened to the beryl-project.org domain? DNS no longer returns an address!

To answer my own question, in case anyone else is trying to install from the repos etc:

*"Beryl main server is down due to hard drive disk failure - Apologies. SVN can still be reached on [http://svn.gentoo-xeffects.org/beryl/](http://svn.gentoo-xeffects.org/beryl/), Ubuntu repos on [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk)"*

---

### Post by jakev383 on 2006-11-28
> **hikaricore said:**
> Wow, I did the same thing, and it works.

I was never able to get beryl (or compiz) to work before following that wiki, which is insane since i've tried 6 times (4 since switching to edgy) lol.

Glad i read your post.  :)

I just did a new install of Edgy, but the "official how-to" is missing. They say they had a server crash and are slowly putting it back in. Would it be possible to get those magic 3 commands that install it and get it working? 
Thanks in advance!

---

### Post by hikaricore on 2006-11-28
svn timeline is online again: [http://bugs.beryl-project.org/timeline?changeset=on]("http://bugs.beryl-project.org/timeline?changeset=on")

also  Treviño's beryl svn repositories still work just fine: [http://www.ubuntuforums.org/showthread.php?t=279456]("http://www.ubuntuforums.org/showthread.php?t=279456")

:)

---

### Post by ldbooth on 2006-12-11
I am having a total NOOB time with the repository add for AIGLX.
The official HOW-TO for Dapper states:

> Edit the sources.list file:

```
sudo nano /etc/apt/sources.list
```

Add this line:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

Make sure to get the public key for the repository:

```
wget http://beryl-mirror.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```

or (If the above key doesn't work then try the one below)

```
wget http://ubuntu.beryl-project.org/1609B551.gpg -O- | sudo apt-key add -
```

Update the package list and upgrade your system before installing

```
sudo apt-get update
sudo apt-get dist-upgrade
```


My problem is this: when I get to sudo apt-update (everything works up until this step) my command line prompt returns:

> Failed to fetch [http://ubuntu.beryl-project.org/dists/dapper/aiglx/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/dapper/aiglx/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

I copied it in word for word. . . am I supposed to specify a name for public key or something?

---

### Post by hikaricore on 2006-12-11
Did you by any chance install the GPG update recently?  This confused me for awhile and messed up some of my keys.  

So personally I moved the gpg.conf file in my home directory:

*~/.gnupg/gpg.conf*

with a simple:

```

mv ~/.gnupg/gpg.conf ~/.gnupg/gpg.conf2

```

and I can now properly install keys.

> sudo gpg --keyserver subkeys.pgp.net --recv-key 3FF0DB166A7476EA
sudo gpg --fingerprint 3FF0DB166A7476EA
sudo gpg --armor --export  3FF0DB166A7476EA| sudo apt-key add -

should fix the issues with you ubuntu beryl project and any other keys you can't install.


NOTE:  I don't know if this is a secure fix, but based on logic if gpg doesn't have a .conf file it will use default setting.  This is my best guess.  Proceed at your own risk.

---

### Post by serlex on 2006-12-13
getting similar problem as ldbooth

```

Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/Release  Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
anyone with solution?

---

### Post by hikaricore on 2006-12-13
> **serlex said:**
> getting similar problem as ldbooth

```

Failed to fetch http://ubuntu.beryl-project.org/dists/dapper/Release  Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
anyone with solution?

That's a repo issue, you'll just have to probably wait until they resolve whatever got messed up in their repository.

---

### Post by serlex on 2006-12-13
when i do
```
sudo apt-get dist-upgrade
```

i get error saying package
```
libcario2
```
is kept back, cant seem to update libcario2
:(

---

### Post by Pablasso on 2006-12-13
try using aptitude to resolve dependencies, its better than apt-get

---

### Post by serlex on 2006-12-14
hmm tried that, some how it asked to remove all the updates (500mb)!

---

### Post by WishMaster on 2006-12-14
Laptop: Acer TravelMate 661 LCi
Graphic: Intel Corporation 82852/855GM Integrated Graphics Device

runs smoothly !


only need to configure the animations and so...

*edit*
I don't know what happened, But my gnome is broken... I don't see any windowborders !! So I can't close windows, I even can't type in textboxes !
sudo apt-get install gnome brought back my taskbars, but I still don't have windowborders
HELP

*edit2*
Seems I have to choose "Beryl" session at GDM....
Problem 2: in the Beryl-config, I only have "general settings". I used to have other things like "water-effect", wobbly windows, 3D desktp,.... where did they go?

---

### Post by Erzei on 2006-12-24
Hi. i'm announcing, finally, after several months, i got Beryl working on my computer with XFCE4...

:D

Sometimes slower, but not critical... :cool:

My pc is a Intel 4HT 3 GHZ, 512 RAM and the Integrated i915

After like 20 or 30 X-server crashes, i'm happy. Before i followed this howto, i always got a black screen or the X-server dead...

Thanks

:-\"

---

### Post by WishMaster on 2007-01-21
Goddammit...

It happened again: I booted my Ubuntu, and my gnome-panel is gone... So I can't do a thing, because I have no menu to start programs (can't even start a terminal)
wtf is this?

---

### Post by ElChupaLibre on 2007-01-22
the dapper guide works for me until the 

```
   sudo update-alternatives --config Xorg
```

line, 
1. it says, there are no alternatives for Xorg, hm.
2. when starting beryl-manager, it says "no display to manage on 0;0". beryl-manager starts anyway
3. when i select beryl as window-manager in the beryl-manager, there are no window-borders, and no effects whatsoever (probably because of 1. ?)

(another minor prob is, that the "linux-dri-modules" package is not available for the 2.6.15-27-386 kernel, so i needed to fall back to the -26 kernel. already mentioned in the wiki btw)

any help with this? I NEED eye-candy !!!111!!!11111! :biggrin: :biggrin:

---

### Post by neoaddict on 2007-01-23
[http://ubuntuforums.org/attachment.php?attachmentid=16774&d=1159857542](http://ubuntuforums.org/attachment.php?attachmentid=16774&d=1159857542)  How do you screenshot a rotating cube?

---

### Post by DarkN00b on 2007-01-23
> **neoaddict said:**
> [http://ubuntuforums.org/attachment.php?attachmentid=16774&d=1159857542](http://ubuntuforums.org/attachment.php?attachmentid=16774&d=1159857542)  How do you screenshot a rotating cube?

You let go of the ctrl & alt keys and press the Print Screen button. On my laptop I have to press the fn+prtSc buttons. 

Proof: [http://smg.photobucket.com/albums/v191/DarkN00b/Caps/](http://smg.photobucket.com/albums/v191/DarkN00b/Caps/)

All these pics were taken that way.

---

### Post by WishMaster on 2007-01-23
> **WishMaster said:**
> Goddammit...

It happened again: I booted my Ubuntu, and my gnome-panel is gone... So I can't do a thing, because I have no menu to start programs (can't even start a terminal)
wtf is this?
When I boot up, I get a popup after GDM: "couldn't find /usr/bin/startberyl.sh. Falling back to default"
Although is _IS_ there....

So I have no windowborders or panel. I had to place a terminal shortcut on my desktop, so I can type "beryl-manager" and then everything works again.
Very frustrating to do this everytime I log in...

---

### Post by neoaddict on 2007-01-23
OK, thanks.  :D

Um... is there anyone way to get a different wallpaper for each viewport/workspace in Beryl/GNOME?  Really want to make a Borg cube... :-/

---

### Post by dimeotane on 2007-01-28
I have the integrated intel graphics in my dell m1210.  
Beryl was pretty easy to set up and run.  

Video has a bluescreen area showing up when i move the window, change the transparency, or rotate the cube.  Anyone else have this problem, or know how to improve the video so there's no blue area?

---

### Post by DarkN00b on 2007-01-28
> **dimeotane said:**
> I have the integrated intel graphics in my dell m1210.  
Beryl was pretty easy to set up and run.  

Video has a bluescreen area showing up when i move the window, change the transparency, or rotate the cube.  Anyone else have this problem, or know how to improve the video so there's no blue area?

Nope. I can't watch videos at all because the window is blue all the time when Beryl is running. This never happened until recently.

---

### Post by neoaddict on 2007-01-28
Try getting the video player to stream via X11?

Eg for VLC:

vlc --vout x11

---

### Post by DarkN00b on 2007-01-28
> **neoaddict said:**
> Try getting the video player to stream via X11?

Eg for VLC:

vlc --vout x11

That worked great, thanks! It even works while rotating the cube. :guitar:

---

### Post by apatti on 2007-03-30
Hi,

I have followed everything but now whenever i am starting it using beryl-manager i am getting the following error:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Also when I am giving beryl-xgl i am getting following error:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl-xgl: No composite extension


Can any one please help me out!!!!


Ashwin Patti

---

### Post by marcianoskate on 2007-06-30
Hi, I've been using ubuntu for a week now and everything has happend to be pretty easy except for beryl.

First of all, this is what a lspci throws to me
```
00:02.0 VGA compatible controller: Intel Corporation Integrated Graphics Controller (rev 02)

```
And can't figure out if beryl can be configured in this card. I've seen a lot of how-to for making beryl work with nvidia, ati and recently with intel, but intel 810 (or something like that).

Other problems I'm having is understanding the things with repositories and packages, and every time i try to update my sourcelist with any url giving by anyone i get this error

```

W: Failed to fetch http://media.blutkind.org/xgl/pool/main/b/beryl-manager/beryl-manager_0.1.1-0ubuntu2_i386.deb
  404 Not Found

W: Failed to fetch http://media.blutkind.org/xgl/pool/main/b/beryl-core/beryl_0.1.1-0ubuntu1_i386.deb
  404 Not Found

W: Failed to fetch http://media.blutkind.org/xgl/pool/main/b/beryl-dbus/beryl-dbus_0.1.1-0ubuntu1_i386.deb
  404 Not Found

W: Failed to fetch http://media.blutkind.org/xgl/pool/main/b/beryl-core/beryl-dev_0.1.1-0ubuntu1_i386.deb
  404 Not Found
```

At this point I wonder if is something I've made wrong or is my source list?

Finally, i manage to install beryl, I mean, an Applications > System Tools > Beryl/Beryl Manager icon has appear, but when i clicked on it my windows become black and after a few seconds I have to re-login and all my stuffs were closed.

Any advice is wellcome.

Thank you for you patience and sorry for my english ;).

---

### Post by justin1278 on 2007-06-30
I have an intel embaedded graphics card in my notebook and beryl runs fine, what Intel graphics chip do you have?

---

### Post by marcianoskate on 2007-07-01
> **justin1278 said:**
> I have an intel embaedded graphics card in my notebook and beryl runs fine, what Intel graphics chip do you have?

How can i see that ... i did an lspci and is showed above.

---

### Post by sunshine12 on 2007-07-19
I have installed beryl, but how to start it..??

I started "applications-system tools-beryl setting manager" but nothing is happening.
also there is no system tray icon

I have intel graphic card, don't know that will run beryl or not..

CARD DETAIL

```
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
```

If somebody can please tell if this will run beryl or not and if yes then how to activate it??

thanks

---

