---
title: "Howto: Feisty Fawn On A Compaq Presario V6000"
date: 2007-05-29
forum: Outdated Tutorials &amp; Tips
---

### Post by soapytheclown on 2007-05-29
Note: the basis of this guide has been written on my **Compaq Presario V6133EU** with the following specs:
[B]
AMD 64X2 Turion Processor
Nvidia Geforce 6150 
Broadcom 4311 Wireless Chipset (known as a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) )
15.4" Widescreen at 1280x800 resolution[/B]

Using the i386 version and The AMD64 ed. of Fesity. As I understand the Intel versions of the V6000 has been fine so this is written for us with the problematic AMD processors! I have tried to write this as simple as possible for anyone who has little ex perience out there. 

So far i have gotten the following out of my laptop:
[B]
1. Install and boot correctly
2. Normal wireless speeds
3. Nvida Driver installed and working correctly
4. Beryl Installed and functioning properly[/B]

Okay lets get going!

[SIZE="5"]1. Installing and booting[/SIZE]

A quick forum search will tell you that in order to boot the live cd for installation requires the "noapic" or "nolapic" flag to be used. This works but like me im sure alot of people had no idea what this option does however i found that it it stops usb hotplugging to work, which means unless the device (ie usb stick or mouse) is plugged in at startup it wont work, however this can be fixed using another flag with the noapic which is: "irqpoll noirqdebug"

so.. turn you computer on make sure it boots form the cd when the option to start the live disc comes on press the F6 key and type in:
[SIZE="3"]"noapic irqpoll noirqdebug"[/SIZE] [without the quotes]
followed by return, it should boot up and install as normal! :D

[SIZE="3"]**Note:- **[/SIZE]If you've already installed using the noapic flag dont worry you can edit a file and it will have the same effect:

open a terminal type:-

sudo gedit /boot/grub/menu.lst

then go to the bottom of the document and look for the grub boot options and look for something like this:

[SIZE="3"]"title Ubuntu, kernel 2.6.20-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=16badbe3-91d7-4ba1-9446-e874976aea45 ro splash noapic 
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault"[/SIZE]

then add the string **"irqpoll noirqdebug"** into the kernel option so you end up with the new line that looks like:-

[SIZE="3"]kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=16badbe3-91d7-4ba1-9446-e874976aea45 ro splash noapic irqpoll noirqdebug[/SIZE]

then look or search for a line that is something like:-

[SIZE="3"]# defoptions=quiet splash noapic[/SIZE]

and add the new flags to it so it looks like:-
[SIZE="3"]
# defoptions=quiet splash noapic irqpoll noirqdebug[/SIZE]

so the flags get carried through each time the kernel is upgraded.

[SIZE="5"]2. Broadcom Wireless[/SIZE]
I spent ages following guides to get a wireless speed that 1/2 worked 1/2 didnt depending on the weather outside. 

I've found that the latest bcm43xx-fwcutter in the repos works a treat. When i had wireless set to roaming it would take ages to connect to wireless sites but when not in roaming its works fine!

so in terminal copy and paste:-
 
[SIZE="3"]sudo apt-get install bcm43xx-fwcutter[/SIZE]

the wireless light should come on and we're most of the way there! just go into "System---> Administration---> Network" and turn roaming mode off and setup your network settings as normal. I restarted at this point but i doubt you'd need to and your wireless should be working!! 

Hurray! for those who aren't interested n the nvidia drivers or beryl / compiz then this is your laptop is setup!

[SIZE="5"]3. Nvidia Drivers[/SIZE]

The drivers in the repos or automatix or the envy script or using the restricted drivers management tool didnt work at all for me.

manually installing the drivers from the nvidia website worked fine though!!

[SIZE="3"]http://www.nvidia.com/object/unix.html[/SIZE]

so download and install using the instructions! 

[SIZE="3"]--edit:- since this isnt as easy as it sounds for some new users heres it explained--[/SIZE]

you may want to take note of these commands as the involve shutting down the graphical part of ubuntu and going to the complete commandline:-

1. Download the latest drivers from the link above (not the legacy ones) save them to your home folder
2. Press together:- Control, Alt and the "f1" keys.
3. On the new screen login with your username and password
4. Type the following command to stop the graphical display:
[SIZE="3"]
sudo /etc/init.d/gdm stop[/SIZE]

5. type "ls" at the prompt and look at the nvidia driver filename to complere to the following to run the nvidia install script :

[SIZE="3"]sudo sh NVIDIA-Linux-i386-etc-etc-etc.run[/SIZE]

6. Follow the on screen instructions and install the driver then exit
7. Back at the terminal type the following to restart the graphical display with the new drivers loaded :D

[SIZE="3"]sudo /etc/init.d/gdm restart[/SIZE]

wow almost done!!

--EDIT--

The latest NVIDIA driver seems to default to 16 bit depth but beryl requires 24 bit so to change this do the following

[SIZE="3"]sudo gedit /etc/X11/xorg.conf[/SIZE]

