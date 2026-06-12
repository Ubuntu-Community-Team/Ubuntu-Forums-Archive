---
title: "Howto: Use BlueProximity and your cellphone for security"
date: 2008-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Iceni on 2008-02-20
**What is it?**
[list][*]BlueProximity is a clever program by Lars Friedrichs that sets up your computer to lock itself when your phone is out of bluetooth range, and unlock itself when it comes close enought again. You can also also make it turn off and on the monitor, music, change msn status and pretty much everything you can imagine.
[/list]
**Why do I want it?**
[list][*]Ultimate coolness! Nothing is as super cool as just walking up to your computer and watch it come alive without you doing anything. Ok, it can be argued that this is semi-useful, but we will all do it for the coolness factor:)
[/list]

**How to do it? {installation}**

If you use Hardy or newer, blueproximity is in the repos, so simply install the usual way and jump to setup instructions:

```
sudo apt-get install blueproximity
```

***If you don't have blueproximity in your reps (older ubuntu than hardy), follow these:***

Install dependencies:
```
sudo apt-get install bluez-utils python-gtk2 python-glade2 python-configobj python-bluez
```

We need a newer version of the *python-support* package:

```
wget http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5ubuntu1_all.deb
```

Install it:

```
sudo dpkg -i python-support_0.7.5_all.deb
```


**Now lets get the BlueProximity program:**

```
wget http://ovh.dl.sourceforge.net/sourceforge/blueproximity/blueproximity_1.2.4-0ubuntu1_all.deb (from official site)

[center]**- alternate download link -**[/center]

wget http://mirrors.kernel.org/ubuntu/pool/universe/b/blueproximity/blueproximity_1.2.4-0ubuntu1_all.deb (from ubuntu universe (hardy?) repositories)

```

Install it:
```
sudo dpkg -i blueproximity_1.2.4-0ubuntu1_all.deb
```


Ok, now it is time to set this up:

**Phone settings:**
[list]
[*]Activate bluetooth
[*]Scan for your computer and authorize it so you won't need a password
[/list]

**Blueproximity settings:**

```
blueproximity
```
[list]
[*]Scan for devices and select "Use selected device"
[*]Then scan channels and select one that comes up as "usable"
[/list]

That should be it! Now fiddle a bit with your proximity details, don't set them too low but not to high either. I get pretty good results with the settings below, but this will of course differ according to the placement of your computer.

**Settings**

My settings are:
[list][*]Lock: Distance: 7 | time: 10 - thus it won't lock at once if bluetooth connection gets disrupted, something it seems to do for a second or two.
[*]Unlock: Distance: 3 | time: 3 - Unlocks very fast when I get close.[/list]

**Turning the monitor off**
It would be more useful if this could turn the monitor on/off as well, right? If you want this enter the BlueProximity preferences, click the *locking* tab and use this command::
[list]
[*]Locking Command: gnome-screensaver-command -l && xset dpms force off
[*]Unlocking command: xset dpms force on && gnome-screensaver-command -d
[/list]
I noticed I had to change the unlock time to 1 to give the monitor time to turn on before I sat down.


**Add the program to your startup list:**
Of course you want to have it starting with Ubuntu. Go system > preferences > sessions. You should be on the "startup programs" tab. Click "Add" and type "blueproximity" (without the "") and a name and description you want. 

This was tested by me on Ubuntu Gutsy with a Samsung D900, and works great. If you try this, please report what phone you got it working with - or not. I don't see this not working because it only really depends on bluetooth from the phone, but you never know. It will be kind of useless if you can't authorize a device on your phone.

**Working phones**
[list]
[*]I removed the phone list because .. well this seem to work with everything:o
[/list]

**Scripts**
As some users have alredy pointed out, there are several cool possiblities for this. Many things can be accomplished with simple or more advanced scripts. Despite my very limited knowledge of bash scripts, I attached a simple set of scripts that will do the following:
[list]
[*]Turn on / off screensaver
[*]Turn on / off monitor
[*]Check if Amarok is playing and pause - then unpause. If amarok is stopped, this will do nothing.
[*]Change your pidgin status to away / available*
[/list]
**To get the pidgin status to work you need [i]libpurple-bin*. (install: sudo apt-get install libpurple-bin)[/i]

To use them, download the attached scripts archive, unpack it, make them all executable and stick them in /usr/bin*. If you only want some of the functions, edit the *bp_lock* and *bp_unlock* files. Then go into BlueProximity preferences - locking tab and put "bp_lock" and "bp_unlock" as locking and unlocking command.
**command is: sudo cp bp_* /usr/bin*

I'm sure more knowledgeable users can make better scripts, but these does the trick for my use:)

**Other scripts**
[gertvdijk details how to make a start/stop script for rhythmbox]("http://ubuntuforums.org/showpost.php?p=4580219&postcount=72")
[crocowhile teaches us how to change skype status]("http://ubuntuforums.org/showpost.php?p=4611199&postcount=77")
[Red_Five shared the mother of all bp scripts!]("http://ubuntuforums.org/showpost.php?p=4644066&postcount=78") 
> Here's the script I use now. It's a single, monolithic script that handles away, available, status update messages, and proximity "poking". I've put in lines for several audio players (GNOME; I don't use KDE), Twitter, Pidgin, and even a line to update my Out of Office status in Exchange via Outlook Web Access.
[monojohnny made a cool script that makes the computer beep when your phone is stolen]("http://ubuntuforums.org/showpost.php?p=5180097&postcount=104")

**Links**
[list]
[*][Offical Site]("http://blueproximity.sourceforge.net/index.html")
[*][Jesse Dyer showcasing how to control lights with BlueProximity and X10]("http://jessedyer.blogspot.com/2008/02/blueproximity-and-x10-peanut-butter-and.html")
[/list]

**FAQ**
[list]
[*]*What happens if the phone runs out of power?*
[*]Nothing. You can still unlock your computer the traditional way. You don't need the phone at all.
[/list][list]
[*]*What happens if someone unplugs your usb bluetooth dongle?*
[*]I tried because someone asked. You'll have to unlock your computer manually. If it is inserted again it will work in a minute or so.
[/list][list]
[*]*Where did the python-support install go?* 
[*]I changed it to a safer and faster method. If you need the other one, plase ask me.
[/list][list]
[*]*It works, but my phone lost sound - I have to manually eneable sound - headset has no sound - other sound problems?*
[*]Do a "sdptool browse" in the terminal and find the channel marked as "object push". Select this channel in BlueProximity preferences. This should do the trick :)
[/list]

---

### Post by wieman01 on 2008-02-20
Just to say that this is a very interesting tutorial. I have approved it and will keep an eye on it. :-)

---

### Post by Anduu on 2008-02-21
This is pretty cool.Going to try it out.

One thing though.You need to **_*[COLOR="Red"][SIZE="4"]really stress[/SIZE][/COLOR]*_** the importance of switching back to your original repos so as not to hose your system.

Oh and don't forget you will have to lock the version of python-support or it will get downgraded next time you update.

---

### Post by Iceni on 2008-02-21
> **Anduu said:**
> This is pretty cool.Going to try it out.

One thing though.You need to **_*[COLOR="Red"][SIZE="4"]really stress[/SIZE][/COLOR]*_** the importance of switching back to your original repos so as not to hose your system.

Oh and don't forget you will have to lock the version of python-support or it will get downgraded next time you update.

Thanks, I added some red color to stress it a bit:)


Are you sure about the the need to hold the package? To my (a bit limited) knowledge, apt-get will not downgrade a package?

---

### Post by red_five on 2008-02-21
There's no need to tweak sources.list for one package installation. Just download the Hardy version from the packages.ubuntu.com listings. Gdebi will complain about an older version being available in the software channels, but it'll still install just fine. No risk of system-hosing.

Oh, and I can confirm that the Verizon Moto RAZR V3m works just fine with BlueProximity.

One other thing: you can put any commands into the lock and unlock text boxes. For example, I created a couple of custom bash scripts to do the locking and unlocking. The lock script activates the screensaver, as well as sets Pidgin to away and pauses Exaile if it's running. The unlock script sets Pidgin to available, hits play on Exaile (again, only if it's running), then pokes the screensaver before deactivating it, to wake the monitors up from sleep. I stuck 'em in ~/bin, made them executable, and set 'em up in BlueProx. Golden!

---

### Post by insert_name_here on 2008-02-21
Wouldn't it be easier to download and install the Hardy version of python-support from the packages.ubuntu.com site, rather than potentially borking my system messing with repos?

(I can't link to the packages.ubuntu.com/ whatever site to find the package itself because the site is down, unfortunately.)

Edit: red_five, you win.

---

### Post by GodsDead on 2008-02-21
woah ausom idea, i just need a bluetooth adaptor for my PC now 0_o
if i use a bluetooth USB.. if someone takes it out, then what happens?

---

### Post by Pinkydead on 2008-02-21
Works for Sony Ericsson K750i.

---

### Post by Ryanmt on 2008-02-21
i dont have that line in my repositorys file. I tried looking for the package but the website seems to be down. Can anybody put up a clearer version of how to install python-support.

Thanks

edit -- found a copy here
[http://security.ubuntu.com/ubuntu/pool/main/p/python-support/](http://security.ubuntu.com/ubuntu/pool/main/p/python-support/)

seems to do the trick!

---

### Post by Iceni on 2008-02-21
> **red_five said:**
> There's no need to tweak sources.list for one package installation. Just download the Hardy version from the packages.ubuntu.com listings. Gdebi will complain about an older version being available in the software channels, but it'll still install just fine. No risk of system-hosing.

Oh, and I can confirm that the Verizon Moto RAZR V3m works just fine with BlueProximity.

One other thing: you can put any commands into the lock and unlock text boxes. For example, I created a couple of custom bash scripts to do the locking and unlocking. The lock script activates the screensaver, as well as sets Pidgin to away and pauses Exaile if it's running. The unlock script sets Pidgin to available, hits play on Exaile (again, only if it's running), then pokes the screensaver before deactivating it, to wake the monitors up from sleep. I stuck 'em in ~/bin, made them executable, and set 'em up in BlueProx. Golden!

Thanks for the tip, I'll edit it in when I get home on my own computer. I've been messing around a bit with scripts myself, but mostly exploring possibilities so far. Maybe you could share yours, so I could add them to the guide? Would make a nice extra:)

---

### Post by Iceni on 2008-02-21
> **Ryanmt said:**
> i dont have that line in my repositorys file. I tried looking for the package but the website seems to be down. Can anybody put up a clearer version of how to install python-support.

Thanks

If you don't have that line you can safely add it yourself, and remove it after you installed python-support.

