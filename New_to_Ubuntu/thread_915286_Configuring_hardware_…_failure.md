---
title: "Configuring hardware … failure"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Suko on 2008-09-09
Hi
I’ve been involved in computers since around 1987. I guess that in that time I have made about perhaps 5 - 10 attempts to wean myself of Microsoft by installing various flavours of Linux.  As I recall I have only succeeded on 3 or 4 occasions. The others have all been failures due in the main to driver/hardware ‘problems’ and my impatience at not being able to easily find answers! 

I thought I would give Linux one more try but this time try being a little bit less impatient! So I’ve built a PC from bits I have lying around, the specs are as listed in my sig.

I am now attempting to install Ubuntu 7.10 from a DVD.

On the two occasions that I have tried this evening the install has failed at the following point …
Installing system 94%
Configuring hardware …
At this stage the screen freezes, the HD light remains on constantly, there is no DVD activity and the keyboard and mouse become inoperable.
A system reset is then the only option.

Any comments, help or observations would be most appreciated.

Suko

---

### Post by egalvan on 2008-09-09
OK a little more info will go a long way...

First, is there a reason you are using an older version?

Second, how did you aquire the DVD? Purchased it, did you download it yourself, from a friend?

Third, some system specs to help us along.

Fourth, have you run any tests on the hardware.

Fifth, did you run the "check cd for errors" option on the DVD.

And from the original post, I would guess either bad RAM, or bad media.
Although the 94% makes me lean towards bad media.


Ernest

---

### Post by robert shearer on 2008-09-09
Hi and welcome,  I have only been involved with computers since 2007 so take my hat off to you and your persistence trying to install linux.
Lets hope Ubuntu is the one.

From my limited experience here a a few suggestions that have worked for me (no doubt some wiser heads will post too with more advanced troubleshooting)

1  Get the latest version of Ubuntu  Hardy 8.04.1   as hardware detection and configuration improves with each release. 

2 on older slower hardware the configuration can take a while. I have had it take 30 minutes plus on a P3. Wait.

3 When you start the install make sure that your broadband device is connected. The installer should find and configure it then sync with a time server. Possibly if additional software is needed at the configuration stage it can then be downloaded by the installer. I have noticed this when installing eAR-OS a Ubuntu derivative.

Hope this is a start. All the best.

---

### Post by Suko on 2008-09-10
I ake your point about the older version, it came with a recent magazine. I am now using the latest version. I have used that to check both my RAM and the DVD, no problems found. The system specs are as in my sig.

I did see a message refering to:
260.107890 BufferI/O errors on drive fD0
I installed a floppy and checked the BIOS settings - stil failed at 94%
I swapped out the HD - still failed at 94%
I am using a USB2 DVD drive and the last message that I managed to catch before the PC locked up was relating to "firewire support for CD ROM".
I tried an Hitachi DVD IDE drive - still failed at 94%
I have tried leaving the PC at 94% for an hour - while I washed the car - still no luck.
The PC is connected to my broadband connection and the message says that time synch has taken place.
As far as I am aware all my hardware is fine - I guess I could try removing the Sound Card ... but that firewire message puzzles me.
I will try installing again and see if I can catch the message.
But having tried to install perhaps 7 times today I think thaat I will try again tomorrow!

Suko

---

### Post by phidia on 2008-09-10
Particulary given the hardware you have helpfully listed I don't see any reason that 7.10 wouldn't install. 
Since you stated that you put the system together from parts you had-you may want to recheck connections and perhaps check the ram too.
There are some hits on "Installing system 94% Configuring hardware &#8230;" but unfortunately not anything that is resolved. 
I think you will need to pay close attention to the error messages and/or when it gives the above quoted message open a tty (Alt+Ctrl+F1) and enter "dmesg" perhaps that will output more usable info. Note: If Alt+Ctrl+F1 doesn't open another interface try F2 thru F7 in place of F1.

---

### Post by robert shearer on 2008-09-10
> **Suko said:**
> I ake your point about the older version, it came with a recent magazine. I am now using the latest version. I have used that to check both my RAM and the DVD, no problems found. The system specs are as in my sig.

I did see a message refering to:
260.107890 BufferI/O errors on drive fD0
I installed a floppy and checked the BIOS settings - stil failed at 94%
I swapped out the HD - still failed at 94%
I am using a USB2 DVD drive and the last message that I managed to catch before the PC locked up was relating to "firewire support for CD ROM".
I tried an Hitachi DVD IDE drive - still failed at 94%
I have tried leaving the PC at 94% for an hour - while I washed the car - still no luck.
The PC is connected to my broadband connection and the message says that time synch has taken place.
As far as I am aware all my hardware is fine - I guess I could try removing the Sound Card ... but that firewire message puzzles me.
I will try installing again and see if I can catch the message.
But having tried to install perhaps 7 times today I think thaat I will try again tomorrow!

Suko


Hmmm, here is a recent post that may be worth checking

[http://ubuntuforums.org/showthread.php?t=914978](http://ubuntuforums.org/showthread.php?t=914978)

Could be video card related ?  Perhaps try installing without the card and using onboard video as the above post says then add the card and enable the drivers?

Once you're installed this may be handy for set up/driver installation...

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