find the "screen" section and change the value of the default depth from 16 to 24 so it now looks like this:
[SIZE="3"]
 Section "Screen"
	**Defaultdepth	24**

[SIZE="5"]4. Beryl[/SIZE]

I installed beryl from the repos as normal which worked fine, in terminal:-

[SIZE="3"]sudo apt-get install beryl-manager beryl emerald-themes[/SIZE]

i then started using trevinos beryl repo at

[http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)

The only issues i had with beryl is that after having a few windows open i would occasionally get a white screen pop up, this was fixed and has been fine (so far!!) by changing 2 settings in the beryl manager.

1. Open beryl manager
2. Go to advance beryl options
3. Change Composite Overlay Window From automatic to "use cow"
4. Change Rendering platform from automatic to "Force AIGLX"

then voila everything should be working fine!!

--EDIT--

if the above doesnt work try using:-

[SIZE="3"]sudo nvidia-xconfig --add-argb-glx-visuals[/SIZE]

if you have any more info or things that you think need changing let me know and ill amend this howto!

good luck guys (and gals)  let me know how your experiences went with this!

---

### Post by joaoeb on 2007-06-04
Tanks, worked like a charm. But wold be a good idea to alter the menu.lst to the ones sugested by MobiuzNZ in this thread: [http://ubuntuforums.org/showthread.php?t=457864](http://ubuntuforums.org/showthread.php?t=457864)

---

### Post by luscinius on 2007-06-04
Thanks! I also had problems with Compaq V6000 and GeForce Go 6150 (64bit Ubuntu); tried to install nvidia-glx, and it had no effect. Same with restricted drivers manager. Finally installed driver directly from nvidia, and it seems to work.:)

---

### Post by Tagallo on 2007-06-06
Hi, i have everything working fine here, im booting without "noapic irqpoll noirqdebug" flags and it works ok, can anyone please explain to me exactly what those options means? Should i use then?

Thanks
Thiago

---

### Post by soapytheclown on 2007-06-06
> **joaoeb said:**
> Tanks, worked like a charm. But wold be a good idea to alter the menu.lst to the ones sugested by MobiuzNZ in this thread: [http://ubuntuforums.org/showthread.php?t=457864](http://ubuntuforums.org/showthread.php?t=457864)


ahh yeah i will do i wrote this a couple of weeks ago before he'd suggested that and the thread only just got approved so ill ammend it now ;)

---

### Post by rosshkhk on 2007-06-10
Hi,

Thanks for these instructions: they got me off to a good start. However, I am stuck at the nvidia section. I have tried using restricted drivers manager, automatix, envy and the nvidia installer, but i keep getting the same result, which is broken x. It dumps me out when I should see the login screen, and the dialogue says it can't find the specified device (nVidia Geforce Go 6150, which is on a PCIe bus).

I will include the relevant xorg contents for working config:

----
Section "Device"
        Identifier      "nVidia Corporation C51 [Geforce 6150 Go]"
        Driver          "nv"
        BusID           "PCI:0:5:0"
EndSection

----

and not working config:

----
Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nvidia"
EndSection
----

I have tried entering the BusID, but to no avail. The odd things is that it appears that whether or not I specify the BusID the X crash output shows that it is looking for the device on a different BusID.

Any help would be much appreciated.

Thanks

Ross

---

### Post by soapytheclown on 2007-06-12
Hi ross,

like it says in the tutorial for some reason installing t he nvidia drivers the "normal" way so you have to go to the nvidia website more specifically this page: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) then install the driver using their instructions. The only problem ive had using this method so far is that every time you install a new kernel you need to reinstall the nvidia driver, if anyone has a fix for this please let me know.

hope that helps you though :D

if you need a bit more help on how to exactly get the driver installed let me know.

---

### Post by rosshkhk on 2007-06-12
soapy,

I messed around and eventually realised that I had initiall used nolapic because noapic did not seem to work. I was tipped off by the xorg message I started to get (but not initially for some reason) talking about edge-triggered interrupts. So I follow around some forums and then went back to noapic. This seems to have worked, and can no boot up and get into an x session and nvidia settings is showing loads of options.

The inbuilt compiz stuff is not working, but I think this might be to do with the color depth. I will try and reset this, and then reboot and see what happens. Will also give beryl ago tomorrow, as prefer it over compiz.

Time for bed soon, otherwise work tomorrow will be a nightmare!

**Thanks for the awesome tutorial, and quick follow up. You are a credit to the open source community.**

Ross

---

### Post by rosshkhk on 2007-06-12
soapy,

OK compiz and beryl both have the same problem, which is that I don't get the window border/frame, and the top bar with the minimise, restore and quit buttons. Also, terminal appears as a white box.

The other aspects of beryl, such as the cube desktop, wobble etc seem to be working fine.

This is no biggy, as priority was nvidia driver so I could use a second monitor, but would be cool to have to show non-linux people how great linux is!

Thanks again.

Ross

---

### Post by soapytheclown on 2007-06-12
using 64bit i presume,
read the bottom of the tutorial ;)

---

