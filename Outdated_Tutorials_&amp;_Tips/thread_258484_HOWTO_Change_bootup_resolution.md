---
title: "HOWTO: Change bootup resolution"
date: 2006-09-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Indras on 2006-09-16
I've seen a few questions about this on the forums, so I've decided to write a full-fledged tutorial on how to set this up in Ubuntu.  This will show you how to change your screen's resolution while booting, during usplash, and at any time one one of the text consoles (by pressing CTRL+ALT+F1 through F6).  I'll try to make this as friendly as possible for newbies, and I'll make sure to explain all acronyms and abbreviations at least once.

[SIZE=4]Explanation:[/SIZE]  (feel free to skip this section, it is only for educational purposes)

Your computer system boots up in multiple stages, each one using the video card and monitor in its own way.  This is important to know when tracking down resolution problems.

First, your computer's BIOS (Basic Input-Output System) detects and powers up your video card during POST (the Power On Self Test) and uses it to display all of its relevant information, such as the memory check, a list of devices, and so on.  Some motherboards will simply display a full-screen logo, particularly branded PCs, like Hewlett Packard and Compaq.  You may have to press the spacebar or escape key to see what's going on behind the logo.  Each PC is different, so consult your vendor's support site, your computer's manual, or, if all else fails, google.com.

The BIOS generally chooses a generic resolution that will work on nearly any video card and monitor, like 640x480x8, so as to not have an error message that the user is unable to read.  I've only seen a couple computers where this resolution could be configured, as it's not a high priority option.

Then, your bootloader starts, using the resolution already in place.  This may be ntldr, on Windows NT/2000/XP systems, darwin on macintosh systems, or Lilo/Grub on Linux systems.  Ubuntu Dapper defaults with a basic plaintext grub.  See the gfxboot grub tutorial here on ubuntuforums if you'd like to use the graphical grub that Suse has: [http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)  However, I'm going to assume you're using default options from here on.

After you choose your operating system and kernel in grub, or it automatically defaults to the first option if you do not press a key during the 3 second countdown, it fires up the kernel and passes it bootup parameters.  There are many different parameters you can send to the kernel before bootup, such as 'single', for single-user mode.

The kernel uses it's own video card driver.  In Ubuntu, it uses the basic vesafb driver, short for vesa framebuffer.  This is a simple, generic, non-accelerated driver, which is optimal for compatibility.  Once again, the point is to never have something bad happen and an error message displayed on the screen that the user cannot see.  There are still users out there whose monitors cannot display above 800x600, and if your kernel tried to run the vesafb at a resolution higher than this, those users would be alienated.

If grub does not pass a vga parameter to the kernel, it assumes vga=normal, which is 640x480 resolution.  From then on, everything running will be at that basic vga resolution, except for the xserver.  First, your usplash screen displays, while all other services are starting.  This is the screen with an orange Ubuntu logo at the top of the screen and a list of processes starting up in the bottom half.  There's also a howto on the forums for changing the colors of the usplash screen, located here: [http://www.ubuntuforums.org/showthread.php?t=82835](http://www.ubuntuforums.org/showthread.php?t=82835).

Near the end of the bootup sequence, it starts up six consoles, using the getty program, and then the xserver.  The first six consoles can be accessed any time by pressing CTRL+ALT+F(x) where x is the number of the console.  The xserver then binds itself to F7, the next available number.  Try it now if you feel like, by holding CTRL and ALT and go through F1 through F7.

The consoles always use the vesafb driver to display, so they are at the same resolution that was passed to your kernel from grub.  The xserver uses its own driver and resolution, defined by /etc/X11/xorg.conf, and then Gnome, KDE, or XFCE run on top of it.  I won't go into detail here on how they work.

[SIZE=4]End explanation section[/SIZE]

Okay, if you jumped ahead, here's where you should start paying attention.  First, I'm going to give you the vesafb modes table.  This was taken from [http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html), so feel free to go there for more information.

