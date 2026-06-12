---
title: "My Screen Resolution"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Acadia on 2008-05-25
I am really trying to get as far as I can before I ask you guys for help.  Here is where I am.

I have a Dell Inspiron 8000 - My Screen Resolution will not go any higher than 800 x 600 right now, and the driver area says I have no drivers.

I downloaded atimp310.rpm and it is sitting on my desktop - according to the dell site, that is what I need - but I don't know what to do with it now.

Any ideas?  I dont want to be stuck at this grandma resolution!  :)

Thanks in advance

---

### Post by xenocide13 on 2008-05-25
do you have an onboard card?

---

### Post by Acadia on 2008-05-25
I know I have a graphics card, but I do not know where in Ubuntu to look to see what kind.

On the windows install, it said ATI - so i assume that's it.

---

### Post by xenocide13 on 2008-05-25
you dont know what kind it is though?
Envy might help if you havent tried that

---

### Post by xenocide13 on 2008-05-25
type in lscpi in your terminal it will tell you what kind of card you have i think thats the right code atleast

---

### Post by Inxsible on 2008-05-25
```
lspci | grep VGA
``` will tell you your graphics card. if you already have the rpm file and if Dell says thats all you need, then you can use alien to convert it to a deb and then install it.

---

### Post by Acadia on 2008-05-25
Hi everyone,

I have Mobilty M4!

"then you can use alien to convert it to a deb and then install it."

???

---

### Post by Tatty on 2008-05-25
I would recommend trying EnvyNG first - it is in the repos.

If that doesnt work then see this link to convert the .rpm into a .deb [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by xenocide13 on 2008-05-25
you guys know more then me so good luck sorry i couldnt help more =]

---

### Post by Acadia on 2008-05-25
> **Tatty said:**
> I would recommend trying EnvyNG first - it is in the repos.

If that doesnt work then see this link to convert the .rpm into a .deb [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

What or where are the repos?

Also - thanks, xenocide13.  :)

---

### Post by xenocide13 on 2008-05-25
code
sudo apt-get install envyng-qt

i beleave that should get you envyNG and it should be fairly straight forwoards from there

---

### Post by Acadia on 2008-05-25
> **xenocide13 said:**
> code
sudo apt-get install envyng-qt

i beleave that should get you envyNG and it should be fairly straight forwoards from there

You rule - 

is there a way to get the command line thingy after I am logged in?  As of now I keep going to the recovery mode in the start up.

---

### Post by xenocide13 on 2008-05-25
ctrl+alt+f1 gives you a text login screen enter your info then you are in the terminal
Ctrl+alt+f7 to go back to a visual screen

sorry if any of this is not quite right i am going off of memory and i cant get my system working properly to checkmyself

---

### Post by Acadia on 2008-05-25
Okay - so I did the envy thing and i cannot change anything past 800 x 600

I installed the alien thing - but I don't know how to get the atimp310.rpm off my desktop to wherever it is supposed to be aliened.

=/

---