Add this line:

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
```

and [COLOR="Red"]remove it after installation[/COLOR]

---

### Post by a5benwillis on 2008-02-21
I paired my Blackberry 7100i just fine but after scanning all 30 channels they all report as "closed or denied". Am I out of luck? I would LOVE to have this work.


Thanks!

Ben in SC

---

### Post by haldean on 2008-02-21
might be better to suggest downloading from here:
[http://mirrors.kernel.org/ubuntu/pool/universe/b/blueproximity/blueproximity_1.2.4-0ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/b/blueproximity/blueproximity_1.2.4-0ubuntu1_all.deb)

---

### Post by solracarevir on 2008-02-21
Interesting, will give it a try as soon as I arrive to my home... I have a blackjack and a nokia will try both and post the results

---

### Post by a5benwillis on 2008-02-21
Got it! Best thing EVER!

---

### Post by insert_name_here on 2008-02-21
Works great with my Verizon-crippled Motorola e815!

---

### Post by jessedyer on 2008-02-21
If you want to make this even more fun, [mix it with X10 to control your lights]("http://jessedyer.blogspot.com/2008/02/blueproximity-and-x10-peanut-butter-and.html").

I've got my instance of BP muting/restoring volume, locking/unlocking a Windows PC, and if I can get Pidgin to cooperate, I'll have it setting my IM status..

Much fun from BP..

---

### Post by Iceni on 2008-02-21
> **a5benwillis said:**
> I paired my Blackberry 7100i just fine but after scanning all 30 channels they all report as "closed or denied". Am I out of luck? I would LOVE to have this work.


Thanks!

Ben in SC

Go to terminal and run:

```
sdptool browse
```

On my phone I'm using the "object push" channel - see if you have something similar and change to this.

---

### Post by zepfan on 2008-02-21
Great How to, thanks! I'm having a problem though. When i turn the bluetooth off on my phone (to simulate leaving), all i get is a silver key, and what looks like a red power plug on the system tray icon. The status says no connection found trying to establish one. I've paired the phone and laptop, and i am using your settings that you advised. The bottom Measured atm is greyed out for me ( i dont know if that's normal, just figured I would give as much info as possible.)  My phone is an LG EnV, with the default Dell 9300 Bluetooth.
Thanks for any input!

Edit. I should add, when i turn the bluetooth back on and am close to my computer they key turns green, so i know it works.

Edit 2 : I restarted and it works fine. Thanks for this!

---

### Post by insert_name_here on 2008-02-21
This is a really neat set up, but unfortunately, I value by battery life on both my laptop and my cell phone.  Is there any way to set them up to ping each other less, or reduce the power used or sometihng?

---

### Post by Anduu on 2008-02-22
LG CX245

Works like a charm.

Only one problem...if I try to use xscreensaver it totally wigs out on me.Locks the screen at random when in range,won't lock when out of range and if it does it doesn't automatically unlock.

Gnome Screensaver works fine...anyone have it working with xscreensaver?

---

### Post by HisEm on 2008-02-22
This sounds really cool, except (I'm a newbie) I wonder what my computer will need to transmit and receive the blue-tooth signal? or is it built in? I am on a WIRED not wireless network, does this matter?
Can anyone answer me? 
Thanks ;)

---

### Post by e30drift on 2008-02-22
This is probably one of the coolest tricks I have seen in a long time.

I have a quick question that hopefully someone can answer...

Knowing that there are 2 Bluetooth hardware standards 1.x and 2.x for both the phone and on the laptop, couldn't the kernel drivers considered "generic" regardless of manufacturers' implementation? 

I have a Dell Latitude D620 w/ the built-in bluetooth module and a HTC S620.  I have not tried this since I just re-installed 7.10 and I am waiting for my replacement HTC S620.  

I just want to throw that out there to get some gears moving (or grinding):KS

---

### Post by Iceni on 2008-02-22
> **HisEm said:**
> This sounds really cool, except (I'm a newbie) I wonder what my computer will need to transmit and receive the blue-tooth signal? or is it built in? I am on a WIRED not wireless network, does this matter?
Can anyone answer me? 
Thanks ;)

Some coputers have bluetooth built-in, mainly laptops to my knowledge. I use this on a stationary computer and a simple bluetooth usb dongle. They can be bough cheap, I imagine $10-$20 and are usefull for other things as well.

---

### Post by ktulu1115 on 2008-02-22
This is perfect.  I can't wait to try it.  I had a similar idea myself but was thinking about using biometrics (fingerprint reader) as a *-screensaver unlocker but wasn't sure how I was going to implement automatic locking.  This is even better, not to mention I wasn't having much luck in my research.    

Oh, I don't know if it's been mentioned....  but must feel to point out the obvious regardless: this is a pretty large security risk if someone with physical access to your machine (and your phone) knew of this security hole.  Admit it, that's basically what this is.  Perhaps it would at least slightly more secure to limit the unlock distance to 1 (or whatever lowest value it takes)... and with a desktop machine, put the bluetooth antenna in hidden location.  Just an idea.

---

### Post by TNH on 2008-02-22
This worked perfectly for me. Just had to add that I can confirm it works for the Samsung X820. Are there any other possible uses for it other than locking the computer, gaim, light switching etc? Prehaps some sort of shell script integration? Any ideas, I'm sure there is a lot of potential for this. :-)

---

### Post by jaltenburg on 2008-02-22
Great Idea! I'm going to try this tonight with a Samsung A930.

---

### Post by Kalenjin on 2008-02-23
LG F2400 is confirmed and a cheap usb bluetooth dongle is enough

Initially had some trouble pairing my phone. Used: [http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu) to get it done.

Got it working nice and stable with the LG F2400 (known for its unstable bluetooth support). I had to set the distance between 8 and 13 because of the unstable signal. I use a cheap usb bluetooth dongle (9 euros) from icidu which could also be responsible for the unstable distance readings. It locks and unlocks at about 3 meters with these settings.

---

### Post by shortguy on 2008-02-23
I'm using an LG Voyager, and this process does work on it.  The only thing is that the phone treats my computer as a bluetooth headset, so I'm not getting any sound on my phone unless I manually switch to audio on phone for every call.  I don't know if this is a phone setting or a computer setting, but can anyone help me out with this?

---

### Post by Kalenjin on 2008-02-23
> **shortguy said:**
> I'm using an LG Voyager, and this process does work on it.  The only thing is that the phone treats my computer as a bluetooth headset, so I'm not getting any sound on my phone unless I manually switch to audio on phone for every call.  I don't know if this is a phone setting or a computer setting, but can anyone help me out with this?

I'm relatively new to linux but i'll try. I've seen a setting in the bluetooth preferences GUI, System->Preferences->Bluetooth preferences, which might help you  (see screenshot). I've got three options, unspecified (default), desktop workstation, laptop computer. Maybe setting one of these will help you?

I've got amarok and pidgin interaction working also. I've written the following snippets. 

First you'll need to install purple-remote to be able to change the status of pidgin:
```
sudo apt-get install libpurple-bin
```

Next you'll need to make two scripts, i've called them proximity-lock.sh and proximity-unlock.sh. But you can rename them to anything you like. 

Lock
```
gedit ~/Scripts/proximity-lock.sh
```
and paste the following:
```
#!/bin/bash

gnome-screensaver-command -l
amarok --pause
purple-remote setstatus?status=away
```

Save and close


Unlock
```
gedit ~/Scripts/proximity-unlock.sh
```

```
#!/bin/bash

gnome-screensaver-command -dp
amarok --play-pause
purple-remote setstatus?status=available
```
Save and close.

Now make these scripts executable by setting the appropriate permissions with nautilus or the following commands

```
chmod 755 ~/Scripts/proximity-lock.sh
chmod 755 ~/Scripts/proximity-unlock.sh
```

Now go to your blueproximity settings and at the locking tab change the lock command to ```
~/Scripts/proximity-lock.sh
``` and the unlock command to ```
~/Scripts/proximity-unlock.sh
``` or the equivalent.

This should do the trick, but i'm no Linux wizard so maybe i'm missing something here... Some may argue this is useless but i like being lazy and being nice to the neighbours ;)

---

### Post by Iceni on 2008-02-23
> **shortguy said:**
> I'm using an LG Voyager, and this process does work on it.  The only thing is that the phone treats my computer as a bluetooth headset, so I'm not getting any sound on my phone unless I manually switch to audio on phone for every call.  I don't know if this is a phone setting or a computer setting, but can anyone help me out with this?

Without being an expert on bluetooth myself, I belive this can be related to the channel you use. If you scan channels:

```
sdptool browse
```

and select the one use for "object push" (that's the one I'm using) instead of the headset one this could solve your problem.

---

### Post by Iceni on 2008-02-23
> **Kalenjin said:**
> 

```
#!/bin/bash

gnome-screensaver-command -l
amarok --pause
purple-remote setstatus?status=away
```


Damn, pausing and unpausing amarok was this easy? I tried for hours to accomplish this (altho lots of my trouble being limited script knowledge).

Btw, take a look at the scripts I attached to the first post - the amarok piece will check if your amarok is playing and only start amarok again if it is paused, not if it is stopped. Found it handy for the times I'm not using amarok.

---

### Post by Mourning Star on 2008-02-23
Sanyo Katana  works like a charm!

Excellent app!

---

### Post by lime4x4 on 2008-02-24
will this work with the usb dongle that comes with a logitech mx5000 bluetooth keyboard and mouse? Or must i go out and buy another bluetooth dongle?

---

### Post by steveneddy on 2008-02-24
> **GodsDead said:**
> woah ausom idea, i just need a bluetooth adaptor for my PC now 0_o
if i use a bluetooth USB.. if someone takes it out, then what happens?

uh.....

---

### Post by Iceni on 2008-02-24
> **GodsDead said:**
> woah ausom idea, i just need a bluetooth adaptor for my PC now 0_o
if i use a bluetooth USB.. if someone takes it out, then what happens?

Then nothing happens and you have to log on the usual way:)

---

### Post by lunatico on 2008-02-24
Oh God, so cool!!!
Works fine on a Sony Ericsson K610i

---

### Post by lunatico on 2008-02-25
Me again...
Just to add and make it more clear for some....
I had the all ports "closed or denied" problem... did the "sdptool browse" command and for my phone the channel that says "object push" is 6, used it and work perfect.

---

### Post by ChrisMalarky on 2008-02-25
Works great here on a SE K800i :-)

---

### Post by Iceni on 2008-02-25
> **lunatico said:**
> Me again...
Just to add and make it more clear for some....
I had the all ports "closed or denied" problem... did the "sdptool browse" command and for my phone the channel that says "object push" is 6, used it and work perfect.

Excellent! I'll add the info to the faq.

---

### Post by Kalenjin on 2008-02-25
> **Iceni said:**
> Damn, pausing and unpausing amarok was this easy? I tried for hours to accomplish this (altho lots of my trouble being limited script knowledge).

Btw, take a look at the scripts I attached to the first post - the amarok piece will check if your amarok is playing and only start amarok again if it is paused, not if it is stopped. Found it handy for the times I'm not using amarok.

That would be handy :), i'll check it out

---

### Post by durand on 2008-02-26
Thanks a lot! Works on my old Sony Ericcson P800. Those scripts are pretty cool...I've been searching on how to do that.

---

### Post by SuperMike on 2008-02-27
This hits tilt on the cool factor. Too bad my Dell PC doesn't have bluetooth.

Now if I could get the microphone to recognize the sound of my voice, I'd love to make a sound to turn on my screen lock, and then another sound to unlock it.

---

### Post by jpjpjr on 2008-02-28
Works great with my Motorola Rokr E1

---

### Post by kasulstyls on 2008-02-28
works good on an 8125 on channel 3.

Thanks for this how to

---

### Post by Windsurfer619 on 2008-02-28
Worked on my Bell Mobility Motorola RAZR V3c!
Thank you so much! This rocks!

---

### Post by Iceni on 2008-02-29
> **kasulstyls said:**
> works good on an 8125 on channel 3.

Thanks for this how to

I don't know what make an 8125 is ;)

---

### Post by Coralin on 2008-03-01
QUick report; a phone that this doesn't seem to work on- T-Mobile Samsung Stripe.
Luckily, it DOES like my bluetooth headset.. ^_^

---

### Post by estanton on 2008-03-02
Painless and works perfectly for my Nokia 6131. The phone went crazy when I scanned the ports though.

---

### Post by Kasakato on 2008-03-02
It appears I cannot get my iPhone to work with this program. Perhaps its because it currently only supports the voice protocol.

---

### Post by estanton on 2008-03-03
I've noticed that even when I set the time down to 0 it still takes a good 20 seconds for the machine to lock. This is when I just switch the bluetooth off on my phone. Also it seems to always find the phone even when I set the range down to 0, admittedly this is in my apartment, but I am placing the phone a good 20 feet away. Anyone else having this (minor) issue?

---

### Post by Basil101 on 2008-03-04
Working great with my Nokia 7600 (RFCOMM Channel 9).
Great how to, thanks! :D

---

### Post by fastfret79 on 2008-03-07
Works great on a Samsung D600 using channel 7 :)
Very cool, Thanks!

---

### Post by lime4x4 on 2008-03-08
i have my phone paired with my pc which is currently running hardy 64 bit. The program doesn't detect my phone even thou it's paired with my computer. Any ideas?

---

### Post by mjamesd on 2008-03-11
Hells yeah. I've been looking for something like this for awhile! Confirmed working on a Samsung a900m after setting the channel to 5 (the "OBEX Push" channel).

---

### Post by highno on 2008-03-15
Hi there,

I am pleased to see so many active users of my software. For those not working I would like to invite you to file a bug on Sourceforge.net or in Launchpad. It seems that most problems can be solved. I know that there are only very few really incompatible devices.

General hints: 
if blueproximity does not see your phone it is most likely an unusable rfcomm port. On some phones these ports will be closed very fast if no traffic or none of the expected traffic is seen. Therefore that port appears to be usable in the scanner but it is not. Try a different port. Few devices will show this on every port, if you think your device is one of those please drop me a line which bluetooth adapter and mobile device you have.

If blueproximity only gives you a zero for the distance at all distances it might be your bluetooth adapter not giving back reasonable results on the signal strength parameter or your mobile's bluetooth device is REALLY strong and you would have to move it to a big distance. My old nokia gave me nice results with lock distance set to 4, my iphone now needs 10, just as an example...

I hope this helps a bit.

Bye
Lars

---

### Post by highno on 2008-03-15
Cool idea - once I find some more time I will look if I could make something like this.

Bye
Lars

---

### Post by lime4x4 on 2008-03-15
i have to phones that this cool app doesn't c for some odd reason
1st phone motorola razor only a couple of months old
2nd phone lg chocolate phone

---

### Post by highno on 2008-03-15
so you don't see any usable channels with them? If so, did you try the manual way:
> Do a "sdptool browse" in the terminal and find the channel marked as "object push". Select this channel in BlueProximity preferences. This should do the trick.

---

### Post by iRule on 2008-03-15
this still working on ubuntu 7.10?

or there is better solutions?

---

### Post by highno on 2008-03-15
There is no reason it should not work. Did I mention that BlueProximity has now made it into Hardy Heron? You could download that package directly and it should install on Feisty and Gutsy without a problem. The python-support dependency was build-time only and was a mistake in the old .deb file.
Bye
Lars

---

### Post by iRule on 2008-03-15
why blueproximity doesn't apear in synaptic or in add/remove programs?!

---

### Post by lime4x4 on 2008-03-15
john@john-hardy:~$ sdptool browse
Inquiring ...
Failed to connect to SDP server on 00:15:83:04:DC:80: Connection timed out
john@john-hardy:~$

---

### Post by lime4x4 on 2008-03-15
that's not even my phone it's my wife's computer..

---

### Post by iRule on 2008-03-15
if this dont appear in synaptic or add/remove programs as i said in my preview post, HOW I UNINSTALL THIS?!?!

plz answer

---

### Post by mkzimms on 2008-03-15
spdtool doesn't show me anything for the device...

```