### Post by rosshkhk on 2007-06-14
soapy,

I followed the instructions regarding cow and at the bottom of your tutorial, but to no avail. I still lose the edges of windows, and terminal comes up white. I have tried the beryl site's installation script as well as loggin in with an xgl session, but all with the same results. With compiz, the screen just goes white and the session becomes non-responsive (have to ctrl-alt-backspace to log out).

Any suggestions?

Ross

---

### Post by rosshkhk on 2007-06-14
soapy,

I got it going with sudo nvidia-xconfig --add-argb-glx-visuals.

Thanks for all the help!

Ross

---

### Post by soapytheclown on 2007-06-14
ooohhh i didnt have to do that on mine, but iw as actually refering to changing the colour depth from 16 to 24 bit the last 2 installs ive done using the latest nvidia driver have in both cases (i386 and AMD64) defaulted to 16bit depth where as beryl needs 24 and that solved my problem both times.

---

### Post by rosshkhk on 2007-06-14
I did change the color depth first, but that didn't do it. Perhaps we have different graphics cards. Mine is a Geforce Go 6150. Is argbglxvisuals set in your xorg.conf or not? I am wondering if nvidia-xconfig did it automatically for yours and not for mine, or if yours is not set at all...

Ross

---

### Post by rosshkhk on 2007-06-16
I decided that the application issues with 64-bit Linux make using it on the desktop a poor decision, so I have reverted to the i386 version. Too many key apps are unavailable in the distros, or you get older versions, or there are hacks to get things to work. AMD64 should work well on the server side I guess.

When installing i386 I could not boot the Live CD version, even with the noapic irqpoll boot options, so did a text install. This worked great, and I put the two options in on first boot and then wrote them to /boot/grub/menu.lst.

---

### Post by soapytheclown on 2007-06-17
> **rosshkhk said:**
> I decided that the application issues with 64-bit Linux make using it on the desktop a poor decision, so I have reverted to the i386 version. Too many key apps are unavailable in the distros, or you get older versions, or there are hacks to get things to work. AMD64 should work well on the server side I guess.

When installing i386 I could not boot the Live CD version, even with the noapic irqpoll boot options, so did a text install. This worked great, and I put the two options in on first boot and then wrote them to /boot/grub/menu.lst.

same reason i reverted to the i386,as for the graphics settings well  ive checked my Xorg.conf and i have the same card go 6150 and i havent had to enable that option interesting, i will test it out on mine see if it makes a difference and i will more than likely add it do the how to incase other users have the same problem

---

### Post by josel777 on 2007-06-21
> **soapytheclown said:**
> using 64bit i presume,
read the bottom of the tutorial ;)

Great tutorial. However, I can't find any reference to 64 bit Ubuntu.

---

### Post by soapytheclown on 2007-06-22
> **josel777 said:**
> Great tutorial. However, I can't find any reference to 64 bit Ubuntu.

i changed it since everything for me worked with 64bit too :) it was originally about the colour depth changing part in xorg for allowing beryl to run i thought it a 64bit version problem but it turns out to be something to do with the new nvidia driver

---

### Post by AvalonSkies on 2007-07-03
Great howto, thanks. The lack-of-WiFi was irking me. :D

---

### Post by soapytheclown on 2007-07-08
> **AvalonSkies said:**
> Great howto, thanks. The lack-of-WiFi was irking me. :D

thanks! i tried the latest gutsy release tribe 2 and they've included broadcom drivers (which work!!) into the restricted drivers manager so it should be even easier when its time to upgrade, boot options are still the same lets hope theyre fixed for the final release, and off memory (im in spain atm) the nvidia driver in the restricted drivers section works too, i will update the how to for compiz fusion when i get back in the next few days :D

---

### Post by ToNiuSKaS on 2007-07-09
No problem at wifi/nvidia drivers instalation but didn't manage to enable hibernation.

Any ideas??

My laptop is Compaq Presario V6025EA

---

### Post by soapytheclown on 2007-07-13
nope not a clue at the moment i presume its one of the things affected byt the noapic switch, and is it just me or does anyone else get crap battery life im talkign about 20mins ish the pc saying one second its got 3243242 hours of life left then the next 3 mins left?

---

### Post by sparks0548 on 2007-07-22
Man thanks so much for this post.  I was pulling my hair out with my 6150.  I have all my effects, I can use the downloadable themes, I just can't get the cube to work.  That's ok I can fix that later.  Not a show stopper.

I had to bookmark this forum since it was so informative.

Thanks again.

---

### Post by Oofda33 on 2007-07-27
Thank you for the great work soapytheclown!  I had a coworker buy a new Compaq Presario and asked if I would install linux for him.  I guess I am the expert here since I know what linux is :).  I am really pretty much a noob though.  I followed your guide and had his laptop purring except the wireless.  I can't for the life of me make it work.  Is there a step by step process to follow?  Any help is greatly appreciated.

*edit* I just did a fresh install of Ubuntu 7.04 and went straight to the Administration>Network Settings and there is no wireless icon there.  should there be one there?