### Post by xenocide13 on 2008-05-25
[http://ubuntuforums.org/showthread.php?t=807451](http://ubuntuforums.org/showthread.php?t=807451)

try that see if any of that works for you 
im still trying to get my system running again
still cant check

---

### Post by Acadia on 2008-05-25
You are such a nice guy, xeno - thanks for your help.  I am banging my head against the wall here, I think.

Ugh

I will try again in the morning - if anyone has a hint, please let me know

---

### Post by xenocide13 on 2008-05-25
no problem just trying to help out
dont know how much its working i am fairly new myself
but hopefully you get it all sorted out and working soon

---

### Post by Acadia on 2008-05-26
I managed to Install the Dell Package with Alien but it did not do anything.  I have sudo nanoe'd my xorg.conf 500 times and I still cannot get any resolution above 800 x 600.  :(

Can anyone let me know if there is something else I can try?

---

### Post by Inxsible on 2008-05-26
> **Acadia said:**
> I managed to Install the Dell Package with Alien but it did not do anything.  I have sudo nanoe'd my xorg.conf 500 times and I still cannot get any resolution above 800 x 600.  :(

Can anyone let me know if there is something else I can try?Have you enabled the restricted drivers for your graphics card?

System>>Administration>>Restricted Driver Manager. Click on enable drivers for your ATI card and then reboot.

---

### Post by Acadia on 2008-05-26
> **Inxsible said:**
> Have you enabled the restricted drivers for your graphics card?

System>>Administration>>Restricted Driver Manager. Click on enable drivers for your ATI card and then reboot.

Hey man!  Hope you are well.

I don't have that option in my list - it goes from Printing right to Services.  Is there somewhere else I can look?

---

### Post by Inxsible on 2008-05-26
> **Acadia said:**
> Hey man!  Hope you are well.

I don't have that option in my list - it goes from Printing right to Services.  Is there somewhere else I can look?
Ok Try to change your resolution in these two places.

System >Prefs>Screen Resolution

And System > Admin>Hardware  drivers

---

### Post by oldrocker99 on 2008-05-26
> **Acadia said:**
> I managed to Install the Dell Package with Alien but it did not do anything.  I have sudo nanoe'd my xorg.conf 500 times and I still cannot get any resolution above 800 x 600.  :(

Can anyone let me know if there is something else I can try?

Go to Synaptic and install display-config-gtk. 

Run it (it'll be in the "Other" menu) and select your monitor on the Screen tab (it's almost certain to be listed).

Then click the tab for Graphics Card and select your video card by manufacturer and model (mine is a NVidia 8000 series, for example).

Reboot and you SHOULD have the resolutions you desire.

Been there, done that...:guitar:

---

### Post by Acadia on 2008-05-26
Well, I started to try that solution and all of a sudden I have 40 bazillion updates to do - so I have to wait - I am excited!

---

### Post by xenocide13 on 2008-05-26
Did they release some new updates for Hardy?

---

### Post by Acadia on 2008-05-26
I don't know what Hardy is - but I do know that I just got like, 41 updates that installed - so I guess?

---

### Post by xenocide13 on 2008-05-26
Did that fix it?

What version of ubuntu are you running?

---

### Post by hfp on 2008-05-26
I had a resolution problem when I first used ubuntu also.  I think it was because I hadn't installed ubuntu to my hard drive yet.  I was just using the cd.

After I installed ubuntu 32 bit to my hard drive the option to install the nvidia drivers appeared in the top right hand corner without me even doing anything.  I didn't have to download any drivers from any websites.  Ubuntu took care of it.

Have you installed ubuntu to your hard drive?

---

### Post by Inxsible on 2008-05-26
> **Acadia said:**
> I don't know what Hardy is - but I do know that I just got like, 41 updates that installed - so I guess?
Hardy Heron or 8.04- as it is officially known after the release - is the latest version of Ubuntu.

Like xeno asked ..what version are you running? and are you in Live CD or have you installed it already ?

---

### Post by Inxsible on 2008-05-26
> **Inxsible said:**
> Ok Try to change your resolution in these two places.

System >Prefs>Screen Resolution

And System > Admin>Hardware  driversDid you try this yet? and did you try out oldrocker's solution ?

---

### Post by xenocide13 on 2008-05-26
What would the difference be if you were running off of the disk? mine worked great off the disk. just curious.

---

### Post by Inxsible on 2008-05-26
> **xenocide13 said:**
> What would the difference be if you were running off of the disk? mine worked great off the disk. just curious.After you enable your restricted drivers for you graphics card, you have to reboot or restart X (Ctrl+Alt+Backspace) to be able to use the new drivers.

If you reboot however, a Live CD doesn't remember the session since everything is in RAM. You can however use Ctrl+Alt+Backspace to use your new drivers. I am not sure if Acadia has done that yet.

---

### Post by xenocide13 on 2008-05-26
Got ya. That makes plenty of sense. thanks

---

### Post by Acadia on 2008-05-26
I just installed it yesterday - i made a CD off the website and installed it, etc.

So I must have the latest one.

I tried the thing you pointed out - but it does not give me any options past 800 x 600 or 640 x 480

I got nothing.

*kicks rock*

---

### Post by xenocide13 on 2008-05-26
i beleave that you will have to edit it so that there will be soemthing past that =) if i know what we are talking about still