mikez@mikez-gusty:~$ sudo sdptool browse
Inquiring ...
Browsing 00:1E:7D:94:7E:C3 ...
mikez@mikez-gusty:~$ 

```

its a Samsung Blackjack II successfully paired, but no luck on finding with finding an open channel.  Anyone get it to work with this phone?

---

### Post by lime4x4 on 2008-03-15
it's in synaptic on hardy

---

### Post by iRule on 2008-03-15
i use 7.10. hardy is version Alpha.....

---

### Post by iRule on 2008-03-16
Its'a all configured, and the system tray icon is working like a charm....BUT, mu PC doesn't execute the commands to lock and unlock the screen. I only see the system tray icon changing the color, but the command dont execute... :(

Can someone plz help me?

---

### Post by highno on 2008-03-16
iRule: Uninstall will work with synaptic as packages installed (also manually) will always appear there.

Yes, it is a Hardy package but on the .deb on the website should also work with Feisty and Gutsy. Just download it and Install it via
sudo dpkg -i filename.deb

If you say commands are not executed are you sure those commands work if you start them manually from the console? Like locking/unlocking with the wrong command? Please try that.

If phones don't show anything with sdptool browse you could try if they are more verbose if you set them to visible mode in your phone's bluetooth settings. This is just a try. of course after finding the phone and a usable channel you can switch off visibility on the phone.

Bye
Lars

---

### Post by lightchaser on 2008-03-24
Wow this is cool. Works on Nokia 5300 Xpress Music.

---

### Post by gertvdijk on 2008-03-24
First of all: great program, great how-to! Genius idea: locking pc on bluetooth signal strength. :lolflag:
Instead of Amarok, I use Rhythmbox and I got it to work with Rhythmbox as well, so here's a little how-to for Rhythmbox.
[LIST=1]
[*]**Make bash scripts**
To be able to run multiple commands it is preferable to use a bash script. Let's make some, if you don't have already.
[LIST=1]
[*]Open up a terminal and execute the commands in the code blocks.
[*]Let's create a blueproximity directory in your home-dir.```
mkdir ~/.blueproximity
```
[*]Create the bash files.```
touch ~/.blueproximity/lock.sh ~/.blueproximity/unlock.sh
```
[*]Edit the lock file:
```
gedit ~/.blueproximity/lock.sh
```
[*]Insert the following code:
```
#!/bin/bash

# Lock the screen (default BlueProximity)
gnome-screensaver-command -l
# Let's pause Rhythmbox
rhythmbox-client --pause --no-start
```
[*]Save and exit Gedit
[*]Likewise for the unlock script:
```
gedit ~/.blueproximity/unlock.sh
```
[*]Insert the following code:
```
#!/bin/bash

# Unlock the screen (default BlueProximity)
gnome-screensaver-command -d
# Let's resume Rhythmbox
rhythmbox-client --play --no-start
```
[*]Save and exit Gedit
[*]Make the bash scripts executable (and readable) for everybody by using the following command
```
chmod a+r+x ~/.blueproximity/lock.sh ~/.blueproximity/unlock.sh
```
[/LIST]
[*]**Let Blueproximity use your bash scripts**
[LIST=1]
[*]You can now close the terminal and open up the BlueProximity preferences (at tab *Locking*).
[*]Use as locking command [FONT="Courier New"]~/.blueproximity/lock.sh[/FONT] and likewise for the unlocking command [FONT="Courier New"]~/.blueproximity/unlock.sh[/FONT].
[/LIST]
[/LIST]

*Note: The *[FONT="Courier New"]--no-start[/FONT]* option makes sure Rhythmbox does not open an instance when there is none. Otherwise, Rhythmbox will start when (un)locking when no instance is open. See also *[FONT="Courier New"]rhythmbox-client --help[/FONT]*.*

Other possible options for the [FONT="Courier New"]rhythmbox-client[/FONT] command, see [FONT="Courier New"]rhythmbox-client --help[/FONT].
I can think of lowering the volume and bringing up again, in a for-loop to increase it smoothly. Or not pausing the music when your favourite artist is playing at the moment... 8-)

N.B. My phone, Nokia E50 works perfectly, at channel 9.

---

### Post by designwiz on 2008-03-25
Amazing App.. works flawlessly on my p1i.. had to use sdptool browse and find the object push channel which is channel 3 for p1i...

for those whom the application does nothing but change icon from green to red etc.. a simple reboot may or rather does solve the prob..

Great Work in puttin this tut Cheers

---

### Post by calraith on 2008-03-27
I'm using Hardy beta, and blueproximity is in the universe repos now.

---

### Post by bobbob1016 on 2008-03-29
My BlackJack II works on channel 1.

If anyone is worried about cell phone battery life, you just have to turn the bluetooth off when you leave, and on when you get back.  Not as "hands free" as it would be to leave it on, but cool none the less.

Is there a way to get this to enable my compiz screensaver?  I'd prefer the cube rotating to the gnome screensavers.  

Thanks for the tutorial.

---

### Post by crocowhile on 2008-03-29
Thanks for the scripts. It is a nice idea.
Only thing is that if Amarok is not running there will be a delay and an error message when the scripts interrogate its status.
I solved modifying the script in the following way:

```

#!/bin/bash 
# amaroK info conky script 

amarok_on=`ps aux | grep amarokapp --count`

if (($amarok_on > 1)); then

	stat=`dcop amarok player status` 
	if (( $stat == 2 )); then 
	`dcop amarok player playPause`
	    	else 
			if (($stat == 1 ));then
			`dcop amarok player playPause`
		
			else
				if (($stat == 0 )); then
				echo amarok nok playing
		
			fi
		fi

	fi 
fi

```

---

### Post by crocowhile on 2008-03-29
Also, if you use skype you can set blueproximity to change skype status too.
In order to do that you first need to install a skype4Python wrapper from [here]("http://sourceforge.net/project/showfiles.php?group_id=202148&package_id=240783").
Download the multiplatform tar.gz, uncompress it in a temporary folder then from that folder execute:
```

sudo python setup.py install

```
This will install the python wrapper. You can now remove that temporary folder.
Now you can download a series of very nice command line python scripts for skype from [here]("http://www.oberle.org/skype_linux_tools").
Place them wherever you like; I chose a subfolder in my home.
Test that everything worked correctly moving to that folder and typing:
```

./change_availability.py AWAY

```
Skype will inform you that a third party program is trying to comunicate to him. Tell him to always accept incoming connection from it.

Then edit the bp_lock script adding these lines:
```

#set skype status away
`/home/gg/bp_scripts/skype_scripts/change_availability.py AWAY`

```
and of course the unlock script too:
```

#set skype status online
`/home/gg/bp_scripts/skype_scripts/change_availability.py ONLINE`

```

And there you go!

---

### Post by red_five on 2008-04-03
Here's the script I use now. It's a single, monolithic script that handles away, available, status update messages, and proximity "poking". I've put in lines for several audio players (GNOME; I don't use KDE), Twitter, Pidgin, and even a line to update my Out of Office status in Exchange via Outlook Web Access. Most things are in functions, and you can add your own functions and status checks for whatever audio programs or web services you use. It could probably use some further cleanup and tweaking, but it works and has some  internal documentation.

Requirements:
purple-remote, to update Pidgin
zenity, for the status update dialog
curl, for sending updates to Twitter and Exchange

Again, I stick this in ~/bin, and set it executable. Oh, and if you run it in a shell with no parameters, it will display some help.

```
#!/bin/bash
# The away message
away_msg="I'm testing my status script."

# The available message
available_msg="I am at my desk."

# Send updates to chat programs and external websites?
# Highly recommended to use a .netrc file for external websites
exchange=1
exch_link="http://barracuda/exchange/NButterworth/?Cmd=options"
twitter=1
pidgin=`pgrep pidgin` # stays null if it's not running

# Tests for running audio applications. Add yours!
if [ `pgrep vlc` ]
then
	audio_player="vlc"
elif [ `pgrep banshee` ]
then
	audio_player="banshee"
elif [ `pgrep exaile` ]
then
	audio_player="exaile"
elif [ `pgrep rhythmbox` ]
then
	audio_player="rhythmbox"
fi

# Misc. variables
DOC_REQUEST=70

: <<DOCUMENTATIONXX
This script is used by BlueProximity (http://blueproximity.sourceforge.net/),
and allows you to automatically set your current status as away or available.
It will:
* Toggle pause state of audio playback
* Set your current status in Pidgin
* Send updates to Twitter
* Update your Microsoft Exchange Out-of-Office status via Outlook Web Access
* Lock your desktop when away, and unlock it upon your return
* Any other status-dependent changes to your desktop or applications

It will also poke the screen saver when you're close, to keep it from
activating and interrupting your work.

Usage: btmon-status <status>
where <status> is one of:
* help -- This help text
* away -- Set your status to away
* available -- Set your status to available
* update -- Set your status-to-be, when you will be away for a while
* poke -- Keep your screen saver from activating

--Nelson Butterworth, Apr 3 2008
nelson.butterworth@gmai.com
DOCUMENTATIONXX

# Function declarations
pause_audio () # This function pauses whatever audio player is playing. Add yours!
{
	player=$1
	case $player in
		"vlc")
			if [ "x`echo status | nc localhost 9000 -q 1 | grep "play state: 1"`" != "x" ]
			then
				amixer set PCM 0 # vlc doesn't like to stream playback, at least not via the telnet pipe
			fi;;
		"exaile")
			exaile --play-pause;;
		*)
			$player --pause;;
	esac
}

resume_audio () # This function resumes whatever audio player is playing. Add yours!
{
	player=$1
	case $player in
		"vlc")
			if [ "x`echo status | nc localhost 9000 -q 1 | grep "play state: 1"`" != "x" ]
			then
				amixer set PCM 70% # vlc doesn't like to stream playback, at least not via the telnet pipe
			fi;;
		*)
			$player --play;;
	esac
}

update_status_msg ()
{
	# Display dialog to enter status
	location=`zenity --entry --title="Where am I?" --text="Current location: $1" --entry-text="I'm..."`
		
	# If text entry isn't null
	if [ -n "$location" ]
	then
		# Update away-status
		sed -e "3 s/away_msg=.*/away_msg=\"I\'m $location\.\"/" $0 > tmp
		mv --update tmp $0
		chmod a+x $0
	fi
}

# Connect to the web services of your choice, and set their statuses
# Add your own functions for other web services
update_twitter ()
{
	status="$1"
	curl --netrc --data status="$status" http://www.twitter.com/statuses/update.xml
}

update_pidgin ()
{
	status="$1"
	message="$2"
	purple-remote setstatus?status="$status"
	purple-remote setstatus?message="$message"
}

update_exchange ()
{
	case $1 in
		"away")
			status="1";;
		"available")
			status="0";;
	esac
	link="$2"
	message="$3"
	curl --netrc --ntlm --data OofState="$status" --data OofReply="$message" $link
}