*edit 2*  I did a " lspci | grep Broadcom\ Corporation" and got the following:

03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)

Hope this helps.


*edit 3*  I just did a fresh install.  I have done it 3 times now with the same results...Install Linux, that works fine.  Install Nvidia drivers and when I restart I get a X-server crash, best I can tell it's something about Nvidia versions.  If I reload the nvidia drivers the way you show on page 1 then I can restart the x-server.  but if I reboot again then it crashes again.  It worked last week, twice, just fine.  not sure what has changed in the past week.

---

### Post by soapytheclown on 2007-07-29
> **Oofda33 said:**
> Thank you for the great work soapytheclown!  I had a coworker buy a new Compaq Presario and asked if I would install linux for him.  I guess I am the expert here since I know what linux is :).  I am really pretty much a noob though.  I followed your guide and had his laptop purring except the wireless.  I can't for the life of me make it work.  Is there a step by step process to follow?  Any help is greatly appreciated.

*edit* I just did a fresh install of Ubuntu 7.04 and went straight to the Administration>Network Settings and there is no wireless icon there.  should there be one there?

*edit 2*  I did a " lspci | grep Broadcom\ Corporation" and got the following:

03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 03)

Hope this helps.


*edit 3*  I just did a fresh install.  I have done it 3 times now with the same results...Install Linux, that works fine.  Install Nvidia drivers and when I restart I get a X-server crash, best I can tell it's something about Nvidia versions.  If I reload the nvidia drivers the way you show on page 1 then I can restart the x-server.  but if I reboot again then it crashes again.  It worked last week, twice, just fine.  not sure what has changed in the past week.

hi there, i have actually removed ubuntu off my laptop for the time being since its too much of a pain in the **** for me atm although i am testing each gutsy tribe release to see if there have been sufficent improvements to warrant a reinstall for longer than a week on it.

firstly i have no idea why your 3rd install is being so werid and can only suggest a reinstall unfortunatley.

installation of the broadcom drivers was literally as i wrote in the tutorial, youre going to need to be hardwired into the net then open a terminal and copy and paste:-

sudo apt-get install sudo apt-get install bcm43xx-fwcutter 

i didnt have to restart but maybe you could try from that point, sorry i cant be of much more help atm, we're going to have to hope that the devs do something about this compaq situation!

---

### Post by paulok64 on 2007-08-06
This Thing Has been a Nightmare. I Don't Believe It's a Ubuntu only problem as far as the Dell wireless 1390 adapter. I  Have read alll the post in other distros as well as the package maintainers web site. It seems the fixes work for some and not for others. The fix worked for me the first time I tried it. I rebooted my machine several times and all worked well. Then I did exactly as was told in The Nvidea section and ran into problems as I needed the GCC Installation Utilities package. I got package but have forgotten its name. I then ran Nvidea install as Instructed and seemed to work fine but upon reboot my X server wouldn't come up. I tried several of the fixes from people who had the same problem to no avail. I Reinstalled system and then I couldn't get the wireless fix to work. I am going to try reinstallation a couple of more time to see if i can get wireless working again and then I'll leave well enough alone but I GURANTEE I will not buy another Compaq Laptop and will make sure next computer doesn't have a wireless adapter from Broadcom. I may keep fighting this thing or Just give up and put windows back on and keep on enjoying Ubuntu on Desktop PC. 

This is a re edit as i wanted to post the bcm43xx error: subprocess post-installation script returned error exit status 255.

---

### Post by paulok64 on 2007-08-07
I think my problem was that the place bcm43xx-fwcutter was trying to get its firmware from is a bandwidth limited server. When I tried downloading  it manually it wouldn't let me onto site. Wireless is working fine now. I found another sight. I just wasn't patient enough.

Thank you for a well written guide. Now to do battle with the Nividea driver

if others are having problems with exit 255 or need the firmware for this card  [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o) worked for me

---

### Post by soapytheclown on 2007-08-07
yep the broadcom chipsets from what i can tell are notoriously shite in linux, i literally tested every distro i could get my hands on jsut to get this laptop working, the only one that got it close out of the box was Sabayon 3.3, booting, wireless, graphics, beryl no configureing at all, although i was very dissapointed with the 3.4 release failing to even boot on my or my brother desktops. Ive been trying to flog this laptop since january with no luck so yep from me a definate no to a future compaq machine also!

---

