---
title: "RE: need help with resolution"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by tilley661 on 2008-09-28
ok i have seen mjany people with the same problem as me, they cannot set the screen res to 
1280 x 1024
v=60 hz
h = 75 khz

now im a complete noob to linux and to hardware. so i realy need help.

i had windows xp pro and recently converted to ubuntu and it ran like a treat. i set everything thing up and then when it came to set the resolution i couldn't get higher that 1280 x 800. now my screen is jerking all over the place and slowing the computer down immensely and really irritating. so i re-installed the whole OS, then again it ran like a charm. but 10 mins later after trying to set the resolution (still no higher that 1280 x 1024 @ 60hz) the screen is running slow and jerking again

looking at similar problems, people have solved the issue by altering the Xorg.cofig file. here is mine:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


--------------------------------

now looking at my file compared to other peoples, mine is screwed up (in my point of view).

if any one can help me solve this problem i would greatly appreciate it. 

p.s my keyboard isnt set up correct the " sign is actually the @ sign (visa versa) any suggestions on that front?

thank you in advance ]
Daniel

---

### Post by justsomedude on 2008-09-28
First, we have to find out what graphics card you have.

Please open a terminal and post the output of:

```
lspci | grep VGA
```

---

### Post by ajgreeny on 2008-09-28
It would also be useful to know which graphics driver is in use, so with alt+F2 (run dialog box) enter ```
gksudo displayconfig-gtk
```and look in the graphics card tab for the driver used at the moment.

---

### Post by tilley661 on 2008-09-28
sorry this took so long: 

to the first post :

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

and to the secondc :  ati - ATI mach 8, mach 32, mach 64 and RAGEXL cards 

thanks again

---

### Post by Kellemora on 2008-09-28
Hi Tilley

See if what I had to do will help you!

Here is an article I put together, AS A NOOB.  There may be better ways, but this is what worked for me and now I have ALL of my screen resolutions available, FINALLY.

TTUL
Gary

Screen Resolution Problems?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
This document is to address Changing Screen Resolution using Preferences causes Screen to Roll horizontally, vertically or just mess up royally.  Also, only 640 x 480 resolution available in Preferences.  This fix may or may not allow you to select other available resolutions from the Preferences Option without changing MODE lines in /etc/X11/xorg.conf which I am not addressing here.
If this fix causes log-in screen obesity (HUGE SCREEN), see my other post titled Huge Log-in Screen?  Easy fix!  Which addresses that problem separately and easily.

To get started we need the Tool called Screens and Graphics.
If it is not available under Applications/Other, then RIGHT CLICK on Applications, select Edit Menu (left click) and wait for the Main Menu screen to open.  From the Main Menu, left column (Menus) select 'Other' and a new list of text will appear in the right screen (items).  Place a check mark in the box to the left of Screens and Graphics, this will automatically select 'Other' if it was NOT in your drop down list under Applications.  Close this window.
You will have to REBOOT for the change to take affect.

Once you're up and running again, left click on Applications/Other/Screens and Graphics.
A log-in screen will appear, type your Normal log-in password.  Why it don't ask for Root I don't know.

In the Screens and Graphics Preferences window select Graphics Card first just to check to make sure your correct graphics card is displayed.  Normally these entries are correct, but check them anyhow!

OK, now select the Screen Tab and get things set up to run properly.

Click on the little Monitor icon to the right of Model:  It may currently say Plug n Play.  A new (Choose Screen) window opens, from the Left window, select the Manufacturer of your Monitor.  The screen on the right will change to the models that manufacturer makes.  Scroll through the list to find your Monitors model name and number and/or identification.
If you have an .inf driver for your particular monitor and it is not listed, select add and follow the directions there.  I've not found a monitor not already in the listing yet.  Then I never have many new things either, that might not be listed long before I get it, hi hi.........  IF a Test button comes up, just IGNORE IT, because your screen will mess up royally.  After selecting your monitor, select OK!  This will bring you back to the Screen and Graphics Preferences screen.
Here you will select the desired resolution you would like your DESKTOP to run in.  The proper bandwidth should self-select, but check to make sure it's right for your monitor.  A wrong setting could damage your monitor!
Select OK and it will change and ask you if you want to Keep this setting.  If all looks OK, select YES.
This change, and all the default parameters for your selected monitor WILL be written to the /etc/X11/xorg.conf file.  Also, the Screens and Graphics window may show UNKNOWN for your monitor.  The result of this Unknown Monitor or sometimes even if the Monitor is KNOWN and displays correctly the resultant change to the xorg.conf file, may cause your log-in screen to become OBESE (HUGE) and you might not be able to see your log-in boxes.

But don't worry, you KNOW they are there! 
Just type in your log-in name, hit enter and type your password, hit enter and wait for the log-in to complete.  Your xwindow (Gnome or others) should be at the desired resolution now.