case $1 in
	"away")	# I've moved away
		if [ -n "$audio_player" ]
		then
			pause_audio "$audio_player"
		fi
		if [ $pidgin ]
		then
			update_pidgin "away" "$away_msg"
		fi
		if [ $twitter ]
		then
			update_twitter "$away_msg"
		fi
		if [ $exchange ]
		then	
			update_exchange "away" "$exch_link" "$away_msg"
		fi
		# Lock desktop
		gnome-screensaver-command --activate
		;;
	"available") # I'm back
		# Unlock desktop and wake monitor(s)
		gnome-screensaver-command --deactivate
		gnome-screensaver-command --poke
		if [ $exchange ]
		then	
			update_exchange "available" "$exch_link" "$available_msg"
		fi
		if [ $pidgin ]
		then
			update_pidgin "available" "$available_msg"
		fi
		if [ $twitter ]
		then
			update_twitter "$available_msg"
		fi
		if [ "x$audio_player" != "x" ]
		then
			resume_audio "$audio_player"
		fi
		;;
	"update") # Update my away status
		update_status_msg "$away_msg"
		;;
	"poke") # Keep things awake when close-by
		gnome-screensaver-command --poke
		;;
	*) # How to use
		echo
		sed --silent -e '/DOCUMENTATIONXX$/,/^DOCUMENTATIONXX$/p' "$0" |
		sed -e '/DOCUMENTATIONXX$/D'
		exit $DOC_REQUEST;;
esac
```

---

### Post by highno on 2008-04-04
Hi red_five,

the script looks cool. I don't know how many people are using blueproximity so I don't know if it would be worth developing a gui to these additional functions. I am short of time at the moment anyway but I think I'll catch on later with this.
Thanks for contributing this nice script.

Bye
Lars

---

### Post by durand on 2008-04-04
Doubt there would be much point cos its already simple enough. I would love to properly use this script but I just don't have any reason to....Maybe its good in an office environment but at home when the computer is off when I'm not on it, there's no reason for this.

---

### Post by meddigo on 2008-04-10
Tried and tested on a SE K810.  Works perfect.  I'll be able to test a K850 in a couple of weeks if no one else has...

Medd

---

### Post by lunatico on 2008-04-10
Hey!
I reinstalled my OS and when installing this I noticed that the link for the python-support package is broken. It should be updated to [http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5ubuntu1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5ubuntu1_all.deb)
Cheers!

---

### Post by bunny rabbit on 2008-04-23
This gadget is really cool, and actually, for me it is handy as well. It (obviously) works with a nokia 6630 too.

But when Amarok plays streaming media, it does not disconnect from the server when it is paused. Isn't that a problem?

In case I want to have Amarok stopped instead of paused when I leave, what would that script, bp_amarokplay, have to look like?

---

### Post by durand on 2008-04-23
Replace "dcop amarok player playPause" with "dcop amarok player stop"

---

### Post by bunny rabbit on 2008-04-24
Thanks. This is fun.

---

### Post by trappy on 2008-05-02
Indeed it is very cool. 
I was figuring if there's a way to totally mute all sound, instead of just pause Amarok (cause I am not using amarok, I am using Exaile, and there are several other sounds that I dont want going off on the highest volume when I'm gone if I forget to turn of my amplifier).

Anyone? :)

---

### Post by durand on 2008-05-02
Not sure about the exact command but u should look up pulseaudio and alsa commands

---

### Post by indomiti on 2008-05-06
It works with my Nokia N95.

But when using a bluetooth headset at the same time the sound when talking to someone is very bad, so i cant use this.

---

### Post by Psyphre on 2008-05-08
Hi, awsome program, ive installed it and its detected my samsung u600, can tell its range etc. But it doesnt lock when its out of range.
In the system tray it does say "simulation mode (locking disabled)", how do i enable it then?

thanks.

---

### Post by Sub101 on 2008-05-08
enable locking in your screensaver and use the lock command of

```
/usr/bin/gnome-screensaver-command --activate 
```

and deactivate with the same as above except with --deactivate

---

### Post by Psyphre on 2008-05-08
thanks sub, but i figured out that if i change to channel 2 (isntead of 1) it works perfectly!!

---

### Post by daverave999 on 2008-05-11
Thanks, this is really good! I've had to turn down the locking duration to 2 seconds or for some reason it takes much longer than the specified time to lock. I'm using a Sony Ericsson W810i

[EDIT] Oh yeah, this is on Hardy and I just installed blueproximity and libpurple-bin through Synaptic... I assume I was correct in setting the owner to root for those scripts in /usr/bin ?

---

### Post by MrJHazelton on 2008-05-20
Thanks for the solid review of this

I got it to work perfectly with Verizons **LG Chocolate**

---

### Post by ubuntism on 2008-05-29
Works for samsung g600 and on mint linux

---

### Post by Kalenjin on 2008-06-01
samsung d500 working flawlessly on hardy, and channel 3.

channel 7 keeps giving warnings on the phone, channel 3 doesn't.

---

### Post by fiatguy85 on 2008-06-10
Channels 1-6 seem to work on a Blackberry 8820

---

### Post by techstop on 2008-06-12
Thanks, eventually got it working here with a Nokia 3500. I'm using Hardy 64-bit. A couple of things though;

-I didn't need to download python, I already had the suggested version installed
-I could install BlueProximity from the repo, no need to download a deb
-When BlueProximity scanned for channels on my phone, all of them were closed (I had to do the scan and find the object push channel as suggested earlier)
-I had to activate locking on the screensaver and change the lock / unlock command as posted by sub101 a few posts above

Apart from that, it was pretty easy! Thanks for an awesomely cool app. I'll have to try the script to pause/unpause Rhythmbox. Cheers!

---

### Post by cudaman73 on 2008-06-12
I'd like to report this howto and Blueproximity as working flawlessly with a Cingular/AT&T 8525 (or HTC Hermes).

Thanks for the how-to!

---

### Post by Hegrow on 2008-06-12
Hi all, 
I would love to use BlueProximity but I can't get it right ....
My phone is detected, but no ports are.. and with spdtool I get this message
```
hegrow@hegrow-desktop:~$ sdptool browse
Inquiring ...
Browsing 00:1A:1B:C9:E8:6A ...
Service Search failed: Connection timed out

```
... I have a motorola l7 slvr. The connection normally times out after 60 seconds but the connection fails after 20-30 seconds ... ( At that time my phone does go back in 'invisible-mode' .. But even if I start the 60 seconds over and over again, it will always stop...
My dongle is a Cheap Usb stick... And my phone and pc are paired

// I also noticed that my phone gets stuck when I try to view the services....
And that the distance is always on 0 ...
I tried to use multiple channels

Anyone?

Thankx!

---

### Post by Hegrow on 2008-06-12
> **Hegrow said:**
> Hi all, 
I would love to use BlueProximity but I can't get it right ....
My phone is detected, but no ports are.. and with spdtool I get this message
```
hegrow@hegrow-desktop:~$ sdptool browse
Inquiring ...
Browsing 00:1A:1B:C9:E8:6A ...
Service Search failed: Connection timed out

```
... I have a motorola l7 slvr. The connection normally times out after 60 seconds but the connection fails after 20-30 seconds ... ( At that time my phone does go back in 'invisible-mode' .. But even if I start the 60 seconds over and over again, it will always stop...
My dongle is a Cheap Usb stick... And my phone and pc are paired

// I also noticed that my phone gets stuck when I try to view the services....
And that the distance is always on 0 ...
I tried to use multiple channels

Anyone?

Thankx!

Aah wonderful ! There was no problem after all ... When I walk away, my screen becomes blank!

Thank you for this revolution!:popcorn:

---

### Post by damis648 on 2008-06-12
I would love to have this... but my iPhone will not pair. After much research, i found out that the iPhone will only pair with audio devices. Has anybody got this to work with thier iPhone and how? I can see it with 'hcitool scan' and can see it when i browse devices but none of my services will connect and my iPhone will not find my computer... help?

---

### Post by Hegrow on 2008-06-13
> **damis648 said:**
> I would love to have this... but my iPhone will not pair. After much research, i found out that the iPhone will only pair with audio devices. Has anybody got this to work with thier iPhone and how? I can see it with 'hcitool scan' and can see it when i browse devices but none of my services will connect and my iPhone will not find my computer... help?

I also wasn't able to pair my cell and my computer by my cell...
I've installed "blueman bluetooth manager", you can find this in the synaptip packages ;). With that program I was able to pair the cell and this pc ! 
Good luck!

---

### Post by damis648 on 2008-06-13
> **Hegrow said:**
> I also wasn't able to pair my cell and my computer by my cell...
I've installed "blueman bluetooth manager", you can find this in the synaptip packages ;). With that program I was able to pair the cell and this pc ! 
Good luck!

Thank you for the suggestion, it worked perfectly! And than!k you for this guide! I wrote my own script that pauses my rhythmbox, sets me as away in pidgin, and locks the computer!

---

### Post by monojohnny on 2008-06-13
And an alternative (crappy!) DIY method can be tried using the following simple shell script - I include this here for fun only. Enjoy !
:)

--- CUT HERE ----
#!/bin/sh
# "bluetooth_alarm.sh".
# Shell script to beep annoyingly at you as your bluetooth enabled phone
# is stolen from you in your local coffee shop.
#
# Fun: 6/10 - "Quite Fun"
# Usefulness: 2/10 "Not Very"
# Phone needs to be connected via bluetooth - just 'browse device' initially
# From KDE bluetooth icon, then run the script.
#
# Install 'beep' for this to work to its full potential
# "sudo apt-get install beep"
#
# 'Tested' on ubuntu 8.04, Dell Optiplex GX110, with USB bluetooth dongle
# 'lsusb' output:
#  "0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)"
# (Replace XX:XX:XX:XX with your device's bluetooth address of course!)
QUALITY=255
while [ "$QUALITY" -ge 200 ]
do
        QUALITY=`hcitool lq  XX:XX:XX:XX |awk -F":" ' { gsub(/ /,""); print $2 } '`
        printf $QUALITY"."
        sleep 2
done
beep -l 100 -f 300 -r 15
--- CUT HERE ---

---

### Post by gvartser on 2008-06-17
I tested this with HTC phone, and it worked great. Had to test a couple of ports, "port # 5 was the best one"

Here you have the script that i wrote: 
- (lock unlock script using input parameters: "LOCK or UNLOCK.")


Usage: ./script_name.sh <LOCK or UNLOCK>
 
```
#!/bin/bash
#
# Author: Gvartser - 20080617
#
ESPEAK="/usr/bin/espeak -v lancashire"
SCRCMD="/usr/bin/gnome-screensaver-command"
export ESPEAK SCRCMD

AmaroK(){
       if [ "$(ps -ef | grep -v grep | grep amarok | wc -l)" != "0" ]
       then
                amarok ${1}
                if [ "${1}" = "--pause" ]
                then
                        sleep 3
                fi
       fi
}

SecureWS(){
         case ${1} in
                LOCK)
                        AmaroK --pause
                        ${ESPEAK} "Terminal lockdown, initiated!"
                        ${SCRCMD} -l
                        purple-remote setstatus?status=away
                        ;;

                UNLOCK)
                        ${ESPEAK} "Terminal is beeing un locked!"
                        ${SCRCMD} -d
                         AmaroK --play-pause
                         purple-remote setstatus?status=available
                        ;;
        esac
}

#######################
# Script starts here:
#
if [ "${#}" -ne "1" ]
then
        echo "Invalid usage: ${0} <LOCK> or <UNLOCK>"
        exit 100
else
        SecureWS ${1}
fi

```

/g

---

### Post by volkanb on 2008-06-18
the lock_on lock_off script use is great. i'm trying to tweak it for my own purposes. from reading the article, some replies from users and common sense i made this lock_on script

```


#!/bin/bash

#turn on screensaver
`gnome-screensaver-command -l`

#this turns the monitor off
`xset dpms force off`

#turn off music
kill `ps -ef | grep songbird | grep -v grep | awk '{print $2}'`

#Skype status to away
`change_availability.py AWAY`

#if inactive for 2 hour then shut down computer
sleep 7200
sudo shutdown -h now


```

I simply kill songbird because i can't pause it from command line, if anyone know how, i really like to know.

Skype away feature is cool, thanks for the tip crocowhile

i also want to suspend the computer if i'm away for a long while, but my pc doesn't come out of suspend clearly so i just shutdown which is ok for me. i used [_this_]("http://ubuntuforums.org/showthread.php?t=135699") page to make shutdown work.

my only problem is that ones the sleep features initiates it doesn't stop anymore even after lock_off.
lock_off script:

```

#!/bin/bash

#turn on screensaver
`gnome-screensaver-command -d`

#this turns the monitor off
`xset dpms force on`

#Skype status to Online
`change_availability.py ONLINE`

