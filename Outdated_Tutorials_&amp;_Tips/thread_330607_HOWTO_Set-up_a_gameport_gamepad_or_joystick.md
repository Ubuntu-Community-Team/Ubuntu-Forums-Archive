---
title: "HOWTO: Set-up a gameport gamepad or joystick"
date: 2007-01-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Extreme Coder on 2007-01-03
Hi everybody. I had some hard time figuring out how to setup my gameport gamepad to work in Ubuntu. But finally, I think I figured it out. I am writing this so that other members do not hit their heads in the wall, like I did:) So without any further ado,



[B]1) First, we need to check if the gameport module is already loaded.
[/B]In a terminal, type the following:
```
lsmod
```It should display a list of the currently loaded modules.
One of the lines should begin with 'gameport'
My line looked like:
```
gameport               17160  2 snd_es1938
```If you didn't find any similar line, look for the way to enable the gameport for your specific sound card in the list below.

[B]2) Now, we need to setup the gamepad/joystick.
[/B]Again in a terminal, type the following:
```
sudo modprobe joydev
```Then, from the list at the bottom, load the right module for your type of gamepad/joystick.

**3) Testing ****and calibrating **[B]the gamepad/joystick.
[/B]If you want to check if everything's working correctly or/and you want to callibrate your device, you can either try out jscalibrator, or if you're using KDE, run kcontrol from the terminal, and in the Peripherals section, there is a joystick calibrator. You can install jscalibrator by searching for it in the Synaptic package manager, or by typing in a terminal:
```
sudo apt-get install jscalibrator
jscalibrator
```A new window should appear which should allow you to test and calibrate your device.

**4) Setting the modules for**** the gamepad/joystick permanently.**
After you figured out what modules work for your gameport and pad or stick, you need to make these modules load every time you boot the PC, or else you will have to type all the commands again every time you reboot.

Begin by doing the following:

If you're using GNOME:
```
sudo gedit /etc/modules
``` 
If you're using KDE:
```
sudo kwrite /etc/modules
```
If you're using XFCE:
```
sudo mousepad /etc/modules
```
Then in the text editor, type the following after the last line in the file:
```
# Modules needed to set-up my gamepad or joystick
<insert your gameport module here>
joydev
<insert your gamepad/joystick module here>
```So for example, if I was to set-up a Creative Cobra gamepad on a SoundBlaster Live! gameport, I would write:
```
# Modules needed to set-up my gamepad or joystick
pcigame
joydev
cobra
```And that's it! Don't forget to save the file :)

[SIZE=5]List of gameports, gamepads/joysticks and their corresponding commands:[/SIZE]

[SIZE=4]Gameports:[/SIZE]

-Classic ISA/PnP gameports: 
```
sudo modprobe ns558
```-Crystal SoundFusion gameports:
```
sudo modprobe cs461x
```-Aureal Vortex and Trident 4DWave gameports:
```
sudo modprobe pcigame
```-SoundBlaster Live! gameports:
```
sudo modprobe emu10k1-gp
```-Any other gameports: (If your sound card isn't one of the above and you couldn't find it in lsmod, try this command)
```
sudo modprobe gameport
```[SIZE=4]
Gamepads and joysticks:[/SIZE]

-Analog joysticks and gamepads: (Most gamepads and joysticks, especially generic ones, work well with this one)
```
sudo modprobe analog
```-Assassin 3D and MadCatz Panther devices:
```
sudo modprobe a3d
```-Logitech ADI digital joysticks and gamepads:
```
sudo modprobe adi
```-Creative Labs Blaster Cobra gamepad:
```
sudo modprobe cobra
```-Genius Flight2000 Digital joysticks and gamepads:
```
 sudo modprobe gf2k
```-Gravis GrIP joysticks and gamepads:
```
sudo modprobe grip
```-InterAct digital joysticks and gamepads:
```
 sudo modprobe interact
```-ThrustMaster DirectConnect joysticks and gamepads:
```
sudo modprobe tmdc
```-Microsoft SideWinder digital joysticks and gamepads:
```
sudo modprobe sidewinder
```So what do you think? Constructive criticism is always welcome. If I forgot to write or add anything, please let me know.

I hope it helps anybody, and please post your experiences!


Extreme Coder

---

### Post by binks on 2007-01-08
if anyone wants to use an xbox controller then the command is 