IF you did have the HUGE log-in problem, see my post on Huge Log-in Screen?  Easy fix!

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video, Samsung SyncMaster 955df.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video, AOC monitor.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video, Samsung SyncMaster 3Ne.


TTUL
Gary/aka Kellemora
9/10/08 – rev 9/15/08

---

### Post by tilley661 on 2008-09-28
> Click on the little Monitor icon to the right of Model: It may currently say Plug n Play. A new (Choose Screen) window opens, from the Left window, select the Manufacturer of your Monitor.

congratulations you have just found the first monitor on that list ha ha, VIDEOSEVEN, any ideas?

also on the graphics section my top graphics card is selected however i have none selected in the bottom section

Videoseven V7 L17PS

thats the full model incase you have any ideas

---

### Post by justsomedude on 2008-09-28
Ok, we know your card now, I'm unsure about the driver though.

ati can mean radeon, r128 or atimisc.

Please post the output of 

```
lsmod
```

---

### Post by tilley661 on 2008-09-28
> **justsomedude said:**
> Ok, we know your card now, I'm unsure about the driver though.

ati can mean radeon, r128 or atimisc.

Please post the output of 

```
lsmod
```


Module                  Size  Used by
ipv6                  267780  8 
af_packet              23812  2 
radeon                124192  2 
drm                    82452  3 radeon
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
lp                     12324  0 
snd_via82xx            29464  3 
gameport               16008  1 snd_via82xx
snd_mpu401_uart         9728  1 snd_via82xx
snd_seq_dummy           4868  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd_via82xx_modem      16264  0 
snd_ac97_codec        101028  2 snd_via82xx,snd_via82xx_modem
snd_seq_oss            35584  0 
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_midi            9376  0 
pcspkr                  4224  0 
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_pcm                78596  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
k8temp                  6656  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  19 snd_via82xx,snd_mpu401_uart,snd_seq_dummy,snd_via82xx_modem,snd_ac97_codec,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
i2c_viapro              9876  0 
soundcore               8800  1 snd
i2c_core               24832  1 i2c_viapro
evdev                  13056  4 
usblp                  15872  0 
button                  9232  0 
amd64_agp              13444  1 
agpgart                34760  2 drm,amd64_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
usbhid                 31872  0 
hid                    38784  1 usbhid
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
floppy                 59588  0 
8139cp                 24704  0 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
pata_via               13316  2 
sata_via               12420  0 
usbcore               146028  5 usblp,usbhid,ehci_hcd,uhci_hcd
sata_promise           14724  0 
skge                   43536  0 
8139too                27520  0 
mii                     6400  2 8139cp,8139too
ohci1394               33584  0 
libata                159344  5 pata_acpi,ata_generic,pata_via,sata_via,sata_promise
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3

---

### Post by justsomedude on 2008-09-28
Okay, the radeon driver seems to be running. So far, so good. I suggest you reconfigure the xserver:
```

sudo dpkg-reconfigure xserver-xorg
```

Answer all the questions to the best of your knowledge and reboot afterwards, you can also solve your keyboard problems on the way.

Good luck...

---

### Post by tilley661 on 2008-09-28
to Gary

your post seemed to help, well it certainly has made my computer speed and everything seems to be in working order. however, everything seems rather... LARGE! maybe this is just my display settings, i might have to alter them somewhere maybe? any ideas? thank you again.


as to justsomedude, im intrigued as to what you are looking for? i appreciate all the help and ill take a look at this thread tomorrow at some time, i hope you find something which my improve my large icons Etc.

thank you.

---

### Post by tilley661 on 2008-09-28
> **justsomedude said:**
> Okay, the radeon driver seems to be running. So far, so good. I suggest you reconfigure the xserver:
```

sudo dpkg-reconfigure xserver-xorg
```

Answer all the questions to the best of your knowledge and reboot afterwards, you can also solve your keyboard problems on the way.

Good luck...


thank you i will do :)

---

### Post by tilley661 on 2008-09-29
ok i followed the tutorial thing you sent me and that worked ok. i was running on 1280 x 1024. i clicked ok on the screen and graphics panel restarted and it was fine. now ive come to use the computer today, and the screen and graphics have changed back to their original state and now my monitor is jerking again. ive tried the process again and for some reason it is not working at all now, i can get the resolution all set up but it will not keep the config at 1280 x 1024.
any ideas would be appreciated :) thanks

---

### Post by justsomedude on 2008-09-29
Sorry it didn't work so far, we could try to use the official ATI driver (fglrx).

Go to the Restricted Drivers Manager, install the driver and reboot. 