```
 
can't seem to fix that, anyone have an idea?

---

### Post by elcman on 2008-07-25
I have a question for you BlueProximity pros out there...

I've got my V3t phone attached and I'm trying to use it with BlueProximity for the basic locking and unlocking functionality. HOWEVER, my ATM always reads 0, even when at a distance.

I have tried every channel to find one consistent reading (10 is the RFCOMM channel, which ends up being the most consistent) but I find that when I walk away from my phone or leave my phone and walk away with my laptop, even at a significant distance, I'll get with 1 or 2 or 127.

At that point, my cell phone disconnects and it won't reconnect without me prodding the machine to discover the phone again.

All of my settings seem to be correct but I do have to do a **hciconfig hci0 reset** or **hciconfig hci0 up** to get it working the first time after a reboot.

Most of the time, my signal strength and quality are just plain erratic with this device yet it does pair and they know each other.

I'm using a Thinkpad x23 with the Bluetooth Daughter Card, it might be the quality of the card, but it seems to do fairly well when it *is* working. It just doesn't give me consistent results on proximity.

Any information would be great!

---

### Post by CaptMorgan on 2008-08-03
Can't seem to get this to work, I have paired my phone is advance, ports 1-5 show up as useable and I have gone through them all, I have set the settings really low to 5 feet 3 seconds, the distance bar jumps continually never just stays put with where my phone really is

Things that come to mind, 

I never installed any drivers for my bluetooth dongle, the icon showed up and can see my phone so I am assuming its good
 

I am using a 64bit machine and install?

When trying to get the updated python I get this

"captain@captain:~$ wget [http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5_all.deb)
--19:14:50--  [http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python-support/python-support_0.7.5_all.deb)
           => `python-support_0.7.5_all.deb'
Resolving security.ubuntu.com... 91.189.88.37
Connecting to security.ubuntu.com|91.189.88.37|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:14:51 ERROR 404: Not Found."

I am using Windows Mobile device HTC Touch - Sprint

Anyone have some words of wisdom?

---

### Post by typetokill on 2008-08-03
Hey people, i have just installed BlueProximity on my computer, i am running Xubuntu, and am unsure on what locking command (screen saver) to set it to, every thing els works fine, i used KBluetooth to pair my phone and every thing is running smoothly, apart from the main point, when i put my phone down stairs, it is well out of range and my window is minimized to the tray (so it wont think I'm on simulation mode) Nothing happens, the little key starts flashing and telling me that my phone is out of range, but still no locking to be seen. :(

Hopefully some of you might shed some light on the problem I'm having?

Hope to hear from you guys soon:)...

Brian A.K.A; Typetokill

PS: Here is The log, however it is not locking or unlocking!

> Mon Aug  4 03:06:33 2008 blueproximity: stopped.
Mon Aug  4 03:25:51 2008 blueproximity: screen is locked
Mon Aug  4 03:25:54 2008 blueproximity: screen is unlocked
Mon Aug  4 03:25:58 2008 blueproximity: screen is locked
Mon Aug  4 03:26:01 2008 blueproximity: screen is unlocked
Mon Aug  4 03:26:13 2008 blueproximity: screen is locked
Mon Aug  4 03:26:16 2008 blueproximity: screen is unlocked
Mon Aug  4 03:26:19 2008 blueproximity: screen is locked
Mon Aug  4 03:26:22 2008 blueproximity: screen is unlocked
Mon Aug  4 03:26:26 2008 blueproximity: screen is locked
Mon Aug  4 03:26:29 2008 blueproximity: screen is unlocked
Mon Aug  4 03:26:32 2008 blueproximity: screen is locked
Mon Aug  4 03:27:06 2008 blueproximity: screen is unlocked
Mon Aug  4 03:27:14 2008 blueproximity: screen is locked
Mon Aug  4 03:29:21 2008 blueproximity: screen is locked
Mon Aug  4 03:29:28 2008 blueproximity: screen is unlocked
Mon Aug  4 03:29:37 2008 blueproximity: screen is locked
Mon Aug  4 03:29:53 2008 blueproximity: screen is unlocked

---

### Post by kaoskorruption on 2008-08-06
Hey, I have a problem similar to CaptMorgan's. I don't know if this is related, but when I walk away, it slowly goes from 0 to 4 to 5 to 6 to 7 to 8 with at least a few seconds in between, even when I RUN the phone 20 feet away quickly. The same occurs when I run the phone back towards the computer. With that said, it takes a good minute to recognize that I'm gone and even longer to recognize that I'm back.

I'm using Verizon's EnV2 by LG with Bluetooth 1.2.

OH, and I also have the problem where the phone thinks the computer is a headset or something so if I call someone or someone calls me while it is connected, I can't hear anything and they can't hear me.

---

### Post by kd7swh on 2008-08-06
My Blackberry 8330 is pairing and seems to keep distance correctly. But BlueProximity seems to not want to lock the screen. It has said it is in simulation mode (locking disabled). 

How can I enable locking?

____

Got it.

---

### Post by Scotty Bones on 2008-08-07
This works great. Nokia 6085

---

### Post by AusIV4 on 2008-08-09
Seems to work with the Motorola RIZR. 

I have a little bit of a security concern here though. I like the idea of my computer locking when I walk away, but in theory someone could spoof my phone's MAC, allowing them to unlock the computer when I'm not there. I'd much prefer it lock when I walk away, and I type in the password when I come back.

Is there any preferred way to disable unlocking the screen? I've set the "Unlocking Command" to "true" (a command that returns true and exits), but I don't know if there's a better way to do this.

---

### Post by PinkFloyd102489 on 2008-08-09
I know it's not my cellphone, but Ive got my desktop working with my laptop. When I leave with my laptop in tow, the desktop runs a script that locks itself then SSHs over to my XP running Cygwin and runs a program called Nircmd that locks it too.

My friend has it working with his Verizon, no idea what brand.

---

### Post by Iceni on 2008-08-10
> **PinkFloyd102489 said:**
> I know it's not my cellphone, but Ive got my desktop working with my laptop. When I leave with my laptop in tow, the desktop runs a script that locks itself then SSHs over to my XP running Cygwin and runs a program called Nircmd that locks it too.

My friend has it working with his Verizon, no idea what brand.

That is seriously cool!

Anyway I finally updated the howto:)

---

### Post by Fanas on 2008-08-12
Thats a little slow, but still looks so awesome :)

---

### Post by Newy11 on 2008-08-26
GREAT!!! howto ive been waiting ages for a program like this to arise in linux and it works beautifully ;)

Has anyone found or can create a status script for Xchat?

Cheers all keep up the great work ;)

---

### Post by kasulstyls on 2008-09-11
Just putting it out there but I noticed on the main page that IPhone is stated not to work.  I have the 3g version and it does lock and unlock the screen.  


Kas

---

### Post by highno on 2008-09-11
Hi Kas,

what "main page" do you mean? I use the old iPhone and it works too. If it's somewhere on my homepage I should fix it :-)

Lars

---

### Post by kasulstyls on 2008-09-11
Hey Lars!!

Thanks for the app!! 

I ment the instructional page has a section of working phones and non-working phones.

--Past--
Working phones

    * I removed the phone list because .. well this seem to work with everything

Non-working phones

    * iPhones are reported as not working:/
--end past --


Thanks for the fix  :)

Have a good day!

kas

---

### Post by Iceni on 2008-09-11
Then I'll remove it;)

---

### Post by m00njal on 2008-09-11
Can someone link me to a guide on pairing the iphone via BT on 8.04? Im using a generic compatible adapter on my desktop, and blueman BT manager. The phone showed up once as a "smart phone" but no longer shows up when I scan, nor did pairing ever work. Hope to get this working for use with Blueproximity.

---

### Post by ocgstyles on 2008-10-03
> **kasulstyls said:**
> Hey Lars!!

Thanks for the app!! 

I ment the instructional page has a section of working phones and non-working phones.

--Past--
Working phones

    * I removed the phone list because .. well this seem to work with everything

Non-working phones

    * iPhones are reported as not working:/
--end past --


Thanks for the fix  :)

Have a good day!

kas

You got this working with iPhone 3G?  Can you post directions?  I tried blueman bluetooth manager like another poster said, but my puter still doesn't see it...

---

### Post by benz0 on 2008-12-05
I'm also not able to get my iPhone 3g to pair.  Do I need to jailbreak my phone to accomplish this?

---

### Post by tianshiz on 2009-02-02
Can anyone recommend a good bluetooth adapter for me? I need an adapter that works flawlessly with blueproximity.

---

### Post by ubuntwinkel on 2009-02-13
I have searched for some clue to solve this, but of the few things I have found, none of them work.  

I just want BlueProximity to run a script when I leave, which will start 'motion', the webcam motion detection program.  But I keep getting 'permission denied' errors, and motion dies.  Honestly, I have never gotten motion to run except by sudo on the CLI, and I do not think I can teach an automated script to do sudo for me--without exposing my root password in plain text which I won't do.  Recently, following some suggestion from somewhere now forgotten, I had chmod-ed some files/directories (changed the sticky bit) and got it to work as just 'motion' on the CLI, sans sudo.  

The problem is that motion cannot create the PID file, /var/run/motion.pid.  Permission denied.  

```
xxx@xxxbox:~$ motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Processing config file /etc/motion/thread1.conf
[0] Processing config file /etc/motion/thread2.conf
[0] Motion 3.2.9 Started
[0] Exit motion, cannot create process id file (pid file) /var/run/motion.pid: Permission denied
[0] Motion going to daemon mode
xxx@xxxbox:~$ sudo killall motion
motion: no process killed
xxx@xxxbox:~$ 

```

Motion does not go to demon mode (like it says).  It exits, like it says earlier.  

I'm mentioning this here since it is a script I am trying to use with blueproximity.  I know it does not have much else to do with this thread, but others here who use a script with blueproximity are likely to have run into something similar, and possibly resolved it.  

I hope.  Thanks.


edit
UPDATE

I can fix this, but only by making /var/run world writable.  Is that terrible to do?

---

### Post by robertos on 2009-03-11
Hi, I can't make it work :-(

I've paired a nokia 6103b with Ubuntu Intrepid Ibex through a broadcomm usb bluetooth stick. I sent images to my computer without problem using bluetooth-applet and gnome-obex-server.

Blueproximity doesn't find my cellphone, even if I shutdown the obex-server, it says "Sorry, the bluetooth devices is busy connecting. Please enter a correct mac address or no address at all for the config that is not connecting and try again later".

I tried shutting down every bluetooth software, unplugging the adapter, starting bluetooth daemon, plugging the adapter again (it gets detected) and starting blueproximity and the result is the same.

When I did an "sdptool browse" as root the answer was:

Inquiring ...
Inquiry failed

I suspect of some limitation of the USB stick... any ideas?

TIA for your help.

---

### Post by GregTheGerg on 2009-03-18
Well, I tried using this on my Motorola Razor (If it matters, the Miami Ink one with the dragon). But it doesn't work.... (Big sigh)

I was wondering if there's anyway to make it work. My phone's with T-Mobile. So, I don't know if that matters either.

Thanks guys! ^_^

---

### Post by rusty0101 on 2009-03-27
> **AusIV4 said:**
> Seems to work with the Motorola RIZR. 

I have a little bit of a security concern here though. I like the idea of my computer locking when I walk away, but in theory someone could spoof my phone's MAC, allowing them to unlock the computer when I'm not there. I'd much prefer it lock when I walk away, and I type in the password when I come back.

Is there any preferred way to disable unlocking the screen? I've set the "Unlocking Command" to "true" (a command that returns true and exits), but I don't know if there's a better way to do this.

One of the reasons that you have to enter a number when pairing two devices in bluetooth is to address the very concern you raise. However if you set the unlocking command to something like 'echo `date` - bluetooth device within range >> ~/btlog.txt' so that you have a log of the device comming within range may help.

Another means would be to create a script that gets an encrypted file off your phone, decrypt it with gpg, verify it matches expectations then unlock the screen, increment a serial number within that file, re-encrypt it, and put the encrypted file back on the device, and you should have a much more secure method of verification than just the mac address for the phone. If you have multiple computers, each could have it's own verification file that gets put on the phone.

-Rusty

---

### Post by GregTheGerg on 2009-03-27
Well, security is not my biggest issue at this point, maybe when someone gets into my computer via bluetooth. Which, I highly doubt will happen.

Have you guys come up with anything on the Razor?

Thanks in advance! ^_^

---

### Post by webfreakz on 2009-05-09
This program does work, however it only gives me a signal strength of '0' or '255'. Nothing in between those two... The problem with that is, that I can walk outside to the garden, and my desktop won't lock... Is there a way to get a value 0>...<255 ?

---