---

### Post by Inxsible on 2008-05-26
Acadia, please post the output of the following command

Open a terminal (Applications>>Accessories>>Terminal)```
cat /etc/X11/xorg.conf
```Please take note of the case

---

### Post by Acadia on 2008-05-26
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by Inxsible on 2008-05-26
you haven't enabled the restricted drivers dude !!

Did you try it under Hardware Drivers like I mentioned twice before?

---

### Post by Acadia on 2008-05-26
> **Inxsible said:**
> you haven't enabled the restricted drivers dude !!

Did you try it under Hardware Drivers like I mentioned twice before?

When I went into that area - there are none to pick from.  I have been trying very hard to follow the instructions and not waste anyone's time.

When I go into Hardware Drivers it says: No Proprietary drivers are in use on this system.

sorry if I am doing this wrong.

---

### Post by xenocide13 on 2008-05-26
Yea i have always had that problem also but i ended up getting them with a command line but i cant think of the command and also cant check on my computer at the moment hopefully someone else comes along and says it

---

### Post by signseeker on 2008-05-26
Looking at your xorg.conf - the ATI drivers aren't being used - which is why you cannot select a higher resolution.

Do you know the maximum resolution your screen can handle?

Did you try aticonfig?

The following thread maybe useful too
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by Acadia on 2008-05-26
I tired aticonfig and it said I didn't have a driver - so now I don't know what to do.  I went googing and found some post somewhere about a guy with the same card "ATI Technologies Inc Rage Mobility M4 AGP" but his comp was a gateway and I was trying to follow what he said but I am SURE I edited my darned xorg.conf wrong and I am just waiting to see what fresh demon greets me upon reboot.

You guys are awesome - I just feel so despondent.

---

### Post by xenocide13 on 2008-05-26
allright lets go through this little checklist here

1. did you install the restricted drivers
2. if not did you use envy to install drivers/or uninstall
3. after you did any of these did you check your config to be sure it was correct

check through all those and it should be working

---

### Post by Acadia on 2008-05-26
> **xenocide13 said:**
> allright lets go through this little checklist here

1. did you install the restricted drivers - **I don't know how because they don't show up in the list.**
2. if not did you use envy to install drivers/or uninstall - **When I try to do Envy it tells me it won't work because I don't have the right hardware...**
3. after you did any of these did you check your config to be sure it was correct - **I have messed with it so many times I don't know which way is up.**

check through all those and it should be working

It may be that I am just too stupid for this, and that I am wasting all of your time.  I apologize.

---

### Post by Hondo88 on 2009-03-10
Edit: sorry wrong post. 
Linux noob

---

### Post by SamNSane on 2009-03-10
> 
When I go into Hardware Drivers it says: No Proprietary drivers are in use on this system.


That's what it always says -- until you put a checkmark in the box beside the driver listed in the box below that statement. It's kind of an odd (read non-Windows) way for them to get the idea across. If you have a driver or drivers listed in that box, all you have to do is put a checkmark beside the one you want to use. Then close out of the dialog and reboot.

If I'm misunderstanding you, and the situation is different, please forgive me. But downloading .rpm packages and converting them to .deb packages, or compiling drivers, or using third party scripts should all be things that you consider trying if, and only if, the Hardware Drivers applet fails you.

The first thing to learn about Ubuntu, or any Linux distribution, is that you're almost always better of trying to get as much of your software and / or drivers as possible from the official repositories for that distribution -- and to try to use the standard tools of the distribution for performing any installations. Those are the best tested means of installing drivers and software.

Sometimes we users just jump in and start suggesting things that worked for us after all else failed without being careful enough to be sure that the standard approach has actually failed for the person asking the question.

Sometimes the alternative methods we suggest make marked changes in the behavior of a system -- changes that may not be easily reversed. The more standard a new user's system is, the easier it will be for her/him to use documentation to figure things out.

---

