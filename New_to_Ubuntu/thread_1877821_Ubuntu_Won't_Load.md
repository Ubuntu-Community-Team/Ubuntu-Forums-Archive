---
title: "Ubuntu Won't Load"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by chemphill on 2011-11-08
Hello,
    I am a brand new Ubuntu user. I just bought a computer with Ubuntu on it from Zareason. I turned it on a couple of times. It worked fine for the first two times, but when I try to turn the computer on now it just shows Ubuntu written across the screen, then it shows a bunch of text. It starts off with:

*Stopping save Kernel messages                 [OK]
*Starting Bluetooth                            [OK]

Then it continues with a bunch of other stuff that I can get if it is necessary, but one (seemingly) note worthy thing is:

*System V runlevel compatibility               [fail]

I think I have Ubuntu 11.10 installed.
I cannot use my mouse or keyboard to enter anything, however, it does recognize they are there because the computer screen leaves the blank state if I move the mouse.
Please help me get to Ubuntu!
Thanks!

---

### Post by chemphill on 2011-11-08
I turned off my computer a few times and back on. It says pretty much the same thing. I copied it all down. Here it is:

*Starting bluetooth                                          [OK]
*PulseAudio configured for per user sessions
saned disabled; edit /etc/default/saned                      [OK]
*Stopping anac(h)ronistic cron                               [OK]

*Starting anac(h)ronistic cron
     *Stopping anac(h)ronsitic cron                          [OK]
fsck from util-linux 2.19.1
/dev/sda2: clean, 15093/60014592 files, 4690853/240037632 blocks
Skipping profile in /ect/apparmor.d/disable: usrbin.firefox  [OK]
    *Starting AppArmor profiles 
Speech-dispatcher disabled; editt/default/speech-dispatcher
Checking for running unattended upgrades:
    *Stopping Failsafe Boot Delay                            [OK]
    *Stopping System V initialisation compatibility          [OK]
    *Starting System V runlevel compatibility                [OK]
    *Stopping automatic crash report generation            [fail]
    *Starting eCryptfs                                       [OK]
    *Starting restore sound card(s') mixer state(s)          [OK]
    *Starting Light DM Display Manager                       [OK]
    *Starting save kernel messages                           [OK]
    *Starting ACPI Daemon                                    [OK]
    *Starting CPU interrupts balancing Daemon                [OK]
    *Stopping eCryptfs                                       [OK]
    *Starting  anac(h)ronistic cron                          [OK]
    *Starting regular background program processing daemon   [OK]
    *Starting deferred execution scheduler                   [OK]
    *Stopping restore sound card(s') mixer state(s)
mountall: Disconnected from Plymouth                         [OK]


Just as a note. Those OKs are in the general area I had a hard time following them across the screen.
Any thoughts would greatly be appreciated!

---

### Post by critin on 2011-11-08
> I cannot use my mouse or keyboard to enter anything, however, it does  recognize they are there because the computer screen leaves the blank  state if I move the mouse.What does this mean exactly?  What do you see?

Did you buy the machine locally, or have you called their support?    You said you only turned it on a few times, were you ever able to get into the system at all?  Did you look around and do anything?  How do you turn it off, go to 'shutdown' or hit the power button?

---

### Post by chemphill on 2011-11-08
I have been in the system. I used LibreOffice and FireFox. I bought the machine from ZaReason. It is a company located some where in California. I have emailed them, but I was hoping some one here might know how to fix the problem sooner. When I could actually get to the Ubuntu desktop I turned it off once with the power button on the computer and once by hitting shutdown on the desktop. When I started the computer up today it started to load Ubuntu (It said Ubuntu across the screen), then it took me to a black screen with white letters. In my previous post I posted what all of those letters said. I cannot input anything into the computer. There is also no mouse shown on the screen (But there isn't anything to click on in the first place). After a period of time the screen goes all black (like a screensaver). If I move my mouse then the "screensaver" will go away. When it brought me to the letters on the black screen it obviously wasn't going to change anytime soon so I pushed the power button on the computer to turn it off. I did this several times in vain hope that it wouldn't do the same thing again.
I hope that made since and it answered your questions.

---

### Post by critin on 2011-11-08
I can't help you, it will take someone who knows the insides of ubuntu --I'm sorry.  It's not a real good idea to shut a computer down with the power button.  You should always use the shut down link on the screentop, but you didn't have any choice. 

It sounds like you do have the blank screensaver.  Try hitting the 'window' or 'meta' button on the keyboard.  I know you said it didn't work, but it did earlier in office.  I don't know what your keyboard is like, the key may not identify itself.  Are you familiar with Windows keyboard?  You know the key that has the windows logo on it?  On mine it's next to the left ctr button.  Try that and see if it brings the menu up.

Otherwise, hopefully someone smarter than me will help you.  :(

---

### Post by Phillip Carver on 2011-11-08
Hi,

I'm also new to Ubuntu, and I'm getting the same boot issue as chemphill.  The boot status messages (image attached) are the same as chemphill's from the second post in this thread with the obvious exception of different drives/partitions indicated.

This happens when I try to boot into Ubuntu normally, but if I boot into Recovery Mode then tell it to continue booting normally, I'm able to properly boot into Ubuntu, login, do whatever.  I'm currently booting Windows 7 from my primary SSD (sda) and Ubuntu off of a second SSD (sdb).  The boot loader (GRUB2 on sda) appears to be setup perfectly, allowing me to boot into either at will.

System:
EVGA E760 main board
Intel Core i7 930
2x Nvidia GTX 480
Windows 7 drive (sda): Samsung 470 256 GB
Ubuntu drive (sdb): Intel X25-M 80 GB
4 HDDs, 2 in a RAID 0 array, 2 in a RAID 1 array

Again, all of the hardware works fine once I'm in the system...it just fails to boot properly.

I apologize for the poor image quality...cell phone shot...

---

### Post by chemphill on 2011-11-09
Phillip Carver,
You said that you booted in recovery mode and then told it to boot normally. If you (or someone else) could tell me how to enter recovery mode and start Ubuntu from there, it would be helpful. At least I could use Ubuntu that way until someone suggests a different way. :)

---

### Post by Phillip Carver on 2011-11-09
> **chemphill said:**
> Phillip Carver,
You said that you booted in recovery mode and then told it to boot normally. If you (or someone else) could tell me how to enter recovery mode and start Ubuntu from there, it would be helpful. At least I could use Ubuntu that way until someone suggests a different way. :)
chemphill,
I believe that if you hold shift while booting -- I'm guessing just after your system POSTs -- you'll get an option to boot into recovery.  I dual-boot, so I automatically get the GRUB2 menu on startup to select which OS to boot.


Also, I installed the 32-bit version of Ubuntu 11.10, and it booted up fine after restart.  I ran into additional issues after it booted, but those should be fixable.

---

### Post by chemphill on 2011-11-09
While I was trying to get into recovery by holding shift, the letters that say Ubuntu came up and it went ahead and booted normally. I didn't select anything. I was still holding the shift key down Ubuntu was loading and the log on screen popped up!:D

I probably will not turn my computer off for a very long time or at least until somebody can tell me what was happening.

I will still keep an eye on this thread just in case somebody that knows what was going on can tell me how to prevent it or what was happening.

Thanks to all :D ,
chemphill

---

### Post by critin on 2011-11-09
Have either of you tried searching the forums and checking the stickies?  I know others have had the same problem, you may find the answers there.

---

### Post by critin on 2011-11-11
> I probably will not turn my computer off for a very long time 

I know what you mean, I leave mine on too.  :P  Glad you got the right advice...

---