### Post by Ejene on 2007-08-08
I was able to get my nvidia card to work (although I'm risking it and using envy, just so my wide screen works). However, I'm having trouble with the wireless card. I did the apt-get only to see

Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
00:14:49 ERROR 404: Not Found.
way 
dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any advice? I'm incredibly new to ubuntu and still trying to learn my way around the command lines and all.

---

### Post by keflavich on 2007-08-08
Has everyone been successful with the bcm43xx-fwcutter drivers on Feisty?  Running Edgy on the v6000, most people reported that that driver either failed completely or went extremely slowly and only ndiswrapper would work correctly; that was also my experience.

Also, does sound work correctly (including the headphone jack) with this install process?  I'm considering the upgrade to Feisty, but I don't want to do it if it will kill my wifi or sound.

Thanks,
Adam

---

### Post by paulok64 on 2007-08-08
Do a Google on Broadlink Ubuntu I couldn't find thread off hand but they all say about the same thing you can ignore the error messages . The bcm43xx.fwcutter was installed. The deal is the firmware needed is at a site thats bandwidth limited. Follow my link for the firmware then use the bcm433xx.fwcutter to extract the files from the file at that link to your /lib/firmware directory. I forgot the Syntax but its basically extract files from this file and place in that directory. If Bradcom Ubuntu doesn't do it add presario to the google the post that explained it all was like 60 pages long but all you really need is any link that explains how to do the extraction. Then you run modprobe and your done. Follow this link before you do though I gave up on the bcm43xx.fmcutter route and gonna use the ndiswrapper route [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) .From what i understand this is much more stable . Hope it helps

Sorry i Did't reply to private message my pop up blocker stopped it and ill be danged if I can figure how to get it back

---

### Post by paulok64 on 2007-08-08
PLEASE GUYS follow the above thread. I now have wireless on my Presario V6000. It works flawlessly. Network manager seems to be all i need to find networks and switch between my hard wire and wireless. I download at speeds close to my cable connection with wireless after I followed the above walk Through. It meant a clean install but its worth every minute of it.

---

### Post by pissedoffdude on 2007-08-09
I get an error while trying to install bcm43xx-fwcutter that says ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--12:55:57--  http://boredklink.googlepages.com/wl_apsta.o
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 72.14.203.118
Connecting to boredklink.googlepages.com|72.14.203.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
12:55:57 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Can someone help me out with this?

---

### Post by paulok64 on 2007-08-10
I Sent you a private message but figured id post the link for all. I found the thread that explains how to install bcm43xx.fmcutter firmware manually.

 [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) 

The reason for your error messages is the script in the installer for the bcm43xx.fmcutter  firmware points to a site that is rarely up so you gotta get the file yourself and do it by hand.

---

### Post by redpiersystems on 2007-08-13
Hi, i have a Compaq Presario v6000....and i only got Ubuntu 7.10 tribe 4 to boot once...*and only once*....tried the previous versions too...no dice. I dont even know what comination of flags got it to work. (of course fwcuter couldnt help me w/ the broadcom wireless)

Thanks for the thread...but i cant boot the live cd. I keep getting errors when the livecd is booting up, and tries to read "hda" (aka, the DVD/CD rom drive).

I get these errors:

hda: cdrom_decode_status: error=0x51 { DriveReady SeekComplete Error}
hda: cdrom_decode_status: error=0x40 { LastFailedSense = 0x04 }
ide: failed opcode was: unknown


..and...


ide_intr: huh? expected NULL handler on exit


...ive tried adding nolapic irqpoll noirqdebug after the --, (also, i added live acpi=off)

still, no dice. Can anyone help me out? im a noob at linux, but i suspect the CD isnt recognized due to some kinda flag (either cause its missing, or cause its in ther)


:popcorn: Thanks!

EDIT: Also...some comination of flags gets it to boot...but GNOME never loads...the only thing that shows is that brown-orange background and a mouse cursor. Go figure. :P

---

### Post by p-stone on 2007-08-13
I'm tearing my hair out here. My girlfriend has a presario v6000 (I'm at work right now and can't check the exact version) Which I actually got up and running without the acpi flag by using the alternate install disk for a text mode install. Unfortunately a chance slip on the keyboard at the GRUB screen got me booted into the recovery partition, which in turn messed up my MBR and gave me the dreaded GRUB 17 error. So I reinstalled, this time completely wiping windows and the recovery disk off the machine. This time though I cannot get the machine to boot. The loader graphic comes up and about halfway through the screen just goes black, an issue I assume is associated with the acpi flag issue that so many other posters have encountered. What's really confusing me is that I've added this flag into GRUB exactly as it describes in the initial post but to no avail. I get the same error. Again I want to mention that installing off this same disk has worked in the past without even using the acpi flag and it's also booted with that flag as after reading this tutorial I added it as a precaution. I can't for the life of me figure out what could be different this time around. Any advice or suggestions would be greatly appreciated as right now I'm somewhat in the doghouse for bricking the girlfriends shiny new laptop, hardly a ringing endorsement for linux I'm afraid.

Thanks again in advance for any assistance

---

### Post by soapytheclown on 2007-08-14
> **p-stone said:**
> I'm tearing my hair out here. My girlfriend has a presario v6000 (I'm at work right now and can't check the exact version) Which I actually got up and running without the acpi flag by using the alternate install disk for a text mode install. Unfortunately a chance slip on the keyboard at the GRUB screen got me booted into the recovery partition, which in turn messed up my MBR and gave me the dreaded GRUB 17 error. So I reinstalled, this time completely wiping windows and the recovery disk off the machine. This time though I cannot get the machine to boot. The loader graphic comes up and about halfway through the screen just goes black, an issue I assume is associated with the acpi flag issue that so many other posters have encountered. What's really confusing me is that I've added this flag into GRUB exactly as it describes in the initial post but to no avail. I get the same error. Again I want to mention that installing off this same disk has worked in the past without even using the acpi flag and it's also booted with that flag as after reading this tutorial I added it as a precaution. I can't for the life of me figure out what could be different this time around. Any advice or suggestions would be greatly appreciated as right now I'm somewhat in the doghouse for bricking the girlfriends shiny new laptop, hardly a ringing endorsement for linux I'm afraid.

Thanks again in advance for any assistance


just a quickie, its "apic" not "apci" so maybe a typo? also if your g/f took note when she had the mahcine she'd have made the recovery disks which restore to a factory default including the recovery partition! prehaps they may be in order for the time being!




to everone else having problems id prehaps wait untill gutsy final like me or brave the beta versions, my last play about with the latest one forget the name are we at 3 now?? seemed stable which i used for over 2 months but WOW played at stupidly slow frame rates so i went back to fiesty, although that was on my linux friendly desktop! im sure the 4th one will be out soon so ill defo be having a look and letting you know how it goes

---

### Post by p-stone on 2007-08-14
Soapy -
I hang my head in shame. I somehow repeatedly read noapic as noapci, perhaps I have mild dyslexia. Anywho thanks so much for the support, on to the rest of the guide for me.

---

### Post by redpiersystems on 2007-08-14
Well...i guess 7.10 only booted 1nce (live cd, amd 64 bit)...
But... 7.04 booted with soapy's info....Thanks Soapytheclown!

---

### Post by Criminosis on 2007-08-16
Just a suggestion. Your way soapy didn't do too well for me (I only got 11 Mb/s no matter what I did) and at times it would break and i'd have to do an unbearing number of reboots to get connected again.

I found this :

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I just installed it, but immediately (it was all automatic, I just clicked and let it run) after the reboot, I was connected at 54 Mb/s. Little bit of an improvement. As far as stability, i'll come back on that after I've tried it for a week or so.

---

### Post by randall_l on 2007-08-17
Has anyone had any luck getting the IR port usable?  It's the only thing that I didn't resolve in the first week (purchased in March, 2007).

Thanks in advance,
Randall

---

### Post by soapytheclown on 2007-08-18
> **redpiersystems said:**
> Well...i guess 7.10 only booted 1nce (live cd, amd 64 bit)...
But... 7.04 booted with soapy's info....Thanks Soapytheclown!

today i sucessfully booted and installed the i386 ed of tribe 4 everything went perfectly, used the exact same boot flags as before, only thing i came across was the broadcom firmware, as discovered a few posts up the link it points to to fetch is down, however after a full upgrade whilst being hardwired in and running the restricted device manager the link has been updated so all is good, using the glx-new nvidia module in the repos works for the graphics not the one reccoemended by the RD manager. Compiz fusion works flawlessly and looks fantastic. No idea why you had any problems maybe cause it was amd 64? but looks like gutsy is getting there for us!

---

### Post by redpiersystems on 2007-08-27
> **soapytheclown said:**
> today i sucessfully booted and installed the i386 ed of tribe 4 everything went perfectly, used the exact same boot flags as before, only thing i came across was the broadcom firmware, as discovered a few posts up the link it points to to fetch is down, however after a full upgrade whilst being hardwired in and running the restricted device manager the link has been updated so all is good, using the glx-new nvidia module in the repos works for the graphics not the one reccoemended by the RD manager. Compiz fusion works flawlessly and looks fantastic. No idea why you had any problems maybe cause it was amd 64? but looks like gutsy is getting there for us!

Yes, i was trying to install the AMD 64 bit version. Im currently stuck with the nvidia install crapping out the X server (i downloaded directly from the nvidia site, got the build-essential header stuff, ...no dice) :popcorn:

---

### Post by soapytheclown on 2007-08-27
glx-new from the repo not working for u either?

---

### Post by soapytheclown on 2007-08-29
another quick one, are u sure your getting the correct install file from memory i ended up downloading the wrong file a couple of times so check ur getting the actual amd64 installer from nvidia, just incase like :)

