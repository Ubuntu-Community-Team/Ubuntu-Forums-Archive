---
title: "ATI Dual-Head RandR Xinerama Radeon HD series and pair modes"
date: 2009-05-20
forum: Outdated Tutorials &amp; Tips
---

### Post by f1r31c3r on 2009-05-20
hey all, its been a while since I been on and droped any posts but hey.

I thought I would right some discoveries and some tips or tricks here for you all to read up on maybe have a play with.

I purchased a new graphics card recently from ati, being as I am on a system with an agp pro 50 slot buying or upgrading my graphics is not an easy task with all the pcie cards out there.

I had to pull out a genuine Firegl X1 256p card to plug this sapphire HD3850 into the system which to me is a far better option than upgrading 4 processors, Adaptec on-board scsi, main-board, memory etc which is not a small upgrade and costs a massive amount for a workstation so this radeon will have to do.

Saying that mind you its performance is jaw-droping so getting it to work in ubuntu is well worth the time and effort.


I start by talking about the xorg-fglrx drivers which for me did not work they crashed the system played havoc with my monitors even brought up the OSD of my monitors after reboot so I removed them and compiled and installed the drivers direct from ATi.com

Done like this(I am assuming 32bit system):

> sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms 

Download the ati driver from ATI Not the firegl one but the radeon driver 9.4 or whatever version there is there just mod the command bellow appropriate to the version:

> sh ati-driver-installer-9-4-x86.x86_64.run --buildpkg Ubuntu/jaunty 

Install the drivers:

> sudo dpkg -I xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb 

Blat your xorg with ATI configs:

> sudo aticonfig --initial -f 

***NOTE The above is a merged Frame buffer configuration NOT Dual-Head because the aticonfig --initial=dual-head command sets up the dual head feature which assigns each monitor as an individual single workspace, they can be merged together using xinerama as explained bellow or even pair modes as mentioned bellow(ati don't half take hard work and make it harder yet the benefits achieved when working are breathtaking visuals lol)

they worked yay but did they.

Problems begin when the driver does not know which monitor is screen 1 and screen 0 urm I think the cards bios from sapphire is to blame so not much we can do about that but there is for things like game play, big desktop etc.

I sat playing with modes and found that RandR 1.2 has some issues allot of issues so I disabled it here is how:

> gksudo gedit /etc/ati/amdpcsdb

once open look for the section:

> [AMDPCSROOT/SYSTEM/DDX]

when you found it add this under it:

> EnableRandR12=Sfalse

you dont really need the next one but hey for a clean configuration under your section device in the xorg.conf:

> Option      "EnableRandR12" "false"

that's it reboot RandR is now off, be warned the Systems>Preferences>Display will now not work because it relies on this RandR to operate.

Why would you want to disable this:

well few reasons ATICONFIG reports error cant do this that the other while RandR 1.2 is running;
Xinerama crashes;
Multiple adapters in your system;
You want to enable pair modes;
randomisation between which monitor is the primary(could be bios bug);
Display corruption on big desktop when running games(one desktop shows game other shows corrupt data);

These are just a few I am sure many more exist and RandR is buggy so 1.3 is expected to deal with some of the above issues.

So there is a few reasons to disable RandR and enable the ATI Drivers Xinerama, most ati users have seen this gray'd out in the amdccc(ati controll panel). 

Here is how to enable this but make sure you have disabled RandR as above, to test it try and load the display properties from System>Preferences>Display, if it says something along the lines of would you like to use your drivers manager, then you have disabled RandR.

once you have done that make sure your xorg.conf is clean when I say clean it has no configure options no previous settings(delete all text inside the xorg.conf) etc you can boot into rescue mode from the grub menu select drop to root shell and enter:

> aticonfig --initial=dual-head --xinerama=on

If you get errors like segmentation fault you have put a space at the end of the line;
other errors could mean your not in root and it dont have permission to write to the xorg.conf;
with ATI drivers there error reporting is as bad as Microsoft there so descriptive only they know what they mean very typical really.

if there were no errors then type:

> exit

and select resume, there will probably be some fine tuning you will need to do as in left or right screen positions etc.

to see all the options in the ATI control panel load it from the terminal like this.

> gksudo amdcccle


you will see more options opened up xinerama should be enabled and multiple monitor modes open up offering you big desktop on the pull down menus.

Another thing to note in this when playing games is that the game will load up as a cloned display so you will have 2 games displayed as if the second monitor was displaying it to your friends etc. No screen corruption mind you so hey success on one side.

Note that saying all of the above about xinerama lol RandR can still be used and there is a graphical user interface if you use RandR so if xinerama is not quite the thing your wanting try installing GrandR this graphical tool is like an admin for RandR.

Use synaptic package manager search and install grandr and load it with:

> gksudo grandr


Last but not least is the PairModes:

This mode also requires you to have disabled RandR but in this mode you waid all control from the GUI control panels. This mode is where a virtual desktop of screen0+screen1 are added together giving the desired effect of big desktop.

If you run;
xinerama in this mode it will crash

RandR will run in all its command lines in this mode but to get the ati driver to recognise the pair RandR needs be disabled as shown above. Grandr should still work while pair mode works so all is good there in regards to RandR.

Games run under pair mode will cause screen corruption as it tries to run it as a virtual resolution and ends up very messed up somehow please don't quote me here but on my card it don't work lol

Oh yea and compiz-fusion runs on all these modes without problems as long as the ati driver is installed and loaded correctly then all above runs compiz-fusion.

to setup a pair mode(RandR has been disabled as above);

begin with clean xorg.conf and;

> sudo aticonfig --initial

then lets setup a virtual resolution in the screen subsection, I found sometimes this is not needed but we shall put it in for completeness:

> Virtual   2880 1024 #make sure this is the maximum res of your monitor if its smaller than the max the ati driver wont have any of it

Next lets set the big desktop option:

> sudo aticonfig --dtop horizontal

Restart X(logout and login or reboot whichever)

Lets add that pair mode(I have 2 screens both the same res so adjust your virtual(above) and your pair mode(bellow) accordingly):

> sudo aticonfig --add-pairmode=1440x900+1440x900


CHeck if the pairmode is listed:

> aticonfig --list-pairmode


If the mode is listed then yay well done so far so good now

Restart your system and finally:

> xrandr

which should bring this up:

> xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 2880 x 1024
default connected 1440x900+0+0 0mm x 0mm                            
   2880x1024      60.0
   2880x900       60.0
   1440x900       60.0*    50.0
   1280x768       60.0     50.0
   1280x720       60.0     50.0
   1152x864       60.0     50.0     75.0     70.0
   1024x768       60.0     50.0     75.0     72.0     70.0
   800x600        60.0     50.0     75.0     72.0     70.0     56.0
   720x480        60.0     50.0
   640x480        60.0     50.0     75.0     72.0
   640x400        60.0     50.0     75.0
   512x384        60.0     50.0     75.0
   400x300        60.0     50.0     75.0
   320x240        60.0     50.0     75.0
   320x200        60.0     50.0     75.0
   1280x1024      75.0     70.0     60.0
   1280x960       60.0
   640x350        70.0
   1680x1050      60.0
   1400x1050      60.0


On a final note I find pair mode to work but I don't find it a very productive option yet I am sure it can be if full screen apps like games would not mess up the second monitor, maybe randr V1.3 would correct these problems.

The System>Preferences>Display will be back in operation just answer no to the use your drivers control applet and you can select the 2880x900 resolution from the list.

Anyway I hope all the above sheds some light on this and helps someone or if you play like me then fun for others lol.

---