```
sudo modprobe xpad
```

then do jscalibrator

ps cheers for jscallibrator i didnt no of this app its great now i have my xbox pad working in epsxe MINT

---

### Post by hito1 on 2007-01-09
Will it work for USB joysticks?

---

### Post by dragonfixed on 2007-01-09
what is the module for playstation 2 controlers

---

### Post by Extreme Coder on 2007-01-11
binks: Thanks a lot for the xbox module, but doesn't the Xbox controller use some other type of port that needs a converter to USB first? If you're talking about the Xbox 360 controller (which uses USB), then you're right, you only need to modprobe xpad.

hito1: USB joysticks and gamepads work automagically :D in Ubuntu. You can try out jscalibrator on your joystick.

dragonfixed:  There isn't currently a specific module for PS2 controllers, since PS2 controllers don't use a Serial or USB port. But if you're using something like the JoyPad, which outputs USB, then I guess it will work fine.

I would like to know if this guide worked for anyone other than me and my friends :P , so if it worked for you, just post!

---

### Post by dragonfixed on 2007-01-11
> **Extreme Coder said:**
> binks: Thanks a lot for the xbox module, but doesn't the Xbox controller use some other type of port that needs a converter to USB first? If you're talking about the Xbox 360 controller (which uses USB), then you're right, you only need to modprobe xpad.

hito1: USB joysticks and gamepads work automagically :D in Ubuntu. You can try out jscalibrator on your joystick.

dragonfixed:  There isn't currently a specific module for PS2 controllers, since PS2 controllers don't use a Serial or USB port. But if you're using something like the JoyPad, which outputs USB, then I guess it will work fine.

I would like to know if this guide worked for anyone other than me and my friends :P , so if it worked for you, just post!

Thanks

---

### Post by hito1 on 2007-01-11
> **Extreme Coder said:**
> 
hito1: USB joysticks and gamepads work automagically :D in Ubuntu. You can try out jscalibrator on your joystick.


Thanks, it worked, but is there another software besides jscalibrator? It inverted my joystick axis (and I don't think it guessed the right model, mine is like ps2 joystick, I think jscalibrator thinks it's an airplane joystick).

---

### Post by Extreme Coder on 2007-01-12
> **hito1 said:**
> Thanks, it worked, but is there another software besides jscalibrator? It inverted my joystick axis (and I don't think it guessed the right model, mine is like ps2 joystick, I think jscalibrator thinks it's an airplane joystick).

The same case happened with my gamepad, but that was before you callibrate it. After you callibrate it, it works fine. Just try calibrating it ;)

---

### Post by Athanasius on 2007-01-16
What games can you use a gamepad with?  

I want one to work with SuperTux and with the FCEU NES emulator.  What else is there?

---

### Post by FidoNatty on 2007-03-25
Thats great, now I can calibrate my USB Jotstick. BUT I cannot get Linux to find my Gameport joystick!! Its connected to the on-board sound card and works ok in windoze.
The sound chip identifies it self as SiS SI7012.

---

### Post by Kegir on 2007-03-28
did anyone actually get their xbox 360 controller to work?  I followed a couple tutorials but all I get is the light to blink.

---

### Post by tqft on 2007-04-03
Thank-you ever so much I have hunted high and low through just about every menu, setting and program and local help files - but no mention of joystick.

Maybe we should make sure someone higher up the food chain sees this before the next Long Term Stable release is putout - at least some doco on how to get a joystick working on the install disc.

---

### Post by dawynn on 2007-04-14
I own a Champ model JS-308 gamepad.  This thing has to be about as generic as they come.  I did the modprobe joydev analog thing.  (snd_cs46xx was already installed)  When I start jscalibrator, it recognizes that there is some kind of joystick, and it recognizes all 4 buttons on the thing, but the directional pad does nothing.

Jscalibrator claims that I'm using a 4-axis 4-button joystick.  No, its a gamepad.  And for whatever reason, jscalibrator and every other test tool I try will not recognize the directional pad at all.

How do we tell the module to look for a gamepad instead of a joystick?  According to the joystick.txt that I found on the web, we should have been able to do something like this:

sudo modprobe analog js=gamepad

But that returns an error message saying "Unknown symbol in module, or unknown parameter"

Any help is appreciated.  If it matters, I'm a feisty fawn user.

---