---

### Post by redpiersystems on 2007-08-29
> **soapytheclown said:**
> another quick one, are u sure your getting the correct install file from memory i ended up downloading the wrong file a couple of times so check ur getting the actual amd64 installer from nvidia, just incase like :)

I am absolutly certain. i did not instal the IA64, i specifically installed the AMD64 stuff directly from nvidia's unix page.

---

### Post by blk03mitsues on 2007-08-31
I'm a noob, i tried to follow the instructions. i'm actually posting on my my V6000, with the wireless connection..... but i'm having issues installing the nvidia drivers.

i installed the non 64-bit version of Linux Mint instead of feisty but everything has seemed to work well with the tutorial. i downloaded the nvidia driver "Linux IA32" V 100.14.11 and not the legacy ones as mentioned in the tutorial. i installed it like it said in the tutorial, Beryl even worked cus i made the change to 24bit. but when i restarted the laptop, the screen was all messed up and it made me go into a xorg log that didnt even looked right cus it was just a bunch of weird characters but it did say something about nvidia drivers not working or something and something like "no display is present"

did i just download the wrong nvidia driver? i also noticed the driver's name from nvidia dont look like the one posted in the tutorial...nvidia-i380.....

---

### Post by soapytheclown on 2007-09-01
no idea why if you're definatley using the 32 bit install which is what i presume you mean when you say non-64bit.