Then, (if your resolution isn't set already) repeat the process above and restart the XServer (ctrl + alt + backspace).

If that doesn't help, you could also try to setup your card with a script called Envy, it's pretty much self explanatory and available in the repos.

Also, if the xorg.conf file you posted in post #1 of this thread changed, post it.

I'll help you to the best of my knowledge, but I don't own an ATI card, so maybe some of the ATI guys can chime in. 

ATI cards can be tricky to setup, but we'll get there...


And remember, if something goes wrong in the process and you're greeted by a text console at the login,

```
sudo dpkg-reconfigure xserver-xorg
```

should work to setup a graphical environment again. So you better write this down, it might come in handy.

---

### Post by tilley661 on 2008-09-30
ok ive managed to get the screen and graphics card set up i think. but now all my icons etc are massive!, any ideas?

thanks again

---

### Post by justsomedude on 2008-09-30
Which icons, the ones on the desktop?

Hit alt + f2 and enter

```
gconf-editor
```

Navigate to *apps --> nautilus --> icon_view*

and set the key *default_zoom_level* to *small*.

---

### Post by Kellemora on 2008-09-30
Hi Tilley

I don't know if this is applicable or not to what you are experiencing, but I'm posting it anyhow for you to check it out.

TTUL
Gary

Huge Log-in Screen?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

This is from a total Noob, but took much research to find out exactly, what changed where, to figure it out.  It's also fairly long because it is geared toward big dummies like myself, hi hi.....

A Simple Test:
If you return your monitor to the original default settings, you should find that your log-in screen once again works right.  This was the CLUE to finding out which file controlled the log-in screen for me!

How to change screen resolution (not using Properties) is in another document titled “Screen Resolution Problems?  Easy fix!”  This too might cause log-in screen obesity!

Being a Noob, there may be an easier faster way to do this, but this is what consistently works for me.

The following changes are made using the “ROOT TERMINAL”.

The Terminal in Applications/Accessories does not work for me.  No Permission when you go to save!
If you do not have the Root Terminal under Applications/System Tools, then RIGHT CLICK on Applications, select Edit Menus (by left click) and a Main Menu will appear shortly.  In Main Menu (under Menus) select System Tools and the screen (titled Items) to your right will change.  Place a check mark in the box to the left of Root Terminal and select CLOSE.  The Root Terminal will now appear as a selection when  you select Applications/System Tools.

NOW, Select the Root Terminal.  Before the Root Terminal Opens you will have to Log-in as Administrator.  This is your NORMAL log-in!  Why it doesn't ask for Root Log-in I have no idea.
Even though it shows you are IN Root, you will notice that you are still in your /home/name/ directory.  If you try to open the required file from here, you will get a blank screen so DON'T save it, Close without Saving.

At the prompt type  cd ..  this will take you back to your /home directory.
Type  cd ..  again and you will be in the ROOT Directory and can perform the following command.

Note that the X is a capital letter, all others are lower case!  It's X Eleven not XII.

gksu gedit /etc/X11/xorg.conf  This will open your xorg.conf file for editing.

SAFETY OPTION:  Right Click on File, select SAVE AS (left click).  Add  .old  behind the filename xorg.conf so it reads xorg.conf.old, then Right Click on SAVE.  You will now be VIEWING the saved file so select Right Click on the OPEN Icon and select xorg.conf to reopen the working file for changes.  You can always revert back to the original file by saving it as xorg.conf without the word .old behind it.  End of Safety Option.

Scroll down (near the bottom) and you will find a line titled Section “Screen”, tabbed in twice you will find a line that reads Virtual followed by two sets of digits.  You should recognize these digits as being common screen resolutions.
Be very careful here!  It's better to be safe than sorry.
You may notice a High screen resolution listed here, one your monitor cannot recognize, like 1792 1344 (which defaults to 640 480), or it may be very low, like 640 480 already.  My desired screen resolution for the log-in screen is 1024 768 so those are the numbers I chose to replace the numbers.

DO NOT delete the existing numbers yet.  They appear to me to be in placeholders is why!

For safety reasons.  Place your cursor after the first digit of the first existing number and if different from the first number already listed, type the new single digit then move left one space and delete the first number, then move back right and enter your remaining numbers, then delete the old numbers from behind it.  If you are going from 1792 down to 1024, just place your cursor between the 1 and 7 and type 024 then delete the 792 ONLY.  I still use this method if I'm going from 640 up to 1024, placing the cursor between the 6 and 4 as my starting point, typing the whole number 1024.
OK, move to the second number, it may be 1344 and you want 768.  Use the same method here too!  Place your cursor between 1 and 3, type 768, delete the 344, move left and delete the leading 1.

This may be an unnecessary overkill way of doing it.  But why take chances when we're only Noob's?

Go to the top of the Screen and Select SAVE, then wait for a bit to make sure it saved before exiting the gedit program.

This has worked on all Ubuntu 8.04 Hardy Heron machines I have tried it on in my testing!

FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video card.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video card.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video card.
e-machine T6524, 2.30GHz Athlon 64-3500+, ATP Radion Express 300 video card.

TTUL
Gary/aka Kellemora
9/10/08 – rev 9/15/08

---