### Post by ubuntwinkel on 2009-05-15
I love blueproximity, but it has on occasion failed to detect my return.  I would like to run a small script as a cron job to restart it hourly to see if that remedies the issue.  

But, how does one stop 'proximity.py' in an automated way?

---

### Post by Billal on 2009-05-25
when i chose to the lock screen manually from the menu or the panel and have my cellphone close, it automatically unlocks the screen.
I want to be able to lock the screen manually and have my phone close to the computer and have Blueproximity unlocking the computer only when Blueproximity has lockt it, is it possible to achieve this?

Thanks.

---

### Post by K_REY_C on 2009-08-17
This is perhaps a bash question, but I've been trying to add a couple things to the rhythmbox script for blueproximity. Specifically
[LIST=1]
[*]Open my to-do list
[*]play a greeting tune
[/LIST]
The problem is that the to-do list (when closed) starts the screensaver lockout again, and then re-opens the todo list and replays the greeting tune. 

Any help appreciated. the little script is below. I've never even attempted any of this before and I just don't quite get it. 

If anyone knows how to, I'd also like to add time dependent items to the script: between 9 am and 5 pm only open the todo list, after 5 auto-open rhythmbox and start playing, etc...

Thanks in advance!

KYLE

> #!/bin/bash

# Unlock the screen (default BlueProximity)
gnome-screensaver-command -d
# Let's resume Rhythmbox
rhythmbox-client --play --no-start --notify
# Play Welcome Back File
play /home/username/Desktop/GMMMP.wav
# Open To-Do List
gnome-open /home/username/file/ToDo

---

### Post by yzf600 on 2009-09-03
I'm having problems getting my iphone 3g (3.0 OS) working with blueproximity on Jaunty 9.04. I have blueman installed, and I used it to pair my phone with my computer. It pairs correctly and a connection is established. Blueproximity sees the connection, and reports proper distance levels. I can even see the distance number grow as I move the phone further away. 

The problem comes in when I separate my phone from the computer for the 1st time, or turn the iPhone bluetooth off. When the phone is back in range (or on), blueproximity toggles between distance 0 and 127. My iPhone bluetooth settings show "not connected". If I instruct my iPhone to connect to my pc, the connection is established and blueproximity starts to detect a proper distance level. 

What is strange, though, is I installed ubuntu on my work mac book pro. Blueproximity works flawless on it. I take the phone out of range, screen locks. Bring the phone back in range, screen unlocks. 

I've tried 2 different bluetooth adapters (Broadcom 0a5c:2101 & Cambridge Silicon 0a12:0001) and both behave the same. I've inspected my syslog, but I don't see anything wrong there. I even tried a fresh 9.04 install on a blank hard drive, all with same results. 

Does anyone have any ideas what could be going on or how I can debug this further? Are usb bluetooth adapters really this sketchy under ubuntu? Do I have to keep buying new adapters until I find one that works?

Thanks a lot. 

BTW - I did notice something interesting in my macbook pro ubuntu syslog: kernel: input (my iPhone mac) as /devices/virtual/input/input18. What is this all about?

---

### Post by Shinger on 2009-09-16
Has somebody succeeded in using android combined with blueproximity?

---