the driver name looks like its been changed since i wrote the tutorial but could someone doing a new install check if nvidia-glx-new in the repos works for feisty now or are we still having to get the driver direct from nvidia? 

prehaps you could test it out for us hey ;)

---

### Post by redpiersystems on 2007-09-03
:popcorn:
Hey guys!** Ubuntu Gutsy Gibbon Tribe 5 (amd64 bit)** installs on my Compaq Presario v6000...and got Flash 9 to work on firefox using the nspluginwrapper library.

I used the method stated by SoapyTheClown to boot off the live CD (once again, Thanks Soapytheclown!)

1) When the CD boots up, press F6, and delete the 3 extra thingies at the end ("quite splash --")

2) go to the very start of that line (press the Home key), and add the following:
      "noapic irqpoll noirqdebug " (without the quotes)

3) Press Enter!

****NOTE: if you keep getting SquashFS errors, and you burned that live cd with the built-in CD/DVD burner of this laptop ....then its because the built-in CD/DVD burner that comes with this laptop is crap and made a crappy iso burn.... do yourself a favor and get an external USB 2.0 CD/DVD Burner, use *that* to make your Ubuntu live cds.*

4) Once the live session is up and running, DO NOT install/enable any of the RESTRICTED driver junk...it doesn't work, and the nvidia stuff will kill your Xorg server thingy..... Instead, just install  using the "Install" link on the desktop (its ubiquity)

[I]***NOTE2: if the Ubiquity install process complains about not being able to unmount the "migration assistant" volume, [B]DO NOT click on "Go Back"....instead, just click "Continue"
[/B][/I]
5) Once the install is done, it will ask you if you want to continue with the Live Session, or Restart. **DO NOT RESTART YET**!!!!!!!!!!

...You must make a quick edit to /boot/grub/menu.lst
Simply open up Applications>Accessories>Terminal and type the following (**replace sda1 with the volume where  Ubiquity installed to**):

      ```
sudo gedit /media/**sda1**/boot/grub/menu.lst
```

...Then, go to the line that starts with "kernel"...:


```
title		Ubuntu, kernel 2.6.22-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=ebbc6eeb-882a-4004-9402-d2d40bd7a726 ro quiet splash
initrd		/boot/initrd.img-2.6.22-10-generic
quiet

title		Ubuntu, kernel 2.6.22-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=ebbc6eeb-882a-4004-9402-d2d40bd7a726 ro single
initrd		/boot/initrd.img-2.6.22-10-generic
```

...and append "noapic irqpoll noirqdebug" to the end, like so:

```
title		Ubuntu, kernel 2.6.22-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=ebbc6eeb-882a-4004-9402-d2d40bd7a726 ro quiet splash noapic irqpoll noirqdebug
initrd		/boot/initrd.img-2.6.22-10-generic
quiet

title		Ubuntu, kernel 2.6.22-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-10-generic root=UUID=ebbc6eeb-882a-4004-9402-d2d40bd7a726 ro single noapic irqpoll noirqdebug
initrd		/boot/initrd.img-2.6.22-10-generic
```

6) Save and exit the text editor. **DO NOT REBOOT BY USING THE SHUTDOWN ICON** in the top menu! This will screw up and not reboot correctly. Instead...type the following into your Terminal:

```
sudo shutdown -r now
```


...and there you have it...when you reboot, your notebook should now have  Ubuntu Gutsy Gibbon Tribe 5 (amd64 bit) running!

******FINAL NOTE1: Do not use the bcm43xx-fwcutter thingy..it just dies intermittently.... instead, use  [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=297092"). You'll thank yourself for it.***

******FINAL NOTE2: To install the nVidia Stuff, follow the instructions soapytheclown stated on page 1 of this thread.(After installing the nvidia drivers, the font DPI gets bigger for some reason)***

******FINAL NOTE3: To install Flash 9, use System>Administration>Synaptec Package Manager in your newly installed Ubuntu system, and install the nspluginwrapper plugin...*THEN* run the [Flash 9 Install Script for AMD64]("http://ubuntuforums.org/showthread.php?t=476924") for Feisty. EVEN THOUGH THE THREAD SAYS IT WONT WORK ON GUTSY, IT SHOULD WORK ANYWAYS IF YOU INSTALL THE NSPLUGINWRAPPER FIRST VIA SYNAPTIC, AND RUN THE SCRIPT SECOND!.***

:popcorn:

---

### Post by blk03mitsues on 2007-09-04
> **soapytheclown said:**
> no idea why if you're definatley using the 32 bit install which is what i presume you mean when you say non-64bit.

the driver name looks like its been changed since i wrote the tutorial but could someone doing a new install check if nvidia-glx-new in the repos works for feisty now or are we still having to get the driver direct from nvidia? 

prehaps you could test it out for us hey ;)