### Post by andersja on 2007-04-17
Does anyone know / has anyone tested whether Ubuntu Feisty Fawn supports Gameport to USB converter things by default? A friend has given me his Microsoft joystick + 2 game pads (since he's a Vista-man and they're no longer supported in Vista) and I'm considering buying one of these:

[http://www.maplin.co.uk/module.aspx?ModuleNo=23256&doy=search]("http://www.maplin.co.uk/module.aspx?ModuleNo=23256&doy=search")
(or equivalent)

---

### Post by rasemmi on 2007-04-22
Hiho,

I'm totally addicted to joysticks, I build my own ones, and so tried to make them run under ubuntu 6.06 Dapper Drake. This topic helped me a lot as a starting point - yet I'd like to add a few pieces of personal experience after I solved tihis delicate issue just to use xmame with JOYSTICKS ;).


1) Missing device files  /dev/input/js0 and /dev/js0

Any attempt to use the joysticks failed simply because there were no device files 

 /dev/input/js0 or /dev/js0 

on my system. Even the command "sudo mknod /dev/input/js0 c 13 0" according to [http://www.charmed.com/txt/joystick.txt](http://www.charmed.com/txt/joystick.txt) did not work.

But after I tried a different sound card (with gameport), the command "sudo modprobe analog" automatically generated the files 

/dev/input/js0
and
/dev/input/event3

So it seems that if the command "sudo modprobe analog" does not generate the needed device files automatically, the hardware is either not supported or faulty.


2) Testing with "jstest" from the "joystick" package

Just to increase the trouble, the program
"jstest" from the ubuntu-package 6.06 Dapper Drake 

"joystick_20051019-1ubuntu1_i386.deb"

is faulty and quits with a "segmentation fault".

The following package from 6.10, Edgy Eft works fine, even under 6.06 Dapper Drake:

joystick_20051019-1ubuntu2_i386.deb


3) Necessary calibration

My finally enabled joystick really works fine in xmame since I calibrated it with
"jscal" from the "joystick" package. 
Before I could hardly use it. It seems necessary to calibrate the Joystick using especially this tool.


4) NOT solved

I did not and probably will never solve how to setup the gameport of my ancient sound card

CREATIVE LABS, CT4810
(Creative Ensoniq AudioPCI CT4810)

Instead my "Terratec 128iPCI" sound card runs very well as gameport-joystick-interface and more under ubuntu-6.06-Edgy Eft.

Regards raLLi

---

### Post by rasemmi on 2007-04-27
Hiho,

after enabling "native ALSA gameport support" I finally even managed to use my joystick on my sound card:

CREATIVE LABS, CT4810
(Creative Ensoniq AudioPCI CT4810)

Look here to see how:

[http://ubuntuforums.org/showpost.php?p=2548045&postcount=13](http://ubuntuforums.org/showpost.php?p=2548045&postcount=13)

Regards raLLi

---

### Post by spookypeanut on 2007-04-28
A wonderful how-to, worked like a charm for me. X-wing here I come!

Will it remember the modules when I re-boot, or will I have to do that every time?

---

### Post by SBFC on 2007-04-28
Thanks for the howto. I managed to get my off-brand POS gamepad working. Can calibrate it fine with jscalibrator (except it shows up as a 4 button when it's actually an 8 button).

Only prob I'm having now is getting it to work properly with GFCEU. When I try and assign buttons for the gamepad the four buttons work. But it detects nothing when using the D-pad...even though jscalibrator detects D-pad movement.

Anyone have a similar issue?

---

### Post by rasemmi on 2007-04-29
Hiho,

spookypeanut: "Extreme Coder" describes is a very good way of proving the correct driver-modules while Linux is running but it has to repeated after every re-boot.

After proving the correct driver-modules I added them to the file
/etc/modules
to be loaded automatically while booting.

See also:

[http://ubuntuforums.org/showpost.php?p=2548045&postcount=13](http://ubuntuforums.org/showpost.php?p=2548045&postcount=13)

Regards raLLi

---

### Post by Andy Troutman on 2007-05-05
I've got my gamepad working under one user with jscalibrator, but when I switch users, jscalibrator doesn't find the control pad get a "could not access specified paths" error. I assume it's some sort of permissions problem, but don't know how to fix it. Anyone got a clue?

I'm using a Logitech Precision USB gamepad. 

Thanks, 
Andy

---

### Post by Extreme Coder on 2007-05-10
Hi everybody,
I'm gravely sorry I couldn't reply to this topic or update it, I though it was going to be buried with the lot(ok, it's already buried, but somebody posts to it every few days), I am going to re-update the first post ASAP.


@Athanasius: Most Linux games and emulators play well with joysticks and gamepads. You can try out Planet Penguin Racer, or Snes9X/ZSnes (both available in the repositories)

@FidoNatty: Did you try doing ```
sudo modprobe gameport
```____ If it's a generic on-board gameport, this module should be already loaded.

@Kegir: There are lots of XBox 360 controller howto's here, and there are some for other distros that might work. If nothing works, make your own help topic on ubuntuforums asking for help. Maybe you may eventually make it work.

@tqft: Thanks a lot, Glad it helped :D

@dawynn: Did you try any games or emulators with your gamepad? jscalibrator is a bit of a wierd program and reports with odd results sometimes.

@andersja: Most, if not all USB joysticks and gamepads work out-of-the-box on Linux. I'd take a guess saying yours will work.

@rasemmi: Thanks for the tips, I will add some of them to the main post ;)

@spookypeanut: No, you will have to do this everytime you re-boot. But I'm adding some bits of rasemmi's advice to the main post, so that what you do is permanent.

@Andy Troutman: Maybe you configured the permissions of dev file for the pad from a root user? That's a really odd message. Try using a game or emulator, and see if it works.


BTW, I want to add this HOWTO to the Ubuntu wiki/help pages. Anyone would know how to do that?

Extreme Coder

---

### Post by grimdestripador on 2007-05-18
I have an Asus onboard joystick controller, and some old crappy UltraRacer joystick/wheel. 
The provided guide did very little in getting my computer to function, but the original documentation from [http://www.charmed.com/txt/joystick.txt](http://www.charmed.com/txt/joystick.txt) was what got me working. And even calibrated.

---

### Post by 1337 on 2007-05-21
> **dawynn said:**
> How do we tell the module to look for a gamepad instead of a joystick?  According to the joystick.txt that I found on the web, we should have been able to do something like this:

sudo modprobe analog js=gamepad

But that returns an error message saying "Unknown symbol in module, or unknown parameter"

Any help is appreciated.  If it matters, I'm a feisty fawn user.

Is this normal I got the same when I try to type a command line for the "analog" module, my joystick was detected wrong and it is not working fine because of that however there is an option:

Type     | Meaning
-----------------------------------
none     | No analog joystick on that port
auto     | Autodetect joystick
2btn     | 2-button n-axis joystick
y-joy    | Two 2-button 2-axis joysticks on an Y-cable
y-pad    | Two 2-button 2-axis gamepads on an Y-cable
fcs      | Thrustmaster FCS compatible joystick
chf      | Joystick with a CH Flightstick compatible hat
fullchf  | CH Flightstick compatible with two hats and 6 buttons
gamepad  | 4/6-button n-axis gamepad
**gamepad8 | 8-button 2-axis gamepad** <-------- I got this one

Where add this js=gamepad8 option to make this work and not get:
[B]
FATAL: Error inserting analog (/lib/modules/2.6.20-15-generic/kernel/drivers/input/joystick/analog.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B]

error, anybody?

---

### Post by 1337 on 2007-05-22
*Bump*

---

### Post by ethana2 on 2007-05-25
[email]ethana2@gmail.com[/email] ('cause I check it every 6 hours)

I want to map my screen to the position of my right analog thumb stick on a Logitech Dual Action USB gamepad so I can use it as a mouse.  I followed the instructions on the page, but I obviously need to do more than that.  Module adi used.

Then I want to map it to the mouse the other way and do key bindings on it for playing tremulous.  Can I make different binding/config profiles to switch between?  Ah yes- I had one set to WASD for online games.  If I use the colemak keyboard layout, would...

Maybe I'll just post a thread.  Yeah.

---

### Post by bittergourd on 2007-05-27
I have exactly the same problem.  jscalibrator works fine for my logitech dual action pad, it finds all buttons including the D-pad.  but when i tried it in xmame and zsnes, the D-pad and two analogue input stick just won't work, while other buttons work fine.

any idea?

-E   

> **SBFC said:**
> Thanks for the howto. I managed to get my off-brand POS gamepad working. Can calibrate it fine with jscalibrator (except it shows up as a 4 button when it's actually an 8 button).

Only prob I'm having now is getting it to work properly with GFCEU. When I try and assign buttons for the gamepad the four buttons work. But it detects nothing when using the D-pad...even though jscalibrator detects D-pad movement.

Anyone have a similar issue?

---

### Post by adam0509 on 2007-06-09
DONT use jscalibrator !!!


see [http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

---

### Post by Shpongled303 on 2007-07-13
> **adam0509 said:**
> DONT use jscalibrator !!!

Seriously, all these instructions and packages (joystick, jscalibrator) actually made my USB gamepad *not* work! I was doing everything from all these different threads -- terminal commands, modifying .conf files, messing with modprobes -- and it turns out that I never had to do any of it in the first place!

I restarted my computer then ran TuxRacer -- It worked fine on my digital USB gamepad.

I then opened JSCalibrator, calibrated my gamepad, and reopened TuxRacer. The gamepad didn't work! So, I uninstalled jscalibrator and joystick, undid all the changes I made and everything is working fine.

Maybe it should be noted in one of these many gamepad-Ubuntu threads that USB gamepads [at least for me] should work without any need of these packages and modifications.

Overall a great learning experience though. :P
Shpongled303

---

### Post by rasemmi on 2007-07-14
Hi Shpongled303,

thanks for your hint. It's a pity you got stuck here but I think the magic word in the topic is "GAMEPORT" and NOT "USB PORT".

Happy gaming and regards raLLi

---

### Post by bignickel on 2007-07-20
Hi I'm having a problem setting up 2 USB gamepads on my mythbox running Feisty.  I can plug them in, and jstest on /dev/input/js1 and js2 seem to show the proper events.  However, when I load frozen-bubble (which I'm using to test) it doesn't recognize the joysticks.

Now here's the kicker.  I can plug them in on my laptop (also running Feisty) and everything works.  Any ideas?

---

### Post by bignickel on 2007-07-26
Well, I ended up getting it working.  For some reason (maybe because I use dancepads sometimes) the gamepads were going on /dev/input/js1, but most games apparently look on js0.  So this did the trick:

sudo ln -s /dev/input/js1 /dev/input/js0

---

### Post by sdhoigt on 2007-09-03
Hi all,

Just finished reading the entire thread.  The problem I'm having is none of gamepad modules seem to work for me (I tried them all starting with 'analog' - Note: I loaded/unloaded each one before trying the next).

None of these give me a /dev/js* or /dev/input/js* device dir.

My gamepad is an old pad which goes through the (serial?) port on the sound card.  

Thanks for any ideas.
SD

---

### Post by tipping point on 2007-09-06
Extreme Coder, that was a great set of instructions, laid out so straight forward even an idiot like me got my joystick up and running. Thank you

---

### Post by lizzie2 on 2007-09-23
From a newbie,
Thanks a lot, got my Logitech Wingman Gamepad working.
Now for the next problem!!
Again thanks a lot,
all the best,
Les

---

### Post by 99bluefoxx on 2007-09-23
is it possible for someone to just make some kind of shell script for people like me who suck at anything but extremely explicit step by step or basic codes?
i tried this for my computer and got nowhere
300w psu
asrock p4vm890via chipset
2.93ghzceleron d processor overclocked to 3.54ghz
bfg graphics nvidia 6200oc 256mb graphics card pci interface
logetech lx710 cordless keyboard and mouse set
logitech itouch office pro corded keyboard and generic ball mouse
seagate 250gb ultra ide hdd
1cdrom, 1cdrw, 1cdrw/dvdrom drives
card reader
3com generic pci networking card
cmi 8738-mc6 sound card[thats what software says, i got preowned so not sure of model]
microsoft sidewinder pro 3d joystick controller connecting through soundcard
im not sure if theres a hardware conflict somewhere there

---

### Post by 99bluefoxx on 2007-11-03
ok, i found out why my old one didnt work, the circuitry in it was broken, so i got a new one, but its a microsoft sidewinder pro 3d plus, and i got it to recognize in  jscalibrator, but it wont do anything else, heres terminal output after a few tries

```


bluefoxx@azurE-prIDE:~$ sudo modprobe joydev
WARNING: /etc/modprobe.d/options line 8: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 9: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 10: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 11: ignoring bad line starting with 'sudo'
bluefoxx@azurE-prIDE:~$ jscalibrator
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
```


and after trying some stuff i found in threads on forums

```
bluefoxx@azurE-prIDE:~$ sudo apt-get install kcontrol
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kcontrol is already the newest version.
kcontrol set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bluefoxx@azurE-prIDE:~$ sudo apt-get install joystick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
joystick is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bluefoxx@azurE-prIDE:~$ jscal -c /dev/input/js0
jscal: error getting version: Inappropriate ioctl for device
bluefoxx@azurE-prIDE:~$ jstest

Usage: jstest [<mode>] <device>

Modes:
  --normal           One-line mode showing immediate status
  --old              Same as --normal, using 0.x interface
  --event            Prints events as they come in
  --nonblock         Same as --event, in nonblocking mode
  --select           Same as --event, using select() call

bluefoxx@azurE-prIDE:~$ sudo apt-get install stepmania
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package stepmania
bluefoxx@azurE-prIDE:~$ sudo modprobe joydev
WARNING: /etc/modprobe.d/options line 8: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 9: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 10: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 11: ignoring bad line starting with 'sudo'
bluefoxx@azurE-prIDE:~$ jscalibrator
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
bluefoxx@azurE-prIDE:~$ sudo modprobe cs461x
WARNING: /etc/modprobe.d/options line 8: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 9: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 10: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 11: ignoring bad line starting with 'sudo'
FATAL: Module cs461x not found.
bluefoxx@azurE-prIDE:~$ sudo modprobe sidewinder
WARNING: /etc/modprobe.d/options line 8: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 9: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 10: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/options line 11: ignoring bad line starting with 'sudo'
bluefoxx@azurE-prIDE:~$ jscalibrator
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
Failed to set joystick /dev/input/js0 correction values: Inappropriate ioctl for device
bluefoxx@azurE-prIDE:~$ 
bluefoxx@azurE-prIDE:~$ 


```

i allso would appreacieat some idea of how to find out what model of soundcard i have, it doesnt say anything on it, and volume control says "C -Media PCI CMI8738-MC6", its got an game/midi port on the back of it, some yellow headphone jack that outputs nothing and a black rear/sub out jack, in addition to the regular plugins. vol control gives options to switch sound in to center out and mic in to sub out, but when i check them off it does nothing, any ideas?

---

### Post by spatialguru on 2008-03-28
Hi all,

I've been through many of these steps many times before with no luck.  In particular no /dev entries are being created when loading any of the modules.  I'm using an interact device and was thrilled to see support for it.

I fear that my device (or port?) may be busted.  Is there a lower-level way of testing the game port?  It does show with dmesg:

```
[ 1978.656567] gameport: NS558 PnP Gameport is pnp00:0d/gameport0, io 0x200, speed 852kHz
[ 1978.681391] analog.c: Unknown joystick device found  (data=0x5, pnp00:0d/gameport0), probably not analog joystick.
```

Is there a way to ping such a thing like I do to test my serial ports with telnet? :)

Regards,
SG

---

### Post by BryanFRitt on 2008-06-06
Hint to anybody using EMS Dual Shooter (PlayStation controller to USB converter) make sure the switch on the device is set to PC and not to GAME.

---

### Post by trappy on 2008-08-04
I am using a Playstation 2 controller, and all the buttons work when I specifiy /dev/input/js0 in the emulator. However, the digital cross doesn't work at all.
It does work i jscalibrator though, and i fceu it all works. 
Does anyone know a way to make some kind of global config for PS2-controllers that can be used by ALL emulators?

---

### Post by brandonblm on 2008-08-05
Please forgive me for I am a NOOB. I have kubuntu 8.04 and a microsoft sidewinder. I have tried all of these commands and it will not find my device anywhere. When I type modprobe and whatever I am looking for it will not do anything but go to the next line and show my home as if I had typed nothing. can you help me further?

Brandon

---

### Post by Neobuntu on 2008-09-09
**Logitech Thunder Pad Digital** here and it is connected to my ASUS motherboard (built in sound "snd_via82xx") on the GAME port. 

gameport module was already loaded.

joydev and

adi modules

did not work with kcontrol or jscalibrator.

I did not have a any js device names until I made them with > sudo MAKEDEV jsin the /dev/input folder. I don't even know if I should have done that.

help....

---

### Post by KillerKiwi on 2008-09-11
for those that want to play games that dont have native joystick control

[http://ubuntuforums.org/showthread.php?t=903858](http://ubuntuforums.org/showthread.php?t=903858)

---

### Post by kerryhall on 2008-10-29
bump

---

### Post by stanz on 2008-11-12
Not finding what I need...

A friend just passed me a "REVEAL" Joystick.
It's a serial connection to my sound card.
I find allot of help with modules for other stick's - except this one.
Does anyone have this brand working???
TIA ~~!

---

### Post by HittingSmoke on 2008-12-03
I've got an old "PC Propad 4" hooked up to my SB Audigy's game port.

I followed this guide and jscalibrator reports everything OK. Both axes report feedback and all the buttons register when I press them, but on three different emulators (GFCE Ultra, XSNES and ePSXe) I cant get any response from the D-pad. I map out all my buttons other than the D-pad and they work fine but when I try to map my UP button to UP in the emulator's settings, It wont register that I'm pressing anything.

Am I missing some config setting?

*edit* I also got a hold of an old Radio Shack game pad and get the same results. Buttons are fine but no D-pad support in my programs other than jscalibrator

---

### Post by bluebear on 2010-02-02
> **1337 said:**
> Is this normal I got the same when I try to type a command line for the "analog" module, my joystick was detected wrong and it is not working fine because of that however there is an option:

Type     | Meaning
-----------------------------------
none     | No analog joystick on that port
auto     | Autodetect joystick
2btn     | 2-button n-axis joystick
y-joy    | Two 2-button 2-axis joysticks on an Y-cable
y-pad    | Two 2-button 2-axis gamepads on an Y-cable
fcs      | Thrustmaster FCS compatible joystick
chf      | Joystick with a CH Flightstick compatible hat
fullchf  | CH Flightstick compatible with two hats and 6 buttons
gamepad  | 4/6-button n-axis gamepad
**gamepad8 | 8-button 2-axis gamepad** <-------- I got this one

Where add this js=gamepad8 option to make this work and not get:
[B]
FATAL: Error inserting analog (/lib/modules/2.6.20-15-generic/kernel/drivers/input/joystick/analog.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/B]

error, anybody?

Just managed to get my old analog CH Flightstick pro working in 9.10. 
Heres how you do it. When loading the analog module you have to add map=chf (for flightstick pro). 

sudo modprobe analog map=chf 

I managed to get my vintagestick up and running again, happy times.

---

### Post by Teks on 2010-02-05
I have a problem with EMS Dualshooter, Ubuntu (Karmic)  doesn't recognize the device and the ps2 controller will not work, any ideas? 
All i have found about this issue is fanboys screaming that usb devices work like magic, well, it doesn't. 
Anyone else run into this problem?

---

### Post by blumblaum on 2010-07-12
Hi guys! I've found this thread via Google when searching for a solution for my problem: I've got four analog gamepads an analog joystick and none of these input devices is **working correctly**.

In the detail: No axis is working! The buttons work fine but there is a strange acitivity &#8230;

1. When pressing the A button for example in a web browser on any of my gamepads, it acts like a mouse click. Lets say the mouse cursor is placed over a word. Pressing the A button twice selects the word. Pressing the A button three times selects the whole line. Just like clicking with the left mosue button.

2. Pressing the B button acts like Shift+Input / Strg+V (pasting the content from the clipboard).

3. Pressing the C button makes a context menu pop up.


And this is what I've made and tried &#8230;

First I've installed the following applications from the Ubuntu repository:
```
sudo apt-get install joystick jstest-gtk
```

Then I've added the following line to **/etc/modules**:

```
analog map=gamepad8
```

&#8230; and loaded the module into the memory:

```
sudo modprobe analog map=gamepad8
```

Adding/loading the **joydev**-module doesn't help, too.

Now I've tried to use the gamepad with several games but it the problem is a described above.

So I've first tried calibrating the gamepad with **jstest-gtk** and then with **jscal -c /dev/input/js0** and also tried running **/etc/init.d/joystick restart** but it didn't work. I've restarted Ubuntu but it didn't help, too.

Somewhere I've red about creating a symbolic link like this, to solve the problem: **sudo ln -s /dev/input/js0 /dev/js0** &#8230; but it also didn't work. :(

The soundcard I'm using is a **Terratec SoundSystem Sixpack 5.1+**.

Can anybody help me please?

PS: Sorry for my bad english!

---