### Post by pveurshout on 2009-10-04
Really nice feature. However, for some reason the connection quite often drops a while after walking away from my computer, which results in not being able to automatically unlock Jaunty (it does always lock itself and if I return shortly I don't experience any problems, though, so I guess the connection only drops after a certain time). After typing my password to log back in I shortly notice the BlueProximity tray icon showing there's no connection, and then the 'key' turns green (and a message shows up on my cell saying it connected to my PC). Does someone perhaps know where to start debugging this? I've tried setting all visibility options to 'visible', but that didn't solve anything. It works perfectly when I try stuff out in simulation mode, so I guess it has something to do with locking the session or something..

---

### Post by yzf600 on 2009-10-04
You might want to lower the unlocking duration to something like 1 or 2 seconds if you haven't already.

---

### Post by pveurshout on 2009-10-04
> **yzf600 said:**
> You might want to lower the unlocking duration to something like 1 or 2 seconds if you haven't already.

Yeah, already did that, but I don't think that's where the problem lies because when I use my password to log back in, the BlueProximity tray icon says there's no connection and it's trying to establish one (it generally succeeds a few seconds later, but as you can imagine it's of no use at that point anymore ;)).

---

### Post by BopNiblets on 2009-10-10
Hello guys, just got this working but when I'm watching videos with SMPlayer in fullscreen, my monitor turns off randomly (pausing blueproximity stops it) even when my phone is right near my bluetooth dongle.
I have the locking/unlocking/proximity commands set up like this:

gnome-screensaver-command -l && xset dpms force off
xset dpms force on && gnome-screensaver-command -d
gnome-screensaver-command -p

I'm guessing one of these is the problem, I just copied and pasted from the first post, not entirely sure why it's happening!

---

### Post by false_chicken on 2009-11-29
I too have the problem of the meter always jumping from 0 to 255. And not stopping anywhere in between. Any suggestions?

---

### Post by aglc2005 on 2010-01-09
So I have this working. Great program. The only issue I have noticed is that once my computer is idle (I have it set to 10 minutes) the screen saver will no longer come on. This has only started happening since I installed BlueProximity.

---

### Post by whiterabbit7500 on 2010-03-15
I have it working sporadicly on Kubuntu. What is the lock and unlock commands for KDE4? I've found several commands, but either they don't work correctly, or refuse to unlock the screen once its back in range.

edit: found info at [http://ubuntuforums.org/showthread.php?t=910276](http://ubuntuforums.org/showthread.php?t=910276)
The screen wakes up and sleeps fine, and it locks fine. but it's not auto-unlocking. Any ideas?

edit 2: solved with the below script
```
#!/bin/sh
PATH=$PATH:/opt/kde3/bin:/usr/bin
echo ${KDE_SESSION_VERSION}
case "$1" in
        lock)
                if [ -n ${KDE_SESSION_VERSION} ] && [ "$KDE_SESSION_VERSION" -eq 4 ]; then
                        echo "KDE4 detected do the magic..."
                        ####qdbus org.freedesktop.ScreenSaver /ScreenSaver Lock #one way
                        # better way bellow (unified) - should work with gnome too (gnome users please test)
                        dbus-send --type=method_call --dest=org.freedesktop.ScreenSaver /ScreenSaver org.freedesktop.ScreenSaver.Lock
                        # Dear NVIDIA shitty drivers so don't use this one too often
                        ####xset dpms force off
                else
                        echo "KDE3 detected do the magic..."
                        dcop kdesktop KScreensaverIface lock
                fi
                ;;
        unlock)
                if [ -n ${KDE_SESSION_VERSION} ] && [ "${KDE_SESSION_VERSION}" -eq 4 ]; then
                        echo "KDE4 detected do the magic..."
                        dbus-send --type=method_call --dest=org.freedesktop.ScreenSaver /ScreenSaver org.freedesktop.ScreenSaver.SetActive boolean:false
                        # Dear NVIDIA shitty drivers so don't use this one too often
                        xset dpms force on
                else
                        # KDE 3
                        echo "KDE3 detected do the magic..."
                        dcop kdesktop KScreensaverIface quit
                fi
                ;;
        *)
                echo "usage of $0:"
                echo " $0 (lock|unlock)"

esac
```

note: in blueproximities options, set the lock to the script location, with the "lock" option. For unlock, set it to "unlock" see below.

[http://launchpadlibrarian.net/31955612/snapshot.png](http://launchpadlibrarian.net/31955612/snapshot.png)

---

### Post by TechNife on 2010-03-26
Have confirmed it works well with these two cell phones.
(a) Motorola Ming A1200
(b) Samsung Corby Speed SCH-F339
Thanks a ton for this really cool utility.
:)

---

### Post by HPD2 on 2010-03-28
Works ok with the iPhone 3Gs just not sensitive enough, my locking distance is 1 for 5s and unlocking is 0 for 5 sec.

---

### Post by Timendus on 2010-06-17
> **ubuntwinkel said:**
> I just want BlueProximity to run a script when I leave, which will start 'motion', the webcam motion detection program.  But I keep getting 'permission denied' errors, and motion dies.

Hey Ubuntwinkel,

I've just built the same setup for myself, it's really quite simple. In case you haven't figured it out yourself yet, here's how I do it:

[LIST][*]I have a directory called Scripts in my home directory, so that's /home/tim/Scripts, which contains scripts called lock.sh and unlock.sh. It also contains a tailored motion.conf.
[*]Blueproximity is set to run lock.sh when I leave and unlock.sh when I come back.
[*]The magic is in the custom motion.conf, which tells motion to also store it's pid in /home/tim/Scripts and to store a video of all detected motion on my desktop.
[*] When I return to my PC, and there's a video file on my desktop, I know somethings up and I can watch the video to see who's been in my room.
[/LIST]

Here's the scripts and the config to replicate my setup:

**lock.sh** - Edit the path to your motion.conf!
```
#!/bin/bash
# "Lock screen" script for BlueProximity

### Lock screen
#gnome-screensaver-command -l

### Start motion

# Is motion running?
MOTIONPID=`pidof motion`
if [ "$MOTIONPID" == "" ]
then
        # Motion is not running
        # So start is up!
        motion -c /home/tim/Scripts/motion.conf
else
        # Motion is running
        # Send it a config reload
        kill -s SIGHUP ${MOTIONPID}
fi

# Done
```

**unlock.sh** - No need to edit
```
#!/bin/bash
# "Unlock screen" script for BlueProximity

### Unlock screen
#gnome-screensaver-command -d

### Stop motion

# Is motion running?
MOTIONPID=`pidof motion`
if [ "$MOTIONPID" != "" ]
then
        # Motion is running
        # Shut it down
        kill -s SIGTERM ${MOTIONPID}
fi

# Done
```

As you can see, the Gnome desktop lock/unlock commands are also still in there, in case you want them. I keep them commented.

**motion.conf** - Edit location for PID file (process_id_file) and location for movie (target_dir), otherwise just configure to match your webcam setup, see [here]("http://www.lavrsen.dk/foswiki/bin/view/Motion/MotionGuideGettingItRunning#Config_File_Options").
```
# Rename this distribution example file to motion.conf
#
# This config file was generated by motion 3.2.11


############################################################
# Daemon
############################################################

# Start in daemon (background) mode and release terminal (default: off)
daemon on

# File to store the process ID, also called pid file. (default: not defined)
process_id_file /home/tim/Scripts/motion.pid 

############################################################
# Basic Setup Mode
############################################################

# Start in Setup-Mode, daemon disabled. (default: off)
setup_mode off

###########################################################
# Capture device options
############################################################

# Videodevice to be used for capturing  (default /dev/video0)
# for FreeBSD default is /dev/bktr0
videodevice /dev/video0

# v4l2_palette allows to choose preferable palette to be use by motion
# to capture from those supported by your videodevice. (default: 8)
# E.g. if your videodevice supports both V4L2_PIX_FMT_SBGGR8 and
# V4L2_PIX_FMT_MJPEG then motion will by default use V4L2_PIX_FMT_MJPEG.
# Setting v4l2_palette to 1 forces motion to use V4L2_PIX_FMT_SBGGR8
# instead.
#
# Values :
# V4L2_PIX_FMT_SN9C10X : 0  'S910'
# V4L2_PIX_FMT_SBGGR8  : 1  'BA81'
# V4L2_PIX_FMT_MJPEG   : 2  'MJPEG'
# V4L2_PIX_FMT_JPEG    : 3  'JPEG'
# V4L2_PIX_FMT_RGB24   : 4  'RGB3'
# V4L2_PIX_FMT_UYVY    : 5  'UYVY'
# V4L2_PIX_FMT_YUYV    : 6  'YUYV'
# V4L2_PIX_FMT_YUV422P : 7  '422P'
# V4L2_PIX_FMT_YUV420  : 8  'YU12'
v4l2_palette 8

# Tuner device to be used for capturing using tuner as source (default /dev/tuner0)
# This is ONLY used for FreeBSD. Leave it commented out for Linux
; tunerdevice /dev/tuner0

# The video input to be used (default: 8)
# Should normally be set to 0 or 1 for video/TV cards, and 8 for USB cameras
input 8

# The video norm to use (only for video capture and TV tuner cards)
# Values: 0 (PAL), 1 (NTSC), 2 (SECAM), 3 (PAL NC no colour). Default: 0 (PAL)
norm 0

# The frequency to set the tuner to (kHz) (only for TV tuner cards) (default: 0)
frequency 0

# Rotate image this number of degrees. The rotation affects all saved images as
# well as mpeg movies. Valid values: 0 (default = no rotation), 90, 180 and 270.
rotate 0

# Image width (pixels). Valid range: Camera dependent, default: 352
width 640

# Image height (pixels). Valid range: Camera dependent, default: 288
height 480

# Maximum number of frames to be captured per second.
# Valid range: 2-100. Default: 100 (almost no limit).
framerate 30

# Minimum time in seconds between capturing picture frames from the camera.
# Default: 0 = disabled - the capture rate is given by the camera framerate.
# This option is used when you want to capture images at a rate lower than 2 per second.
minimum_frame_time 0

# URL to use if you are using a network camera, size will be autodetected (incl http:// ftp:// or file:///)
# Must be a URL that returns single jpeg pictures or a raw mjpeg stream. Default: Not defined
; netcam_url value

# Username and password for network camera (only if required). Default: not defined
# Syntax is user:password
; netcam_userpass value

# The setting for keep-alive of network socket, should improve performance on compatible net cameras.
# 1.0:         The historical implementation using HTTP/1.0, closing the socket after each http request.
# keep_alive:  Use HTTP/1.0 requests with keep alive header to reuse the same connection.
# 1.1:         Use HTTP/1.1 requests that support keep alive as default.
# Default: 1.0
; netcam_http 1.0

# URL to use for a netcam proxy server, if required, e.g. "http://myproxy".
# If a port number other than 80 is needed, use "http://myproxy:1234".
# Default: not defined
; netcam_proxy value 

# Set less strict jpeg checks for network cameras with a poor/buggy firmware.
# Default: off
netcam_tolerant_check off

# Let motion regulate the brightness of a video device (default: off).
# The auto_brightness feature uses the brightness option as its target value.
# If brightness is zero auto_brightness will adjust to average brightness value 128.
# Only recommended for cameras without auto brightness
auto_brightness off

# Set the initial brightness of a video device.
# If auto_brightness is enabled, this value defines the average brightness level
# which Motion will try and adjust to.
# Valid range 0-255, default 0 = disabled
brightness 0

# Set the contrast of a video device.
# Valid range 0-255, default 0 = disabled
contrast 0

# Set the saturation of a video device.
# Valid range 0-255, default 0 = disabled
saturation 0

# Set the hue of a video device (NTSC feature).
# Valid range 0-255, default 0 = disabled
hue 0


############################################################
# Round Robin (multiple inputs on same video device name)
############################################################

# Number of frames to capture in each roundrobin step (default: 1)
roundrobin_frames 1

# Number of frames to skip before each roundrobin step (default: 1)
roundrobin_skip 1

# Try to filter out noise generated by roundrobin (default: off)
switchfilter off


############################################################
# Motion Detection Settings:
############################################################

# Threshold for number of changed pixels in an image that
# triggers motion detection (default: 1500)
threshold 6000

# Automatically tune the threshold down if possible (default: off)
threshold_tune off

# Noise threshold for the motion detection (default: 32)
noise_level 32

# Automatically tune the noise threshold (default: on)
noise_tune on

# Despeckle motion image using (e)rode or (d)ilate or (l)abel (Default: not defined)
# Recommended value is EedDl. Any combination (and number of) of E, e, d, and D is valid.
# (l)abeling must only be used once and the 'l' must be the last letter.
# Comment out to disable
despeckle EedDl

# Detect motion in predefined areas (1 - 9). Areas are numbered like that:  1 2 3
# A script (on_area_detected) is started immediately when motion is         4 5 6
# detected in one of the given areas, but only once during an event.        7 8 9
# One or more areas can be specified with this option. (Default: not defined)
; area_detect value

# PGM file to use as a sensitivity mask.
# Full path name to. (Default: not defined)
; mask_file value

# Dynamically create a mask file during operation (default: 0)
# Adjust speed of mask changes from 0 (off) to 10 (fast)
smart_mask_speed 0

# Ignore sudden massive light intensity changes given as a percentage of the picture
# area that changed intensity. Valid range: 0 - 100 , default: 0 = disabled
lightswitch 90

# Picture frames must contain motion at least the specified number of frames
# in a row before they are detected as true motion. At the default of 1, all
# motion is detected. Valid range: 1 to thousands, recommended 1-5
minimum_motion_frames 3

# Specifies the number of pre-captured (buffered) pictures from before motion
# was detected that will be output at motion detection.
# Recommended range: 0 to 5 (default: 0)
# Do not use large values! Large values will cause Motion to skip video frames and
# cause unsmooth mpegs. To smooth mpegs use larger values of post_capture instead.
pre_capture 2

# Number of frames to capture after motion is no longer detected (default: 0)
post_capture 0

# Gap is the seconds of no motion detection that triggers the end of an event
# An event is defined as a series of motion images taken within a short timeframe.
# Recommended value is 60 seconds (Default). The value 0 is allowed and disables
# events causing all Motion to be written to one single mpeg file and no pre_capture.
gap 60

# Maximum length in seconds of an mpeg movie
# When value is exceeded a new mpeg file is created. (Default: 0 = infinite)
max_mpeg_time 0

# Always save images even if there was no motion (default: off)
output_all off


############################################################
# Image File Output
############################################################

# Output 'normal' pictures when motion is detected (default: on)
# Valid values: on, off, first, best, center
# When set to 'first', only the first picture of an event is saved.
# Picture with most motion of an event is saved when set to 'best'.
# Picture with motion nearest center of picture is saved when set to 'center'.
# Can be used as preview shot for the corresponding movie.
output_normal off

# Output pictures with only the pixels moving object (ghost images) (default: off)
output_motion off

# The quality (in percent) to be used by the jpeg compression (default: 75)
quality 90

# Output ppm images instead of jpeg (default: off)
ppm off


############################################################
# FFMPEG related options
# Film (mpeg) file output, and deinterlacing of the video input
# The options movie_filename and timelapse_filename are also used
# by the ffmpeg feature
############################################################

# Use ffmpeg to encode mpeg movies in realtime (default: off)
ffmpeg_cap_new on

# Use ffmpeg to make movies with only the pixels moving
# object (ghost images) (default: off)
ffmpeg_cap_motion off

# Use ffmpeg to encode a timelapse movie 
# Default value 0 = off - else save frame every Nth second
ffmpeg_timelapse 0

# The file rollover mode of the timelapse video
# Valid values: hourly, daily (default), weekly-sunday, weekly-monday, monthly, manual
ffmpeg_timelapse_mode daily

# Bitrate to be used by the ffmpeg encoder (default: 400000)
# This option is ignored if ffmpeg_variable_bitrate is not 0 (disabled)
ffmpeg_bps 500000

# Enables and defines variable bitrate for the ffmpeg encoder.
# ffmpeg_bps is ignored if variable bitrate is enabled.
# Valid values: 0 (default) = fixed bitrate defined by ffmpeg_bps,
# or the range 2 - 31 where 2 means best quality and 31 is worst.
ffmpeg_variable_bitrate 0

# Codec to used by ffmpeg for the video compression.
# Timelapse mpegs are always made in mpeg1 format independent from this option.
# Supported formats are: mpeg1 (ffmpeg-0.4.8 only), mpeg4 (default), and msmpeg4.
# mpeg1 - gives you files with extension .mpg
# mpeg4 or msmpeg4 - gives you files with extension .avi
# msmpeg4 is recommended for use with Windows Media Player because
# it requires no installation of codec on the Windows client.
# swf - gives you a flash film with extension .swf
# flv - gives you a flash video with extension .flv
# ffv1 - FF video codec 1 for Lossless Encoding ( experimental )
# mov - QuickTime ( testing )
ffmpeg_video_codec mpeg4

# Use ffmpeg to deinterlace video. Necessary if you use an analog camera
# and see horizontal combing on moving objects in video or pictures.
# (default: off)
ffmpeg_deinterlace off


############################################################
# Snapshots (Traditional Periodic Webcam File Output)
############################################################

# Make automated snapshot every N seconds (default: 0 = disabled)
snapshot_interval 0


############################################################
# Text Display
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second, %T = HH:MM:SS,
# %v = event, %q = frame number, %t = thread (camera) number,
# %D = changed pixels, %N = noise level, \n = new line,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# %C = value defined by text_event - do not use with text_event!
# You can put quotation marks around the text to allow
# leading spaces
############################################################

# Locate and draw a box around the moving object.
# Valid values: on, off and preview (default: off)
# Set to 'preview' will only draw a box in preview_shot pictures.
locate on

# Draws the timestamp using same options as C function strftime(3)
# Default: %Y-%m-%d\n%T = date in ISO format and time in 24 hour clock
# Text is placed in lower right corner
text_right %Y-%m-%d\n%T-%q

# Draw a user defined text on the images using same options as C function strftime(3)
# Default: Not defined = no text
# Text is placed in lower left corner
; text_left CAMERA %t

# Draw the number of changed pixed on the images (default: off)
# Will normally be set to off except when you setup and adjust the motion settings
# Text is placed in upper right corner
text_changes off

# This option defines the value of the special event conversion specifier %C
# You can use any conversion specifier in this option except %C. Date and time
# values are from the timestamp of the first image in the current event.
# Default: %Y%m%d%H%M%S
# The idea is that %C can be used filenames and text_left/right for creating
# a unique identifier for each event.
text_event %Y%m%d%H%M%S

# Draw characters at twice normal size on images. (default: off)
text_double off


############################################################
# Target Directories and filenames For Images And Films
# For the options snapshot_, jpeg_, mpeg_ and timelapse_filename
# you can use conversion specifiers
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number, %t = thread (camera) number,
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# %C = value defined by text_event
# Quotation marks round string are allowed.
############################################################

# Target base directory for pictures and films
# Recommended to use absolute path. (Default: current working directory)
target_dir /home/tim/Desktop

# File path for snapshots (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-snapshot
# Default value is equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d/%H/%M/%S-snapshot
# File extension .jpg or .ppm is automatically added so do not include this.
# Note: A symbolic link called lastsnap.jpg created in the target_dir will always
# point to the latest snapshot, unless snapshot_filename is exactly 'lastsnap'
snapshot_filename %v-%Y%m%d%H%M%S-snapshot

# File path for motion triggered images (jpeg or ppm) relative to target_dir
# Default: %v-%Y%m%d%H%M%S-%q
# Default value is equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d/%H/%M/%S-%q
# File extension .jpg or .ppm is automatically added so do not include this
# Set to 'preview' together with best-preview feature enables special naming
# convention for preview shots. See motion guide for details
jpeg_filename %v-%Y%m%d%H%M%S-%q

# File path for motion triggered ffmpeg films (mpeg) relative to target_dir
# Default: %v-%Y%m%d%H%M%S
# Default value is equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d/%H%M%S
# File extension .mpg or .avi is automatically added so do not include this
# This option was previously called ffmpeg_filename
movie_filename %v-%Y%m%d%H%M%S

# File path for timelapse mpegs relative to target_dir
# Default: %Y%m%d-timelapse
# Default value is near equivalent to legacy oldlayout option
# For Motion 3.0 compatible mode choose: %Y/%m/%d-timelapse
# File extension .mpg is automatically added so do not include this
timelapse_filename %Y%m%d-timelapse


############################################################
# Live Webcam Server
############################################################

# The mini-http server listens to this port for requests (default: 0 = disabled)
;webcam_port 8081
webcam_port 0

# Quality of the jpeg images produced (default: 50)
webcam_quality 80

# Output frames at 1 fps when no motion is detected and increase to the
# rate given by webcam_maxrate when motion is detected (default: off)
webcam_motion off

# Maximum framerate for webcam streams (default: 1)
webcam_maxrate 1

# Restrict webcam connections to localhost only (default: on)
webcam_localhost on

# Limits the number of images per connection (default: 0 = unlimited)
# Number can be defined by multiplying actual webcam rate by desired number of seconds
# Actual webcam rate is the smallest of the numbers framerate and webcam_maxrate
webcam_limit 0


############################################################
# HTTP Based Control
############################################################

# TCP/IP port for the http server to listen on (default: 0 = disabled)
;control_port 8080
control_port 0

# Restrict control connections to localhost only (default: on)
control_localhost on

# Output for http server, select off to choose raw text plain (default: on)
control_html_output on

# Authentication for the http based control. Syntax username:password
# Default: not defined (Disabled)
; control_authentication username:password


############################################################
# Tracking (Pan/Tilt)
############################################################

# Type of tracker (0=none (default), 1=stepper, 2=iomojo, 3=pwc, 4=generic, 5=uvcvideo)
# The generic type enables the definition of motion center and motion size to
# be used with the conversion specifiers for options like on_motion_detected
track_type 0

# Enable auto tracking (default: off)
track_auto off

# Serial port of motor (default: none)
; track_port value

# Motor number for x-axis (default: 0)
track_motorx 0

# Motor number for y-axis (default: 0)
track_motory 0

# Maximum value on x-axis (default: 0)
track_maxx 0

# Maximum value on y-axis (default: 0)
track_maxy 0

# ID of an iomojo camera if used (default: 0)
track_iomojo_id 0

# Angle in degrees the camera moves per step on the X-axis
# with auto-track (default: 10)
# Currently only used with pwc type cameras
track_step_angle_x 10

# Angle in degrees the camera moves per step on the Y-axis
# with auto-track (default: 10)
# Currently only used with pwc type cameras
track_step_angle_y 10

# Delay to wait for after tracking movement as number
# of picture frames (default: 10)
track_move_wait 10

# Speed to set the motor to (stepper motor option) (default: 255)
track_speed 255

# Number of steps to make (stepper motor option) (default: 40)
track_stepsize 40


############################################################
# External Commands, Warnings and Logging:
# You can use conversion specifiers for the on_xxxx commands
# %Y = year, %m = month, %d = date,
# %H = hour, %M = minute, %S = second,
# %v = event, %q = frame number, %t = thread (camera) number,
# %D = changed pixels, %N = noise level,
# %i and %J = width and height of motion area,
# %K and %L = X and Y coordinates of motion center
# %C = value defined by text_event
# %f = filename with full path
# %n = number indicating filetype
# Both %f and %n are only defined for on_picture_save,
# on_movie_start and on_movie_end
# Quotation marks round string are allowed.
############################################################

# Do not sound beeps when detecting motion (default: on)
# Note: Motion never beeps when running in daemon mode.
quiet on

# Command to be executed when an event starts. (default: none)
# An event starts at first motion detected after a period of no motion defined by gap 
; on_event_start value

# Command to be executed when an event ends after a period of no motion
# (default: none). The period of no motion is defined by option gap.
; on_event_end value

# Command to be executed when a picture (.ppm|.jpg) is saved (default: none)
# To give the filename as an argument to a command append it with %f
; on_picture_save value

# Command to be executed when a motion frame is detected (default: none)
; on_motion_detected value

# Command to be executed when motion in a predefined area is detected
# Check option 'area_detect'.   (default: none)
; on_area_detected value

# Command to be executed when a movie file (.mpg|.avi) is created. (default: none)
# To give the filename as an argument to a command append it with %f
; on_movie_start value

# Command to be executed when a movie file (.mpg|.avi) is closed. (default: none)
# To give the filename as an argument to a command append it with %f
; on_movie_end value

# Command to be executed when a camera can't be opened or if it is lost
# NOTE: There is situations when motion doesn't detect a lost camera!
# It depends on the driver, some drivers don't detect a lost camera at all
# Some hang the motion thread. Some even hang the PC! (default: none)
; on_camera_lost value

############################################################
# Common Options For MySQL and PostgreSQL database features.
# Options require the MySQL/PostgreSQL options to be active also.
############################################################

# Log to the database when creating motion triggered image file  (default: on)
sql_log_image on

# Log to the database when creating a snapshot image file (default: on)
sql_log_snapshot on

# Log to the database when creating motion triggered mpeg file (default: off)
sql_log_mpeg off

# Log to the database when creating timelapse mpeg file (default: off)
sql_log_timelapse off

# SQL query string that is sent to the database
# Use same conversion specifiers has for text features
# Additional special conversion specifiers are
# %n = the number representing the file_type
# %f = filename with full path
# Default value:
# insert into security(camera, filename, frame, file_type, time_stamp, text_event) values('%t', '%f', '%q', '%n', '%Y-%m-%d %T', '%C')
sql_query insert into security(camera, filename, frame, file_type, time_stamp, event_time_stamp) values('%t', '%f', '%q', '%n', '%Y-%m-%d %T', '%C')


############################################################
# Database Options For MySQL
############################################################

# Mysql database to log to (default: not defined)
; mysql_db value

# The host on which the database is located (default: localhost)
; mysql_host value

# User account name for MySQL database (default: not defined)
; mysql_user value

# User password for MySQL database (default: not defined)
; mysql_password value


############################################################
# Database Options For PostgreSQL
############################################################

# PostgreSQL database to log to (default: not defined)
; pgsql_db value

# The host on which the database is located (default: localhost)
; pgsql_host value

# User account name for PostgreSQL database (default: not defined)
; pgsql_user value

# User password for PostgreSQL database (default: not defined)
; pgsql_password value

# Port on which the PostgreSQL database is located (default: 5432)
; pgsql_port 5432


############################################################
# Video Loopback Device (vloopback project)
############################################################

# Output images to a video4linux loopback device
# The value '-' means next available (default: not defined)
; video_pipe value

# Output motion images to a video4linux loopback device
# The value '-' means next available (default: not defined)
; motion_video_pipe value


##############################################################
# Thread config files - One for each camera.
# Except if only one camera - You only need this config file.
# If you have more than one camera you MUST define one thread
# config file for each camera in addition to this config file.
##############################################################

# Remember: If you have more than one camera you must have one
# thread file for each camera. E.g. 2 cameras requires 3 files:
# This motion.conf file AND thread1.conf and thread2.conf.
# Only put the options that are unique to each camera in the
# thread config files. 
; thread /usr/local/etc/thread1.conf
; thread /usr/local/etc/thread2.conf
; thread /usr/local/etc/thread3.conf
; thread /usr/local/etc/thread4.conf

```

This way, all files that motion needs to read from or write to are in accessible locations, owned by the user. Hope this helps, good luck with it :)

---

### Post by blaede22 on 2010-10-03
Anyone gotten this to work with Ubuntu 10.04? It seems to be reporting the distance very incorrectly.

My setup:
[LIST]
[*]Ubuntu 10.04
[*]Mac Mini's built-in Bluetooth Adapter
[*]HTC EVO 4G running Android 2.2
[/LIST]

Even when my EVO is far away it reports 3,4,5,6,7, or 255. :(

---

### Post by djben75 on 2010-10-08
> **blaede22 said:**
> Anyone gotten this to work with Ubuntu 10.04? It seems to be reporting the distance very incorrectly.

My setup:
[LIST]
[*]Ubuntu 10.04
[*]Mac Mini's built-in Bluetooth Adapter
[*]HTC EVO 4G running Android 2.2
[/LIST]

Even when my EVO is far away it reports 3,4,5,6,7, or 255. :(

I am using in 10.04 with Samsung impression.
Sounds like just a strong Bluetooth connection on one device or maybe both.

---

### Post by lifelike27 on 2010-11-28
Ok, so I didn't go through all fifteen pages of replies to check if someone already asked this before, but I'm going to take the chance that no one gets annoyed.

Does this also work at start up, without an initial login? It's one of my start up applications and all, but I'm just not sure about how Ubuntu works. Whether it loads the program in the background before a user has logged in, which would lead it to login automatically, or would I have to log in the first time and then on I wouldn't until the next restart?

:popcorn:

---

### Post by Sub101 on 2010-11-28
> **lifelike27 said:**
> Ok, so I didn't go through all fifteen pages of replies to check if someone already asked this before, but I'm going to take the chance that no one gets annoyed.

Does this also work at start up, without an initial login? It's one of my start up applications and all, but I'm just not sure about how Ubuntu works. Whether it loads the program in the background before a user has logged in, which would lead it to login automatically, or would I have to log in the first time and then on I wouldn't until the next restart?

:popcorn:

If its in startup apps it will load after login, along with the Bluetooth manager.

However im sure there will be a way to alter the order so you can login with it - hopefully someone else will have the answer for how.

---

### Post by gangsterkb on 2010-12-13
i just love this application. it is very handy and now i don't have to worry that I forget that I have locked my computer.
 

 It is also nice that you can choose witch command he runs!

---

### Post by rockerZ71 on 2011-02-04
I am paired to a blackberry 8900.  When I place the phone on a desk about 10 feet away, the distance jumps up to around 10 or maybe a bit more, drops to 6 or 7, and then settles to zero.  Any ideas why?

---

### Post by pveurshout on 2011-03-02
Does anyone know what the 'Command interval' setting does? It's in the 'Locking' tab below the actual commands. The default setting is 60 seconds, but I can't figure out what difference it makes when I set it to e.g. 5 seconds.

---

### Post by lunatico on 2011-04-14
Using this on 10.04 with a Samsung Europa (GT-I5500) on channel 3 which is the OBEX Push channel.
It works most of the time but some times when I come back it fails to unlock my computer.
Any ideas?

---

### Post by kruykaze on 2011-05-28
Is it possible to have different bluetooth devices trigger diffrent actions?
thank you much

---

### Post by lunatico on 2011-06-27
> **lunatico said:**
> Using this on 10.04 with a Samsung Europa (GT-I5500) on channel 3 which is the OBEX Push channel.
It works most of the time but some times when I come back it fails to unlock my computer.
Any ideas?

Bump.
Anyone?

Someone else here using it with an Android phone?

---

### Post by nilarimogard on 2011-06-27
> **lunatico said:**
> Bump.
Anyone?

Someone else here using it with an Android phone?

It works fine here. Just make sure you set the unlocking distance to less than the locking distance or else these will conflict (if the locking distance is smaller than the unlocking distance, the computer will never unlock)

---

### Post by lunatico on 2011-06-27
> **nilarimogard said:**
> It works fine here. Just make sure you set the unlocking distance to less than the locking distance or else these will conflict (if the locking distance is smaller than the unlocking distance, the computer will never unlock)

Yeah it is... and it does work most of the time. It's just some times it won't and I'll have to turn bluetooth off and on again on the phone to get it to unlock.
Other threads I have on this:
[http://ubuntuforums.org/showthread.php?p=10945555](http://ubuntuforums.org/showthread.php?p=10945555)
[http://sourceforge.net/projects/blueproximity/forums/forum/724286/topic/4522894](http://sourceforge.net/projects/blueproximity/forums/forum/724286/topic/4522894)

---

### Post by Minime1 on 2011-07-10
I absolutely love this little app. Tried it in Mint 10 & iphone4 and it works like a charm. Now i have something to wow my Windoze friends and make them jealous.:lolflag:

Just a question regarding media playback and how to pause:
I use an excellent media streaming app called [**Subsonic**]("http://www.subsonic.org/pages/index.jsp") for all my media streaming(from within lan and outside).This app has a webgui that uses flash(JW player)to stream the media and it makes it possible to have access to your media from any pc/smart phone and from anywhere. My question regarding the script is:
Is it possible to change/write a new script that will pause this JW flash player when my laptop is locked, then resume playback when i am within proximity again and my laptop is unlocked?

Many thanks all,

---

### Post by lunatico on 2011-07-11
> **Minime1 said:**
> Is it possible to change/write a new script that will pause this JW flash player when my laptop is locked, then resume playback when i am within proximity again and my laptop is unlocked?

Most likely yes... but I'm not familiar with that application. Look through the app's documentation and find out if it's possible to control it via CLI. If it is then it can be scripted and controlled by blueproximity.

---

### Post by xc1024 on 2011-07-11
Works perfectly. Samsung E2121B. The configuration was very easy and quick. 
Some people said that the screen didn't lock - please check your distance settings AND close the configuration window. If it's open, the screen will not lock.

---

### Post by Minime1 on 2011-07-15
> **lunatico said:**
> Most likely yes... but I'm not familiar with that application. Look through the app's documentation and find out if it's possible to control it via CLI. If it is then it can be scripted and controlled by blueproximity.

Hi Lunatico,

This app is opensource and you can read all about it [here]("http://www.subsonic.org"). It has an API if anyone wants to have a look( I am not a programmer unfortunately so cant get into it).

But generally speaking, the playback is via flash in a web browser, so my question is, does this script(or any other) control(pause/resume)playback just like rhythmbox etc is being controlled by the script?

---

### Post by lunatico on 2011-07-16
> **Minime1 said:**
> 
This app is opensource and you can read all about it [here]("http://www.subsonic.org"). It has an API if anyone wants to have a look( I am not a programmer unfortunately so cant get into it).


On the API page there's a link: "Feel free to join the Subsonic App Developers group for discussions, suggestions and questions."
Join and ask them, I'm pretty sure that if it's a supported feature they'll know and come back with a simple one-liner of the command you need.

---

### Post by Minime1 on 2011-07-16
> **lunatico said:**
> On the API page there's a link: "Feel free to join the Subsonic App Developers group for discussions, suggestions and questions."
Join and ask them, I'm pretty sure that if it's a supported feature they'll know and come back with a simple one-liner of the command you need.



I may do that. Thanks

---