i downloaded the nvidia-glx-new from the repos and going to restart right now and change it to 24bit if i have to.

---

### Post by blk03mitsues on 2007-09-04
well i did, i dont see any nvidia utilities like before but beryl starts now, thats how i know something changed, before i would just get a white screen.

but i dont see any beryl effects.....no emerald themes, no cube, no nothing.

i manually changed the screen resolution in Xorg to 24 bit. think the nvidia files in repo still not working?

---

### Post by soapytheclown on 2007-09-04
did you check in beryl manager to see if metacity or beryl is checked?

---

### Post by El Rogueo on 2007-09-09
If this isn't a sticky it should be, and if it is more people need to see it, myself included ;)

It looks like such a common problem, thanks for posting an easy solution!

---

### Post by 1337_ubunutu_teen on 2007-09-10
Soapy,
Found info on the Compaq 6715b..
Click this thread to follow
<url>http://ubuntuforums.org/showthread.php?t=488332&page=2</url>
Thanks for your help though...:lolflag:

---

### Post by 1337_ubunutu_teen on 2007-09-10
What about Beryl for ATI Radeon???

---

### Post by soapytheclown on 2007-09-11
no idea how that link u posted is relevant to be honest but when i wrote this tutorial i had no idea there were v6000's with x1250 or ati chipsets to be honest, i did a forum search and i found this

[http://ubuntuforums.org/showthread.php?t=503695&highlight=ATI+Radeon+X1250](http://ubuntuforums.org/showthread.php?t=503695&highlight=ATI+Radeon+X1250)

hope it helps

---

### Post by p-stone on 2007-09-22
Is anyone else having issues with fsck failing? I've had it happen to me twice now, fcsk comes up, begins a scan and at an apparently random interval hangs. There doesn't appear to be a pattern in where in the disk check it fails, I've seen it get as high as 47% and fail as low as 0.9%. I don't think it's a disk failure issue. The last time it happened I just reinstalled, but since it's happened again it's apparent that is not a permanent solution. I found on a previous thread how to disable fsck
> 
To decide if you want fsck or not:
```

sudo gedit /etc/default/rcS
[/code.
Now change the FSCKFIX line to the following:

[code]
FSCKFIX=yes or no if you don't want it to run

```
To decide how often you want check disk:
```

sudo tune2fs -c 50 /dev/hdax

```
- change the 50 value to whatever
- change the x to whatever you get running sudo fdisk -l

but I can't figure out a way to get my computer up to the point where I could make that change. Booting from a live CD doesn't give me access to the current file system as far as I can tell. If it really comes down to it I know I can always reinstall but I'd really prefer not to go down that road as I finally have everything else on the lappy working the way I want. Suggestions would be greatly appreciated

---

### Post by soapytheclown on 2007-09-22
never had that hppen although everytime i installed feisty as a whole (desktop or laptop) i usually got atleast one fsk check being done on first boot sometimes up to 3 (i have 3 hdd's in my desktop) but each check requiring a reboot, no idea why though didnt seem to happen in the gutsy installs from what i can remember.

im pretty sure u can mount the filesystem from within a live cd ive done it many times before to rescue data although its late and i cant for the life of me remmber the mount options for an ext3 drive just search for it then turn the check off???

btw guys after 9 months of dealing with this hastle ive managed to flog this laptop to my girlfriends sister for £250 half what i got it for :(  and invested in a tasty Dell Vostro 1700 so after the 6th of october i wont be able to continue testing this laptop infact ill be laptop-less till october 26th since there is such a damnd for these dells but just intime for gutsys release and since illbe dual booting on there im sure ill ceom across some problems i wish u gusy the best of luck with this lappy and ill be checking back now and then to see if there is anything else i can help you with :)

---

### Post by MOkAONE on 2008-03-15
after i try to install the wireless drivers (*sudo apt-get install bcm43xx-fwcutter*) i get this message. any suggestions (btw... still ned to the OS)

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcm43xx-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up bcm43xx-fwcutter (006-1) ...
--11:10:03--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
           => `wl_apsta.o'
Resolving boredklink.googlepages.com... 209.85.141.118
Connecting to boredklink.googlepages.com|209.85.141.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:10:03 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by soapytheclown on 2008-03-20
hey lucky i checked back!! yeah..

HTTP request sent, awaiting response... 404 Not Found
11:10:03 ERROR 404: Not Found.

the link your trying to download from is dead so you'll need to do a google search for "wl_apsta.o" which is the file you're after =) if you install the package through synaptic i THINK (not sure been a long time) that it lets you specify the source to download from so try that and point it to one you find on the net. 

are you still using fiesty btw cause im 99% certain that gutsy had an updated download link to get this file from

---