[SIZE="4"]The Table[HTML]Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?[/HTML][/SIZE]
(I apologize for the way this table looks, it's the only way I could get the columns to line up)

So first, choose which resolution you'd like to run your consoles and usplash in from the chart above.

Now, open your menu.lst file:
```
sudo nano /boot/grub/menu.lst
``` 

And find the entry you normally use to boot with and go to the line that begins with "kernel", it should say something like this:
```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
``` 

Add a "vga=" option to the end of the line, and put in the code from the table above.  So if you want 1024x768 at 16 bit color at command line, add "vga=0x317" to the end of your kernel parameters.  This is the option I like to use most.  You also can use the decimal equivalent, since 0x317 is in hex.  The decimal equivalent is 791, so you'd use "vga=791" instead.

Now, save the file, and it will take effect when you restart.

Note: Normally, when you upgrade your kernel or run grub-reconfigure, it will remove this option and set it back to defaults. In order to make this change permanent, go up a couple lines to one that looks like this:
```
# defoptions=quiet splash
``` 
(yes, it's commented out, but grub-reconfigure looks for this (and other) commented-out options when rebuilding your grub menu)

And add the same vga= option to the end of that as well, and it will make this new resolution permanent, even after new kernels are installed.

Another ubuntuforums member, Herman, made a very important suggestion: you can make modifications to your grub boot sequence for a single boot by editing grub before you boot.  Since it does not alter Grub's menu.lst file, the change isn't permanent.  When grub first boots up, at the GUI menu, select an option you want to modify and press the 'e' key.  This will bring up the full list of commands from the menu.lst file that grub uses to boot that particular option.  From there, you can go to your kernel line and add the vga option there, just like in my instructions above, and it will boot Ubuntu a single time with a different vesafb resolution.

As a bonus, here's some extra tidbits, some of it useless knowledge, for your perusal:

[LIST]
[*]For the mathematically challenged, there is a hex to decimal converter in Ubuntu.  Go to Applications->Accessories->Calculator.  From there, go to View->Scientific.  Right under the display screen is a button for Hex.  Press it and type the code from the table above (like 31C) and press the Dec button.

[*]When booting from the LiveCD, you can change this option as well, but you have to do it while still at the graphical grub menu.  When the CD boots and shows the Ubuntu logo with a 30 second timeout, press the escape key.  A box will come up warning you about going to the text-based grub interface.  Just press enter.  This will drop you to a boot: prompt.  Type "live vga=791", or whatever your desired resolution is, and then the liveCD will boot its kernel at this resolution.  Note that this is temporary for one boot only.

[*]You can set "vga=ask" in your menu.lst file to force the kernel to ask you what resolution you prefer each time, but you will choose from a rather small list of options.  You can type "scan" to have it check your hardware to see which modes it is capable of, but this is mainly for compatibility issues, and it won't give you as complete of a list as above, and you cannot type in 791, or 0x317 here, only a number from 0 to 9 from the list it gives you.
[/LIST]
If you see any incorrect information here in this tutorial, or you have something notable to add, please reply below and I'll try my best to make the changes in good time.  I do my best to visit the forums daily, so hopefully I'll catch it quickly.

Also, if you're looking for some very well written, illustrated information on using grub to its fullest, please visit Herman's website on grub here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Indras on 2006-09-21
Just a quick little update... here's the full table in easy to read (and easy to remember) decimal format.

[SIZE="4"][html]Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?[/html][/SIZE]

I've also seen questions from people wanting widescreen resolutions.  I'm sorry, but it seems that vesafb doesn't support any resolution not in the table above.

---

### Post by ethan@xmlstandards.org on 2006-09-25
Thanks so much for this post.

I have used all of the features you mentioned to great benefit.

Much appreciated.

Ethan Cane
Web Developer

---

### Post by pejcao on 2006-09-29
same 4 edgy?

---

### Post by DonnieP on 2006-10-18
This works for me in edgy, but just a note that the 1152x864 resolution doesn't seem to be recognized.  It gives an error message and presents the limited 1-9 menu listed in the explanation above.

---

### Post by meimato on 2006-10-31
I've always used this nice feature, but now in Edgy it doesn't seem to work: the boot screen appears not centered on the screen, but rather in the top left corner.

---

### Post by livinginx on 2006-10-31
Nice info, but I am trying to figure out for the default login screen.

---

### Post by Kerry Lange on 2006-10-31
Sorry, re-read the thread and saw anything other than what's in the table is not supported.

What do I need to use if I'm trying to achieve 1900 x 1200 at 24 or 32 bit?

---

### Post by techstop on 2006-10-31
> **meimato said:**
> I've always used this nice feature, but now in Edgy it doesn't seem to work: the boot screen appears not centered on the screen, but rather in the top left corner.

I've only just found the feature, and yes, the boot screen is not centred. Anyone know how to fix this? BTW,tty1-6 is awesome at high res, thanks for the pointer!

---

### Post by dizzie on 2006-11-01
If only 1280x800 was supported...

---

### Post by sg.forums on 2006-11-14
> **dizzie said:**
> If only 1280x800 was supported...

Does this mean that I would never be able to install ubuntu on my 1280x800 screen laptop ?
Which part of the software don't support this resolution the xorg server ?
Where can we get more info about 1280x800 support ?

---

### Post by davro on 2006-11-14
Whats the vga setting for a laptop screen resolution 1400x1050
with a dual screen of running 1280x1024 of a docking station.

---

### Post by techstop on 2006-11-14
> **sg.forums said:**
> Does this mean that I would never be able to install ubuntu on my 1280x800 screen laptop ?

No, of course not. This thread is a howto for a mod to change the "Bootup resolution". ie. the splash screen with the progress bar you see before x starts. 1280 x 800 is not supported *for this mod*, but of course is supported for xorg or whatever.

---

### Post by samoht on 2006-11-22
To change your framebuffer to something like 1280x800 append "vga=0x368" to your kerneloptions. This looks better then "791" or similar but breaks the  centered position of usplash!

---

### Post by sniffass on 2006-11-25
hi this was a great and very very informative and well-written post. Thank you very much.
Now I just want to find out how to get coloured fonts in the console, so that files/folders appear differently. Like on the gentoo/knoppix live cds.

---

### Post by jdarias on 2006-12-17
About this subject i would like to ask,
Is it possible to set up a background image for the virtual consoles like  SUSE does?

I mean, when i hit CTRL-ALT-F1 in suse, i get the console with a background image wich has the suse logo on top, and a sort of shading in it. 
In ubuntu it's just black. Can it be changed?

---

### Post by emarkay on 2006-12-18
I get:
"You passed an undefined mode",  and it tells me that I have just a VESA VGA, and lists all the modes when requested, but then does not go "graphical" until the booting is finished.

The modes it lists are all DOS modes - 80X25, 132x60, 80x43, etc...

 BTW have an Intel 82810E DC-133 on board graphics controller.  :(

(Having other probs with it - posts elsewhere- , but I want to see if I can get this one solved here...)

Thanks

---

### Post by cevans on 2006-12-19
> **samoht said:**
> To change your framebuffer to something like 1280x800 append "vga=0x368" to your kerneloptions. This looks better then "791" or similar but breaks the  centered position of usplash!
I am rather certain that doing so doesn't work at all in Ubuntu. I also know that there **are** modelines that work for 1400x1050, but I don't remember them right now.

---

### Post by jpmorelli on 2006-12-21
I have found a very interesting tool in this forum, Startup-manager. You can set all the options in the grub and usplash image.
[http://www.ubuntuforums.org/showthread.php?t=295524]("http://www.ubuntuforums.org/showthread.php?t=295524")

Works great ! Installs into the Administration menu.

---

### Post by cypr3ss on 2007-01-25
> **cevans said:**
> I am rather certain that doing so doesn't work at all in Ubuntu. I also know that there **are** modelines that work for 1400x1050, but I don't remember them right now.

Hi,

Was searching for the 1400x1050 settings also, because setting grub to 1280x1024 (image size) didn't display correctly, and came across this post on the gentoo forum: [http://forums.gentoo.org/viewtopic-t-333300.html](http://forums.gentoo.org/viewtopic-t-333300.html)

Where it lists the respective codes for 1400x1050 vga are 834 (16 bit), 835 (24 bit) and 836 (32 bit).   I'm using 835 and it's working great (IBM t43 and grub).

Regards,

Cypr3ss.

---

### Post by wh0rd on 2007-01-27
I've got a Sony SDM-HS95 with 1280x1040, but it's weird and has a different refresh rate from any other LCD with 1280x1040. The refresh rates are:
        HorizSync    28.0 - 80.0
        VertRefresh  48.0 - 75.0

So when I use the 795 decimal value for grub the monitor just shows a warning message. I also had trouble during installation unless I lowered the resolution. Does anyone know how to get the vga= values for those specific sepcs?

---

### Post by reacocard on 2007-01-27
For those who have resolutions not in the table, fear not, they may be available. To get them, first install hwinfo
```
sudo apt-get install hwinfo
```
now run 
```
sudo hwinfo --framebuffer | grep 'Mode '
```
it'll spew out a bunch of lines like this: (Your numbers may be different)
```
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
...
```

Just use the Mode number you want after vga=. So, if you wanted 1280x800 and 24-bit color, you would use "vga=0x0362".

---

### Post by wh0rd on 2007-01-27
> **reacocard said:**
> For those who have resolutions not in the table, fear not, they may be available. To get them, first install hwinfo
```
sudo apt-get install hwinfo
```
now run 
```
sudo hwinfo --framebuffer | grep 'Mode '
```
it'll spew out a bunch of lines like this: (Your numbers may be different)
```
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
...
```

Just use the Mode number you want after vga=. So, if you wanted 1280x800 and 24-bit color, you would use "vga=0x0362".

It actually gives me the same values posted in the beginning of the thread.

---

### Post by reacocard on 2007-01-27
> **wh0rd said:**
> It actually gives me the same values posted in the beginning of the thread.

Then those are the only modes your framebuffer supports. My tip is more applicable to those with widescreens, whose resolutions aren't part of the vesa spec.

---

### Post by coolen on 2007-01-28
Hey, Edgy user here.
I'm having a problem with my usplash. It's not serious, just a little annoying.
When I first installed Edgy, both my startup and shutdown screens displayed at too high a resolution. My monitor displayed them both, but had this irritating box saying "Input Not Supported".
I fixed my shutdown usplash by editing /etc/usplash.conf (a file, might I add, that is needlessly complex :P), and I changed my startup resolution in the same way mentioned here, however according to this post, it should be displaying at a low resolution, which it's not, and that resolution should be used for my virtual consoles, which, again, it is not. My virtual consoles look about 800x600.
Also, I'm getting the off-center issue when using this fix. Does anyone know how to change the resolution of the splash image, or even just its position on the screen?

---

### Post by Mr. Eddy on 2007-02-04
@coolen You should start a new thread for that

---

### Post by CheeseEatingBulldog on 2007-02-05
I still can't get any resolution to work except for the default 680x480 (which uses only the center part of my laptop screen), no matter what vesa value I fill in (all give unsupported mode). X boots nicely into 1024x768 but console and startup remain in 680x480.

I have read that one needs to enable framebuffering for the i810 (built in 4mb card), but have no idea how to do that (do I need to compile my own kernel?).

(before people start posting links to things like i810fb, I looked and don't understand where what needs to be changed, let alone compiling a kernel with bits and pieces (or do I need to patch it?)) I am not useless at linux, but on this part I have no idea.

---

### Post by gliderman on 2007-03-22
I was able to change my bootup resolution to 1280x1024 but how do I change the refresh rate of the bootup resolution from 60Hz to 75Hz?

---

### Post by jonas.p on 2007-03-25
I'm using a 1600x1200 resolution.

hwinfo gives me a maximal resolution of 1280x1024.
Thats also the highest resolution i can use usplash with.

Can anybody tell me what exactly hinders me from using a higher resolution?

Jonas

---

### Post by vstoykov on 2007-05-02
> **Indras said:**
> Just a quick little update... here's the full table in easy to read (and easy to remember) decimal format.

[SIZE="4"][html]Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?[/html][/SIZE]

I've also seen questions from people wanting widescreen resolutions.  I'm sorry, but it seems that vesafb doesn't support any resolution not in the table above.


There is a error. Mode 640x480@16b is 785.

This is script to convert table (only nubmers):

[SIZE="4"][html]
#!/bin/bash 

while read LN ; do
NEWLN=`echo $LN | sed s/?/0/`
for NUMB in $NEWLN ; do
let x=0 ; let x=$NUMB 2>/dev/null
echo -ne "\t$x"
done

echo -ne "\n"

done
[/html][/SIZE]

Usage example:
[SIZE="4"][html]
valentin@darkstar:~/lab$ cat tbl1
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?         ?

valentin@darkstar:~/lab$ cat tbl1  | convert_hex_table_to_dec.bash
        0       0       0       0       0       0       0       0
        0
        4       0       0       0       0       770     0       0       0       0
        8       0       0       768     769     771     773     353     775     796
        15      0       0       0       784     787     790     354     793     797
        16      0       0       0       785     788     791     355     794     798
        24      0       0       0       786     789     792     0       795     799
        32      0       0       0       0       0       0       356     0       0

valentin@darkstar:~/lab$    

valentin@darkstar:~/lab$ cat tbl2
Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
 4bits      ?       ?     0x302      ?        ?        ?         ?
 8bits    0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15bits      ?     0x310   0x313    0x316    0x162    0x319     0x31D
16bits      ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24bits      ?     0x312   0x315    0x318      ?      0x31B     0x31F
32bits      ?       ?       ?        ?      0x164      ?         ?

valentin@darkstar:~/lab$ cat tbl2  | convert_hex_table_to_dec.bash
        0       0       0       0       0       0       0       0
        0       0       0       770     0       0       0       0
        0       768     769     771     773     353     775     796
        0       0       784     787     790     354     793     797
        0       0       785     788     791     355     794     798
        0       0       786     789     792     0       795     799
        0       0       0       0       0       356     0       0

valentin@darkstar:~/lab$     
[/html][/SIZE]

The result is:
[html]
 Colours  640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
 ----------------------------------------------------------------------
  4 bits     -       -      770       -        -        -         -
  8 bits    768     769     771      773      353      775       796
 15 bits     -      784     787      790      354      793       797
 16 bits     -      785     788      791      355      794       798
 24 bits     -      786     789      792       -       795       799
 32 bits     -       -       -        -       356       -         -
[/html]

---

### Post by xi_Slick_ix on 2007-05-04
Probably a waste of time but i'm assuming 1440 x 900 is not supported?

---

### Post by reacocard on 2007-05-04
> **xi_Slick_ix said:**
> Probably a waste of time but i'm assuming 1440 x 900 is not supported?

Not officially, but if you use [my hwinfo hack]("http://ubuntuforums.org/showpost.php?p=2071872&postcount=22"), you may be able to use it anyway. If hwinfo fails to work, then your hardware simply can't do it, period.

---

### Post by Tacklebox on 2007-06-28
Thanks so much for this guide. I've been trying to get my installation of Ubuntu to work for a while now, and this has let it work. Whenever I would try to run the liveCD, the only way I could run it was to change the resolution setting on there from VGA to my monitor's native resolution, and I had always thought that if I could change the boot resolution, then that would solve the problem. Apparently, I was correct.

My video card is X800 XL, in case that helps anything.:o


Thanks again, 

Tacklebox
:D

---

### Post by chrisrhode on 2007-07-05
This guide is awesome!! Thank you sooooo much!! ;D ;D ;D

---

### Post by zefram on 2007-07-06
Really good and helpful, thanks!

---

### Post by GriffiN on 2007-07-07
how does one center the image while it loads?
cause as someone said before... its a bit off centered.. to the left and up...
set vga=795 which is supported... but off centered... any info on this?

---

### Post by reacocard on 2007-07-07
> **GriffiN said:**
> how does one center the image while it loads?
cause as someone said before... its a bit off centered.. to the left and up...
set vga=795 which is supported... but off centered... any info on this?

No idea, it does the same thing to me, I think it's just a bug in usplash (I should report that sometime...)

---

### Post by Rohen on 2007-07-20
HI!  I really appreciate you taking the time to post this.  This really helps me out.  I'm gonna try it now and I'll let you know if I have any further problems.

THANKS!:biggrin:

---

### Post by podfish on 2007-08-05
> **reacocard said:**
> No idea, it does the same thing to me, I think it's just a bug in usplash (I should report that sometime...)

It's not a bug in usplash; it's the image itself.  If you're setting up a 1280x1024 framebuffer, you can't expect a 1024x768 image to fill the screen.  There should be 1280x1024 usplash themes out there.

---

### Post by reacocard on 2007-08-05
> **podfish said:**
> It's not a bug in usplash; it's the image itself.  If you're setting up a 1280x1024 framebuffer, you can't expect a 1024x768 image to fill the screen.  There should be 1280x1024 usplash themes out there.

I didn't mean it should stretch, just center itself. I know the resolution is harcoded into the themes (why?), but if the framebuffer is bigger than the selected usplash resolution, usplash should center itself onscreen so that it looks better. This also fixes the issue of widescreen themes quite nicely, since you can simply use a normal one and have it only take up the center part of the screen.

---

### Post by falcon1620 on 2007-08-25
Doesn't work for my G3 still get freq out of range issue during boot, used 
lilve vga=716 
live-powerpc vga=716
and a whole bunch of others... Cant get it to boot at  all off of the CD I wait to try an invoke a console and no dice....PPC users need to adjust resolutions too, this really is an issue that needs a better fix. Anyone have any idea on how to FORCE ppc version to invoke a lower res/refresh rate. Using the CRT that came with the G3 at the time... If i cant get this Ill have to use FreeBSD on this thing, os X dosnt offer what I want even with server...

Yes I did try another monitor! No it didn't work!

---

### Post by falcon1620 on 2007-08-25
When all else fails try try again! I got it YEA!!! apparently I had chubby digits when I typed in 
boot: live-powerpc video=ofonly
in the boot prompt, did it again and it finally worked, try this if your having issues with PPC installs. Ill have to do a manual x.org configuration but I can do that if i can see it! :lolflag:

---

### Post by skullmunky on 2007-09-05
Re: hwinfo hack for widescreen

i have an apple HD display; configuring X using a different monitor first, it's recognized and displays at full 1920x1200.  it needs, apparently, either that, or 1280x800, or 1024x640.  hwinfo doesn't show me any of these, just the usual old non-widescreen res's...  this is an nvidia quadrofx; does this mean it only makes those rezs available to the binary nvidia driver, and not to nv or vesafb?

is there a way to make the kernel use nvidia instead of vesa?  the idea of vesa as a failsafe isn't useful anymore for me since it always just gives a black screen during boot or in text mode :)

---

### Post by reacocard on 2007-09-06
> **skullmunky said:**
> Re: hwinfo hack for widescreen

i have an apple HD display; configuring X using a different monitor first, it's recognized and displays at full 1920x1200.  it needs, apparently, either that, or 1280x800, or 1024x640.  hwinfo doesn't show me any of these, just the usual old non-widescreen res's...  this is an nvidia quadrofx; does this mean it only makes those rezs available to the binary nvidia driver, and not to nv or vesafb?

is there a way to make the kernel use nvidia instead of vesa?  the idea of vesa as a failsafe isn't useful anymore for me since it always just gives a black screen during boot or in text mode :)

this trick affects the framebuffer ONLY, nothing to do with nv/vesa/etc. If hwinfo doens't give you the res you want, then AFAIK, no it is not possible to get it.

---

### Post by barb3tta on 2007-10-01
Hi all,
I noticed that if I change the resolution on livecd boot screen, the Xserver changes the resolution accordingly.
Do you know how livecd do that? We're trying to to make a small ubuntu version to use in the car, but using reconstructor, we cannot get the right X resolution. Maybe we wiped the package that do the resolution change... Do you know what's its name?

thanks in advance

---

### Post by goonies on 2007-10-04
**walks out of this thread with his head down and 1680x1050 resolution in right hand.*

:(

---

### Post by Octagonal on 2007-10-04
Thanks for this great post and the additional info from wh0rd.

Added the vga number to the menu.lst file
after determining the correct number from hwinfo
I was able to get 1680x1050 resolution perfectly.

kernel          /boot/vmlinuz-2.6.20-16-generic root<bleh> ro quiet splash vga=872

---

### Post by Dark_X on 2007-10-17
This isn't working for me in gutsy.  I have been trying to get the resolution lower so my monitor can display it but even at 640x480 it won't display.

---

### Post by OmeuNOME on 2007-10-18
> **Dark_X said:**
> This isn't working for me in gutsy.  I have been trying to get the resolution lower so my monitor can display it but even at 640x480 it won't display.

same here :(

my gutsy just don't show usplash on boot, but in beta version it works.
to appear in shutdown i go to usplash.conf and change de resolution, but don't work in boot.

---

### Post by mustardman on 2007-10-19
I'm having same or similar problem on released version of Gutsy (7.10).  I have a 1024x768 LCD that won't show above that which may be related?

Boot up it says out of range but once it get's to log in screen it's ok.  PC is only a couple months old, onboard Nvidia 6150GPU using 128MB RAM.  Never had this problem in Feisty.

---

### Post by Octagonal on 2007-10-19
Bootup resolution wouldn't work for me either after upgrading to Gutsy.

The bug has been posted here along w/ some work arounds: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

The following worked for me to get my bootup res back to 1680x1050.
vga=872


>  
1. sudo vi /etc/initramfs-tools/modules and add fbcon and vesafb

so my /etc/initramfs-tools/modules looks like:

fbcon
vesafb

2. sudo update-initramfs -u

3. sudo vi /etc/modprobe.d/blacklist-framebuffer

change the line "blacklist vesafb" to "# blacklist vesafb"

4. reboot and everything is fine


---

### Post by shimoda on 2007-11-03
thanks a lot... It worked for me :)

---

### Post by namanbagga on 2007-11-06
[This]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") is the proper way to do it-
:lolflag:

---

### Post by halabb on 2007-11-17
Your screen being 'off centered' is probably due to the refresh rate being @ 60Hz. Assuming you're using a CRT.

---

### Post by Angus77 on 2008-01-06
My monitor supports 1680x1050, so I tried setting vga=872 as Octagonal suggested, but usplash ends up displaying the same as if vga=791 --- meaning the image is stretched.

I did as reacocard [suggested]("http://http://ubuntuforums.org/showpost.php?p=2071872&postcount=22") and ran
```
sudo hwinfo --framebuffer | grep 'Mode '
```
which gave me
 ```
Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0310: 640x480 (+1280), 16 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 32 bits
  Mode 0x0313: 800x600 (+1600), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 32 bits
  Mode 0x0316: 1024x768 (+2048), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 32 bits
  Mode 0x0319: 1280x1024 (+2560), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 32 bits
  Mode 0x030d: 320x200 (+640), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 32 bits
  Mode 0x0320: 320x200 (+1280), 32 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0394: 320x240 (+640), 16 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 32 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b4: 512x384 (+1024), 16 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 32 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c4: 640x350 (+1280), 16 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 32 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 32 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0334: 720x400 (+1472), 16 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 32 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0354: 1152x864 (+2304), 16 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 32 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0364: 1280x1024 (+2560), 16 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 32 bits
  Mode 0x0321: 640x480 (+2560), 32 bits
  Mode 0x0322: 800x600 (+3200), 32 bits
  Mode 0x0323: 1024x768 (+4096), 32 bits
  Mode 0x0324: 1280x1024 (+5120), 32 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0344: 1400x1050 (+2816), 16 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 32 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0374: 1600x1200 (+3200), 16 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 32 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 32 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d4: 1856x1392 (+3712), 16 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 32 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e4: 1920x1440 (+3840), 16 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 32 bits
```
No 1680x1050 in there!  Despite the fact that Gutsy runs in 1680x1050 as soon as I get to the login screen.  And I'm pretty sure my monitor (Samsung Syncmaster 206BW) doesn't actually support 1920x1440 (which would be the wrong aspect ratio anyways. I think all of the Modes listed above are the wrong ratio!).

---

### Post by reacocard on 2008-01-06
> **Angus77 said:**
> My monitor supports 1680x1050, so I tried setting vga=872 as Octagonal suggested, but usplash ends up displaying the same as if vga=791 --- meaning the image is stretched.

I did as reacocard [suggested]("http://http://ubuntuforums.org/showpost.php?p=2071872&postcount=22") and ran
```
sudo hwinfo --framebuffer | grep 'Mode '
```
which gave me
 ```
Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0310: 640x480 (+1280), 16 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 32 bits
  Mode 0x0313: 800x600 (+1600), 16 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 32 bits
  Mode 0x0316: 1024x768 (+2048), 16 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 32 bits
  Mode 0x0319: 1280x1024 (+2560), 16 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 32 bits
  Mode 0x030d: 320x200 (+640), 16 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 32 bits
  Mode 0x0320: 320x200 (+1280), 32 bits
  Mode 0x0393: 320x240 (+320), 8 bits
  Mode 0x0394: 320x240 (+640), 16 bits
  Mode 0x0395: 320x240 (+640), 16 bits
  Mode 0x0396: 320x240 (+1280), 32 bits
  Mode 0x03b3: 512x384 (+512), 8 bits
  Mode 0x03b4: 512x384 (+1024), 16 bits
  Mode 0x03b5: 512x384 (+1024), 16 bits
  Mode 0x03b6: 512x384 (+2048), 32 bits
  Mode 0x03c3: 640x350 (+640), 8 bits
  Mode 0x03c4: 640x350 (+1280), 16 bits
  Mode 0x03c5: 640x350 (+1280), 16 bits
  Mode 0x03c6: 640x350 (+2560), 32 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 32 bits
  Mode 0x0333: 720x400 (+768), 8 bits
  Mode 0x0334: 720x400 (+1472), 16 bits
  Mode 0x0335: 720x400 (+1472), 16 bits
  Mode 0x0336: 720x400 (+2944), 32 bits
  Mode 0x0353: 1152x864 (+1152), 8 bits
  Mode 0x0354: 1152x864 (+2304), 16 bits
  Mode 0x0355: 1152x864 (+2304), 16 bits
  Mode 0x0356: 1152x864 (+4608), 32 bits
  Mode 0x0363: 1280x1024 (+1280), 8 bits
  Mode 0x0364: 1280x1024 (+2560), 16 bits
  Mode 0x0365: 1280x1024 (+2560), 16 bits
  Mode 0x0366: 1280x1024 (+5120), 32 bits
  Mode 0x0321: 640x480 (+2560), 32 bits
  Mode 0x0322: 800x600 (+3200), 32 bits
  Mode 0x0323: 1024x768 (+4096), 32 bits
  Mode 0x0324: 1280x1024 (+5120), 32 bits
  Mode 0x0343: 1400x1050 (+1408), 8 bits
  Mode 0x0344: 1400x1050 (+2816), 16 bits
  Mode 0x0345: 1400x1050 (+2816), 16 bits
  Mode 0x0346: 1400x1050 (+5632), 32 bits
  Mode 0x0373: 1600x1200 (+1600), 8 bits
  Mode 0x0374: 1600x1200 (+3200), 16 bits
  Mode 0x0375: 1600x1200 (+3200), 16 bits
  Mode 0x0376: 1600x1200 (+6400), 32 bits
  Mode 0x0383: 640x400 (+640), 8 bits
  Mode 0x0384: 640x400 (+1280), 16 bits
  Mode 0x0385: 640x400 (+1280), 16 bits
  Mode 0x0386: 640x400 (+2560), 32 bits
  Mode 0x03d3: 1856x1392 (+1856), 8 bits
  Mode 0x03d4: 1856x1392 (+3712), 16 bits
  Mode 0x03d5: 1856x1392 (+3712), 16 bits
  Mode 0x03d6: 1856x1392 (+7424), 32 bits
  Mode 0x03e3: 1920x1440 (+1920), 8 bits
  Mode 0x03e4: 1920x1440 (+3840), 16 bits
  Mode 0x03e5: 1920x1440 (+3840), 16 bits
  Mode 0x03e6: 1920x1440 (+7680), 32 bits
```
No 1680x1050 in there!  Despite the fact that Gutsy runs in 1680x1050 as soon as I get to the login screen.  And I'm pretty sure my monitor (Samsung Syncmaster 206BW) doesn't actually support 1920x1440 (which would be the wrong aspect ratio anyways. I think all of the Modes listed above are the wrong ratio!).

what xorg supports and what the framebuffer supports are completely different things. I'm sorry to say that in your case it seems that your framebuffer simply doesn't support your monitor's native resolution. You'll just have to choose the closest mode to what you want and live with the stretching.

---

### Post by Angus77 on 2008-01-07
Oh, well...

---

### Post by sevenearths on 2008-03-17
I thought I would just throw in my two cents into this issue...

I haven't ever had a boot up screen in Gutsy and my machine and used to take 3 to 4 minutes to boot :( So I had a look round uesterday and combined a couple of threads to get it working. This is what I did on a Toshiba laptop with a ATI mobile graphics card just to get it to display a simple 800x600 boot screen (I presume most monitors should display that).

1.Type the following into a terminal```
sudo gedit /boot/grub/menu.lst
```

2. Find the following line ```
# defoptions=quiet splash
```

or```
# defoptions=quiet splash vga=<something>
```

3. Replace the line with ```
# defoptions=quiet splash vga=791
```

(791 = 800x600 16bit)

(a full chart can be found [here]("http://ubuntuforums.org/showthread.php?t=258484&highlight=vga%253D791+usplash"))

4. Then look for something like this in the same file:

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4d529b74-7274-4f41-85fd-0ecca4d1265f ro quiet splash vga=<something>
initrd		/boot/initrd.img-2.6.22-14-generic
```

and again replace the ```
vga=<something>
```
with ```
vga=791
```

5. Save and quit the file

6. type the following in to a terminal ```
sudo gedit /etc/X11/xorg.conf
```

7.look for the section starting ```
Section "Screen"
```

8. Find where it says ```
Modes		"1280x800"	"1280x768"
```

(remember that this line is different for each machine based on the size of the screen and what graphics card you have)

9. Change the line so it has '800x600' on the end of it ```
Modes		"1280x800"	"1280x768"	"800x600"
```

10. Exit and save the file.

11.Type the following into a terminal ```
sudo gedit /etc/usplash.conf
```

12. Change the text in the file to lokk like this ```
# Usplash configuration file
xres=800
yres=600
```

13. Save and exit

14. Reboot

After I did this I had no boot problems and now my boot time is down from 3-4 mins to 15-30sec... Sweet!!!:)

---

### Post by markonhismobile on 2008-03-17
Excellent HOWTO, I bookmarked this as I'm forever trying to do this but always lose the table with the mode numbers in!
I originally used this to get a 1024*768 res screen working for an old laptop that I had installed with a basic LAMP setup. It was fantastic working on a CLI with nice sharp text and Midnight Commander was great with the extra screen real estate!

---

### Post by jdarias on 2008-05-03
Does this work in hardy?

---

### Post by scorp123 on 2008-05-04
> **jdarias said:**
> Does this work in hardy? Yes. I tested it with the one laptop I installed with Ubuntu 8.04 "Hardy" (fresh install). What I'd recommend is you follow the instructions in these two postings:

First, do as Octagonal says in posting #51 - His posting will help you get the framebuffer back to work:
[http://ubuntuforums.org/showpost.php?p=3573289&postcount=51](http://ubuntuforums.org/showpost.php?p=3573289&postcount=51)

Then follow the link Namanbagga gives in posting #53 - His posting will fix the splash screen during boot and shutdown (just do the 3 steps there he mentions on his blog):
[http://ubuntuforums.org/showpost.php?p=3715308&postcount=53](http://ubuntuforums.org/showpost.php?p=3715308&postcount=53)


I always first apply the tips in posting #51 and then those in posting #53 and it always works tip top so far.

---

### Post by brunobenayon on 2008-05-24
> **reacocard said:**
> For those who have resolutions not in the table, fear not, they may be available. To get them, first install hwinfo
```
sudo apt-get install hwinfo
```
now run 
```
sudo hwinfo --framebuffer | grep 'Mode '
```
it'll spew out a bunch of lines like this: (Your numbers may be different)
```
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
...
```

Just use the Mode number you want after vga=. So, if you wanted 1280x800 and 24-bit color, you would use "vga=0x0362".

Hey, 

It's really solved my problem
I have a Notebook with wide screen and resolution of 1280 x 768  
Now my Ubuntu 8.04 have much more columns on CLI

\\:D/ 

Tks,

---

### Post by gcoats23 on 2008-10-25
Hello there- Great work on explaining things- that made it so easy- i have one question will adding vga=0x315 to my boot option change the resolution for ubuntu or just during boot- thanks 
garrett

---

### Post by Martje_001 on 2008-10-26
You could also do the following:
```
sudo gedit /etc/usplash.conf
```
and add:
```
xres=1680
yres=1050
```
(if you want 1680*1050). Then run:
```
sudo update-initramfs -u -k `uname -r`
```
and go! ;)

---

### Post by reacocard on 2008-10-26
> **Martje_001 said:**
> You could also do the following:
```
sudo gedit /etc/usplash.conf
```
and add:
```
xres=1680
yres=1050
```
(if you want 1680*1050). Then run:
```
sudo update-initramfs -u -k `uname -r`
```
and go! ;)

That'll change usplash's resolution but not that of the text consoles, which is arguably the main point of setting this. 1680x1050 text consoles are absolutely wonderful ^___^.

---

### Post by jonnybgreen on 2008-11-22
> **Indras said:**
> I've seen a few questions about this on the forums, so I've decided to write a full-fledged tutorial on how to set this up in Ubuntu.  This will show you how to change your screen's resolution while booting, during usplash, and at any time one one of the text consoles (by pressing CTRL+ALT+F1 through F6).  I'll try to make this as friendly as possible for newbies, and I'll make sure to explain all acronyms and abbreviations at least once.

[SIZE=4]Explanation:[/SIZE]  (feel free to skip this section, it is only for educational purposes)

Your computer system boots up in multiple stages, each one using the video card and monitor in its own way.  This is important to know when tracking down resolution problems.

First, your computer's BIOS (Basic Input-Output System) detects and powers up your video card during POST (the Power On Self Test) and uses it to display all of its relevant information, such as the memory check, a list of devices, and so on.  Some motherboards will simply display a full-screen logo, particularly branded PCs, like Hewlett Packard and Compaq.  You may have to press the spacebar or escape key to see what's going on behind the logo.  Each PC is different, so consult your vendor's support site, your computer's manual, or, if all else fails, google.com.

The BIOS generally chooses a generic resolution that will work on nearly any video card and monitor, like 640x480x8, so as to not have an error message that the user is unable to read.  I've only seen a couple computers where this resolution could be configured, as it's not a high priority option.

Then, your bootloader starts, using the resolution already in place.  This may be ntldr, on Windows NT/2000/XP systems, darwin on macintosh systems, or Lilo/Grub on Linux systems.  Ubuntu Dapper defaults with a basic plaintext grub.  See the gfxboot grub tutorial here on ubuntuforums if you'd like to use the graphical grub that Suse has: [http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)  However, I'm going to assume you're using default options from here on.

After you choose your operating system and kernel in grub, or it automatically defaults to the first option if you do not press a key during the 3 second countdown, it fires up the kernel and passes it bootup parameters.  There are many different parameters you can send to the kernel before bootup, such as 'single', for single-user mode.

The kernel uses it's own video card driver.  In Ubuntu, it uses the basic vesafb driver, short for vesa framebuffer.  This is a simple, generic, non-accelerated driver, which is optimal for compatibility.  Once again, the point is to never have something bad happen and an error message displayed on the screen that the user cannot see.  There are still users out there whose monitors cannot display above 800x600, and if your kernel tried to run the vesafb at a resolution higher than this, those users would be alienated.

If grub does not pass a vga parameter to the kernel, it assumes vga=normal, which is 640x480 resolution.  From then on, everything running will be at that basic vga resolution, except for the xserver.  First, your usplash screen displays, while all other services are starting.  This is the screen with an orange Ubuntu logo at the top of the screen and a list of processes starting up in the bottom half.  There's also a howto on the forums for changing the colors of the usplash screen, located here: [http://www.ubuntuforums.org/showthread.php?t=82835](http://www.ubuntuforums.org/showthread.php?t=82835).

Near the end of the bootup sequence, it starts up six consoles, using the getty program, and then the xserver.  The first six consoles can be accessed any time by pressing CTRL+ALT+F(x) where x is the number of the console.  The xserver then binds itself to F7, the next available number.  Try it now if you feel like, by holding CTRL and ALT and go through F1 through F7.

The consoles always use the vesafb driver to display, so they are at the same resolution that was passed to your kernel from grub.  The xserver uses its own driver and resolution, defined by /etc/X11/xorg.conf, and then Gnome, KDE, or XFCE run on top of it.  I won't go into detail here on how they work.

[SIZE=4]End explanation section[/SIZE]

Okay, if you jumped ahead, here's where you should start paying attention.  First, I'm going to give you the vesafb modes table.  This was taken from [http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html](http://www.tldp.org/HOWTO/Framebuffer-HOWTO-5.html), so feel free to go there for more information.

[SIZE="4"]The Table[HTML]Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?[/HTML][/SIZE]
(I apologize for the way this table looks, it's the only way I could get the columns to line up)

So first, choose which resolution you'd like to run your consoles and usplash in from the chart above.

Now, open your menu.lst file:
```
sudo nano /boot/grub/menu.lst
``` 

And find the entry you normally use to boot with and go to the line that begins with "kernel", it should say something like this:
```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
``` 

Add a "vga=" option to the end of the line, and put in the code from the table above.  So if you want 1024x768 at 16 bit color at command line, add "vga=0x317" to the end of your kernel parameters.  This is the option I like to use most.  You also can use the decimal equivalent, since 0x317 is in hex.  The decimal equivalent is 791, so you'd use "vga=791" instead.

Now, save the file, and it will take effect when you restart.

Note: Normally, when you upgrade your kernel or run grub-reconfigure, it will remove this option and set it back to defaults. In order to make this change permanent, go up a couple lines to one that looks like this:
```
# defoptions=quiet splash
``` 
(yes, it's commented out, but grub-reconfigure looks for this (and other) commented-out options when rebuilding your grub menu)

And add the same vga= option to the end of that as well, and it will make this new resolution permanent, even after new kernels are installed.

Another ubuntuforums member, Herman, made a very important suggestion: you can make modifications to your grub boot sequence for a single boot by editing grub before you boot.  Since it does not alter Grub's menu.lst file, the change isn't permanent.  When grub first boots up, at the GUI menu, select an option you want to modify and press the 'e' key.  This will bring up the full list of commands from the menu.lst file that grub uses to boot that particular option.  From there, you can go to your kernel line and add the vga option there, just like in my instructions above, and it will boot Ubuntu a single time with a different vesafb resolution.

As a bonus, here's some extra tidbits, some of it useless knowledge, for your perusal:

[LIST]
[*]For the mathematically challenged, there is a hex to decimal converter in Ubuntu.  Go to Applications->Accessories->Calculator.  From there, go to View->Scientific.  Right under the display screen is a button for Hex.  Press it and type the code from the table above (like 31C) and press the Dec button.

[*]When booting from the LiveCD, you can change this option as well, but you have to do it while still at the graphical grub menu.  When the CD boots and shows the Ubuntu logo with a 30 second timeout, press the escape key.  A box will come up warning you about going to the text-based grub interface.  Just press enter.  This will drop you to a boot: prompt.  Type "live vga=791", or whatever your desired resolution is, and then the liveCD will boot its kernel at this resolution.  Note that this is temporary for one boot only.

[*]You can set "vga=ask" in your menu.lst file to force the kernel to ask you what resolution you prefer each time, but you will choose from a rather small list of options.  You can type "scan" to have it check your hardware to see which modes it is capable of, but this is mainly for compatibility issues, and it won't give you as complete of a list as above, and you cannot type in 791, or 0x317 here, only a number from 0 to 9 from the list it gives you.
[/LIST]
If you see any incorrect information here in this tutorial, or you have something notable to add, please reply below and I'll try my best to make the changes in good time.  I do my best to visit the forums daily, so hopefully I'll catch it quickly.

Also, if you're looking for some very well written, illustrated information on using grub to its fullest, please visit Herman's website on grub here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Hi  Not simple enough for me I'm afraid.Tried to follow but first problem: should I open a terminal? I did and found the line to change resolution,very pleased with myself!,filled in info and went to save but where? Tried enter but no good.....read it through again.Then as suggested tried hitting f1 got of I dont know what,went on with f2 got to f6 with absolutely no idea of what was happening( i see now its till f7)..
anyway couldn't get away from that page and switched off pc. Restarted and now I have an unmoveable message from my moniter saying Mode Not Supported H:80.9KHZ V:64.7HZ Its right in the middle of the screen,the pointer slides underneath it and the monitor menu doesn't come up and I cant get rid of it.I'm hoping it would go if I could change the resolution but I'm totally lost now....any ideas.Yours in hope.Noob Jonnyb

---

### Post by scorp123 on 2008-11-22
> **jonnybgreen said:**
> Hi  Not simple enough for me I'm afraid. In that case: Why were you even following this guide?? You should first check if you really understand all steps in a guide before you blindly follow it. Besides: The guide is for (advanced) users who sometimes work on pure text consoles, away from the GUI. If you purely use the GUI desktop and are not likely to ever be working in a pure text console (= no mouse, no GUI, nothing to click on!), then you should not bother with this guide at all.

---

### Post by jonnybgreen on 2008-11-28
> **scorp123 said:**
> In that case: Why were you even following this guide?? You should first check if you really understand all steps in a guide before you blindly follow it. Besides: The guide is for (advanced) users who sometimes work on pure text consoles, away from the GUI. If you purely use the GUI desktop and are not likely to ever be working in a pure text console (= no mouse, no GUI, nothing to click on!), then you should not bother with this guide at all.

Hi..Ok I've fixed it with mouse clicks so thanks Scorp for making me look around more on my level!! I went to System-administration-NVIDIA Xserver settings-Xserver display configuration and set resolution and refresh.
Everything great now...dual booting Vista/Intrepid.
Starting to read up about terminals so maybe throw the mouse away before my wife gets back!!

---

### Post by scorp123 on 2008-11-29
> **jonnybgreen said:**
>  Everything great now... Excellent :)

---

### Post by the8thstar on 2008-11-29
> **dizzie said:**
> If only 1280x800 was supported...

It is. Type vga=866.

---

### Post by scorp123 on 2008-11-29
> **the8thstar said:**
> It is. Type vga=866. He posted that almost two years ago ... ;)

---

### Post by the8thstar on 2008-11-30
True, yet the answer is still valid. It should be useful for other users whose native resolution is 1280x800.

---

### Post by scorp123 on 2008-11-30
> **the8thstar said:**
> It should be useful for other users whose native resolution is 1280x800. Well, my laptop has that. And I found the answer easily via Google a long long time ago ;)

vga=0x0361  ... does the same thing, "0x0361" is just the hexadecimal notation.

In case anyone cares (e.g. people who found this thread via Google): You can easily find out yourself what your device (Laptop or PC) is capable of with the help of the **hwinfo** program ... it's not installed per default though, you have to tell your system to install it first:  ```
sudo apt-get install hwinfo
```

Once this is installed you can tell it to check your graphics card's BIOS for available framebuffer modes:  ```
sudo hwinfo --framebuffer
```

In the case of my laptop this would spit out this information:
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.450]
  Unique ID: rdCR.il6towt04X5
  Hardware Class: framebuffer
  Model: "Intel(r) 82945GM Chipset Family Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r) 82945GM Chipset Family Graphics Controller"
  SubVendor: "Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 704 kB
  Memory Range: 0xc0000000-0xc07affff (rw)
  Mode 0x0360: 1280x800 (+1280), 8 bits
[COLOR="Red"]  Mode **0x0361**: 1280x800 (+2560), 16 bits[/COLOR]
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

``` Here we go, there's the correct value I need for the "vga=...." boot parameter. 

All I'd need to do here is go up to posting #51 and change two config files which "Octagonal" mentions in his post:
[http://ubuntuforums.org/showpost.php?p=3573289&postcount=51](http://ubuntuforums.org/showpost.php?p=3573289&postcount=51)

Voila, done.

---

### Post by the8thstar on 2008-12-04
> **scorp123 said:**
> Well, my laptop has that. And I found the answer easily via Google a long long time ago ;)

vga=0x0361  ... does the same thing, "0x0361" is just the hexadecimal notation.

In case anyone cares (e.g. people who found this thread via Google): You can easily find out yourself what your device (Laptop or PC) is capable of with the help of the **hwinfo** program ... it's not installed per default though, you have to tell your system to install it first:  ```
sudo apt-get install hwinfo
```

Once this is installed you can tell it to check your graphics card's BIOS for available framebuffer modes:  ```
sudo hwinfo --framebuffer
```

In the case of my laptop this would spit out this information:
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.450]
  Unique ID: rdCR.il6towt04X5
  Hardware Class: framebuffer
  Model: "Intel(r) 82945GM Chipset Family Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r) 82945GM Chipset Family Graphics Controller"
  SubVendor: "Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 704 kB
  Memory Range: 0xc0000000-0xc07affff (rw)
  Mode 0x0360: 1280x800 (+1280), 8 bits
[COLOR="Red"]  Mode **0x0361**: 1280x800 (+2560), 16 bits[/COLOR]
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

``` Here we go, there's the correct value I need for the "vga=...." boot parameter. 

All I'd need to do here is go up to posting #51 and change two config files which "Octagonal" mentions in his post:
[http://ubuntuforums.org/showpost.php?p=3573289&postcount=51](http://ubuntuforums.org/showpost.php?p=3573289&postcount=51)

Voila, done.

Good for you.

---

### Post by sarah.fauzia on 2008-12-10
> **scorp123 said:**
> In case anyone cares (e.g. people who found this thread via Google): You can easily find out yourself what your device (Laptop or PC) is capable of with the help of the **hwinfo** program ... it's not installed per default though, you have to tell your system to install it first:  ```
sudo apt-get install hwinfo
```

Once this is installed you can tell it to check your graphics card's BIOS for available framebuffer modes:  ```
sudo hwinfo --framebuffer
```

In the case of my laptop this would spit out this information:
```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.450]
  Unique ID: rdCR.il6towt04X5
  Hardware Class: framebuffer
  Model: "Intel(r) 82945GM Chipset Family Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r) 82945GM Chipset Family Graphics Controller"
  SubVendor: "Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 704 kB
  Memory Range: 0xc0000000-0xc07affff (rw)
  Mode 0x0360: 1280x800 (+1280), 8 bits
[COLOR="Red"]  Mode **0x0361**: 1280x800 (+2560), 16 bits[/COLOR]
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

How about support for my 1400 x 1050 resolution? I installed hwinfo, and it outputs:

```
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.450]
  Unique ID: rdCR.il6towt04X5
  Hardware Class: framebuffer
  Model: "Intel(r) 82945GM Chipset Family Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(r) 82945GM Chipset Family Graphics Controller"
  SubVendor: "Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 7 MB + 704 kB
  Memory Range: 0xc0000000-0xc07affff (rw)
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

where my tablet's native resolution doesn't show up.

Any ideas? Thanks!

---

### Post by reacocard on 2008-12-10
> **sarah.fauzia said:**
> How about support for my 1400 x 1050 resolution? I installed hwinfo, and it outputs:

<snip>

where my tablet's native resolution doesn't show up.

Any ideas? Thanks!

If it doesn't show up it's not supported. Period. You'll have to pick a different resolution.

---

### Post by scorp123 on 2008-12-10
> **sarah.fauzia said:**
> How about support for my 1400 x 1050 resolution? ... my tablet's native resolution doesn't show up. There is a difference between what the display is capable of and what the framebuffer device might be capable of. If the resolution is not listed then your framebuffer can't do it.

I have the same problem. I'd like to do 1920x1200 on one of my SUN's ... but the framebuffer can't handle more than 1600x1200 on that particular machine. X11 (= GUI) however has no troubles running at 1920x1200.

---

### Post by eludlow on 2009-01-27
Can anyone recommend what setting I should use for my new 24" WS monitor which supports up to 1920x1080 resolution?

Thanks.

---

### Post by reacocard on 2009-01-27
> **eludlow said:**
> Can anyone recommend what setting I should use for my new 24" WS monitor which supports up to 1920x1080 resolution?

Thanks.

Try the instructions in this post: [http://ubuntuforums.org/showpost.php?p=2071872&postcount=22](http://ubuntuforums.org/showpost.php?p=2071872&postcount=22)

---

### Post by eludlow on 2009-01-28
That's great thanks, now got it running at what I presume is the max res.  Now just to see if I can get the splash screen centred...

---

### Post by miromiro on 2009-03-14
For those that have struggled with this, as I have (hardly any hair left at this point) this is what I did for my LG **1680x1050** screen.

Changed the vga to 873 (this had zero effect, btw), but it seems like a good idea...

Worked out, after multiple reboots, that the only way to make the splash screen display without distortion is to opt for a 4:30 ratio, *irrespective of the resolution of your screen*.

Hence for mine, I went with x=1660 y=1220 in usplash.conf and it now displays beautifully - crystal clear and the ubuntu logo is a perfect circle.

Was it worth all the hair? Probably not, but damn it looks good now.

---

### Post by tturrisi on 2009-03-14
> **reacocard said:**
> For those who have resolutions not in the table, fear not, they may be available. To get them, first install hwinfo
```
sudo apt-get install hwinfo
```
now run 
```
sudo hwinfo --framebuffer | grep 'Mode '
```
it'll spew out a bunch of lines like this: (Your numbers may be different)
```
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
...
```

Just use the Mode number you want after vga=. So, if you wanted 1280x800 and 24-bit color, you would use "vga=0x0362".
Thanks. For a couple years I'd been using vga=791 on my widescreen laptop.  I'd thought that I was limited to the original framebuffer table, but I discovered that my framebuffer does support 1280x800...much cleaner than 1024x768 on a widescreen.

```
~# hwinfo --framebuffer | grep 'Mode '
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  [color=red]Mode 0x0361: 1280x800 (+5120), 24 bits[/color]
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits

```

---

### Post by sprezzatura on 2009-04-04
I can only see Ubuntu in _640x480_ resolution. I am using ver. 9.04 (Jaunty). I would like to display 1024x768.

I am using an HP Pavillion 753n, with an Intel 82845G/GL Graphics Card (according to 'lspci'). The monitor is a plain Samsung SyncMaster 753DF.

When I click on System-> Preferences-> Display, the only option available is '640x480'. No other options appear. 'Detect Monitor' does nothing.

'System-> Administration-> Hardware drivers' says there are no proprietary drivers on boad.

When Ubuntu starts up, the resolution of the splash screen seems to be higher than 640x480, which would indicate that the hardware is working.

I have edited /boot/grub/menu.lst and added 'vga=0x303' at the end of the 'kernel' line. This definitely causes the splash screen to shrink a bit. But when Gnome comes up, it's back to 640x480.

I modified /etc/X11/xorg.conf and added a 'Modes  1024x768', but that caused errors at boot time.

'hwinfo' confirms that the card is Intel Brookdale-G Graphics Controler. The only mode it shows is 0x301  640x480.

Also, when I run: ```
dpkg-reconfigure xserver-xorg
``` I get one superficial question about the display, nothing whatsoever about screen resolutions, then a whole lot of questions about the keyboard.

I did ```
sudo apt-get update
``` Is there a place where I can get drivers for the Intel card?

All I want to do is surf the Internet safely. I would appreciate advice.

Thanks.

---

### Post by sprezzatura on 2009-04-05
OK, I finally got it running! I did this as described in [_this post_]("http://ubuntuforums.org/showthread.php?t=998754") (thank you Klange): ```
sudo apt-get install libdrm-intel1
```

I also did [_this_]("http://ubuntuforums.org/showthread.php?p=6431510#post6431510") (merci beaucoup Nepherte): ```
Section "Device"
	Identifier	"Configured Video Device"
        Driver          "intel"
EndSection
```

I am now surfing safely at 1024x768. I am a happy camper.

(See [_here_]("http://ubuntuforums.org/showthread.php?p=7017671#post7017671") for more comments).

---

### Post by pjalegria on 2009-04-13
Does anyone now the code for WSVGA 1024x600 GRUB???

thanks

---

### Post by juanmoreno92 on 2009-04-13
In order to get a console in 1280x800 you need to append:
```
vga=865
```
to your kernel boot line.

Works for me. It is for 1280x80 at 32 bit. 24 bit is 864.

---

### Post by calrogman on 2009-04-14
> **dizzie said:**
> if only 1280x800 was supported...

+1

---

### Post by alanwall on 2009-04-24
Ok I am still new to Ubuntu so dled 9.04 and decided to opt to install under Windows on its own partition.After the install/reboot
just got a blank screen so sent a note to a friend who uses and he send me to this thread.I have a 1024x768 screen so set vga=792 in all the vga lines and still a blank screen ?
Ideas/fixes ?
Thanks !

---

### Post by scorp123 on 2009-04-30
> **alanwall said:**
> Ok I am still new to Ubuntu ...
OK ... 

> **alanwall said:**
>  After the install/reboot
just got a blank screen so sent a note to a friend who uses and he send me to this thread.  Is your friend a newbie too? He should have known better. See below why.

> **alanwall said:**
>  I have a 1024x768 screen so set vga=792 in all the vga lines and still a blank screen ?  First of all, these resolution settings have _NOTHING_ to do with the graphical user interface (= desktop with mouse and icons). So if you don't get a desktop login then you probably have other problems and nothing in this thread will help you.

Please also see the explanation given in posting #67:
[http://ubuntuforums.org/showpost.php?p=6231808&postcount=67](http://ubuntuforums.org/showpost.php?p=6231808&postcount=67)

As I said there: this is purely about choosing a resolution for us nerds and sysadmins who would like to have a higher text resolution than just the standard 80x25 ... this does absolutely nothing for the desktop settings.  

Under Linux (and a lot of other UNIX-style operating systems) there are multiple displays available to you. You can switch between them using Ctrl+Alt+F1 up to Ctrl+Alt+F8 ... But more can be configured with relative ease. 

Your graphical user interface / desktop will usually reside on display #7 ... so you'd hit Ctrl+Alt+F7 to switch to it. Usually the system should switch to it automatically upon boot. I just mention this that if you should ever accidentally switch away from it, you could hit Ctrl+Alt+F7 to switch back to the GUI (newer Ubuntu releases from 8.10 onwards even do this automatically). These "displays" are sometimes called "tty's", "vty's" or "vc's" ... these are ancient 1970 era abbreviations for "**_t_**ele**_ty_**per", "**_v_**irtual tele**_ty_**per" and "**_v_**irtual **_c_**onsole". As you can see those terms originate from an era when computers did not yet have CRT screens but were fed with paper punchcards and output was produced on teletype machines. Hence these terms. So from Linux's point of view your computer does not have just one display .. it has at least 8 (!!) of them. Display No. #7 is where your desktop usually resides. The others (displays #1 - #6 + #8) are pure text consoles. All the tips in this thread concern those consoles and how to gain a higher resolution on those. As I said ... I don't think the tips here will help you.

You said you were new .. OK, so you couldn't know all this.

And the reason why your display still remains totally black is that you probably did not enable the framebuffer device. Just entering "vga=..." into the boot parameters is not enough anymore. Out of some IMHO silly design decision Canonical Ltd. have disabled the framebuffer device in Ubuntu so unless you re-enable it again those "vga=" parameters will not do anything. Hence the need for this thread ;)

---

### Post by drbrando007 on 2009-04-30
what a post!

rock on :guitar:

eight thumbs up

---

### Post by zmdmw52 on 2009-09-16
VGA Resolution codes (VGA + Hex)

[http://forums.remote-exploit.org/backtrack-4-general-support/23746-vga-resolution-codes-lilo-grub.html](http://forums.remote-exploit.org/backtrack-4-general-support/23746-vga-resolution-codes-lilo-grub.html)

> [FONT=Times New Roman]Width-Height-Depth    VGA Codes    HEX Codes
80x25 (TEXT)        3840        0xF00
80x50 (TEXT)        3841        0xF01
80x43 (TEXT)        3842        0xF02
80x28 (TEXT)        3843        0xF03
80x30 (TEXT)        3845        0xF05
80x34 (TEXT)        3846        0xF06
80x60 (TEXT)        3847        0xF07

320x200x8        816        0x330
320x200x16        782        0x30E
320x200x24        783        0x30F

320x240x8        820        0x334
320x240x16        821        0x335
320x240x24        822        0x336

320x400x8        817        0x331
320x400x16        818        0x332
320x400x24        819        0x333

640x400x8        768        0x300
640x400x16        829        0x33d
640x400x24        830        0x33e

640x480x8        769        0x301
640x480x16        785        0x311
640x480x24        786        0x312
=========================================

Width-Height-Depth    VGA Codes    HEX Codes
768x480x8        866        0x362
768x480x16        ???        ????
768x480x24        ???        ????

800x600x8        771        0x303
800x600x16        788        0x314
800x600x24        789        0x315

1024x768x8        773        0x305
1024x768x16        791        0x317
1024x768x24        792        0x318

1280x800x8        864        0x360
1280x800x16        ???        ????
1280x800x24        865        0x361

1280x1024x8            775             0x307
1280x1024x16           794             0x31a
1280x1024x24           795             0x31b

1440x900x8        868        0x364
1440x900x16        ???        ????
1440x900x24        869        0x365

1600x1200x8            796             0x372
1600x1200x16           798             0x374
1600x1200x24           799             0x375[/FONT]

---

### Post by Esthellin on 2009-09-24
hwinfo fails in Ubuntu Jaunty.

Running sudo hwinfo --framebuffer | grep "Mode " looks like it ouputs something, then goes straight back to the prompt.
I tried hwinfo --framebuffer by itself and nothing gets printed - goes straight back to the terminal prompt.

hwinfo --all didn't show anything to do with the framebuffers either :(

I want 1280x800 dammit!

startupmanager only has 640x480, 800x600, 1024x768, 1280x1024 and 1600x1200. Noe of these have the right ratio for 1280x800.

---

### Post by scorp123 on 2009-09-26
> **Esthellin said:**
> hwinfo fails in Ubuntu Jaunty. Are you sure it's even installed?

---

### Post by Esthellin on 2009-09-28
> **scorp123 said:**
> Are you sure it's even installed?

It is installed because putting in any of the other command line tags works for the program - only the framebuffer one doesn't work. Could this mean my laptop doesnt have a framebuffer? XD
Or something where the framebuffer settings are not viewable? Whatever it is, you can't get 1280x800. Startupmanager only had a few choices - all the wrong ones.

Changing the values in /etc/usplash.conf did not result in the temrinal screen before login (with gdm disabled) being the right resolution.

---

### Post by reacocard on 2009-09-29
> **Esthellin said:**
> It is installed because putting in any of the other command line tags works for the program - only the framebuffer one doesn't work. Could this mean my laptop doesnt have a framebuffer? XD
Or something where the framebuffer settings are not viewable? Whatever it is, you can't get 1280x800. Startupmanager only had a few choices - all the wrong ones.

Changing the values in /etc/usplash.conf did not result in the temrinal screen before login (with gdm disabled) being the right resolution.

Sometimes the framebuffer hardware just doesn't support the native resolution in VGA-modes, nothing you can do about it really. :(

---

### Post by arnab_das on 2009-09-29
how to do it for 1366x768 ie 720p on ubuntu 9.04?

---

### Post by scorp123 on 2009-09-29
> **arnab_das said:**
> how to do it for 1366x768 ie 720p on ubuntu 9.04? Same method ... you'd just pick 1366x768 instead of 1280x800 as I did in my example (if your framebuffer can do it, that is ...)

[http://ubuntuforums.org/showpost.php?p=6281148&postcount=73](http://ubuntuforums.org/showpost.php?p=6281148&postcount=73)

---

### Post by Esthellin on 2009-09-29
> **reacocard said:**
> Sometimes the framebuffer hardware just doesn't support the native resolution in VGA-modes, nothing you can do about it really. :(

That sucks. No support for 1280x800. I must have a pretty weird laptop then :P.

I still can't understand what hwinfo doesn't even display framebuffer information.
-shakes fist at hwinfo-

---

### Post by n.hinton on 2009-11-27
Hi,

Really need a new monitor problem: Display is a bit wider than the monitors (set fully narrow for res). 

In windows using desktop>setting>advanced>adaptor>settings>adjust tab, or something like that, was able to adjust display to a usable configuration.

Have used Power Strip to capture the windows config (not adjust) and spent hours playing with xvidtune attempting to duplicate the settings in Linux without success (xvidtune lack of decimal place and general limited configurability) trying match the windows settings.

Question: Can anyone explain to me how to translate the windows settings in the screenshot to linux?

PS there are literaly hundreds of ways to achieve the totals (none of which work) and pixel clock is not adjustable with xvidtune. V and H refresh's can not be accieved due to only two decimal places.

Please see screenshot.

Many Thanks

---

### Post by scorp123 on 2009-11-29
> **n.hinton said:**
>  Really need a new monitor problem ...  Why are you hijacking this thread and not opening your own new one??

> **n.hinton said:**
>  In windows ... xvidtune.  In case you didn't get it --and you apparently didn't-- this thread here has **NOTHING** to do with anything related to the GUI or GNOME or X11 or anything like that.

Explanation already posted here:
[http://ubuntuforums.org/showpost.php?p=6231808&postcount=67](http://ubuntuforums.org/showpost.php?p=6231808&postcount=67)

Far more details explained here:
[http://ubuntuforums.org/showpost.php?p=7182310&postcount=89](http://ubuntuforums.org/showpost.php?p=7182310&postcount=89)

---

### Post by n.hinton on 2009-11-29
Hi scorp123, 

Sorry I missed the no mouse, no GUI bit.

Thanks for pointing it out.

---

### Post by scorp123 on 2009-11-29
> **n.hinton said:**
>  Sorry I missed the no mouse, no GUI bit. No problem.

---

### Post by kajman on 2010-06-14
How to do above steps in 10.4 or 9.10, where grub2 is the default and there's no file as etc/grub/menu.lst ??

When I've installed 10.4 today I've saw a great hi-res terminal, but when I've downloaded and installed nvidia drivers the resolution changed to a lower one, and I don't know how to restore it. Any ideas?

---

### Post by COKEDUDE on 2011-03-07
> **Indras said:**
> 

[SIZE="4"]The Table[HTML]Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?[/HTML][/SIZE]
(I apologize for the way this table looks, it's the only way I could get the columns to line up)



Nice table. Thx for this info.

---

